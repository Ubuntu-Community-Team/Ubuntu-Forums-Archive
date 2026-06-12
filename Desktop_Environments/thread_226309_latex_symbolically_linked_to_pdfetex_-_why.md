---
title: "latex symbolically linked to pdfetex - why?"
date: 2006-07-31
forum: Desktop Environments
---

### Post by yotam on 2006-07-31
Why :confused: is

```

# (cd /usr/bin; ls -l latex)
lrwxrwxrwx 1 root root 7 2006-07-30 23:54 latex -> pdfetex*

```

I just upgraded my box from breezy to dapper
via editing /etc/apt/sources.list 
and the 
```

   apt-get update && apt-get dist-upgrade

```
commands.

And I miss generating good old [FONT="Lucida Console"]**.dvi**[/FONT] files.

---

### Post by jordilin on 2006-07-31
Well, I have installed the latex system from TeXLiveCd and I get as you a link latex->pdfetex, but I get dvi files when compiling latex source code. So you should get .dvi files as well when running latex nameofthefile.tex. Make a simple latex file and try again, and tell us.

---

### Post by yotam on 2006-07-31
My latex comes from:
```

# dpkg-query -S /usr/bin/latex
tetex-bin: /usr/bin/latex

```
indeed running it on 'simple' LaTeX file such as
the sample2e.tex does produce nice sample2e.dvi.

But this new tetex installation does present 
a problem with some complicated .tex sources I have
that used to work both with and without pdfoutput.
I'll dive in, figure out and report.

---

### Post by jordilin on 2006-07-31
Well, it seems that you have installed from the repos. If it does not work, I would consider removing it and installing the latest latex system from the TeX Live Cd. I have recently posted a HowTo on how to do that. Follow the following thread:
[http://www.ubuntuforums.org/showthread.php?t=226332](http://www.ubuntuforums.org/showthread.php?t=226332)
and tell us sth.

---

### Post by yotam on 2006-07-31
I have minimized the problem as can be seen below.
Following it, is a bypass - or may be this is 
the right way to deal with pdf.

Jordilin(?), or anyone wants to try 
problematic case with latex coming from 'TeX Live'
and post results?

The '*bad*'  :(  case:
```

**# cat p.tex**
\ifx\pdfoutput\undefined % We're not running pdftex
\documentclass[11pt,a4paper]{book}
\else
\documentclass[pdftex,twoside,a4paper]{book}
\fi

\ifx\pdfoutput\undefined % We're not running pdftex
\else
\RequirePackage[colorlinks,hyperindex,plainpages=false]{hyperref}
\def\pdfBorderAttrs{/Border [0 0 0] } % No border arround Links
\fi

\title{My Title} \author{My Name}
\begin{document}
\chapter{About this}
Hello Goodbye.
\end{document}
**# latex p.tex**
This is pdfeTeX, Version 3.141592-1.21a-2.2 (Web2C 7.5.4)
entering extended mode
(./p.tex
LaTeX2e <2003/12/01>
Babel <v3.8d> and hyphenation patterns for american, french, german, ngerman, b
ahasa, basque, bulgarian, catalan, croatian, czech, danish, dutch, esperanto, e
stonian, finnish, greek, icelandic, irish, italian, latin, magyar, norsk, polis
h, portuges, romanian, russian, serbian, slovak, slovene, spanish, swedish, tur
kish, ukrainian, nohyphenation, loaded.
(/usr/share/texmf-tetex/tex/latex/base/book.cls
Document Class: book 2004/02/16 v1.4f Standard LaTeX document class
(/usr/share/texmf-tetex/tex/latex/base/bk10.clo))
(/usr/share/texmf-tetex/tex/latex/hyperref/hyperref.sty
(/usr/share/texmf-tetex/tex/latex/graphics/keyval.sty)
(/usr/share/texmf-tetex/tex/latex/hyperref/pd1enc.def)
(/usr/share/texmf-tetex/tex/latex/hyperref/hyperref.cfg)
Implicit mode ON; LaTeX internals redefined
(/usr/share/texmf-tetex/tex/latex/url/url.sty))
*hyperref using driver hpdftex*
(/usr/share/texmf-tetex/tex/latex/hyperref/hpdftex.def
(/usr/share/texmf-tetex/tex/latex/psnfss/pifont.sty
(/usr/share/texmf-tetex/tex/latex/psnfss/upzd.fd)
(/usr/share/texmf-tetex/tex/latex/psnfss/upsy.fd))) (./p.aux)
(/usr/share/texmf-tetex/tex/latex/graphics/color.sty
(/usr/share/texmf-tetex/tex/latex/graphics/color.cfg)
(/usr/share/texmf-tetex/tex/latex/graphics/pdftex.def
(/usr/share/texmf-tetex/tex/context/base/supp-pdf.tex
(/usr/share/texmf-tetex/tex/context/base/supp-mis.tex
loading : Context Support Macros / Miscellaneous (2004.10.26)
)
loading : Context Support Macros / PDF (2004.03.26)
))) (/usr/share/texmf-tetex/tex/latex/hyperref/nameref.sty) (./p.out) (./p.out)
Chapter 1.
[1{/var/lib/texmf/fonts/map/pdftex/updmap/pdftex.map}] (./p.aux) )</usr/share/t
exmf-tetex/fonts/type1/bluesky/cm/cmr10.pfb></usr/share/texmf-tetex/fonts/type1
/bluesky/cm/cmbx12.pfb>
Output written on p.pdf (1 page, 11308 bytes).
Transcript written on p.log.
**# ls -l p.{dvi,pdf}**
ls: p.dvi: No such file or directory
-rw-r--r-- 1 yotam yotam 11308 2006-07-31 18:23 p.pdf

```

The '*good*' bypass :)   :
```

**# cat pif.tex**
\RequirePackage{ifpdf}
\ifpdf
 \documentclass[pdftex,twoside,a4paper]{book}
\else
  \documentclass[11pt,a4paper]{book}
\fi

\ifpdf % We're not running pdftex
\else
\RequirePackage[colorlinks,hyperindex,plainpages=false]{hyperref}
\def\pdfBorderAttrs{/Border [0 0 0] } % No border arround Links
\fi

\title{My Title} \author{My Name}
\begin{document}
\chapter{About this}
Hello Goodbye.
\end{document}
**# latex pif.tex**
This is pdfeTeX, Version 3.141592-1.21a-2.2 (Web2C 7.5.4)
entering extended mode
(./pif.tex
LaTeX2e <2003/12/01>
Babel <v3.8d> and hyphenation patterns for american, french, german, ngerman, b
ahasa, basque, bulgarian, catalan, croatian, czech, danish, dutch, esperanto, e
stonian, finnish, greek, icelandic, irish, italian, latin, magyar, norsk, polis
h, portuges, romanian, russian, serbian, slovak, slovene, spanish, swedish, tur
kish, ukrainian, nohyphenation, loaded.
(/usr/share/texmf-tetex/tex/latex/oberdiek/ifpdf.sty)
(/usr/share/texmf-tetex/tex/latex/base/book.cls
Document Class: book 2004/02/16 v1.4f Standard LaTeX document class
(/usr/share/texmf-tetex/tex/latex/base/bk11.clo))
(/usr/share/texmf-tetex/tex/latex/hyperref/hyperref.sty
(/usr/share/texmf-tetex/tex/latex/graphics/keyval.sty)
(/usr/share/texmf-tetex/tex/latex/hyperref/pd1enc.def)
(/usr/share/texmf-tetex/tex/latex/hyperref/hyperref.cfg)
Implicit mode ON; LaTeX internals redefined
(/usr/share/texmf-tetex/tex/latex/url/url.sty))
*hyperref using default driver hdvips*
(/usr/share/texmf-tetex/tex/latex/hyperref/hdvips.def
(/usr/share/texmf-tetex/tex/latex/hyperref/pdfmark.def)) (./pif.aux)
(/usr/share/texmf-tetex/tex/latex/graphics/color.sty
(/usr/share/texmf-tetex/tex/latex/graphics/color.cfg)
(/usr/share/texmf-tetex/tex/latex/graphics/dvips.def)
(/usr/share/texmf-tetex/tex/latex/graphics/dvipsnam.def))
(/usr/share/texmf-tetex/tex/latex/hyperref/nameref.sty) (./pif.out) (./pif.out)
Chapter 1.
[1] (./pif.aux) )
Output written on pif.dvi (1 page, 2420 bytes).
Transcript written on pif.log.

```

---

### Post by jordilin on 2006-07-31
What tex system do you have now? Tetex from the repos or the one installed from the TeX Live Cd?

---

### Post by yotam on 2006-07-31
I still am with tetex as packaged by Dapper.

---

### Post by jordilin on 2006-07-31
As for the examples, I've got the same results as you with a Fedora distro. I will try to run the examples in my Ubuntu Dapper box and tex from texlivecd, but I'm afraid I'm going to obtain the same. It seems there's nothing wrong with your examples.

---

### Post by yotam on 2006-07-31
So my guess is that the pdfetex executable
when running as **latex**
gets confused of a second
```

\ifx\pdfoutput\undefined ....

```
and decides to produce a [FONT="Lucida Console"]**.pdf**[/FONT] instead of a [FONT="Lucida Console"]**.dvi**[/FONT] file.

---

### Post by jordilin on 2006-07-31
> **yotam said:**
> So my guess is that the pdfetex executable
when running as **latex**
gets confused of a second
```

\ifx\pdfoutput\undefined ....

```
and decides to produce a [FONT="Lucida Console"]**.pdf**[/FONT] instead of a [FONT="Lucida Console"]**.dvi**[/FONT] file.

To be sincere, I am not a Latex expert. I would consider to ask this in the TeX google groups at:
[http://groups.google.com/group/comp.text.tex](http://groups.google.com/group/comp.text.tex)

---

