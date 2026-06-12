---
title: "LaTeX geometry package"
date: 2010-03-28
forum: Education &amp; Science
---

### Post by kbaumen on 2010-03-28
Hi

I'm having trouble with the geometry package. Even if I call it in the preamble, pdflatex doesn't recognize \newgeometry and \restoregeometry commands in my code. I've checked that geometry requires keyval, ifpdf, ifvtex. I've got all three of them. I've googled this problem, however couldn't find anything. Maybe it's too late now to work and I'm just missing something trivial, but here's the code anyway.

```

\documentclass[a4paper,titlepage,12pt]{report}
\setlength{\parindent}{1cm}
\usepackage{amssymb,amsmath,tikz,graphicx,fancyhdr,gensymb,circuitikz}
\usepackage[small]{caption}
[COLOR=Red]\usepackage{geometry}[/COLOR]
\usetikzlibrary{arrows}
\newcommand{\HRule}{\rule{\linewidth}{0.5mm}}
\renewcommand{\chaptername}{Part}

\begin{document}

    \tikzset{font=\small}
    \tikzset{>=latex}
    \tikzset{align=flush center}
    \ctikzset{bipoles/length=1cm}

    \input{./title.tex} \newpage
    \tableofcontents
    \newpage
    
    BLADIBLADIBLA

    [COLOR=Red][COLOR=Black]\newpage[/COLOR]
    \newgeometry{margin=0.01cm}
    [COLOR=black]bladibladibla[/COLOR]
    [COLOR=Black]\newpage[/COLOR]
    \restoregeometry
[/COLOR] 
    BLADIBLADIBLA
\end{document}

```Cheers for any help.

---

### Post by meborc on 2010-03-29
might be the geometry package (included in texlive-latex-base) is too old to support \newgeometry

[http://www.tug.org/teTeX/tetex-texmfdist/doc/latex/geometry/geometry.pdf](http://www.tug.org/teTeX/tetex-texmfdist/doc/latex/geometry/geometry.pdf) - here is nothing on that command

> 		    LaTeX Package: Geometry 2010/03/13 v5.3
----------------------------------------
Flexible and easy interface to page dimensions

Copyright (C) 1996-2010
by Hideo Umeki 

Abstract:
  This package provides a flexible and easy interface to page dimensions.
  You can set the page layout with intuitive parameters. For instance,
  if you want to set a margin to 2cm from each edge of the paper,
  you can go \usepackage[margin=2cm]{geometry}. With \newgeometry command
  you can change the layout anywhere in the document.

CTAN: macros/latex/contrib/geometry

Recent changes:
 [Release 5.3]
  * Fixed missed initialization of \Gm@lines.

 [Release 5.0-]
  * Changing page layout mid-document.
  * A new set of options to specify the layout area.
  * A new driver option 'xetex'.
  * New paper size presets for JIS B-series.
  * Changing default for underspecified margin.
  * The option 'showframe' works on every page.
  * Loading geometry.cfg precedes processing class options.
  * Deleted options: 'compat2' and 'twosideshift'.
  * Added 'onecolumn' option as a shorthand for 'twocolumn=false'.
  * Changed the format of the verbose mode.

(changes.txt for more history)

Files:
  * README         -  this file
  * changes.txt    -  history of changes
  * geometry.ins   -  for installation to get .sty from .dtx
  * geometry.dtx   -  including sources and documentation
  * geometry.pdf   -  print-ready documentation

Installation: 
[manual installation]
  * To get geometry.sty out of geometry.dtx
        $ tex geometry.dtx 
    or  $ (la)tex geometry.ins
  * To build documentation
        $ latex geometry.dtx  
    or  $ latex geometry.drv
  * Put the derived files in the proper directories:
      -  tex/latex/geometry/geometry.sty
      -  doc/latex/geometry/geometry.pdf
      -  source/latex/geometry/geometry.dtx

[TeXLive]
  * Use 'tlmgr' command
        $ tlmgr show geometry          -- to check the package info
        $ sudo tlmgr update geometry   -- to update the package
  * You can use 'TeX Live Utility' instead of 'tlmgr', if on MacOSX.

[MikTeX]
  * Use the MikTeX Update Wizard to update geometry package.

License:
  This work may be distributed and/or modified under the conditions
  of the LaTeX Project Public License, either version 1.3c of this
  license or (at your option) any later version. The latest version
  of this license is in [http://www.latex-project.org/lppl.txt](http://www.latex-project.org/lppl.txt)
  and version 1.3c or later is part of all distributions of LaTeX
  version 2005/12/01 or later.

--
Happy TeXing!
Hideo Umeki
 
EOF
            

as you see, the \newgeometry is quite a new thing... not sure it has been backported to karmic

---

### Post by kbaumen on 2010-03-29
> **meborc said:**
> might be the geometry package (included in texlive-latex-base) is too old to support \newgeometry

[http://www.tug.org/teTeX/tetex-texmfdist/doc/latex/geometry/geometry.pdf](http://www.tug.org/teTeX/tetex-texmfdist/doc/latex/geometry/geometry.pdf) - here is nothing on that command



as you see, the \newgeometry is quite a new thing... not sure it has been backported to karmic


Oh, cheers. Fortunately, we have CTAN to solve such problems.

---

### Post by milind_21_03 on 2010-08-09
I am facing the same problem using TeX-Live 2009 on Ubuntu 9.10. Using \newgeometry{} or \restoregeometry gives me the error "Undefined control sequence".

I have updated the geometry package using "tlmgr update geometry". Yet, I keep getting the error message :(.

Thanks for any help.

---

### Post by frisket on 2010-08-13
> **milind_21_03 said:**
> I am facing the same problem using TeX-Live 2009 on Ubuntu 9.10. Using \newgeometry{} or \restoregeometry gives me the error "Undefined control sequence".

I have updated the geometry package using "tlmgr update geometry". Yet, I keep getting the error message :(.


I've never used tlmgr yet: I don't know if it's stable.

Check to see where geometry.sty is. The original installed version should be in /usr/share/texmf-texlive/tex/latex/geometry/, and any manual update should put the new version in /usr/local/share/texmf/tex/latex/geometry/ (which always gets searched *before* the texmf-texlive tree); or if you don't have access to /usr/local, put it in ~/texmf/tex/latex/geometry/, which gets searched first of all.

But I don't know where tlmgr puts stuff: as geometry.sty is a distribution-installed (default) package, it may be that it has simply replaced the version in the texmf-texlive tree. See what date is on geometry.sty...

Whichever way, it sounds as if tlmgr has not run texhash, the indexer, which **MUST** be run after any update, otherwise files simply won't be found. To update the texmf-texlive tree, you need to run sudo texhash, as normal users don't have write access to the ls-R index in that tree.

---

