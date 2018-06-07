# unfoldingWord translationNotes

This is the repository for the unfoldingWord translationNotes (tN) resource.

## Description

unfoldingWord tN are open-licensed exegetical notes that provide historical, cultural, and linguistic information for translators. It provides translators and checkers with pertinent, just-in-time information to help them make the best possible translation decisions.

## Editing the tNs

To edit the tN files there are three options:

* Use LibreOffice (Recommended)
* Use a text editor on your computer
* Use the online web editor in DCS

Each of these options and there caveats are described below.

The first two options require you to clone the repository to your computer first. You may do this on the command line or using a program such as SmartGit. After making changes to the files you will need to commit and push your changes to the server and then create a Pull Request to merge them to the `master` branch.

### Editing in LibreOffice

This is the recommended way to edit the TSV files. You may [download LibreOffice](https://www.libreoffice.org/download/download/) for free.

After you have the file on your computer, you may open the respective TSV file with LibreOffice. Follow these notes on the Text Import Screen:

* Set "Separated by" to "Tab"
* Set "Text Delimiter" to blank, you will need to highlight the character and use backspace or delete to remove it

It should look like this:

![](https://cdn.door43.org/assets/img/tn/LibreOfficeTextImport.png)


When you are done editing, click Save and then select "Use Text CSV Format" on the pop up dialogue. Note that even though it says CSV, it will use tab characters as the field separators.

**Note:** Other spreadsheet editors **should not** be used because they will add or remove quotation marks which will affect the notes negatively.

### Editing in a Text Editor

You may also use a regular text editor to make changes to the files.

**Note:** You must be careful not to delete or add any tab characters when editing with this method.

### Editing in DCS

If you only need to change a word or two, this may be the quickest way to make your change. See the [protected branch workflow](https://help.door43.org/en/knowledgebase/15-door43-content-service/docs/46-protected-branch-workflow) document for step by step instructions.

**Note:** You must be careful not to delete any tab characters when editing with this method.

## Structure

The tN are structured as TSV files to simplify importing and exporting into various formats for translation and presentation. This enables the tNs to be keyed to the original Greek and Hebrew text instead of only a Gateway Language translation.

### TSV Format Overview

A Tab Separated Value (TSV) file is like a Comma Separated Value file except that the tab character is what divides the values instead of a comma. This makes it easier to include prose text in the files because many languages require the use of commas, single quotes, and double quotes in their sentences and paragraphs.

The tNs are structured as one file per book of the bible and encoded in TSV format, for example, `01-GEN.tsv`. The columns are `Book`, `Chapter`, `Verse`, `ID`, `SupportReference`, `OrigQuote`, `Occurrence`, `GLQuote`, and `OccurrenceNote`.

### tN TSV Column Description

The following lists each column with a brief description and example.

* `Book` - USFM book code name (e.g. `TIT`)
* `Chapter` - Chapter number (e.g. `1`)
* `Verse` - Verse number (e.g. `3`)
* `ID` - Four character **alphanumeric** string unique *within* the verse for the resource (e.g. `swi9`)
  * This will be helpful in identifing which notes are translations of the original English tNs and which notes have been added by GLs.
  * The Universal ID (UID) of a note is the combination of the `Book`, `Chapter`, `Verse`, and `ID` fields. For example, `tit/1/3/swi9`.
    * This is a useful way to unambiguously refer to notes.
    * An [RC link](http://resource-container.readthedocs.io/en/latest/linking.html) can resolve to a specific note like this: `rc://en/tn/help/tit/01/01/swi9`.
* `SupportReference`
  * Normally a link to a supporting reference text or blank
  * This will usually be a link to translationAcademy, like `rc://*/ta/man/translate/figs-metaphor`
* `OrigQuote` - Original language quote (e.g. `ἐφανέρωσεν ... τὸν λόγον αὐτοῦ`)
  * Software (such as tC) should use this for highlighting terms rather than the `GLQuote`
  * Three periods (...), forming an ellipsis, indicates that the quote is discontinuous, software should interpret this in a non-greedy manner
* `Occurrence` - Specifies which occurrence in the original language text the entry applies to.
  * `-1`: entry applies to every occurrence of OrigQuote in the verse
  * `0`: entry does not occur in original language (for example, "Connecting Statement:")
  * `1`: entry applies to first occurrence of OrigQuote only
  * `2`: entry applies to second occurrence of OrigQuote only
  * etc.
* `GLQuote` (OPTIONAL) - Gateway language quote (e.g. `he revealed his word`)
  * Software (such as tC) should disregard this field.
  * This field is a reference text for GL translators
  * For certain notes, this field represents the display text for notes that do not relate to a specific word or phrase in the text. There are two such cases in the tN:
      * "Connecting Statement:" and
      * "General Information:"
  * GL translations teams **should not translate** this column. They do need to provide a translation of the above 2 statements.
* `OccurrenceNote` - The Markdown formatted note itself. For example, `Paul speaks of God's message as if it were an object that could be visibly shown to people. Alternate translation: "He caused me to understand his message" (See: [[rc://en/ta/man/translate/figs-metaphor]])`
  * The text should be Markdown formatted, which means the following are also acceptable:
    * Plaintext - if you have no need for extra markup, just use plain text in this column
    * HTML - if you prefer to use inline HTML for markup, that works because it is supported in Markdown

## GL Translators

To learn how to translate these notes please see the [Translate the translationNotes](http://gl-manual.readthedocs.io/en/latest/gl_translation.html#gltranslation-transtn) article in the [Gateway Languages Manual](http://gl-manual.readthedocs.io/).

## License

See the [LICENSE](https://git.door43.org/Door43/tn-en/src/master/LICENSE.md) file for licensing information.
