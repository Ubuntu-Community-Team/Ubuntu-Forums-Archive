---
title: "how do I print a pdf file?"
date: 2009-02-21
forum: General Help
---

### Post by nicol_bolas on 2009-02-21
A command or a program that will print a PDF file to my printer.

I am using Cups

Thx


Solution:
Install standard ubuntu pdf viewer (evince).

---

### Post by paydaydaddy on 2009-02-21
I do not understand why this would be a problem. On my computer I opent the .pdf file, click"file" in the upper left corner, choose "print". Does your printer work with other documents? Do you have the print option when you open the pdf? More info about the problem you are having would help.

---

### Post by Klaue on 2009-02-21
I suppose you mean from console?
First, convert it to postscript:
```
pdftops <pdf-file> temp.ps
```
then print it
```
lpr temp.ps
```
or
```
lpr -P <printername> temp.ps
```
and delete the temp file

(I'm not sure if pdftops is standard.. if not, get the package poppler-utils

---

### Post by nicol_bolas on 2009-02-22
This just prints temp.ps file as if it were a text file which is gibberish.

Is there a program that prints PDF files?

---

### Post by Klaue on 2009-02-22
> **nicol_bolas said:**
> This just prints temp.ps file as if it were a text file which is gibberish.
then your printer does not understand postscript. try this:
```
pdftops <pdf-file> temp.ps
gs -dSAFER -dNOPAUSE -sDEVICE=deskjet -sOutputFile=\|lpr temp.ps
```


Or just print it through the GUI as paydaydaddy said

---

### Post by steveneddy on 2009-02-22
Open the file with Adobe Reader 8 and print the file.

Easy.

Have you installed acroread?

```
sudo apt-get install acroread
```

---

### Post by Klaue on 2009-02-22
> **steveneddy said:**
> Open the file with Adobe Reader 8 and print the file.

Easy.

Have you installed acroread?

```
sudo apt-get install acroread
```

The standard ubuntu pdf viewer (evince) would also work, that's why I think he means through console, not GUI

---

### Post by steveneddy on 2009-02-22
> **Klaue said:**
> The standard ubuntu pdf viewer (evince) would also work, that's why I think he means through console, not GUI

He said command or program in the original post.

You are correct, evince or Adobe Reader 8 should work very well.

If he is coming from the Windows world, he may feel more comfortable with AR8.

---

### Post by nicol_bolas on 2009-02-24
> **Klaue said:**
> The standard ubuntu pdf viewer (evince) would also work, that's why I think he means through console, not GUI

This works, thank you all for your help

---

