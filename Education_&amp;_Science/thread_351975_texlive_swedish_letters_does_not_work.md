---
title: "texlive swedish letters does not work"
date: 2007-02-02
forum: Education &amp; Science
---

### Post by kapetanski on 2007-02-02
It does not work with the swedish letters, I use this to enable them but nope, 
```
\usepackage[T1]{fontenc}
\usepackage[swedish]{babel}
```

Apparently latex is loading the font but I get no swedish letters in the outputfile, neither dvi or pdf.

```
This is pdfeTeX, Version 3.141592-1.21a-2.2 (Web2C 7.5.4)
entering extended mode
(/media/NANO/research/pcnreferences/ds_inl1.tex
LaTeX2e <2003/12/01>
Babel <v3.8d> and hyphenation patterns for american, french, german, ngerman, b
ahasa, basque, bulgarian, catalan, croatian, czech, danish, dutch, esperanto, e
stonian, finnish, greek, icelandic, irish, italian, latin, magyar, norsk, polis
h, portuges, romanian, russian, serbian, slovak, slovene, spanish, swedish, tur
kish, ukrainian, nohyphenation, loaded.
(/usr/share/texmf-tetex/tex/latex/base/article.cls

```

I'm going crazy on this now, I have  ideas on using xp instead to do it...

---

### Post by kapetanski on 2007-02-03
bump

---

### Post by kapetanski on 2007-02-03
I changed the font encoding to Western European iso 8859-1 and now it works perfect!

these packages gives the correct font as well 
```
\usepackage[latin1]{inputenc}
\usepackage{verbatim}
```

---

