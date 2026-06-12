---
title: "Problem with like .bib files"
date: 2008-12-02
forum: Education &amp; Science
---

### Post by kokonobs on 2008-12-02
I have a .bib file which contains my references. Whenever i reopen my work, and run the pdf, i have question marks instead of the cited refs. I always have to load it again and re cite them all. Is there a particular place i have to store the .bib file to make sure they remain?
Thanks

---

### Post by stumbleUpon on 2008-12-29
The .bib file must be in the same directory as the .tex file.

How are you generating the pdf file...?

You should do

latex filename.tex
latex filename.tex
bibtex filename
latex filename.tex

which will produce a filename.dvi file which you can then convert to postscript (dvips filename.dvi) and then later to pdf (ps2pdf filename.ps)

---

