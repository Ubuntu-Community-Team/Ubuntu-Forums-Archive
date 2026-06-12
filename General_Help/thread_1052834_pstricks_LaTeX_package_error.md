---
title: "pstricks LaTeX package error"
date: 2009-01-28
forum: General Help
---

### Post by bixejo on 2009-01-28
Hi all.

Any time I **\usepackage{pstricks}** in my LaTeX documents I get the following error wherever I put one figure (it doesn't matter what kind of figure is):

> 
./introduccion.tex:153:\begin{document} ended by \end{figure}. \end{figure}
./introduccion.tex:153:Extra \endgroup. \end{figure}
These errors vanish if I remove/comment the **\usepackage{pstricks}** line (but then I obviously cannot include .pst files in my figures).

Did anyone find this error before and, hopefully, find a workaround for this?

Thank you in advance.

PS: I'm running Ubuntu 8.04 amd64. My LaTeX installed suite:

> 
hlatex-fonts-base                install
hlatex-fonts-extra                install
html2text                    install
latex-ucs                    deinstall
latex-ucs-contrib                deinstall
liblocale-gettext-perl                install
libtext-charwidth-perl                install
libtext-iconv-perl                install
libtext-wrapi18n-perl                install
openoffice.org-writer2latex            install
preview-latex-style                install
tex-common                    install
texinfo                        install
texlive                        install
texlive-base                    install
texlive-base-bin                install
texlive-bibtex-extra                install
texlive-common                    install
texlive-doc-base                install
texlive-doc-en                    install
texlive-doc-es                    install
texlive-extra-utils                install
texlive-font-utils                install
texlive-fonts-extra                install
texlive-fonts-recommended            install
texlive-generic-recommended            install
texlive-lang-spanish                install
texlive-latex-base                install
texlive-latex-extra                install
texlive-latex-recommended            install
texlive-math-extra                install
texlive-pictures                install
texlive-pstricks                install


---

### Post by bixejo on 2009-01-29
I've realized that this happens when I simultaneously use in the same document the Dalhousie University thesis style package:

 [http://www.itu.dk/stud/projects_f2004/handtracking/program/WinEdt/Samples/Thesis/XThesis.sty](http://www.itu.dk/stud/projects_f2004/handtracking/program/WinEdt/Samples/Thesis/XThesis.sty)

The point is that I can use separately any of these two packages, but both together raises this problem...

 Any help or suggestion is still highly appreciated.

---

