---
title: "How to include different encoding in LaTeX"
date: 2007-01-11
forum: Education &amp; Science
---

### Post by Zdravko on 2007-01-11
I would like to start writing some papers with LaTeX. But I need them in Bulgarian language. Is there a way to set up a Cyrillic encoding for the input file. Currently a simple tex file with cyrillic symbols gets compiled, but the output is usually empty or with garbage.

---

### Post by Zdravko on 2007-01-11
I managed to switch to a universal encoding, but the problem is, that LaTeX doesn't find it:
> 
zdravko@ztm-desktop:~/doc$ latex first.tex
This is pdfeTeX, Version 3.141592-1.21a-2.2 (Web2C 7.5.4)
entering extended mode
(./first.tex
LaTeX2e <2003/12/01>
Babel <v3.8d> and hyphenation patterns for american, french, german, ngerman, bahasa, basque, bulgarian, catalan, croatian, czech, danish, dutch, esperanto, estonian, finnish, greek, icelandic, irish, italian, latin, magyar, norsk, polish, portuges, romanian, russian, serbian, slovak, slovene, spanish, swedish, turkish, ukrainian, nohyphenation, loaded.
(/usr/share/texmf-tetex/tex/latex/base/article.cls
Document Class: article 2004/02/16 v1.4f Standard LaTeX document class
(/usr/share/texmf-tetex/tex/latex/base/size12.clo))

! LaTeX Error: File `ucs.sty' not found.

Type X to quit or <RETURN> to proceed,
or enter new name. (Default extension: sty)

Enter file name: 
! Emergency stop.
<read *> 
         
l.3 \usepackage
               [utf8x]{inputenc}^^M
No pages of output.
Transcript written on first.log.


With my code being:
```

\documentclass[a4paper, 12pt]{article}
\usepackage{ucs}
\usepackage[utf8x]{inputenc}
\author{&#1047;&#1076;&#1088;&#1072;&#1074;&#1082;&#1086; &#1052;&#1086;&#1085;&#1086;&#1074;}
\title{&#1054;&#1073;&#1097;&#1080; &#1087;&#1088;&#1072;&#1074;&#1080;&#1083;&#1072; &#1085;&#1072; &#1092;&#1086;&#1088;&#1091;&#1084;&#1080;&#1090;&#1077;}
\begin{document}
\end{document}

```

---

### Post by Zdravko on 2007-01-11
I even tried:
```

\documentclass[a4paper, 12pt]{article}
\usepackage[T1, T2A]{fontenc}
\usepackage[koi8-ru]{inputenc}
\usepackage[english, bulgarian, russian]{babel}
\author{&#1047;&#1076;&#1088;&#1072;&#1074;&#1082;&#1086; &#1052;&#1086;&#1085;&#1086;&#1074;}
\title{&#1054;&#1073;&#1097;&#1080; &#1087;&#1088;&#1072;&#1074;&#1080;&#1083;&#1072; &#1085;&#1072; &#1092;&#1086;&#1088;&#1091;&#1084;&#1080;&#1090;&#1077;}
\begin{document}
&#1092;&#1076;&#1093;&#1092;&#1081;&#1076;
\end{document}

```

But as end-effect I get:
> 
LaTeX2e <2003/12/01>
Babel <v3.8d> and hyphenation patterns for american, french, german, ngerman, b
ahasa, basque, bulgarian, catalan, croatian, czech, danish, dutch, esperanto, e
stonian, finnish, greek, icelandic, irish, italian, latin, magyar, norsk, polis
h, portuges, romanian, russian, serbian, slovak, slovene, spanish, swedish, tur
kish, ukrainian, nohyphenation, loaded.
(/usr/share/texmf-tetex/tex/latex/base/article.cls
Document Class: article 2004/02/16 v1.4f Standard LaTeX document class
(/usr/share/texmf-tetex/tex/latex/base/size12.clo))
(/usr/share/texmf-tetex/tex/latex/base/fontenc.sty
(/usr/share/texmf-tetex/tex/latex/base/t1enc.def)
(/usr/share/texmf-tetex/tex/latex/cyrillic/t2aenc.def)
(/usr/share/texmf-tetex/tex/latex/cyrillic/t2acmr.fd))
(/usr/share/texmf-tetex/tex/latex/base/inputenc.sty
(/usr/share/texmf-tetex/tex/latex/cyrillic/koi8-ru.def))
(/usr/share/texmf-tetex/tex/generic/babel/babel.sty
(/usr/share/texmf-tetex/tex/generic/babel/english.ldf
(/usr/share/texmf-tetex/tex/generic/babel/babel.def))
(/usr/share/texmf-tetex/tex/generic/babel/bulgarian.ldf)
(/usr/share/texmf-tetex/tex/generic/babel/russianb.ldf)) (./first.aux)

! Package inputenc Error: Keyboard character used is undefined
(inputenc)                in inputencoding `koi8-ru'.

See the inputenc package documentation for explanation.
Type  H <return>  for immediate help.
 ...                                              
                                                  
l.8 &#1092;
      &#1076;&#1093;&#1092;&#1081;&#1076;
? ! Interruption.
\GenericError  ...                                
                                                  \endgroup 
l.8 &#1092;
      &#1076;&#1093;&#1092;&#1081;&#1076;
? 



---

### Post by slaanco on 2007-01-14
try 

\usepackage[utf8]{inputenc}

and just type it in as you normally would type in OpenOffice, you just have to save the file in the same encoding. I'm sure sure if it'll work with your language, bit I'm using it for typing in my language (slovak) and it works. ;):cool:

---

### Post by Zdravko on 2007-01-14
Yup! It worked!
> 
\usepackage[utf8]{inputenc}
\usepackage[T2A]{fontenc}
\usepackage[english, bulgarian]{babel}


---

### Post by mrdean on 2007-01-15
Hi Zdravko,

I suggest you use Kile environment and install UTF-8 support for Kile!
It worked excellent to me for writing Serbian documents!

---

### Post by Zdravko on 2007-04-29
> **mrdean said:**
> Hi Zdravko,

I suggest you use Kile environment and install UTF-8 support for Kile!
It worked excellent to me for writing Serbian documents!

How to do this?
The following doesn't compile under Kile:
```

\documentclass[a4paper,12pt]{book}

\usepackage[utf8]{inputenc}
\usepackage[american]{babel}
\usepackage[T1]{fontenc}
\usepackage[dvips]{graphicx}

\author{XXX}
\title{Introduction to design patterns}
\date{2007-04-29}

\begin{document}

\end{document}


```It says:
> 
[LaTeX] intro.tex => intro.dvi (latex)
[LaTeX] finished with exit status 1
/usr/share/texmf-tetex/tex/latex/base/fontenc.sty:100:Font T1/cmr/m/n/12=ecrm1200 at 12.0pt not loadable: Metric (TFM) file not found. \fontencoding\encodingdefault\selectfont
[LaTeX] 1 error, 0 warnings, 0 badboxes


---

### Post by slaanco on 2007-04-30
shouldn't be there ?
```
\maketitle
```

---

### Post by Zdravko on 2008-05-11
> **Zdravko said:**
> Yup! It worked!
Now it doesn't work: 
> ! Package fontenc Error: Encoding file `t2aenc.def' not found.
(fontenc)                You might have misspelt the name of the encoding.


---

