---
title: "how to create a pdf file from gnome?"
date: 2004-12-06
forum: Desktop Environments
---

### Post by giorsat on 2004-12-06
Hi.  scanned a document via gimp and now I'm wondering the quickiest graphical wayto crete a pdf file from it. It seems that gimp can't' create pdf files. what workaround can I use. In mandrake kprinter did the job but in ubuntu there is no gnomeprinter

---

### Post by Sniffer on 2004-12-06
I think openoffice will do the trick :)

---

### Post by burlap on 2004-12-06
Openoffice is one solution, but you can also use some oher tools:

1. Print your image to file (file.ps) and then run (in terminal) - you need gs-common package for this one
```
ps2pdf file.ps file.pdf
```
2. Make tiff image and run in terminal - you need libtiff-tools package for this one:
```
tiff2pdf file.tiff
```
Use man to get more options.

---

