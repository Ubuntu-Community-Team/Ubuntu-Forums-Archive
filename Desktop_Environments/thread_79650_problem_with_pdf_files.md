---
title: "problem with pdf files"
date: 2005-10-20
forum: Desktop Environments
---

### Post by paddy2706 on 2005-10-20
hello ppl,

i have a problem: i cannot convert any pdf file to a graphics, neither pdf2ps works, nor thumbpdf nor convert.
also adobe acrobat doesn't start up at all. do you have any idea, where to find the problem? newest gs version is installed...

or: with what function does nautilus create the pdf thumbs? I just need a way to get there...

btw: im running a clean breezy up-to-date with backports, universe and multiverse.
kernel: 2.6.12-9
anything else u need to know?

regards,

paddy2706

---

### Post by rmjokers on 2005-10-20
What type of graphic are you trying to create?  Also, what is going wrong with the programs you mentioned?  When I want to create a high res image from a PDF, I usually use pdftoppm.  Give it the first page, last page, and a DPI value and it gives you a bunch of portable pixmap images.  You can then use other programs (ppmtojpeg or ppmtobmp for instance) to convert to a normal format.

---

### Post by paddy2706 on 2005-10-21
i tried to get a png or gif from ps. pdfs are single paged. but its even not possible to create a ps from pdf
```

gs -q -dNOPAUSE -dBATCH -dSAFER -sDEVICE=pswrite -sOutputFile=051011-1_Protokoll.ps -c save pop -f 051011-1_Protokoll.pdf
Segmentation fault

```

---

