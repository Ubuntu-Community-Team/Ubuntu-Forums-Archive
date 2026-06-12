---
title: "Character encoding with pdftotext utility"
date: 2009-04-12
forum: General Help
---

### Post by kaibob on 2009-04-12
I use the pdftotext utility to convert PDF files to text files. Often, the PDF files are of web pages created with cups-pdf. 

This works fine except that the text files created by pdftotext occasionally contain small boxes with letters inside (see sample screenshot below). I spent some time googling this issue but can't seem to find anything. I assume but don't know that this is an issue with character encoding.

The pdfttotext utility contains the following option:

> -enc encoding-name
Sets the encoding to use for text output.  The encoding-name must be
defined with the unicodeMap command (see xpdfrc(5)).   The  encoding
name  is  case-sensitive.   This  defaults  to  "Latin1" (which is a
built-in encoding).  [config file: textEncoding]

Is there any encoding that will get rid of the small boxes or am I completely off base as to the cause of this problem. The web pages are in English, and I don't need any extended characters.

As an aside, I use the pdftotext utility in a shell script (see code snippet below). As an alternative to character encoding, is it possible to filter out the unwanted characters with sed?

```
STRINGMATCH=$(pdftotext -q -layout "$FILE" - | tr -s ' ' | fgrep -i -m 1 "$WORDONE")
```

Thanks.

EDIT:

I did a bit more research and found a page suggesting the following, which appears to work:

```
tr -d '\001-\010\013-\037\177-\377'
```

---

