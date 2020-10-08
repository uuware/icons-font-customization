# icons-font-customization
A collection of over 33,000 high-quality free svg icons and tools for generating customized icon font. All icons are completely free for personal or business requirements.
[See all icons](https://uuware.github.io/icons-font-customization/dist/)

---

All icons collected here are completely free for your personal or business requirements.<br>
You can use this tool to combine / generate your own icon webfonts for your project from different sources.

# How to use (for NPM projects)
## 1, Install the project
Actually there are two projects that can work for you.<br>
- 1.1, This project (`icons-font-customization`) contains more than 26M of svgs data. You can install this project if you don't mind the size then it works locally and copies icons quickly.<br>
`nmp install icons-font-customization`<br>
- 1.2, You can install a sub project called `icons-font-command`, which doesn't contain any icons and is very small. `icons-font-command` copies icons from Github's repository of `icons-font-customization` remotely. If you don't have too many icons for your font then you can choose this approach<br>
`nmp install icons-font-command`<br>
    *Project `icons-font-customization` contains `icons-font-command`. So either of them uses same command to generate font.*<br>
## 2, Choose your icons<br>
Open [See all icons](https://uuware.github.io/icons-font-customization/dist/), then you can view all icons.<br>
  You can change color, background color, size for icons. Also you can search and click them to choose.<br>
  Click button "Populate Configuration" to output configuration string.<br>
## 3, Copy file "icons-font.config.js" from root of `icons-font-command` to the root of your project. And paste the string from step 2 to this file.<br>
Also you can run command `icons-font-command --copyconfig` to copy "icons-font.config.js" to your current folder(where you are running this command)<br>
As a sample, the final structure should be (Don't use this sample but copy icons-font.config.js from root of `icons-font-command` please):<br>
```javascript
module.exports = {
  fontName: 'i-font',
  outputPath: 'dist/sample/',
  outputName: 'i-font', /* automatically add font extension to it  */
  startChar: 10000, // unicode start number
  icons: [
     /* copy svg from icons-font-customization locally or remotely */
    { path: 'font-awesome/brands/apple.svg', name: 'fa-apple' },
    ...
     /* download svg from any other websites */
    { path: 'https://raw.githubusercontent.com/fontello/awesome-uni.font/29d4e3ff028fc850a21b5eaafde0a83f22f59cf1/src/svg/amazon.svg', name: 'fa-amazon' },
  ],
  fontType: {
    'woff2': true,
    'woff': true,
    'ttf': true,
    'eot': false,
    'svg': false,
  },
  cssTemplate: 'copy from icons-font.config.js...',
  htmlTemplate: 'copy from icons-font.config.js...',
}
```
## 4, Run command "icons-font-command" in terminal to generate font:
`icons-font-command -- config the_path_to_icons-font.config.js`<br>
  If the file name is "icons-font.config.js" and located at the folder where you are running the command, then run it directly without any parameter. <br>
`icons-font-command`<br>
## 5, Open sample.html at output folder to confirm the result and include the icon-style.css in your html to use those icons font.

# Compatibility
- WOFF2: Chrome 36, Firefox 39, Opera 23, Safari 10, IE no support, Edge 14<br>
	WOFF File Format 2.0. WOFF2 is the next generation of WOFF. The WOFF2 format offers a 30% average compression gain over the original WOFF. <br>

- WOFF: Chrome 5, Firefox 3.6, Opera 11.10, Safari 5.1, IE 9, Edge 12<br>
	Web Open Font Format. WOFF is basically OTF or TTF with metadata and compression supported by all major browsers.<br>
	It is the result of collaboration by the Mozilla Foundation, Microsoft, and Opera Software. Because fonts are compressed, they load faster.<br>

- TTF: Chrome 4, Firefox 3.5, Opera 10, Safari 3.1, IE 9, Edge 12<br>
	TrueType Font. This format has been supported by all major browsers, but TTF fonts work in IE 9 and later only when the embedding bits are set to installable.<br>

- EOT:Chrome no support, Firefox no support, Opera no support, Safari no support, IE 6-11<br>
	Embedded OpenType. It’s the only format that IE8 and below will recognize when using @font-face.<br>

- SVG font: Chrome 4-37, Firefox no support, Opera 10-24, Safari 3.2-14, IE/Edge no support<br>
	Scalable Vector Graphics font. SVG fonts are always uncompressed and the only one allowed by version 4.1 and below of Safari for iOS (iPhone, iPad).<br>

## Suggestions:
- 1, use WOFF2 for major browsers except IE;<br>
- Or: 2, use WOFF for major browsers and IE 9~, Edge 12~<br>
- Or: 3, combine WOFF2 with TTF for IE8~<br>
     *All 1, 2, 3 needs this code in HTML: `<i class="ifc-icon icon_name"></i>`*<br>
 - Or: 4, IE6-7 requires alternate CSS: Because '.css_class_name:before (not double-colon){ content: "" }' in css is only supported from IE8, so it needs different code in html: <i class="icon ifc-icon">&#x66;(icons code)</i><br>

# Contacts
Bug reports & Questions & Suggestion: [Issue tracker](https://github.com/uuware/icons-font-customization/issues)

# Contribute
How to add an new wonderful svg icons project?<br>
## If you are the owner of a svg icons project and want to share it to others, then I'm very happy to add it if you send the request to me.<br>
## If you want to add for your local development, then you can do like this:<br>
-  1. Download or Clone this project https://github.com/uuware/icons-font-customization.git<br>
-  2. Create a new folder under /dist/svgs, based on your project name. For example, here we call it new-project, so the new folder should be /dist/svgs/new-project.<br>
-  3. Add a json file to describe the information of the project and a license file.<br>
  The sample json file structure (confirm files in existing folders):<br>
-  4. Add sub folder (svgs or whatever) and copy svgs to /dist/svgs/new-project/svgs<br>
-  5. Run cmd "icons-font-command --maintain" to optimize svgs and create demo page.<br>
-  6. Then you can use your new svg icons as same as all others.<br>

# License
- All code (all files, except svgs, fonts) is distributed under MIT license.<br>
- All svgs and fonts are distributed under their primary licenses.<br>
See information for credits & links to homepages in individual folders under /dist/svgs. This information is also included in generated css file.<br>
All used trademarks, brands and/or names are the property of their respectiveowners. The use of these trademarks, brands and/or names does not indicateendorsement of the property holder by us, nor vice versa.<br>

# Known issues:
- 1, It seems that svgs with fill-rule="evenodd" do not work correctly<br>
Currently if svgs have fill-rule="evenodd" then they lose some shapes when change to font. I havn't found any way to do so easily. So if a icon seems weird, just skip to use it.
- 2, Some icons are reduplicated.<br>

# Donation
The main contribution belongs to the elites who created these elves. Please encourage and reward them a cup of coffee!
