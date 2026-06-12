---
title: "LyX templates and Ubuntu"
date: 2012-02-04
forum: Education &amp; Science
---

### Post by ASav on 2012-02-04
Hello,
I am unable to use the aea.lyx journals (for American economic  association journals). When I try to access it (aea.lyx is  pre-installed) I get the following message:

  [CENTER]*The selected document class*[/CENTER]
 [CENTER][/CENTER]
 [CENTER]*	article (American Economic Association)*[/CENTER]
 [CENTER][/CENTER]
 [CENTER]*requires external files that are not available.*[/CENTER]
 [CENTER][/CENTER]
 [CENTER]*The document class can still be used, but the*[/CENTER]
 [CENTER][/CENTER]
 [CENTER]*document cannot be compiled until the following*[/CENTER]
 [CENTER][/CENTER]
 [CENTER]*prerequisites are installed:*[/CENTER]
 [CENTER][/CENTER]
 [CENTER]*	AEA.cls*[/CENTER]
 [CENTER][/CENTER]
 [CENTER]*	harvard.sty*[/CENTER]
 [CENTER][/CENTER]
 [CENTER]*See section 3.1.2.2 (Class Availability) of the*[/CENTER]
 [CENTER][/CENTER]
 [CENTER]*User's Guide for more information.*[/CENTER]
 (I understand this problem occurs for several document classes that appear as 'unavailable' in  documents>settings>document class). A generic solution would be useful as I may use some of the other templates e.g. CV and thesis.

I downloaded the archive file provided on the following page (Step  1) [http://wiki.lyx.org/Examples/AEA](http://wiki.lyx.org/Examples/AEA) (i understand this contains  AEA.cls, but it does not contain Harvard.sty, which is another point of  confusion). I extracted these files, excluding the .sty ones (as instructed), to  usr/local/share/texmf. I then reconfigured in lyx and tried the 'sudo  texhash' command. Still the same error message arises when I go onto lyx  and try to open aea.lyx. I also tried by extracting the files to  usr/share/lyx/templates and doing the same. Still I fail. 

Please can I have some help?

I have tried gleaning help from the Mac page [http://wiki.lyx.org/FAQ/MacInstall](http://wiki.lyx.org/FAQ/MacInstall) which relates to this, but I suppose this is over-complicating the problem as I am using Ubuntu Ocelot.

Thank you

---

### Post by ASav on 2012-02-04
I overcame this problem by extracting the files to usr/share/texmf/tex/latex/lyx instead of the two paths I tried in the previous comment. So, now I can open the template so it appears in the lyx window. However, when I try to compile, so I can view, I get the following errors:

```
This is pdfTeX, Version 3.1415926-1.40.10 (TeX Live 2009/Debian) (format=pdflatex 2012.2.3)  4 FEB 2012 14:48
entering extended mode
 %&-line parsing enabled.
**newfile1.tex
(./newfile1.tex
LaTeX2e <2009/09/24>
Babel <v3.8l> and hyphenation patterns for english, usenglishmax, dumylang, noh
yphenation, loaded.

(/usr/share/texmf/tex/latex/lyx/latex_templates/AEA.cls
Document Class: AEA 2011/07/24 American Economic Association Article Classes
(/usr/share/texmf-texlive/tex/latex/tools/multicol.sty
Package: multicol 2008/12/05 v1.6h multicolumn formatting (FMi)
\c@tracingmulticols=\count79
\mult@box=\box26
\multicol@leftmargin=\dimen102
\c@unbalance=\count80
\c@collectmore=\count81
\doublecol@number=\count82
\multicoltolerance=\count83
\multicolpretolerance=\count84
\full@width=\dimen103
\page@free=\dimen104
\premulticols=\dimen105
\postmulticols=\dimen106
\multicolsep=\skip41
\multicolbaselineskip=\skip42
\partial@page=\box27
\last@line=\box28
\mult@rightbox=\box29
\mult@grightbox=\box30
\mult@gfirstbox=\box31
\mult@firstbox=\box32
\@tempa=\box33
\@tempa=\box34
\@tempa=\box35
\@tempa=\box36
\@tempa=\box37
\@tempa=\box38
\@tempa=\box39
\@tempa=\box40
\@tempa=\box41
\@tempa=\box42
\@tempa=\box43
\@tempa=\box44
\@tempa=\box45
\@tempa=\box46
\@tempa=\box47
\@tempa=\box48
\@tempa=\box49
\c@columnbadness=\count85
\c@finalcolumnbadness=\count86
\last@try=\dimen107
\multicolovershoot=\dimen108
\multicolundershoot=\dimen109
\mult@nat@firstbox=\box50
\colbreak@box=\box51
) (/usr/share/texmf-texlive/tex/latex/setspace/setspace.sty
Package: setspace 2000/12/01 6.7 Contributed and Supported LaTeX2e package
Package: `setspace' 6.7 <2000/12/01>
) (/usr/share/texmf-texlive/tex/latex/amsmath/amsmath.sty
Package: amsmath 2000/07/18 v2.13 AMS math features
\@mathmargin=\skip43
For additional information on amsmath, use the `?' option.
(/usr/share/texmf-texlive/tex/latex/amsmath/amstext.sty
Package: amstext 2000/06/29 v2.01
(/usr/share/texmf-texlive/tex/latex/amsmath/amsgen.sty
File: amsgen.sty 1999/11/30 v2.0
\@emptytoks=\toks14
\ex@=\dimen110
)) (/usr/share/texmf-texlive/tex/latex/amsmath/amsbsy.sty
Package: amsbsy 1999/11/29 v1.2d
\pmbraise@=\dimen111
) (/usr/share/texmf-texlive/tex/latex/amsmath/amsopn.sty
Package: amsopn 1999/12/14 v2.01 operator names
)
\inf@bad=\count87
LaTeX Info: Redefining \frac on input line 211.
\uproot@=\count88
\leftroot@=\count89
LaTeX Info: Redefining \overline on input line 307.
\classnum@=\count90
\DOTSCASE@=\count91
LaTeX Info: Redefining \ldots on input line 379.
LaTeX Info: Redefining \dots on input line 382.
LaTeX Info: Redefining \cdots on input line 467.
\Mathstrutbox@=\box52
\strutbox@=\box53
\big@size=\dimen112
LaTeX Font Info:    Redeclaring font encoding OML on input line 567.
LaTeX Font Info:    Redeclaring font encoding OMS on input line 568.
\macc@depth=\count92
\c@MaxMatrixCols=\count93
\dotsspace@=\muskip10
\c@parentequation=\count94
\dspbrk@lvl=\count95
\tag@help=\toks15
\row@=\count96
\column@=\count97
\maxfields@=\count98
\andhelp@=\toks16
\eqnshift@=\dimen113
\alignsep@=\dimen114
\tagshift@=\dimen115
\tagwidth@=\dimen116
\totwidth@=\dimen117
\lineht@=\dimen118
\@envbody=\toks17
\multlinegap=\skip44
\multlinetaggap=\skip45
\mathdisplay@stack=\toks18
LaTeX Info: Redefining \[ on input line 2666.
LaTeX Info: Redefining \] on input line 2667.
)
Journal Selected: THE AMERICAN ECONOMIC REVIEW
Mode Selected: final
\abstractIndent=\skip46
\abstractWidth=\skip47
\c@part=\count99
\c@section=\count100
\c@subsection=\count101
\c@subsubsection=\count102
\c@paragraph=\count103
\c@subparagraph=\count104
\c@figure=\count105
\c@table=\count106
\abovecaptionskip=\skip48
\belowcaptionskip=\skip49
\bibindent=\dimen119
) (/usr/share/texmf-texlive/tex/latex/base/fontenc.sty
Package: fontenc 2005/09/27 v1.99g Standard LaTeX package
(/usr/share/texmf-texlive/tex/latex/base/t1enc.def
File: t1enc.def 2005/09/27 v1.99g Standard LaTeX file
LaTeX Font Info:    Redeclaring font encoding T1 on input line 43.
)
! Font T1/cmr/m/n/10.95=dcr10 at 11.0pt not loadable: Metric (TFM) file not fou
nd.
<to be read again> 
                   relax 
l.100 \fontencoding\encodingdefault\selectfont
                                              
I wasn't able to read the size data for this font,
so I will ignore the font specification.
[Wizards can fix TFM files using TFtoPL/PLtoTF.]
You might try inserting a different font spec;
e.g., type `I\font<same font id>=<substitute font name>'.

! Font \T1/cmr/m/n/11=nullfont not loadable: Metric (TFM) file not found.
<to be read again> 
                   \relax 
l.100 \fontencoding\encodingdefault\selectfont
                                              
I wasn't able to read the size data for this font,
so I will ignore the font specification.
[Wizards can fix TFM files using TFtoPL/PLtoTF.]
You might try inserting a different font spec;
e.g., type `I\font<same font id>=<substitute font name>'.

) (/usr/share/texmf-texlive/tex/latex/base/inputenc.sty
Package: inputenc 2008/03/30 v1.1d Input encoding file
\inpenc@prehook=\toks19
\inpenc@posthook=\toks20
(/usr/share/texmf/tex/latex/html/latin9.def
File: latin1.def 1998/03/05 v0.97 Input encoding file(test version: still liabl
e to change)
)) (/usr/share/texmf/tex/latex/lyx/harvard/harvard.sty
Package: harvard 
(/usr/share/texmf-texlive/tex/latex/base/ifthen.sty
Package: ifthen 2001/05/26 v1.1c Standard LaTeX ifthen package (DPC)
) (/usr/share/texmf/tex/latex/html/html.sty (/usr/share/texmf-texlive/tex/latex
/hyperref/hyperref.sty
Package: hyperref 2009/10/09 v6.79a Hypertext links for LaTeX
(/usr/share/texmf-texlive/tex/latex/graphics/keyval.sty
Package: keyval 1999/03/16 v1.13 key=value parser (DPC)
\KV@toks@=\toks21
) (/usr/share/texmf-texlive/tex/generic/oberdiek/ifpdf.sty
Package: ifpdf 2009/04/10 v2.0 Provides the ifpdf switch (HO)
Package ifpdf Info: pdfTeX in pdf mode detected.
) (/usr/share/texmf-texlive/tex/generic/oberdiek/ifvtex.sty
Package: ifvtex 2008/11/04 v1.4 Switches for detecting VTeX and its modes (HO)
Package ifvtex Info: VTeX not detected.
) (/usr/share/texmf-texlive/tex/generic/ifxetex/ifxetex.sty
Package: ifxetex 2009/01/23 v0.5 Provides ifxetex conditional
) (/usr/share/texmf-texlive/tex/latex/oberdiek/hycolor.sty
Package: hycolor 2009/10/02 v1.5 Code for color options of hyperref/bookmark (H
O)
(/usr/share/texmf-texlive/tex/latex/oberdiek/xcolor-patch.sty
Package: xcolor-patch 2009/10/02 xcolor patch
))
\@linkdim=\dimen120
\Hy@linkcounter=\count107
\Hy@pagecounter=\count108
(/usr/share/texmf-texlive/tex/latex/hyperref/pd1enc.def
File: pd1enc.def 2009/10/09 v6.79a Hyperref: PDFDocEncoding definition (HO)
) (/usr/share/texmf-texlive/tex/generic/oberdiek/etexcmds.sty
Package: etexcmds 2007/12/12 v1.2 Prefix for e-TeX command names (HO)
(/usr/share/texmf-texlive/tex/generic/oberdiek/infwarerr.sty
Package: infwarerr 2007/09/09 v1.2 Providing info/warning/message (HO)
)
Package etexcmds Info: Could not find \expanded.
(etexcmds)             That can mean that you are not using pdfTeX 1.50 or
(etexcmds)             that some package has redefined \expanded.
(etexcmds)             In the latter case, load this package earlier.
) (/usr/share/texmf-texlive/tex/latex/latexconfig/hyperref.cfg
File: hyperref.cfg 2002/06/06 v1.2 hyperref configuration of TeXLive
) (/usr/share/texmf-texlive/tex/latex/oberdiek/kvoptions.sty
Package: kvoptions 2009/08/13 v3.4 Keyval support for LaTeX options (HO)
(/usr/share/texmf-texlive/tex/generic/oberdiek/kvsetkeys.sty
Package: kvsetkeys 2009/07/30 v1.5 Key value parser with default handler suppor
t (HO)
))
Package hyperref Info: Hyper figures OFF on input line 2975.
Package hyperref Info: Link nesting OFF on input line 2980.
Package hyperref Info: Hyper index ON on input line 2983.
Package hyperref Info: Plain pages OFF on input line 2990.
Package hyperref Info: Backreferencing OFF on input line 2995.
Implicit mode ON; LaTeX internals redefined
Package hyperref Info: Bookmarks ON on input line 3191.
(/usr/share/texmf-texlive/tex/latex/ltxmisc/url.sty
\Urlmuskip=\muskip11
Package: url 2006/04/12  ver 3.3  Verb mode for urls, etc.
)
LaTeX Info: Redefining \url on input line 3428.
(/usr/share/texmf-texlive/tex/generic/oberdiek/bitset.sty
Package: bitset 2007/09/28 v1.0 Data type bit set (HO)
(/usr/share/texmf-texlive/tex/generic/oberdiek/intcalc.sty
Package: intcalc 2007/09/27 v1.1 Expandable integer calculations (HO)
) (/usr/share/texmf-texlive/tex/generic/oberdiek/bigintcalc.sty
Package: bigintcalc 2007/11/11 v1.1 Expandable big integer calculations (HO)
(/usr/share/texmf-texlive/tex/generic/oberdiek/pdftexcmds.sty
Package: pdftexcmds 2009/09/23 v0.6 LuaTeX support for pdfTeX utility functions
 (HO)
(/usr/share/texmf-texlive/tex/generic/oberdiek/ifluatex.sty
Package: ifluatex 2009/04/17 v1.2 Provides the ifluatex switch (HO)
Package ifluatex Info: LuaTeX not detected.
) (/usr/share/texmf-texlive/tex/generic/oberdiek/ltxcmds.sty
Package: ltxcmds 2009/08/05 v1.0 Some LaTeX kernel commands for general use (HO
)
)
Package pdftexcmds Info: LuaTeX not detected.
Package pdftexcmds Info: \pdf@primitive is available.
Package pdftexcmds Info: \pdf@ifprimitive is available.
)))
\Fld@menulength=\count109
\Field@Width=\dimen121
\Fld@charsize=\dimen122
\Field@toks=\toks22
Package hyperref Info: Hyper figures OFF on input line 4377.
Package hyperref Info: Link nesting OFF on input line 4382.
Package hyperref Info: Hyper index ON on input line 4385.
Package hyperref Info: backreferencing OFF on input line 4392.
Package hyperref Info: Link coloring OFF on input line 4397.
Package hyperref Info: Link coloring with OCG OFF on input line 4402.
Package hyperref Info: PDF/A mode OFF on input line 4407.
(/usr/share/texmf-texlive/tex/generic/oberdiek/atbegshi.sty
Package: atbegshi 2008/07/31 v1.9 At begin shipout hook (HO)
)
\Hy@abspage=\count110
\c@Item=\count111
\c@Hfootnote=\count112
)
*hyperref using driver hpdftex*
(/usr/share/texmf-texlive/tex/latex/hyperref/hpdftex.def
File: hpdftex.def 2009/10/09 v6.79a Hyperref driver for pdfTeX
\Fld@listcount=\count113
)
Package: html 1999/07/19 v1.38 hypertext commands for latex2html (nd, hws, rrm)

\c@lpart=\count114
\c@lchapter=\count115
\c@chapter=\count116
\c@lsection=\count117
\c@lsubsection=\count118
\c@lsubsubsection=\count119
\c@lparagraph=\count120
\c@lsubparagraph=\count121
\c@lsubsubparagraph=\count122
\ptrfile=\write3
))
\c@remark=\count123
(/usr/share/texmf-texlive/tex/generic/babel/babel.sty
Package: babel 2008/07/06 v3.8l The Babel package
(/usr/share/texmf-texlive/tex/generic/babel/english.ldf
Language: english 2005/03/30 v3.3o English support from the babel system
(/usr/share/texmf-texlive/tex/generic/babel/babel.def
File: babel.def 2008/07/06 v3.8l Babel common definitions
\babel@savecnt=\count124
\U@D=\dimen123
)
\l@british = a dialect from \language\l@english 
\l@UKenglish = a dialect from \language\l@english 
\l@canadian = a dialect from \language\l@american 
\l@australian = a dialect from \language\l@british 
\l@newzealand = a dialect from \language\l@british 
))
No file newfile1.aux.
\openout1 = `newfile1.aux'.

LaTeX Font Info:    Checking defaults for OML/cmm/m/it on input line 32.
LaTeX Font Info:    ... okay on input line 32.
LaTeX Font Info:    Checking defaults for T1/cmr/m/n on input line 32.
LaTeX Font Info:    ... okay on input line 32.
LaTeX Font Info:    Checking defaults for OT1/cmr/m/n on input line 32.
LaTeX Font Info:    ... okay on input line 32.
LaTeX Font Info:    Checking defaults for OMS/cmsy/m/n on input line 32.
LaTeX Font Info:    ... okay on input line 32.
LaTeX Font Info:    Checking defaults for OMX/cmex/m/n on input line 32.
LaTeX Font Info:    ... okay on input line 32.
LaTeX Font Info:    Checking defaults for U/cmr/m/n on input line 32.
LaTeX Font Info:    ... okay on input line 32.
LaTeX Font Info:    Checking defaults for PD1/pdf/m/n on input line 32.
LaTeX Font Info:    ... okay on input line 32.
Package hyperref Info: Link coloring OFF on input line 32.
(/usr/share/texmf-texlive/tex/latex/hyperref/nameref.sty
Package: nameref 2007/05/29 v2.31 Cross-referencing by name of section
(/usr/share/texmf-texlive/tex/latex/oberdiek/refcount.sty
Package: refcount 2008/08/11 v3.1 Data extraction from references (HO)
)
\c@section@level=\count125
)
LaTeX Info: Redefining \ref on input line 32.
LaTeX Info: Redefining \pageref on input line 32.
\@outlinefile=\write4
\openout4 = `newfile1.out'.

\AtBeginShipoutBox=\box54
Package hyperref Info: *** compatibility with harvard ****  on input line 32.
! Font T1/cmr/m/n/14=dcr12 at 14.0pt not loadable: Metric (TFM) file not found.
<to be read again> 
                   relax 
l.63 \begin
           {acknowledgement}
I wasn't able to read the size data for this font,
so I will ignore the font specification.
[Wizards can fix TFM files using TFtoPL/PLtoTF.]
You might try inserting a different font spec;
e.g., type `I\font<same font id>=<substitute font name>'.

! Font T1/cmss/m/n/14=dcss12 at 14.0pt not loadable: Metric (TFM) file not foun
d.
<to be read again> 
                   relax 
l.63 \begin
           {acknowledgement}
I wasn't able to read the size data for this font,
so I will ignore the font specification.
[Wizards can fix TFM files using TFtoPL/PLtoTF.]
You might try inserting a different font spec;
e.g., type `I\font<same font id>=<substitute font name>'.

! Font T1/cmss/bx/n/14=dcssbx10 at 14.0pt not loadable: Metric (TFM) file not f
ound.
<to be read again> 
                   relax 
l.63 \begin
           {acknowledgement}
I wasn't able to read the size data for this font,
so I will ignore the font specification.
[Wizards can fix TFM files using TFtoPL/PLtoTF.]
You might try inserting a different font spec;
e.g., type `I\font<same font id>=<substitute font name>'.

Missing character: There is no T in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no l in font nullfont!
Missing character: There is no e in font nullfont!
! Font T1/cmr/m/it/10.95=dcti10 at 11.0pt not loadable: Metric (TFM) file not f
ound.
<to be read again> 
                   relax 
l.63 \begin
           {acknowledgement}
I wasn't able to read the size data for this font,
so I will ignore the font specification.
[Wizards can fix TFM files using TFtoPL/PLtoTF.]
You might try inserting a different font spec;
e.g., type `I\font<same font id>=<substitute font name>'.

! Font \T1/cmr/m/it/11=nullfont not loadable: Metric (TFM) file not found.
<to be read again> 
                   \relax 
l.63 \begin
           {acknowledgement}
I wasn't able to read the size data for this font,
so I will ignore the font specification.
[Wizards can fix TFM files using TFtoPL/PLtoTF.]
You might try inserting a different font spec;
e.g., type `I\font<same font id>=<substitute font name>'.

Missing character: There is no B in font nullfont!
Missing character: There is no y in font nullfont!
! Font T1/cmr/m/sc/10.95=dccsc10 at 11.0pt not loadable: Metric (TFM) file not 
found.
<to be read again> 
                   relax 
l.63 \begin
           {acknowledgement}
I wasn't able to read the size data for this font,
so I will ignore the font specification.
[Wizards can fix TFM files using TFtoPL/PLtoTF.]
You might try inserting a different font spec;
e.g., type `I\font<same font id>=<substitute font name>'.

! Font \T1/cmr/m/sc/11=nullfont not loadable: Metric (TFM) file not found.
<to be read again> 
                   \relax 
l.63 \begin
           {acknowledgement}
I wasn't able to read the size data for this font,
so I will ignore the font specification.
[Wizards can fix TFM files using TFtoPL/PLtoTF.]
You might try inserting a different font spec;
e.g., type `I\font<same font id>=<substitute font name>'.

Missing character: There is no A in font nullfont!
Missing character: There is no u in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no h in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no 1 in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no d in font nullfont!
Missing character: There is no A in font nullfont!
Missing character: There is no u in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no h in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no 2 in font nullfont!
! Font T1/cmr/m/n/8=dcr8 at 8.0pt not loadable: Metric (TFM) file not found.
<to be read again> 
                   relax 
l.63 \begin
           {acknowledgement}
I wasn't able to read the size data for this font,
so I will ignore the font specification.
[Wizards can fix TFM files using TFtoPL/PLtoTF.]
You might try inserting a different font spec;
e.g., type `I\font<same font id>=<substitute font name>'.

Missing character: There is no Y in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no u in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no b in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no c in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no h in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no ( in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no x in font nullfont!
Missing character: There is no c in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no p in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no f in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no J in font nullfont!
Missing character: There is no E in font nullfont!
Missing character: There is no P in font nullfont!
Missing character: There is no / in font nullfont!
Missing character: There is no P in font nullfont!
Missing character: There is no P in font nullfont!
Missing character: There is no ) in font nullfont!
Missing character: There is no . in font nullfont!
Missing character: There is no J in font nullfont!
Missing character: There is no E in font nullfont!
Missing character: There is no L in font nullfont!
Missing character: There is no : in font nullfont!
Missing character: There is no K in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no y in font nullfont!
Missing character: There is no w in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no d in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no : in font nullfont!
! Font T1/cmr/m/n/6=dcr6 at 6.0pt not loadable: Metric (TFM) file not found.
<to be read again> 
                   relax 
l.63 \begin
           {acknowledgement}
I wasn't able to read the size data for this font,
so I will ignore the font specification.
[Wizards can fix TFM files using TFtoPL/PLtoTF.]
You might try inserting a different font spec;
e.g., type `I\font<same font id>=<substitute font name>'.

Missing character: There is no S in font nullfont!
Missing character: There is no u in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no m in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no 1 in font nullfont!
Missing character: There is no : in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no f in font nullfont!
Missing character: There is no f in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no l in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no 1 in font nullfont!
Missing character: There is no , in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no d in font nullfont!
Missing character: There is no d in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no 1 in font nullfont!
Missing character: There is no , in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no m in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no l in font nullfont!
Missing character: There is no 1 in font nullfont!
Missing character: There is no . in font nullfont!
Missing character: There is no S in font nullfont!
Missing character: There is no u in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no m in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no 2 in font nullfont!
Missing character: There is no : in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no f in font nullfont!
Missing character: There is no f in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no l in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no 2 in font nullfont!
Missing character: There is no , in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no d in font nullfont!
Missing character: There is no d in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no 2 in font nullfont!
Missing character: There is no , in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no m in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no l in font nullfont!
Missing character: There is no 2 in font nullfont!
Missing character: There is no . in font nullfont!
Missing character: There is no A in font nullfont!
Missing character: There is no c in font nullfont!
Missing character: There is no k in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no w in font nullfont!
Missing character: There is no l in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no d in font nullfont!
Missing character: There is no g in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no m in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no I in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no d in font nullfont!
Missing character: There is no u in font nullfont!
Missing character: There is no c in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no y in font nullfont!
Missing character: There is no m in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no l in font nullfont!
Missing character: There is no c in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no m in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no h in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no . in font nullfont!
LaTeX Font Info:    Try loading font information for OMS+cmr on input line 72.
(/usr/share/texmf-texlive/tex/latex/base/omscmr.fd
File: omscmr.fd 1999/05/25 v2.5h Standard LaTeX font definitions
)
LaTeX Font Info:    Font shape `OMS/cmr/m/n' in size <10.95> not available
(Font)              Font shape `OMS/cmsy/m/n' tried instead on input line 72.
Missing character: There is no D in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no u in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no " in font nullfont!
Missing character: There is no I in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no d in font nullfont!
Missing character: There is no u in font nullfont!
Missing character: There is no c in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no " in font nullfont!
Missing character: There is no h in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no d in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no g in font nullfont!
Missing character: There is no . in font nullfont!
Missing character: There is no B in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no g in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no y in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no u in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no d in font nullfont!
Missing character: There is no u in font nullfont!
Missing character: There is no c in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no y in font nullfont!
Missing character: There is no m in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no l in font nullfont!
Missing character: There is no b in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no f in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no h in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no f in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no c in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no h in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no d in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no g in font nullfont!
Missing character: There is no . in font nullfont!
Missing character: There is no U in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no l in font nullfont!
Missing character: There is no y in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no c in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no , in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no u in font nullfont!
Missing character: There is no b in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no c in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no , in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no d in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no u in font nullfont!
Missing character: There is no b in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no u in font nullfont!
Missing character: There is no b in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no c in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no h in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no d in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no g in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no . in font nullfont!
Missing character: There is no A in font nullfont!
Missing character: There is no v in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no d in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no y in font nullfont!
Missing character: There is no l in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no m in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no k in font nullfont!
Missing character: There is no u in font nullfont!
Missing character: There is no p in font nullfont!
Missing character: There is no ( in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no x in font nullfont!
Missing character: There is no c in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no p in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no p in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no g in font nullfont!
Missing character: There is no l in font nullfont!
Missing character: There is no y in font nullfont!
Missing character: There is no f in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no m in font nullfont!
Missing character: There is no p in font nullfont!
Missing character: There is no h in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no ) in font nullfont!
Missing character: There is no . in font nullfont!
Missing character: There is no A in font nullfont!
Missing character: There is no v in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no d in font nullfont!
Missing character: There is no u in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no g in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no x in font nullfont!
Missing character: There is no p in font nullfont!
Missing character: There is no l in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no c in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no v in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no c in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no l in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no h in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no z in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no l in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no p in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no c in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no . in font nullfont!
Missing character: There is no C in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no p in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no h in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no d in font nullfont!
Missing character: There is no g in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no b in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no l in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no w in font nullfont!
Missing character: There is no f in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no g in font nullfont!
Missing character: There is no u in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no b in font nullfont!
Missing character: There is no u in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no b in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no v in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no b in font nullfont!
Missing character: There is no l in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no . in font nullfont!
Missing character: There is no I in font nullfont!
Missing character: There is no f in font nullfont!
Missing character: There is no y in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no u in font nullfont!
Missing character: There is no h in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no v in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no d in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no f in font nullfont!
Missing character: There is no f in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no c in font nullfont!
Missing character: There is no u in font nullfont!
Missing character: There is no l in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no w in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no h in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no h in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no m in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no h in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no m in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no p in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no c in font nullfont!
Missing character: There is no k in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no g in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no , in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no d in font nullfont!
Missing character: There is no j in font nullfont!
Missing character: There is no u in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no h in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no p in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no c in font nullfont!
Missing character: There is no k in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no g in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no p in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no p in font nullfont!
Missing character: There is no p in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no p in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no l in font nullfont!
Missing character: There is no y in font nullfont!
Missing character: There is no f in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no y in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no u in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no p in font nullfont!
Missing character: There is no l in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no f in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no m in font nullfont!
Missing character: There is no . in font nullfont!
Missing character: There is no I in font nullfont!
Missing character: There is no f in font nullfont!
Missing character: There is no y in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no u in font nullfont!
Missing character: There is no c in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no ' in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no g in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no w in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no k in font nullfont!
Missing character: There is no , in font nullfont!
Missing character: There is no j in font nullfont!
Missing character: There is no u in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no m in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no v in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no h in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no p in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no c in font nullfont!
Missing character: There is no k in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no g in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no . in font nullfont!
Missing character: There is no I in font nullfont!
Missing character: There is no f in font nullfont!
Missing character: There is no y in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no u in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no u in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no g in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no p in font nullfont!
Missing character: There is no p in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no d in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no x in font nullfont!
Missing character: There is no , in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no g in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no l in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no , in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no f in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no h in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no b in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no b in font nullfont!
Missing character: There is no l in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no g in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no p in font nullfont!
Missing character: There is no h in font nullfont!
Missing character: There is no y in font nullfont!
Missing character: There is no . in font nullfont!
Missing character: There is no U in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no g in font nullfont!
Missing character: There is no u in font nullfont!
Missing character: There is no l in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no c in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no h in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no d in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no g in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no m in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no k in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no h in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no p in font nullfont!
Missing character: There is no p in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no d in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no x in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no p in font nullfont!
Missing character: There is no p in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no d in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no c in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no . in font nullfont!
Missing character: There is no I in font nullfont!
Missing character: There is no f in font nullfont!
Missing character: There is no y in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no u in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no u in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no g in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no p in font nullfont!
Missing character: There is no p in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no d in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no x in font nullfont!
Missing character: There is no , in font nullfont!
Missing character: There is no y in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no u in font nullfont!
Missing character: There is no m in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no y in font nullfont!
Missing character: There is no d in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no l in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no h in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no p in font nullfont!
Missing character: There is no p in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no d in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no x in font nullfont!
Missing character: There is no c in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no m in font nullfont!
Missing character: There is no m in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no d in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no d in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no m in font nullfont!
Missing character: There is no p in font nullfont!
Missing character: There is no l in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no p in font nullfont!
Missing character: There is no p in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no d in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no x in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no c in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no h in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no d in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no g in font nullfont!
Missing character: There is no . in font nullfont!
Missing character: There is no S in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no m in font nullfont!
Missing character: There is no p in font nullfont!
Missing character: There is no l in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no f in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no g in font nullfont!
Missing character: There is no u in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no : in font nullfont!
Missing character: There is no F in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no g in font nullfont!
Missing character: There is no u in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no h in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no . in font nullfont!
! Font T1/cmr/m/sc/8=dccsc10 at 8.0pt not loadable: Metric (TFM) file not found
.
<to be read again> 
                   relax 
l.95 \QTR{caption}{Caption for figure below.}
                                             
I wasn't able to read the size data for this font,
so I will ignore the font specification.
[Wizards can fix TFM files using TFtoPL/PLtoTF.]
You might try inserting a different font spec;
e.g., type `I\font<same font id>=<substitute font name>'.

Missing character: There is no F in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no g in font nullfont!
Missing character: There is no u in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no 1 in font nullfont!
Missing character: There is no . in font nullfont!
Missing character: There is no C in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no p in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no f in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no f in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no g in font nullfont!
Missing character: There is no u in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no b in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no l in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no w in font nullfont!
Missing character: There is no . in font nullfont!
Missing character: There is no S in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no m in font nullfont!
Missing character: There is no p in font nullfont!
Missing character: There is no l in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no b in font nullfont!
Missing character: There is no l in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no : in font nullfont!
Missing character: There is no T in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no b in font nullfont!
Missing character: There is no l in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no 1 in font nullfont!
Missing character: There is no - in font nullfont!
Missing character: There is no - in font nullfont!
Missing character: There is no - in font nullfont!
Missing character: There is no C in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no p in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no f in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no b in font nullfont!
Missing character: There is no l in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no b in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no v in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no . in font nullfont!
Missing character: There is no H in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no d in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no g in font nullfont!
Missing character: There is no 1 in font nullfont!
Missing character: There is no H in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no d in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no g in font nullfont!
Missing character: There is no 2 in font nullfont!
Missing character: There is no R in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no w in font nullfont!
Missing character: There is no 1 in font nullfont!
Missing character: There is no 1 in font nullfont!
Missing character: There is no 2 in font nullfont!
Missing character: There is no R in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no w in font nullfont!
Missing character: There is no 2 in font nullfont!
Missing character: There is no 3 in font nullfont!
Missing character: There is no 4 in font nullfont!
Missing character: There is no R in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no f in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no c in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no h in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no ( in font nullfont!
Missing character: There is no m in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no u in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no l in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no r in font nullfont!
Missing character: There is no b in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no b in font nullfont!
Missing character: There is no T in font nullfont!
Missing character: There is no E in font nullfont!
Missing character: There is no X in font nullfont!
Missing character: There is no ) in font nullfont!
Missing character: There is no . in font nullfont!
! Font T1/cmr/m/sc/10=dccsc10 at 10.0pt not loadable: Metric (TFM) file not fou
nd.
<to be read again> 
                   relax 
l.123 \section{Mathematical Appendix}
                                     
I wasn't able to read the size data for this font,
so I will ignore the font specification.
[Wizards can fix TFM files using TFtoPL/PLtoTF.]
You might try inserting a different font spec;
e.g., type `I\font<same font id>=<substitute font name>'.

Missing character: There is no M in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no h in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no m in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no c in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no l in font nullfont!
Missing character: There is no A in font nullfont!
Missing character: There is no p in font nullfont!
Missing character: There is no p in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no d in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no x in font nullfont!
! Font T1/cmr/m/it/8=dcti8 at 8.0pt not loadable: Metric (TFM) file not found.
<to be read again> 
                   relax 
l.124 \end{document}
                    
I wasn't able to read the size data for this font,
so I will ignore the font specification.
[Wizards can fix TFM files using TFtoPL/PLtoTF.]
You might try inserting a different font spec;
e.g., type `I\font<same font id>=<substitute font name>'.

Missing character: There is no 1 in font nullfont!
[1

{/var/lib/texmf/fonts/map/pdftex/updmap/pdftex.map}] (./newfile1.aux) ) 
Here is how much of TeX's memory you used:
 5248 strings out of 495061
 72835 string characters out of 1182622
 153672 words of memory out of 3000000
 8353 multiletter control sequences out of 15000+50000
 8839 words of font info for 29 fonts, out of 3000000 for 9000
 28 hyphenation exceptions out of 8191
 53i,8n,36p,346b,305s stack positions out of 5000i,500n,10000p,200000b,50000s
 </root/
.texmf-var/fonts/pk/ljfour/jknappen/ec/ecbx1000.600pk> </root/.texmf-var/fonts/
pk/ljfour/jknappen/ec/ecbx1095.600pk></usr/share/texmf-texlive/fonts/type1/publ
ic/amsfonts/cm/cmsy10.pfb></usr/share/texmf-texlive/fonts/type1/public/amsfonts
/cm/cmsy6.pfb></usr/share/texmf-texlive/fonts/type1/public/amsfonts/cm/cmsy8.pf
b>
Output written on newfile1.pdf (1 page, 39862 bytes).
PDF statistics:
 82 PDF objects out of 1000 (max. 8388607)
 7 named destinations out of 1000 (max. 500000)
 1 words of extra memory for PDF output out of 10000 (max. 10000000)


```

Again, any help would be appreciated.

Thank you

---

### Post by ASav on 2012-02-05
I have overcome the problem. Here is a step-by-step to what I did:

AEA template on LyX.
Help for LyX (help installing a template)

TO use a template that is recognised but unavailable (in lyx check in documents>settings>document class).
Find the necessary package online e.g. google AEA latex. Download this package. 
Extract it to:
        1. usr/share/texmf/tex/latex/lyx (this will mean lyx works when logged in as root) OR extract to
        2. usr/local/share/texmf (this will work from user account)
Not sure which one to unpack to, or if it will work in just unpacked to the user directory (i did both).
        3. Once extracted go into the terminal type 'sudo texhash' to compile.
        4. Open LyX choose tools>reconfigure then close LyX and re-open.
If the package still does not compile to a pdf, (i.e. opens up in lyx but when compile there is font errors or something) make sure you check any notes included in the document e.g. AEA gives advice on disabling T1 font in 'preferences' . Try looking in tools>preferences and document>preferences toggle some of these options.

---

### Post by PGScooter on 2012-02-06
hey ASav, thank you for updating your post with the solution! Unfortunately, few people do that.

There is a LyX list that is very helpful if you have future questions.
see the lyx-users list here: [http://www.lyx.org/MailingLists](http://www.lyx.org/MailingLists)
Also, if you find any bugs, please do report them! The developers of LyX are very helpful with fixing bugs.

---

### Post by PGScooter on 2012-02-06
Also, the manuals for LyX are extremely helpful. They are all in the help menu. Again, if you have suggestions, send them to the lyx team as they would love to hear them! Thanks

---

