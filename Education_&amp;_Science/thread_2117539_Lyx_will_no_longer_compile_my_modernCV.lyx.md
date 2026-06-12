---
title: "Lyx will no longer compile my modernCV.lyx"
date: 2013-02-18
forum: Education &amp; Science
---

### Post by mercury80 on 2013-02-18
I have a CV written in Lyx (that I update from time to time), and it will no longer compile. The template I use is modernCV.
All files are up to date, updated through the repository. I get the same error message twise::
Undefined control sequence.

Decription:
 \begin{document}
                     
The control sequence at the end of the top line
of your error message was never \def'ed. If you have
misspelled it (e.g., `\hobx'), type `I' and the correct
spelling (e.g., `I\hbox'). Otherwise just continue,
and I'll forget about whatever was undefined.

Here's a portion of the log:
```
LaTeX Font Info:    Try loading font information for OMX+lmex on input line 74.

(/usr/share/texmf/tex/latex/lm/omxlmex.fd
File: omxlmex.fd 2009/10/30 v1.6 Font defs for Latin Modern
)
LaTeX Font Info:    External font `lmex10' loaded for size
(Font)              <10.95> on input line 74.
LaTeX Font Info:    External font `lmex10' loaded for size
(Font)              <8> on input line 74.
LaTeX Font Info:    External font `lmex10' loaded for size
(Font)              <6> on input line 74.
(/usr/share/texlive/texmf-dist/tex/latex/microtype/mt-mvs.cfg
File: mt-mvs.cfg 2006/07/05 v1.1 microtype config. file: Marvosym Euro (RS)
)
! Undefined control sequence.
\hyper@linkurl ...tionraw >>}\relax \Hy@colorlink 
                                                  \@urlcolor #1\Hy@xspace@en...
l.74 \begin{document}
                     
The control sequence at the end of the top line
of your error message was never \def'ed. If you have
misspelled it (e.g., `\hobx'), type `I' and the correct
spelling (e.g., `I\hbox'). Otherwise just continue,
and I'll forget about whatever was undefined.

! Undefined control sequence.
\close@pdflink ->\Hy@endcolorlink 
                                  \Hy@VerboseLinkStop \pdfendlink 
l.74 \begin{document}
                     
The control sequence at the end of the top line
of your error message was never \def'ed. If you have
misspelled it (e.g., `\hobx'), type `I' and the correct
spelling (e.g., `I\hbox'). Otherwise just continue,
and I'll forget about whatever was undefined.

\makecvtitlepicturebox=\box39
<QR_vCard_S2.png, id=2, 82.3075pt x 82.3075pt>
File: QR_vCard_S2.png Graphic file (type png)
<use QR_vCard_S2.png>
Package pdftex.def Info: QR_vCard_S2.png used on input line 74.
(pdftex.def)             Requested size: 60.0pt x 60.00107pt.
\makecvtitledetailswidth=\skip78
\makecvtitlepicturewidth=\skip79

Underfull \hbox (badness 10000) in paragraph at lines 74--74

 []

\AtBeginShipoutBox=\box40
Package hyperref Info: Link coloring OFF on input line 74.
(/usr/share/texlive/texmf-dist/tex/latex/hyperref/nameref.sty
Package: nameref 2010/04/30 v2.40 Cross-referencing by name of section
(/usr/share/texlive/texmf-dist/tex/generic/oberdiek/gettitlestring.sty
Package: gettitlestring 2010/12/03 v1.4 Cleanup title references (HO)
)
\c@section@level=\count181
)
```

Anyone have an idea?

---

### Post by mercury80 on 2013-02-19
Solved...

The the preamble of my old lyx-file was not compatible with the updated versions of the ModernCV-template...
The following line does no longer belong in the preamble:
```
\AtBeginDocument{\maketitle}
```

---

