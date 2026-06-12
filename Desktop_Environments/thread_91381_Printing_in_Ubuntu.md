---
title: "Printing in Ubuntu"
date: 2005-11-17
forum: Desktop Environments
---

### Post by mamato on 2005-11-17
Hi, I hope this is the right forum for asking this. When I use M$ XP, I usually use FinePrint for helping me to print. It can adjust the layout of paper, so we can print 4 pages in 1 paper, etc. Is there any ways to do like that in GNU/Linux? 
Thanks for helping :)

---

### Post by RikoW on 2005-11-17
If you have a Postscript (.ps) or pdf file, you can use psnup or pdfnup, respectively, to put several pages on one sheet of paper.  For example:

```
pdfnup --nup 2x2 paper.pdf

```

or 

```
psnup --nup 2x2 paper.ps

```

They each create a new output file according to the format you specify in the command line. the output file you then print in the usual way, e.g.

```
lpr paper_2x2.ps
```

or through ggv, xpdf, acroread or whatever!

Hope that helped!

  - Riko

---

