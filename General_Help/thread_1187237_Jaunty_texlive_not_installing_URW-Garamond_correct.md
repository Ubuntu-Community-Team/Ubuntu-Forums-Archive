---
title: "Jaunty: texlive not installing URW-Garamond correctly?"
date: 2009-06-14
forum: General Help
---

### Post by dpm_edinburgh on 2009-06-14
I'm trying to get mathdesign with the URW-Garamond font installed on Jaunty with texlive.  If I remember, on Ibex, it was sufficient to install texlive-fonts-extra and things would be sorted, and indeed when searching for garamond with apt-cache search texlive-fonts-extra is returned.

Having installed texlive-fonts-extra, and trying to compile my document with

\usepackage[T1]{fontenc}
\usepackage[urw-gamamond]{mathdesign}

in the preamble, all the fonts appear corrupted.  pdfLaTeX complains in the output that:

pdfTeX warning: pdflatex (file ugmm8a.pfb): cannot open Type 1 font file for reading


pdfTeX warning: pdflatex (file ugmr8a.pfb): cannot open Type 1 font file for reading


pdfTeX warning: pdflatex (file ugmri8a.pfb): cannot open Type 1 font file for reading

So, what's going on, and how can I fix this?

Thanks in advance!

---

