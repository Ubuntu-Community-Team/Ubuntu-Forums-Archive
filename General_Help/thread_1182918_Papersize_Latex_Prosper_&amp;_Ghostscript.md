---
title: "Papersize: Latex Prosper &amp; Ghostscript"
date: 2009-06-09
forum: General Help
---

### Post by bigoperm on 2009-06-09
I'm trying to get letter-sized PDFs from latex prosper. There are several resources on the web that say use the 'a4' option to dvips or dvipdf, but I'm having no luck:
```
$> head -1 test.tex
\documentclass[ps]{prosper}
$> latex test
$> dvipdf -sPAPERSIZE=a4 test
$> pdfinfo test.pdf
...
Page size:      595 x 842 pts (A4)
...
$> head -1 test.tex
\documentclass[pdf]{prosper}
$> latex test
$> dvipdf -sPAPERSIZE=a4 test
$> pdfinfo test.pdf
...
Page size:      584 x 752 pts
...
```
First, why does the prosper header matter ('ps' versus 'pdf')? Second, why does Ghostscript not produce correct letter point size ('584 x 752' instead of '612 x 792')?

Has anyone had luck?

---

