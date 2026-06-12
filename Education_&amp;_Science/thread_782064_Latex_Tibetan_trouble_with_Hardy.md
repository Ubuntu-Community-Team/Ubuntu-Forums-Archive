---
title: "Latex Tibetan trouble with Hardy"
date: 2008-05-04
forum: Education &amp; Science
---

### Post by Bill magee on 2008-05-04
I am having trouble with the Tibetan package (ctib) in Hardy Heron.

When I use pdflatex (from texlive installation) to compile the following file including package ctib, I get Tibetan in the pdf but not the English. 

When I use comment out the \usepackage{ctib} and the \tib line, I get the English.

Below I include the .tex files and .log files with and without the Tibetan. 

This worked fine under Feisty. Any suggestions?

WITH TIBETAN

\batchmode
\documentclass{article}
\usepackage{ctib}
\begin{document}
This is a test of English and Tibetan.
\tib{sems can thams cad.}
\end{document}

This is pdfTeXk, Version 3.141592-1.40.3 (Web2C 7.5.6) (format=pdflatex 2008.5.2)  4 MAY 2008 16:44
entering extended mode
 %&-line parsing enabled.
**test.tex
(./test.tex
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
) (/etc/texmf/tex/latex/ctib/ctib.sty
Package: ctib 2002/07/01\ 0.6\ Tibetan for TeX and LaTeX2e
(/usr/share/texmf-texlive/tex/latex/base/fontenc.sty
Package: fontenc 2005/09/27 v1.99g Standard LaTeX package
(/etc/texmf/tex/latex/ctib/lctenc.def
File: lctenc.def 2002/07/01 v0.6 Mongolian Language Support Tibetan Encoding
) (/usr/share/texmf-texlive/tex/latex/base/t1enc.def
File: t1enc.def 2005/09/27 v1.99g Standard LaTeX file
LaTeX Font Info:    Redeclaring font encoding T1 on input line 43.
)
! Font T1/cmr/m/n/10=ecrm1000 at 10.0pt not loadable: Metric (TFM) file not fou
nd.
<to be read again> 
                   relax 
l.100 \fontencoding\encodingdefault\selectfont
                                              
I wasn't able to read the size data for this font,
so I will ignore the font specification.
[Wizards can fix TFM files using TFtoPL/PLtoTF.]
You might try inserting a different font spec;
e.g., type `I\font<same font id>=<substitute font name>'.

) (/etc/texmf/tex/latex/ctib/ctib.tex)) (./test.aux)
\openout1 = `test.aux'.

LaTeX Font Info:    Checking defaults for OML/cmm/m/it on input line 4.
LaTeX Font Info:    ... okay on input line 4.
LaTeX Font Info:    Checking defaults for T1/cmr/m/n on input line 4.
LaTeX Font Info:    ... okay on input line 4.
LaTeX Font Info:    Checking defaults for OT1/cmr/m/n on input line 4.
LaTeX Font Info:    ... okay on input line 4.
LaTeX Font Info:    Checking defaults for OMS/cmsy/m/n on input line 4.
LaTeX Font Info:    ... okay on input line 4.
LaTeX Font Info:    Checking defaults for OMX/cmex/m/n on input line 4.
LaTeX Font Info:    ... okay on input line 4.
LaTeX Font Info:    Checking defaults for U/cmr/m/n on input line 4.
LaTeX Font Info:    ... okay on input line 4.
LaTeX Font Info:    Checking defaults for LCT/ctib/m/n on input line 4.
LaTeX Font Info:    Try loading font information for LCT+ctib on input line 4.
(/etc/texmf/tex/latex/ctib/lctctib.fd
File: lctctib.fd 2002/07/01 v0.6 Tibetan Font Definitions based on Sirlin's Gly
phs
)
LaTeX Font Info:    ... okay on input line 4.
Missing character: There is no T in font nullfont!
Missing character: There is no h in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no o in font nullfont!
Missing character: There is no f in font nullfont!
Missing character: There is no E in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no g in font nullfont!
Missing character: There is no l in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no h in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no d in font nullfont!
Missing character: There is no T in font nullfont!
Missing character: There is no i in font nullfont!
Missing character: There is no b in font nullfont!
Missing character: There is no e in font nullfont!
Missing character: There is no t in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no n in font nullfont!
Missing character: There is no . in font nullfont!
LaTeX Font Info:    Try loading font information for LCT+cmr on input line 7.
LaTeX Font Info:    No file LCTcmr.fd. on input line 7.

LaTeX Font Warning: Font shape `LCT/cmr/m/n' undefined
(Font)              using `LCT/ctib/m/n' instead on input line 7.

Missing character: There is no 1 in font nullfont!
[1

{/var/lib/texmf/fonts/map/pdftex/updmap/pdftex.map}] (./test.aux)

LaTeX Font Warning: Some font shapes were not available, defaults substituted.

 ) 
Here is how much of TeX's memory you used:
 572 strings out of 95086
 5846 string characters out of 1183256
 48374 words of memory out of 1500000
 3809 multiletter control sequences out of 10000+50000
 7464 words of font info for 17 fonts, out of 1200000 for 2000
 28 hyphenation exceptions out of 8191
 29i,4n,23p,143b,129s stack positions out of 5000i,500n,6000p,200000b,5000s
 <./ctib.600pk>
Output written on test.pdf (1 page, 5635 bytes).
PDF statistics:
 20 PDF objects out of 1000 (max. 8388607)
 0 named destinations out of 1000 (max. 131072)
 1 words of extra memory for PDF output out of 10000 (max. 10000000)


WITHOUT TIBETAN

\batchmode
\documentclass{article}
%\usepackage{ctib}
\begin{document}
This is a test of English and Tibetan.
%\tib{sems can thams cad.}
\end{document}


This is pdfTeXk, Version 3.141592-1.40.3 (Web2C 7.5.6) (format=pdflatex 2008.5.2)  4 MAY 2008 16:46
entering extended mode
 %&-line parsing enabled.
**test.tex
(./test.tex
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
) (./test.aux)
\openout1 = `test.aux'.

LaTeX Font Info:    Checking defaults for OML/cmm/m/it on input line 4.
LaTeX Font Info:    ... okay on input line 4.
LaTeX Font Info:    Checking defaults for T1/cmr/m/n on input line 4.
LaTeX Font Info:    ... okay on input line 4.
LaTeX Font Info:    Checking defaults for OT1/cmr/m/n on input line 4.
LaTeX Font Info:    ... okay on input line 4.
LaTeX Font Info:    Checking defaults for OMS/cmsy/m/n on input line 4.
LaTeX Font Info:    ... okay on input line 4.
LaTeX Font Info:    Checking defaults for OMX/cmex/m/n on input line 4.
LaTeX Font Info:    ... okay on input line 4.
LaTeX Font Info:    Checking defaults for U/cmr/m/n on input line 4.
LaTeX Font Info:    ... okay on input line 4.
[1

{/var/lib/texmf/fonts/map/pdftex/updmap/pdftex.map}] (./test.aux) ) 
Here is how much of TeX's memory you used:
 201 strings out of 95086
 2113 string characters out of 1183256
 45944 words of memory out of 1500000
 3459 multiletter control sequences out of 10000+50000
 3640 words of font info for 14 fonts, out of 1200000 for 2000
 28 hyphenation exceptions out of 8191
 23i,4n,17p,136b,107s stack positions out of 5000i,500n,6000p,200000b,5000s
</usr/share/
texmf-texlive/fonts/type1/bluesky/cm/cmr10.pfb>
Output written on test.pdf (1 page, 7045 bytes).
PDF statistics:
 10 PDF objects out of 1000 (max. 8388607)
 0 named destinations out of 1000 (max. 131072)
 1 words of extra memory for PDF output out of 10000 (max. 10000000)

---

### Post by Bill magee on 2008-05-04
Dear Ubunters,

Regarding the above problem where I get Tibetan but no English...

I can get the English as well as the Tibetan if I declare the English font. For instance:

\newfont{\modern}{cmr10 scaled\magstep1}

and then surround the English with {\modern ....}

But my question remains the same. Did not have to do this in Feisty. What gives with my Latex installation under Hardy?

Cheers,
Bill magee

---

### Post by Bill magee on 2008-05-04
I have solved my problem with a timely sudo apt-get install texlive-latex-recommended.

Now I get English and Tibetan without having to call the English font in a declaration.

There is still one small weirdness. In Feisty the call \tib{ma} gave me the Tibetan character ma then returned me to the English set. Now under my new installation I need to put curly brackets around the entire thing:
{\tib{ma}}. Otherwise the Tibetan remains on.

Small problem, no complaining.

Anyone having weirdness with latex under Hardy?

-Bill

---

