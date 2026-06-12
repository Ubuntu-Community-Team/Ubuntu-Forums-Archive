---
title: "usetikzlibrary"
date: 2011-03-16
forum: Education &amp; Science
---

### Post by jazzgossen on 2011-03-16
I'm having trouble using the Lua/Tikz terminal of gnuplot together with latex. 

I tried following the guide shown [here]("http://www.timteatro.net/2010/07/18/gnuplottikz-for-stunning-latex-plots/"). The gnuplot side of things works fine, but when I run pdflatex I get the error message 
```

...
(/usr/share/texmf-texlive/tex/generic/ifxetex/ifxetex.sty)
! Undefined control sequence.
l.13 \usetikzlibrary
                    {arrows,patterns,plotmarks}
? 

```
and then a bunch of other errors. 

Has anybody else got this working on Ubuntu?

I'm using Ubuntu 10.04 with pfg 2.00-1 and texlive-pictures 2009-7.

---

### Post by jazzgossen on 2011-03-23
Aha! I found that I had some remains of an old PGF version 1.01 under /usr/local. Removing that and running a texhash solved my problem.

---

