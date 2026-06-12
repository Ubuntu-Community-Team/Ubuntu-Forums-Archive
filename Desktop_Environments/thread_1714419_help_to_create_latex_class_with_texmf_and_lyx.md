---
title: "help to create latex class with texmf and lyx"
date: 2011-03-25
forum: Desktop Environments
---

### Post by jamaas on 2011-03-25
I'm trying to create a new .cls  file for a journal called Bayesian Analysis.  They supply a list of files called "latex macros" which I would like to use with Lyx to create the correct format.  I've tried lots of things but no luck yet.  This is the list of files I can get, anyone care to offer suggestions?

Lyx 2.0, texmf, ubuntu 10.10

Thanks a bunch

Jim


ba.bst
ba.cls
baextra.readme
ba.sty
ba.version
bayes.sty
chapterbib.sty
crop.dtx
crop.ins
crop.sty
main.aux
main.bbl
main.bib
main.blg
main.dvi
main.log
main.pdf
main.pp1
main.tag
main.tex
natbib.dtx
natbib.ins
natbib.pdf
natbib.sty
output1.eps
README
table1.tex
tyle files.
xart.aux
xart.bbl
xart.blg
xart.tex

---

### Post by sputnik on 2011-03-27
It looks like you have your class file (ba.cls).  You also seem to have a readme file (baextra.readme) and possibly most importantly an example (main.tex & main.dvi).

Files will need to be installed somewhere TeX/LaTeX can find them - probably usr/share/texmf/tex/latex/ba or usr/share/texmf-texlive/tex/latex/ba. I am not sure of the convention here.

You will also need to refresh Tex (sudo texhash) so the packages can be found.

---

### Post by sputnik on 2011-03-28
From the LyX list it was recommended that the files were put under
/usr/local/share/texmf/  rather than /usr/share...

or under ~/texmf

2nd one removes need for sudo, it may also remove need for running texhash I am not sure.

---

