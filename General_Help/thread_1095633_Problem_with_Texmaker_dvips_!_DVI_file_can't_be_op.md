---
title: "Problem with Texmaker: dvips: ! DVI file can't be opened."
date: 2009-03-13
forum: General Help
---

### Post by Happy-Dude on 2009-03-13
Heya guys!!

So, my INTEL CS class introduced my to LaTeX... And it's absolutely beautiful.

Now that I need to learn TeX and how to format/ use it to a good extent, I've installed Texmaker (which I felt was more -backended- from LyX).

However, I'm running into a problem generating previews.

Let's say I am beginning a document:
```
\documentclass[10pt,a4paper]{article}
\usepackage[utf8x]{inputenc}
\usepackage{ucs}
\author{}
\begin{document}

\end{document}
```

Then I would hit the LaTeX button on top, right? I get back 
```

Process started

Process exited normally
```

Then I hit Quick Build. Which should work, but returns an error:
```
Process started

This is dvips(k) 5.96.1 Copyright 2007 Radical Eye Software (www.radicaleye.com) dvips: ! DVI file can't be opened.

Process exited with error(s)
```

Here is my generated logfile:
```

This is pdfTeXk, Version 3.141592-1.40.3 (Web2C 7.5.6) (format=latex 2009.2.4)  13 MAR 2009 23:29
entering extended mode
 %&-line parsing enabled.
**example.tex
(./example.tex
LaTeX2e <2005/12/01>
Babel <v3.8h> and hyphenation patterns for english, usenglishmax, dumylang, noh
yphenation, loaded.
(/usr/share/texmf-texlive/tex/latex/base/article.cls
Document Class: article 2005/09/16 v1.4f Standard LaTeX document class
(/usr/share/texmf-texlive/tex/latex/base/size10.clo
File: size10.clo 2005/09/16 v1.4f Standard LaTeX file (size option)
)
\c@part=\count79
\c@section=\count80
\c@subsection=\count81
\c@subsubsection=\count82
\c@paragraph=\count83
\c@subparagraph=\count84
\c@figure=\count85
\c@table=\count86
\abovecaptionskip=\skip41
\belowcaptionskip=\skip42
\bibindent=\dimen102
)
(/usr/share/texmf-texlive/tex/latex/base/inputenc.sty
Package: inputenc 2006/05/05 v1.1b Input encoding file
\inpenc@prehook=\toks14
\inpenc@posthook=\toks15

(/usr/share/texmf-texlive/tex/latex/ucs/utf8x.def
File: utf8x.def 2004/10/17 UCS: Input encoding UTF-8
))
(/usr/share/texmf-texlive/tex/latex/ucs/ucs.sty
Package: ucs 2004/10/17 UCS: Unicode input support

(/usr/share/texmf-texlive/tex/latex/ucs/data/uni-global.def
File: uni-global.def 2004/10/17 UCS: Unicode global data
)
\uc@secondtry=\count87
\uc@combtoks=\toks16
\uc@combtoksb=\toks17
\uc@temptokena=\toks18
) (./example.aux)
\openout1 = `example.aux'.

LaTeX Font Info:    Checking defaults for OML/cmm/m/it on input line 5.
LaTeX Font Info:    ... okay on input line 5.
LaTeX Font Info:    Checking defaults for T1/cmr/m/n on input line 5.
LaTeX Font Info:    ... okay on input line 5.
LaTeX Font Info:    Checking defaults for OT1/cmr/m/n on input line 5.
LaTeX Font Info:    ... okay on input line 5.
LaTeX Font Info:    Checking defaults for OMS/cmsy/m/n on input line 5.
LaTeX Font Info:    ... okay on input line 5.
LaTeX Font Info:    Checking defaults for OMX/cmex/m/n on input line 5.
LaTeX Font Info:    ... okay on input line 5.
LaTeX Font Info:    Checking defaults for U/cmr/m/n on input line 5.
LaTeX Font Info:    ... okay on input line 5.

(/usr/share/texmf-texlive/tex/latex/ucs/ucsencs.def
File: ucsencs.def 2003/11/29 Fixes to fontencodings LGR, T3
) (./example.aux) ) 
Here is how much of TeX's memory you used:
 463 strings out of 95087
 7128 string characters out of 1183279
 62140 words of memory out of 1500000
 3705 multiletter control sequences out of 10000+50000
 3640 words of font info for 14 fonts, out of 1200000 for 2000
 28 hyphenation exceptions out of 8191
 23i,1n,19p,323b,36s stack positions out of 5000i,500n,6000p,200000b,5000s

No pages of output.
```

Here are my Texmaker configuration paths:
```

latex -interaction=nonstopmode %.tex
dvips -o texout.ps %.dvi
bibtex %.aux
makeindex %.idx
evince %.dvi
evince %.ps
pdflatex -interaction=nonstopmode %.tex
dvipdfm %.dvi
ps2pdf %.ps
evince %.pdf
mpost --interaction nonstopmode 
gs

```

Well, if there's anything more needed of me, I will gladly see what I can do. Can anyone help me out here? I don't know what wrong, but I want to get to making some beautiful LaTeX-powered documents now :) .. Thanks very much guys, I really appreciate it!!

---

### Post by firefly2442 on 2009-03-14
I'm also kind of a beginner with Latex but I remember when I tried compiling something it was complaining about external libraries that were missing.  If you don't already have this package "tetex-extra" you should probably install it.

Kile is another Latex editor (but for KDE).  It's fairly similar to Texmaker I think.  Not related to your problem but just FYI.

I assume you already have bibtex, dvips, and all the other programs listed in the Texmaker configuration?

Sorry I can't be of more help, maybe someone else can chime in.

Good luck. :)

---

### Post by Happy-Dude on 2009-03-14
Good morning!!

Thanks for the reply!! I'm trying that tetex-extra package with synaptic right now.

How do I double check if all the programs are installed? What's the program for dvips? (I'm sure Evince is installed, but what is it's path?)

Thanks very much!! I really appreciate it :) !!
I'll post back with my results.

---

### Post by Happy-Dude on 2009-03-14
Unfortunately, I am still having problems generating a 'Quick Build' preview.

Can any give a hand here? (It must be something with the program paths, but I have no experience whatsoever as to what they should be; anyone know them/ know which I should install?)

**Note: sudo nautilus --> texmaker --> quick build works... I dunno [o.O].

---

### Post by Happy-Dude on 2009-03-14
Here are some logfiles:

running latex tex.tex
```
This is pdfTeXk, Version 3.141592-1.40.3 (Web2C 7.5.6) (format=latex 2009.3.14)  14 MAR 2009 16:48
entering extended mode
 %&-line parsing enabled.
**tex.tex
(./tex.tex
LaTeX2e <2005/12/01>
Babel <v3.8h> and hyphenation patterns for english, usenglishmax, dumylang, noh
yphenation, croatian, ukrainian, russian, bulgarian, czech, slovak, danish, dut
ch, finnish, basque, french, german, ngerman, ibycus, greek, monogreek, ancient
greek, hungarian, italian, latin, mongolian, norsk, icelandic, interlingua, tur
kish, coptic, romanian, welsh, serbian, slovenian, estonian, esperanto, upperso
rbian, indonesian, polish, portuguese, spanish, catalan, galician, swedish, loa
ded.
(/usr/share/texmf-texlive/tex/latex/base/article.cls
Document Class: article 2005/09/16 v1.4f Standard LaTeX document class
(/usr/share/texmf-texlive/tex/latex/base/size10.clo
File: size10.clo 2005/09/16 v1.4f Standard LaTeX file (size option)
)
\c@part=\count79
\c@section=\count80
\c@subsection=\count81
\c@subsubsection=\count82
\c@paragraph=\count83
\c@subparagraph=\count84
\c@figure=\count85
\c@table=\count86
\abovecaptionskip=\skip41
\belowcaptionskip=\skip42
\bibindent=\dimen102
)
(/usr/share/texmf-texlive/tex/latex/base/inputenc.sty
Package: inputenc 2006/05/05 v1.1b Input encoding file
\inpenc@prehook=\toks14
\inpenc@posthook=\toks15

(/usr/share/texmf-texlive/tex/latex/ucs/utf8x.def
File: utf8x.def 2004/10/17 UCS: Input encoding UTF-8
))
(/usr/share/texmf-texlive/tex/latex/ucs/ucs.sty
Package: ucs 2004/10/17 UCS: Unicode input support

(/usr/share/texmf-texlive/tex/latex/ucs/data/uni-global.def
File: uni-global.def 2004/10/17 UCS: Unicode global data
)
\uc@secondtry=\count87
\uc@combtoks=\toks16
\uc@combtoksb=\toks17
\uc@temptokena=\toks18
) (./tex.aux)
\openout1 = `tex.aux'.

LaTeX Font Info:    Checking defaults for OML/cmm/m/it on input line 5.
LaTeX Font Info:    ... okay on input line 5.
LaTeX Font Info:    Checking defaults for T1/cmr/m/n on input line 5.
LaTeX Font Info:    ... okay on input line 5.
LaTeX Font Info:    Checking defaults for OT1/cmr/m/n on input line 5.
LaTeX Font Info:    ... okay on input line 5.
LaTeX Font Info:    Checking defaults for OMS/cmsy/m/n on input line 5.
LaTeX Font Info:    ... okay on input line 5.
LaTeX Font Info:    Checking defaults for OMX/cmex/m/n on input line 5.
LaTeX Font Info:    ... okay on input line 5.
LaTeX Font Info:    Checking defaults for U/cmr/m/n on input line 5.
LaTeX Font Info:    ... okay on input line 5.

(/usr/share/texmf-texlive/tex/latex/ucs/ucsencs.def
File: ucsencs.def 2003/11/29 Fixes to fontencodings LGR, T3
) (./tex.aux) ) 
Here is how much of TeX's memory you used:
 461 strings out of 94102
 7083 string characters out of 1165833
 63499 words of memory out of 1500000
 3809 multiletter control sequences out of 10000+50000
 3640 words of font info for 14 fonts, out of 1200000 for 2000
 637 hyphenation exceptions out of 8191
 23i,1n,19p,319b,36s stack positions out of 5000i,500n,6000p,200000b,5000s

No pages of output.
```

running pdflatex tex.tex
```
This is pdfTeXk, Version 3.141592-1.40.3 (Web2C 7.5.6) (format=pdflatex 2009.3.14)  14 MAR 2009 16:48
entering extended mode
 %&-line parsing enabled.
**tex.tex
(./tex.tex
LaTeX2e <2005/12/01>
Babel <v3.8h> and hyphenation patterns for english, usenglishmax, dumylang, noh
yphenation, croatian, ukrainian, russian, bulgarian, czech, slovak, danish, dut
ch, finnish, basque, french, german, ngerman, ibycus, greek, monogreek, ancient
greek, hungarian, italian, latin, mongolian, norsk, icelandic, interlingua, tur
kish, coptic, romanian, welsh, serbian, slovenian, estonian, esperanto, upperso
rbian, indonesian, polish, portuguese, spanish, catalan, galician, swedish, loa
ded.
(/usr/share/texmf-texlive/tex/latex/base/article.cls
Document Class: article 2005/09/16 v1.4f Standard LaTeX document class
(/usr/share/texmf-texlive/tex/latex/base/size10.clo
File: size10.clo 2005/09/16 v1.4f Standard LaTeX file (size option)
)
\c@part=\count79
\c@section=\count80
\c@subsection=\count81
\c@subsubsection=\count82
\c@paragraph=\count83
\c@subparagraph=\count84
\c@figure=\count85
\c@table=\count86
\abovecaptionskip=\skip41
\belowcaptionskip=\skip42
\bibindent=\dimen102
)
(/usr/share/texmf-texlive/tex/latex/base/inputenc.sty
Package: inputenc 2006/05/05 v1.1b Input encoding file
\inpenc@prehook=\toks14
\inpenc@posthook=\toks15

(/usr/share/texmf-texlive/tex/latex/ucs/utf8x.def
File: utf8x.def 2004/10/17 UCS: Input encoding UTF-8
))
(/usr/share/texmf-texlive/tex/latex/ucs/ucs.sty
Package: ucs 2004/10/17 UCS: Unicode input support

(/usr/share/texmf-texlive/tex/latex/ucs/data/uni-global.def
File: uni-global.def 2004/10/17 UCS: Unicode global data
)
\uc@secondtry=\count87
\uc@combtoks=\toks16
\uc@combtoksb=\toks17
\uc@temptokena=\toks18
) (./tex.aux)
\openout1 = `tex.aux'.

LaTeX Font Info:    Checking defaults for OML/cmm/m/it on input line 5.
LaTeX Font Info:    ... okay on input line 5.
LaTeX Font Info:    Checking defaults for T1/cmr/m/n on input line 5.
LaTeX Font Info:    ... okay on input line 5.
LaTeX Font Info:    Checking defaults for OT1/cmr/m/n on input line 5.
LaTeX Font Info:    ... okay on input line 5.
LaTeX Font Info:    Checking defaults for OMS/cmsy/m/n on input line 5.
LaTeX Font Info:    ... okay on input line 5.
LaTeX Font Info:    Checking defaults for OMX/cmex/m/n on input line 5.
LaTeX Font Info:    ... okay on input line 5.
LaTeX Font Info:    Checking defaults for U/cmr/m/n on input line 5.
LaTeX Font Info:    ... okay on input line 5.

(/usr/share/texmf-texlive/tex/latex/ucs/ucsencs.def
File: ucsencs.def 2003/11/29 Fixes to fontencodings LGR, T3
) (./tex.aux) ) 
Here is how much of TeX's memory you used:
 461 strings out of 94101
 7083 string characters out of 1165810
 63499 words of memory out of 1500000
 3809 multiletter control sequences out of 10000+50000
 3640 words of font info for 14 fonts, out of 1200000 for 2000
 637 hyphenation exceptions out of 8191
 23i,1n,19p,319b,36s stack positions out of 5000i,500n,6000p,200000b,5000s

No pages of output.
PDF statistics:
 0 PDF objects out of 1000 (max. 8388607)
 0 named destinations out of 1000 (max. 131072)
 1 words of extra memory for PDF output out of 10000 (max. 10000000)
```

---

### Post by firefly2442 on 2009-03-14
Well, for searching for things, I usually just go into synaptic and search for them.  Then you can click on package names and see a detailed description.

So you said it works when you use sudo?  Is there a difference in the Texmaker configuration between sudo versus your regular user?

Can you try a different latex source (something really really simple) and see if it compiles?

Other than that I'm kinda out of ideas, maybe try Kile and see if it works?....

Good luck. :)

---

### Post by silbar on 2009-05-07
Greetings, Happy-Dude

> **Happy-Dude said:**
> 
I've installed Texmaker.
However, I'm running into a problem generating previews.
When I hit Quick Build. Which should work, but returns an error:

Here are my Texmaker configuration paths:
```

latex -interaction=nonstopmode %.tex
dvips -o texout.ps %.dvi
bibtex %.aux
makeindex %.idx
evince %.dvi
evince %.ps
pdflatex -interaction=nonstopmode %.tex
dvipdfm %.dvi
ps2pdf %.ps
evince %.pdf
mpost --interaction nonstopmode 
gs

```


I too had some trouble generating a Quick Build display.  In my case, what now works has some differences in the configuration window,  In particular, instead of the three evince lines, I have "Dvi Viewer xdvi %.dvi", "PS Viewer gv %.ps", and "Pdf Viewer spdf %.pdf".  I recall I had to install gv before this would work.

It may be the difference is that you are using KDE instead of Gnome?  Or, you haven't installed Texmaker 1.7?

Dick Silbar

---

### Post by moehfi on 2009-06-26
I've used Texmaker and found this problem too.
Is there anyway to fix it?
is this a bug?

This is My Log file :
```
This is pdfTeXk, Version 3.141592-1.40.3 (Web2C 7.5.6) (format=latex 2009.5.29)  27 JUN 2009 01:07
entering extended mode
 %&-line parsing enabled.
**proposal_ta_mupi.tex
(./proposal_ta_mupi.tex
LaTeX2e <2005/12/01>
Babel <v3.8h> and hyphenation patterns for english, usenglishmax, dumylang, noh
yphenation, loaded.
(/usr/share/texmf-texlive/tex/latex/base/book.cls
Document Class: book 2005/09/16 v1.4f Standard LaTeX document class
(/usr/share/texmf-texlive/tex/latex/base/bk12.clo
File: bk12.clo 2005/09/16 v1.4f Standard LaTeX file (size option)Xmaker
)
\c@part=\count79
\c@chapter=\count80
\c@section=\count81
\c@subsection=\count82
\c@subsubsection=\count83
\c@paragraph=\count84
\c@subparagraph=\count85
\c@figure=\count86
\c@table=\count87
\abovecaptionskip=\skip41
\belowcaptionskip=\skip42
\bibindent=\dimen102
)
(/usr/share/texmf-texlive/tex/latex/graphics/graphicx.sty
Package: graphicx 1999/02/16 v1.0f Enhanced LaTeX Graphics (DPC,SPQR)

(/usr/share/texmf-texlive/tex/latex/graphics/keyval.sty
Package: keyval 1999/03/16 v1.13 key=value parser (DPC)
\KV@toks@=\toks14
)
(/usr/share/texmf-texlive/tex/latex/graphics/graphics.sty
Package: graphics 2006/02/20 v1.0o Standard LaTeX Graphics (DPC,SPQR)

(/usr/share/texmf-texlive/tex/latex/graphics/trig.sty
Package: trig 1999/03/16 v1.09 sin cos tan (DPC)
)
(/etc/texmf/tex/latex/config/graphics.cfg
File: graphics.cfg 2007/01/18 v1.5 graphics configuration of teTeX/TeXLive
)
Package graphics Info: Driver file: pdftex.def on input line 90.

(/usr/share/texmf-texlive/tex/latex/pdftex-def/pdftex.def
File: pdftex.def 2007/01/08 v0.04d Graphics/color for pdfTeX
\Gread@gobject=\count88
))
\Gin@req@height=\dimen103
\Gin@req@width=\dimen104
)
(/usr/share/texmf-texlive/tex/latex/graphics/color.sty
Package: color 2005/11/14 v1.0j Standard LaTeX Color (DPC)

(/etc/texmf/tex/latex/config/color.cfg
File: color.cfg 2007/01/18 v1.5 color configuration of teTeX/TeXLive
)
Package color Info: Driver file: pdftex.def on input line 130.

(/usr/share/texmf-texlive/tex/latex/graphics/dvipsnam.def
File: dvipsnam.def 1999/02/16 v3.0i Driver-dependant file (DPC,SPQR)
))
(/usr/share/texmf-texlive/tex/latex/geometry/geometry.sty
Package: geometry 2002/07/08 v3.2 Page Geometry
\Gm@cnth=\count89
\Gm@cntv=\count90
\c@Gm@tempcnt=\count91
\Gm@bindingoffset=\dimen105
\Gm@wd@mp=\dimen106
\Gm@odd@mp=\dimen107
\Gm@even@mp=\dimen108
\Gm@dimlist=\toks15
)
(/usr/share/texmf-texlive/tex/latex/hyperref/hyperref.sty
Package: hyperref 2007/02/07 v6.75r Hypertext links for LaTeX
\@linkdim=\dimen109
\Hy@linkcounter=\count92
\Hy@pagecounter=\count93

(/usr/share/texmf-texlive/tex/latex/hyperref/pd1enc.def
File: pd1enc.def 2007/02/07 v6.75r Hyperref: PDFDocEncoding definition (HO)
)
(/etc/texmf/tex/latex/config/hyperref.cfg
File: hyperref.cfg 2002/06/06 v1.2 hyperref configuration of TeXLive
)
(/usr/share/texmf-texlive/tex/latex/oberdiek/kvoptions.sty
Package: kvoptions 2006/08/22 v2.4 Connects package keyval with LaTeX options (
HO)
)
Package hyperref Info: Option `final' set `true' on input line 2238.
Package hyperref Info: Option `colorlinks' set `true' on input line 2238.
Package hyperref Info: Hyper figures OFF on input line 2288.
Package hyperref Info: Link nesting OFF on input line 2293.
Package hyperref Info: Hyper index ON on input line 2296.
Package hyperref Info: Plain pages OFF on input line 2303.
Package hyperref Info: Backreferencing OFF on input line 2308.

Implicit mode ON; LaTeX internals redefined
Package hyperref Info: Bookmarks ON on input line 2444.
(/usr/share/texmf-texlive/tex/latex/ltxmisc/url.sty
\Urlmuskip=\muskip10
Package: url 2005/06/27  ver 3.2  Verb mode for urls, etc.
)
LaTeX Info: Redefining \url on input line 2599.
\Fld@menulength=\count94
\Field@Width=\dimen110
\Fld@charsize=\dimen111
\Choice@toks=\toks16
\Field@toks=\toks17
Package hyperref Info: Hyper figures OFF on input line 3102.
Package hyperref Info: Link nesting OFF on input line 3107.
Package hyperref Info: Hyper index ON on input line 3110.
Package hyperref Info: backreferencing OFF on input line 3117.
Package hyperref Info: Link coloring ON on input line 3120.
\Hy@abspage=\count95
\c@Item=\count96
\c@Hfootnote=\count97
)
*hyperref using driver hpdftex*
(/usr/share/texmf-texlive/tex/latex/hyperref/hpdftex.def
File: hpdftex.def 2007/02/07 v6.75r Hyperref driver for pdfTeX
\Fld@listcount=\count98
)
(/usr/share/texmf-texlive/tex/latex/graphics/lscape.sty
Package: lscape 2000/10/22 v3.01 Landscape Pages (DPC)
)
(/usr/share/texmf-texlive/tex/latex/tools/longtable.sty
Package: longtable 2004/02/01 v4.11 Multi-page Table package (DPC)
\LTleft=\skip43
\LTright=\skip44
\LTpre=\skip45
\LTpost=\skip46
\LTchunksize=\count99
\LTcapwidth=\dimen112
\LT@head=\box26
\LT@firsthead=\box27
\LT@foot=\box28
\LT@lastfoot=\box29
\LT@cols=\count100
\LT@rows=\count101
\c@LT@tables=\count102
\c@LT@chunks=\count103
\LT@p@ftn=\toks18
)
(/usr/share/texmf-texlive/tex/latex/setspace/setspace.sty
Package: setspace 2000/12/01 6.7 Contributed and Supported LaTeX2e package

Package: `setspace' 6.7 <2000/12/01>
) (/usr/share/texmf-texlive/tex/generic/babel/babel.sty
Package: babel 2005/11/23 v3.8h The Babel package

(/usr/share/texmf-texlive/tex/generic/babel/bahasai.ldf
Language: bahasa 2005/11/23 v1.0k Bahasa Indonesia support from the babel syste
m

(/usr/share/texmf-texlive/tex/generic/babel/babel.def
File: babel.def 2005/11/23 v3.8h Babel common definitions
\babel@savecnt=\count104
\U@D=\dimen113
)

Package babel Warning: No hyphenation patterns were loaded for
(babel)                the language `Bahasa Indonesia'
(babel)                I will use the patterns loaded for \language=0 instead.

\l@bahasa = a dialect from \language0
)) (/usr/share/texmf-texlive/tex/latex/fancyhdr/fancyhdr.sty
\fancy@headwidth=\skip47
\f@ncyO@elh=\skip48
\f@ncyO@erh=\skip49
\f@ncyO@olh=\skip50
\f@ncyO@orh=\skip51
\f@ncyO@elf=\skip52
\f@ncyO@erf=\skip53
\f@ncyO@olf=\skip54
\f@ncyO@orf=\skip55
)
(/usr/share/texmf-texlive/tex/latex/lastpage/lastpage.sty
Package: lastpage 1994/06/25 v0.1b LaTeX2e package for refs to last page number
 (JPG)
)
(/usr/share/texmf-texlive/tex/latex/fncychap/fncychap.sty
Package: fncychap 2004/09/21 v1.33 LaTeX package (Revised chapters)
\RW=\skip56
\mylen=\skip57
\myhi=\skip58
\px=\skip59
\py=\skip60
\pyy=\skip61
\pxx=\skip62
)
(/usr/share/texmf-texlive/tex/latex/pstricks/pstricks.sty
Package: pstricks 2006/08/10 v0.32 LaTeX wrapper for `PSTricks' (RN,HV)

(/usr/share/texmf-texlive/tex/generic/pstricks/pstricks.tex
`PSTricks' v1.15  <2006/12/22> (tvz)
\pst@dima=\dimen114
\pst@dimb=\dimen115
\pst@dimc=\dimen116
\pst@dimd=\dimen117
\pst@dimg=\dimen118
\pst@dimh=\dimen119
\pst@hbox=\box30
\pst@boxg=\box31
\pst@cnta=\count105
\pst@cntb=\count106
\pst@cntc=\count107
\pst@cntd=\count108
\pst@cntg=\count109
\pst@cnth=\count110
\pst@toks=\toks19
(/usr/share/texmf-texlive/tex/generic/pstricks/pstricks.con)
\psunit=\dimen120
\psxunit=\dimen121
\psyunit=\dimen122
\pslinewidth=\dimen123
\pst@customdefs=\toks20
\pslinearc=\dimen124
\everypsbox=\toks21
\psframesep=\dimen125
\pslabelsep=\dimen126
\psk@shift=\dimen127
\pst@shift=\dimen128
\theoverlaybox=\box32
)
File: pstricks.tex 2006/12/22 v1.15 `PSTricks' (tvz)

(/usr/share/texmf/tex/latex/xcolor/xcolor.sty
Package: xcolor 2007/01/21 v2.11 LaTeX color extensions (UK)

(/etc/texmf/tex/latex/config/color.cfg
File: color.cfg 2007/01/18 v1.5 color configuration of teTeX/TeXLive
)
Package xcolor Info: Package option `override' ignored on input line 216.
Package xcolor Info: Driver file: pdftex.def on input line 225.
LaTeX Info: Redefining \color on input line 702.
Package xcolor Info: Model `cmy' substituted by `cmy0' on input line 1337.
Package xcolor Info: Model `hsb' substituted by `rgb' on input line 1341.
Package xcolor Info: Model `RGB' extended on input line 1353.
Package xcolor Info: Model `HTML' substituted by `rgb' on input line 1355.
Package xcolor Info: Model `Hsb' substituted by `hsb' on input line 1356.
Package xcolor Info: Model `tHsb' substituted by `hsb' on input line 1357.
Package xcolor Info: Model `HSB' substituted by `hsb' on input line 1358.
Package xcolor Info: Model `Gray' substituted by `gray' on input line 1359.
Package xcolor Info: Model `wave' substituted by `hsb' on input line 1360.
))
Package hyperref Info: Option `bookmarksnumbered' set `true' on input line 23.
Package hyperref Info: Option `bookmarksnumbered' set `true' on input line 48.
 (./proposal_ta_mupi.aux)
\openout1 = `proposal_ta_mupi.aux'.

LaTeX Font Info:    Checking defaults for OML/cmm/m/it on input line 88.
LaTeX Font Info:    ... okay on input line 88.
LaTeX Font Info:    Checking defaults for T1/cmr/m/n on input line 88.
LaTeX Font Info:    ... okay on input line 88.
LaTeX Font Info:    Checking defaults for OT1/cmr/m/n on input line 88.
LaTeX Font Info:    ... okay on input line 88.
LaTeX Font Info:    Checking defaults for OMS/cmsy/m/n on input line 88.
LaTeX Font Info:    ... okay on input line 88.
LaTeX Font Info:    Checking defaults for OMX/cmex/m/n on input line 88.
LaTeX Font Info:    ... okay on input line 88.
LaTeX Font Info:    Checking defaults for U/cmr/m/n on input line 88.
LaTeX Font Info:    ... okay on input line 88.
LaTeX Font Info:    Checking defaults for PD1/pdf/m/n on input line 88.
LaTeX Font Info:    ... okay on input line 88.
-------------------- Geometry parameters
paper: a4paper
landscape: --
twocolumn: --
twoside: --
asymmetric: --
h-parts: 113.81102pt, 398.3386pt, 85.35826pt
v-parts: 113.81102pt, 645.87756pt, 85.35826pt
hmarginratio: --
vmarginratio: --
lines: --
heightrounded: --Xmaker
bindingoffset: 0.0pt
truedimen: --
includehead: true
includefoot: true
includemp: --
driver: pdftex
-------------------- Page layout dimensions and switches
\paperwidth  597.50787pt
\paperheight 845.04684pt
\textwidth  398.3386pt
\textheight 584.00377pt
\oddsidemargin  41.54103pt
\evensidemargin 41.54103pt
\topmargin  41.54103pt
\headheight 12.0pt
\headsep    19.8738pt
\footskip   30.0pt
\marginparwidth 38.0pt
\marginparsep   7.0pt
\columnsep  10.0pt
\skip\footins  10.8pt plus 4.0pt minus 2.0pt
\hoffset 0.0pt
\voffset 0.0pt
\mag 1000

(1in=72.27pt, 1cm=28.45pt)
-----------------------
Package hyperref Info: Link coloring ON on input line 88.

(/usr/share/texmf-texlive/tex/latex/hyperref/nameref.sty
Package: nameref 2006/12/27 v2.28 Cross-referencing by name of section

(/usr/share/texmf-texlive/tex/latex/oberdiek/refcount.sty
Package: refcount 2006/02/20 v3.0 Data extraction from references (HO)
)
\c@section@level=\count111
)
LaTeX Info: Redefining \ref on input line 88.
LaTeX Info: Redefining \pageref on input line 88.

(./proposal_ta_mupi.out) (./proposal_ta_mupi.out)
\@outlinefile=\write3
\openout3 = `proposal_ta_mupi.out'.

LaTeX Font Info:    External font `cmex10' loaded for size
(Font)              <12> on input line 103.
LaTeX Font Info:    External font `cmex10' loaded for size
(Font)              <8> on input line 103.
LaTeX Font Info:    External font `cmex10' loaded for size
(Font)              <6> on input line 103.

<./images/logoUSU.png, id=7, 88.85655pt x 88.85655pt>
File: ./images/logoUSU.png Graphic file (type png)

<use ./images/logoUSU.png> [1
Non-PDF special ignored!
Non-PDF special ignored!


{/var/lib/texmf/fonts/map/pdftex/updmap/pdftex.map} <./images/logoUSU.png>] AED
: lastpage setting LastPage (./proposal_ta_mupi.aux) ) 
Here is how much of TeX's memory you used:
 4929 strings out of 95087
 64703 string characters out of 1183278
 149381 words of memory out of 1500000
 8033 multiletter control sequences out of 10000+50000
 7903 words of font info for 28 fonts, out of 1200000 for 2000
 51 hyphenation exceptions out of 8191
 30i,6n,43p,292b,366s stack positions out of 5000i,500n,6000p,200000b,5000s
</usr/share/texmf-texlive
/fonts/type1/bluesky/cm/cmbx12.pfb></usr/share/texmf-texlive/fonts/type1/bluesk
y/cm/cmr12.pfb>
Output written on proposal_ta_mupi.pdf (1 page, 74812 bytes).
PDF statistics:
 25 PDF objects out of 1000 (max. 8388607)
 2 named destinations out of 1000 (max. 131072)
 22 words of extra memory for PDF output out of 10000 (max. 10000000)

```

---

