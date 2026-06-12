---
title: "Saving man pages to txt, ps and pdf files using a2ps"
date: 2009-05-16
forum: General Help
---

### Post by V. Wayne on 2009-05-16
Here are some handy terminal commands using a2ps for saving manual or info pages to a text, postscript or pdf file.  Example is man pages for list directory (ls).

Commands to print man pages on screen and save in a text, ps and pdf files with 2 columns per sheet with headers:
man ls | col -b | tee ls.txt; a2ps ls.txt -o ls.ps && ps2pdf ls.ps

Commands to print man pages on screen and save in a text, ps and pdf files with 2 columns per sheet without headers:
man ls | col -b | tee ls.txt; a2ps -B ls.txt -o ls.ps && ps2pdf ls.ps

Commands to print man pages on screen and save in a text, ps and pdf files in 1 column with headers and without a border:
man ls | col -b | tee ls.txt; a2ps ls.txt -R --columns=1 --borders=0 -o ls.ps && ps2pdf ls.ps

---

