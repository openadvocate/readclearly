OPENADVOCATE READCLEARLY DEVELOPER DOCUMENTATION

# INSTALLATION

ReadClearly is available as an external JavaScript library that can be
installed on any website. To install ReadClearly, follow the steps
below:

## Step 1

Include the ReadClearly JavaScript file. Add the following line to the
`<HEAD>` tag on the page where you would like to use ReadClearly:

```
<SCRIPT type="text/javascript"
  src="http://writeclearly.openadvocate.org/oarc/oarc.js">
</SCRIPT>
```

## Step 2

Initialize ReadClearly. Add the following JavaScript code to either
the `<HEAD>` tag or the `<BODY>` tag. If you add it to the `<HEAD>`
tag, be sure to place it after the line you added in step 1.

```
<SCRIPT type="text/javascript">
  $(function () {
    OARC.init({autoActivate}, {location}, {theme}, {footnotes}, {glossary});
  });
</SCRIPT>
```

Replace `{autoActivate}`, `{location}`, `{theme}`, and `{glossary}`
with the desired configuration.

Following are the available configuration options:

`{autoActivate}`: Specifies whether the glossary items should be
automatically activated. If not activated automatically, glossary
items will not be shown until the visitor manually turns them
on. Possible values: true, false

`{location}`: Specifies the location of the widget that allows the
visitor to turn ReadClearly on and off. Possible values: 'top-left',
'top-right', 'bottom-left', 'bottom-right'

`{theme}`: Specifies the color scheme of ReadClearly. Possible values:
'default', 'neutral'

`{footnotes}`: If true, glossary items are also inserted as footnotes
at the end of the content. Possible values: true, false

`{glossary}`: The name of the glossary to use. For available options,
see http://openadvocate.org/readclearly/.  Omit this parameter to use
the latest English edition.

Example code:

```
OARC.init(true, 'top-left', 'neutral', '2016-08-22-ES');
```

## Step 3

Mark up content. In order to help ReadClearly identify the actual
content, either add a <div> wrapper around the main content in your
page as below, or add the 'openadvocate-content' CSS class to an
already existing wrapper element. This step is not required, but will
enhance the user experience and minimize incompatibility issues.

```
<div class="openadvocate-content">
  {main content}
</div>
```


# CUSTOM GLOSSARIES

In addition to the glossaries offered by ReadClearly, you have the
option to use glossaries contributed by other users, or contribute
your own. Contributed glossaries can be found in our GitHub
repository: https://github.com/openadvocate/readclearly

To use one of the contributed glossaries in our GitHub repository,
simply provide the name of the subdirectory in which the glossary
resides in the 'glossary' parameter as described above. For example,
to use the glossary residing in the 'spanish-common' subdirectory,
provide its name when initializing the ReadClearly as follows:

```
OARC.init(true, 'top-left', 'neutral', 'spanish-common');
```

If you wish to contribute your own glossary, please issue a pull
request in our GitHub repository. Please follow these guidelines when
creating your own glossary:

 - Fork the ReadClearly repository.
  - Choose a descriptive name for your glossary. The name should only contain
    letters, numbers, and hyphens. Choose a name that is not already used.
  - Create a subdirectory with the name you chose for you glossary.
  - Create the info.yml file in your directory. This file should be in [YAML](https://en.wikipedia.org/wiki/YAML)
    format, and should contain the following attributes:
     - name: A human readable name for the glossary.
     - author: The name of the author. This may be your personal name or your
       organization's name.
     - description: A sentence describing the content of the glossary.
  - Create the glossary.csv file. This file should be in [CSV](https://en.wikipedia.org/wiki/Comma-separated_values)
    format, containing two columns: 'word' and 'definition'. The 'word' column
    should contain the word or expression for which you are providing 
    an explanation. The 'definition' column should contain the text that will be
    shown to the user. Use one row per expression, and place column headers
    in the first row. See existing glossaries for example.
  - Commit your new directory, and issue a pull request. 
  - Once your glossary has been merged, you can provide your glossary's name
    in the 'glossary' parameter when initializing ReadClearly.

# REQUIREMENTS

ReadClearly relies on jQuery. Be sure to insert the jQuery library
before the line in step 1.


# TROUBLESHOOTING

In order to enable popup glossary items in the website content,
ReadClearly adds markup to the HTML structure of the page. This may
cause incompatibility issues in some case. For instance, it may cause
JavaScript code inside the page content to run multiple times. To
minimize the chances of such issues, try to avoid placing any script
or embedded elements inside the ReadClearly wrapper element.

http://openadvocate.org/readclearly
