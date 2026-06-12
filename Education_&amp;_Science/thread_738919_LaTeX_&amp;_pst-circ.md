---
title: "LaTeX &amp; pst-circ"
date: 2008-03-29
forum: Education &amp; Science
---

### Post by Astrophysiker on 2008-03-29
I have a problem with the pst-circ package. I used this example as source code:
```
\documentclass[a4paper,10pt]{article}

\usepackage{pst-circ}
%opening
\title{}
\author{}

\begin{document}

\pnode(0,1){A}
\pnode(3,1){B}
\pnode(3,3){C}
\resistor(A)(B){$R$}
\resistor(B)(C){$R_2$}
\end{document}
```
but the output (dvi and pdf) shows the labels at the wrong place. Here my dvi-file:
[DVI]("http://astrophysiker.as.funpic.de/test.dvi")
Putting more element means more labels at the same place.
Has somebody an idea whats going wrong?

Thx, Astro

---

### Post by beren.olvar on 2008-03-29
nvm

---

### Post by beren.olvar on 2008-03-29
in the thread you posted before is the solution

you have to do as follows:

latex circuit.tex
dvipdf circuit.dvi
evince circuit.pdf

that worked for me

cheers

---

### Post by Astrophysiker on 2008-03-29
Ok, the pdf-file is correct. Is there any possibility to show also the dvi-file correctly?

---

