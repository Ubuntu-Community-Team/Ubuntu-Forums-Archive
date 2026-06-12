---
title: "problems with KILE and BibTeX"
date: 2010-01-15
forum: Education &amp; Science
---

### Post by Sy78 on 2010-01-15
hey there,
i'm writing my master's thesis at them moment and decided to do it with Kile and BibTeX. i'm pretty content with the outlook of the thesis itself, but i can't figure out how to include my bibliography. here are the different codes:

```
\input{meta/_meta}

\documentclass
[a4paper, %A4
12pt,
oneside, %einseitig
titlepage, %Titelblatt
parskip,
headsepline, %Trennlinie zwischen Kopfzeile und Seite
%Trennlinie linksb?ndig
liststotoc, % Verzeichnisse im Inhaltsverzeichnis auffhren
bibtotoc, % Literaturverzeichnis im Inhaltsverzeichnis auffhren
tablecaptionabove %Kapitelangabe in Kopfzeile automatisch erstellen
]
{scrartcl} %dokumentenklasse
\cleardoublepage
\usepackage[ngerman]{babel} %deutsch

\input{meta/packages}
\input{meta/seitenstil}

%opening
\title{Die Generierung von Angst und Schrecken in Harley 3954 der British Library, London}
\author{Simon Gr?ning}

\begin{document}

% auch subsubsection nummerieren
\setcounter{secnumdepth}{3}
\setcounter{tocdepth}{3}
\setcounter{footnote}{0}

% keine Kopf-/Fuzeilen bei Deckblatt und Abstract
\include{inhalt/deckblatt}
\include{inhalt/abstract}

\pagenumbering{arabic}
\addtocounter{page}{2}
\thispagestyle{empty}
\tableofcontents            % Inhaltsverzeichnis

%Inhalt
\include{inhalt/mandeville_buch}

%Abbildungsverzeichnis
\include{inhalt/bildanhang}
\listoffigures

%Bibliographie
 \bibliography{magisterarbeit}
\end{document}

```

```
\usepackage[left=2.5cm,right=4.0cm,top=2.5cm,bottom=5cm]{geometry} %seiteneinrichtung
% Anpassung an Landessprache -----------------------------------------------
%     Verwendet globale Option german siehe \documentclass
% --------------------------------------------------------------------------
\usepackage[utf8x]{inputenc} % Erlaubt die direkte Verwendung von Sonderzeichen, z.B. Umlauten
\usepackage[T1]{fontenc}
%\usepackage{ae} % "schneres" 
\usepackage[ngerman]{babel} %deutsch
\usepackage{wrapfig}
\usepackage[]{graphicx} %Graphiken einbinden
\graphicspath{{Bilder/}} %Bildquelle
\usepackage{mathptmx} %timesnewroman als standartschrift
\usepackage{setspace}

% Anpassung des Seitenlayouts ----------------------------------------------
%     siehe Seitenstil.tex
% --------------------------------------------------------------------------
\usepackage[
    automark,            % Kapitelangaben in Kopfzeile automatisch erstellen
    headsepline,    % Trennlinie unter Kopfzeile
    ilines                % Trennlinie linksbï¿œndig ausrichten
]{scrpage2}


% Einfache Definition der Zeilenabstï¿œnde und Seitenrï¿œnder etc. -------------
\usepackage{setspace}
\usepackage{geometry}

% Zum Umflieï¿œen von Bildern -------------------------------------------------
\usepackage{floatflt}


% Wichtig fï¿œr korrekte Zitierweise ------------------------------------------
\usepackage{jtbnew}
\bibliographystyle{jtbnew}

% Zum fortlaufenden Durchnummerieren der Fuï¿œnoten ---------------------------
\usepackage{chngcntr}
```

```
@book{UBHD3529163,
 author={Baumann, Hans D.}, 
 title={Horror}, 
 title={die Lust am Grauen}, 
  year={1989}, 
 address={Weinheim [u.a.]}, 
} 

@book{UBHD65503699,
 author={ Chance, Jane  [Hrsg.]},
 title={Tolkien the medievalist}, 
 series={Routledge studies in medieval religion and culture ; 3}, 
 year={2003},
}
```

i just can't figure out whats wrong. i got the jtbnew.bst in the same folder as magisterarbeit.tex and magisterarbeit.bib but it just won't work.
If I try to make a PDF Kile says:
> ./meta/packages.tex:35:File 'jtbnew.sty' not found ./bibstyle and the *.sty is not automatically generated as CTAN says.

When I run latex through the terminal it says:
> This is pdfTeXk, Version 3.141592-1.40.3 (Web2C 7.5.6)
 %&-line parsing enabled.
entering extended mode
(./magisterarbeit.tex
LaTeX2e <2005/12/01>
Babel <v3.8h> and hyphenation patterns for english, usenglishmax, dumylang, noh
yphenation, arabic, farsi, croatian, ukrainian, russian, bulgarian, czech, slov
ak, danish, dutch, finnish, basque, french, german, ngerman, ibycus, greek, mon
ogreek, ancientgreek, hungarian, italian, latin, mongolian, norsk, icelandic, i
nterlingua, turkish, coptic, romanian, welsh, serbian, slovenian, estonian, esp
eranto, uppersorbian, indonesian, polish, portuguese, spanish, catalan, galicia
n, swedish, ukenglish, pinyin, loaded.
(/usr/share/texmf/tex/latex/koma-script.tds/tex/latex/koma-script/scrartcl.cls
Document Class: scrartcl 2009/07/24 v3.04a KOMA-Script document class (article)

(/usr/share/texmf/tex/latex/koma-script.tds/tex/latex/koma-script/scrkbase.sty
(/usr/share/texmf/tex/latex/koma-script.tds/tex/latex/koma-script/scrbase.sty
(/usr/share/texmf-texlive/tex/latex/graphics/keyval.sty)
(/usr/share/texmf/tex/latex/koma-script.tds/tex/latex/koma-script/scrlfile.sty
Package scrlfile, 2009/03/25 v3.03 KOMA-Script package (loading files)
                  Copyright (C) Markus Kohm

)))
(/usr/share/texmf/tex/latex/koma-script.tds/tex/latex/koma-script/tocbasic.sty)

(/usr/share/texmf/tex/latex/koma-script.tds/tex/latex/koma-script/scrsize12pt.c
lo)
(/usr/share/texmf/tex/latex/koma-script.tds/tex/latex/koma-script/typearea.sty
Package typearea, 2009/07/24 v3.04a KOMA-Script package (type area)
                  Copyright (C) Frank Neukam, 1992-1994
                  Copyright (C) Markus Kohm, 1994-

)) (/usr/share/texmf/tex/latex/inputenc.sty
(/usr/share/texmf-texlive/tex/latex/base/latin1.def))
(/usr/share/texmf/tex/latex/german/ngerman.sty v2.5e 1998-07-08)
(/usr/share/texmf-texlive/tex/generic/babel/babel.sty

! Package babel Error: You haven't specified a language option.

See the babel package documentation for explanation.
Type  H <return>  for immediate help.
 ...                                              
                                                  
l.149 ...ry to proceed from here, type x to quit.}


i actually don't know what else to do.
thanks for help!

---

### Post by samden on 2010-01-17
I am unable to compile your document, as you have not specified what the file names of the documents you have supplied should be (although I can guess), and your code refers to documents you have not supplied. However I have picked up two errors that should hopefully help.

Firstly, you include the document 'meta/_meta.tex' before the '\documentclass' statement. '\documentclass' must be the first line. Change the start of 'magisterarbeit.tex' to:
```


\documentclass
[a4paper, %A4
12pt,
oneside, %einseitig
titlepage, %Titelblatt
parskip,
headsepline, %Trennlinie zwischen Kopfzeile und Seite
%Trennlinie linksb?ndig
liststotoc, % Verzeichnisse im Inhaltsverzeichnis auffhren
bibtotoc, % Literaturverzeichnis im Inhaltsverzeichnis auffhren
tablecaptionabove %Kapitelangabe in Kopfzeile automatisch erstellen
]
{scrartcl} %dokumentenklasse

\input{meta/_meta}

\usepackage[ngerman]{babel} %deutsch
```
Note that you can remove the \cleardoublepage command, it will do nothing as it comes before the \begin{document} command.

The reason BibTeX looks for a fictitious jtbnew.sty file is because you tell it to look for that instead of natbib.sty. Change the relevant lines in _meta.tex to:
```
% Wichtig fï¿&#339;r korrekte Zitierweise ------------------------------------------
\usepackage{natbib}
\bibliographystyle{jtbnew}
```

Does that help? It must be really frustrating writing in German and having to input all your commands in English. Best wishes with your thesis, I did my PhD one with LaTeX and have had to solve a lot of issues myself, and there are many other keen LaTeX users here, so just post back if you have any more problems. Also check out [http://www.latex-community.org/forum/](http://www.latex-community.org/forum/) if you can't get an answer here.

---

