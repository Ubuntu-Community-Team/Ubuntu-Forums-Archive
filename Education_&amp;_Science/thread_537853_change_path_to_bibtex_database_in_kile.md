---
title: "change path to bibtex database in kile"
date: 2007-08-29
forum: Education &amp; Science
---

### Post by totalnewbi on 2007-08-29
Hi Folks,

i just changed over from Win and Miktex to Ubuntu and Kile. After some hassle and a lot of googleing i managed to get the bibliography stuff working. My question now is, whether it is possible to have one central bibtex database (*.bib) stored somewhere in the computer so that you do not have to copy that file always in the directory where the *.tex file is.

EDIT: OK, that question was dump! For other greenhorns like me:
simply add the path inside the Brackets after "\bibliography":
\bibliography{/home/example/bibliography.bib}

Another question is, whether there is a way of not always having to run Latex several times and then BiBtex in a certain order to prevent error messages? For example, compiling the document without the Bibliography and just in the final run go through all this several Latex runs?


Thx
Newbi

---

### Post by helmingstay on 2008-03-28
> **totalnewbi said:**
> Hi Folks,
simply add the path inside the Brackets after "\bibliography":
\bibliography{/home/example/bibliography.bib}

Another question is, whether there is a way of not always having to run Latex several times and then BiBtex in a certain order to prevent error messages? For example, compiling the document without the Bibliography and just in the final run go through all this several Latex runs?
i

Thanks for the tip.I screwed it up the first few times :) It looks like bibtex groks relative file positions (../) but not shell-like, globby thingies ( ~user ).
Scripting the latex build is short and simple.  I build pdfs, which changes the last line of the script:

```

#!/bin/bash
# turn the first argument (file basename, no .tex extension)
# into a pdf.  change last line to "latex $1" to get dvi output
latex $1
bibtex $1
latex $1
pdflatex $1

```

---

