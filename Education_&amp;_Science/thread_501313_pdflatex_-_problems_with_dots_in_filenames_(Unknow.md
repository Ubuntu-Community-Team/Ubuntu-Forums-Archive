---
title: "pdflatex - problems with dots in filenames (Unknown graphics extension)"
date: 2007-07-15
forum: Education &amp; Science
---

### Post by xadder on 2007-07-15
Hi,

I just started learning to use pdflatex (I have used LaTeX for years with .eps files), and want to include figures with name such as  "output.2002.pdf". pdflatex complains about unknown graphics extensions for ".2002.".

I could of course rename all such files to output_2002.pdf, but I would rather not for several reasons.

Is there a solution to this?  Thanks.

---

### Post by parktownprawn on 2007-07-17
hmmm  not sure how to fix this  - i still use epsfig.

rather than rename all the files you could just create symbolic links

ln -s  output.2002.pdf output_2002.pdf

---

### Post by xadder on 2007-07-17
Thanks, but that doesn't help. Often I am working with hundreds of files for different model runs, year, scenarios, etc,. and I like to use files with names set in a csh, bash or perl script, e.g.

set ofile=Output.$run.$year.$scenario.eps

If using "_" as the seperator, I would need "" or {}, e.g.

set ofile=Output_"$run"_"$year"_$scenario.eps

Not a disaster, but a but messier. (Having to link as you suggest would just add even more files).

Just seemed a shame to me that pdflatex seems to work assuming DOS-like conventions, that the dot is just for indicating file type and cannot be used in the filename.

---

### Post by parktownprawn on 2007-07-17
yeah it seemed disappointing to me so i read the manual 
[http://www.ctan.org/tex-archive/help/Catalogue/entries/graphicx.html](http://www.ctan.org/tex-archive/help/Catalogue/entries/graphicx.html)

firstly use the graphicx package and try something like:

\includegraphics[type=pdf,ext=.pdf,read=.pdf]{output.2002}

if that doesn't work check out

[http://www.tug.org/TeXnik/mainFAQ.cgi?file=Graphics/graphics](http://www.tug.org/TeXnik/mainFAQ.cgi?file=Graphics/graphics)

---

### Post by xadder on 2007-07-18
Many thanks - that works great!

I had also tried reading that graphicx manual but didn't spot the  combination of factors you suggested.
Anyway, problem solved :)

---

### Post by parktownprawn on 2007-07-18
yeah it seems unnecessarily complicated

---

### Post by sternschnupper on 2010-02-17
even more convenient to me is:
\usepackage{grffile}
then you don't need any extra syntax, just type for example:
\includegraphics{foo.bar.png}

only be aware that it parses quotation marks as well!

---

