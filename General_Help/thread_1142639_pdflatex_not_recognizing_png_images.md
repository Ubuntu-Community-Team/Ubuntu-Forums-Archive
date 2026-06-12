---
title: "pdflatex not recognizing png images"
date: 2009-04-29
forum: General Help
---

### Post by alexandre.tp on 2009-04-29
Hello. I'm using 8.10. I have texlive-full installed. When I run pdflatex on a sample late file, like

\documentclass{article}
\usepackage{graphicx}
\begin{document}
\includegraphics{foo}
\end{document}

Even if I have a foo.png in that directory, pdflatex complains that no image was found, and says it did not find an image with eps, eps.gx, ps or ps.gz extensions. Any idea what could cause that?

---

### Post by Simian Man on 2009-04-29
Odd, I don't have any other directives that make a difference, graphicx was it.  I'd fire up your package manager and install every latex package in there and see if that makes a difference.  From what I remember  of Ubuntu, it split the LaTeX distribution into a lot of packages.

---

### Post by alexandre.tp on 2009-04-29
I have already done that--supposedly, texlive-full is a metapackage with all tex packages included, as seen in [http://packages.ubuntu.com/intrepid/tex/texlive-full](http://packages.ubuntu.com/intrepid/tex/texlive-full) . Graphicx.sty is included in texlive-latex-base ( [http://packages.ubuntu.com/jaunty/all/texlive-latex-base/filelist](http://packages.ubuntu.com/jaunty/all/texlive-latex-base/filelist) ), and is installed in my system.

The problem is not that it does not find graphicx, is that pdflatex (the binary) acts the same way latex (the binary) would act when confronted with a \includegraphics{} directive, which is to look for eps or ps images, but not for .pdf, .png or .jpeg

---

### Post by Stefan_K on 2009-04-30
Hi Alexandre,

if you would post your .log file of the compilation of the sample latex file we probably could tell you more.

Stefan

--
[TeXblog.net]("http://texblog.net")

---

### Post by delcypher on 2009-04-30
Try...```

\documentclass{article}
\usepackage[pdftex]{graphicx}
\DeclareGraphicsExtensions{.png}
\begin{document}
\includegraphics{foo}
\end{document}

```

and see if that works.

---

### Post by alexandre.tp on 2009-05-02
Adding the pdftex option to graphicx worked. Thank you very much, I didn't know it existed (and never had to use it in older ubuntus and other distros)

---

