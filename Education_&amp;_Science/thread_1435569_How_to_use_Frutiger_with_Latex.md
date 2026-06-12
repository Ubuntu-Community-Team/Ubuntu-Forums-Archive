---
title: "How to use Frutiger with Latex?"
date: 2010-03-21
forum: Education &amp; Science
---

### Post by RubVer on 2010-03-21
Hello,

I recently switched from Microsoft Word on Windows to Latex on Ubuntu.

I have the *.otf files of Frutiger LT. I would like the titles in my Latex document to have the font "FrutigerLTStd-BlackCN" (Linotype Frutiger Standard Black Condensed.)

The instructions on [http://www.lcdf.org/type/otftotfm.1.html](http://www.lcdf.org/type/otftotfm.1.html) told me to do:
[FONT=Courier New]otftotfm -a -e texnansx FrutigerLTStd-BlackCn.otf -fkern -fliga LY1--FrutigerLTStd-BlackCn[/FONT]
So I did that and everything went well. However, then I need to create a ".fd" file or something, but I don't understand what it is saying, and it doesn't say where to put that ".fd" file...

Please help me!

[LIST]
[*]What should the .fd file contain?
[*]Where should I put it?
[*]How can I use the font from my Latex file?
[/LIST]
Thanks!

Robert

---

### Post by frabjous on 2010-04-25
Installation of new fonts for use with regular LaTeX or pdfLaTeX is a real pain. I'd suggest trying XeLaTeX with the [fontspec](http://ctan.org/pkg/fontspec) package--this will allow you to use any OpenType or TrueType font installed installed on your system easily with an almost-identical source file.

---

