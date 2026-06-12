---
title: "tex problems"
date: 2007-03-24
forum: Education &amp; Science
---

### Post by slaanco on 2007-03-24
I'm trying to put my diploma thesis into formatting which is required by my uni. I have a style file, with everything i need to do. 

The problem is that when i put \input{head} where head.tex is file with \usepackage and stuff. Whe I try to compile it throught kile I get this message > 

The document /foo/foo.tex is not a LaTeX root document continue anyway ?

i dont know why i get this message, becasue the main file is foo.tex not head.tex

the other problem is when i continue compiling i get this >

```
 ./foo.toc:0:Package inputenc Error: Unicode char \u 8:\GenericError {(inputenc)ignored.
```(the encoding is set to utf8 language slovak, is there any possibility, that this is result of bad encoding between style file ?)
and the new tab opens with this >
```

\select@language {slovak}
\contentsline {section}{Abstrakt/Abstract}{9}
\contentsline {section}{\GenericError {(inputenc) }{Package inputenc Error: Unicode char \u 8:&#65533; not set up for use with LaTeX}{See the inputenc package documentation for explanation.}{Your command was ignored.\MessageBreak Type I <command> <return> to replace it with another command,\MessageBreak or <return> to continue without it.}od}{10}
\contentsline {section}{\numberline {1}Prehistorick\IeC {\'e} modely a n\IeC {\'a}zory na vesm\IeC {\'\i }r }{11}
\contentsline {section}{\numberline {2}Antick\IeC {\'e} modely}{12}
\contentsline {section}{\numberline {3}Kopern\IeC {\'\i }kov model}{17}
\contentsline {section}{\numberline {4}Zalo\IeC {\v z}enie astrofyziky}{21}
\contentsline {subsection}{\numberline {4.1}Gravita\IeC {\v c}n\IeC {\'y} paradox}{23}
\contentsline {subsection}{\numberline {4.2}Olbersov (fotometrick\IeC {\'y}) paradox}{24}
\contentsline {section}{\numberline {5}Modern\IeC {\'a} kozmol\IeC {\'o}gia}{26}
\contentsline {section}{\numberline {6}V\IeC {\v s}eobecn\IeC {\'a} te\IeC {\'o}ria relativity}{28}
\contentsline {section}{\numberline {7}Statick\IeC {\'e} kozmologick\IeC {\'e} rie\IeC {\v s}enia}{32}
\contentsline {subsection}{\numberline {7.1}Einsteinove rie\IeC {\v s}enie}{32}
\contentsline {subsection}{\numberline {7.2}de Sitterov model}{36}
\contentsline {section}{\numberline {8}Dynamick\IeC {\'e} kozmologick\IeC {\'e} rie\IeC {\v s}enia}{38}
\contentsline {section}{\numberline {9}Expanzia Vesm\IeC {\'\i }ru a Hubblov z\IeC {\'a}kon}{39}
\contentsline {section}{\numberline {10}Te\IeC {\'o}ria ust\IeC {\'a}len\IeC {\'e}ho stavu}{41}
\contentsline {section}{\numberline {11}Reliktov\IeC {\'e} (zostatkov\IeC {\'e}) mikrovln\IeC {\'e} \IeC {\v z}iarenie}{42}
\contentsline {subsection}{\numberline {11.1}Vlastnosti CMB}{45}
\contentsline {subsection}{\numberline {11.2}Modern\IeC {\'y} v\IeC {\'y}skum CMB}{48}
\contentsline {section}{\numberline {12}Te\IeC {\'o}ria Ve\IeC {\v l}k\IeC {\'e}ho tresku.}{54}
\contentsline {subsection}{\numberline {12.1}Probl\IeC {\'e}my \IeC {\v s}tandardn\IeC {\'e}ho modelu}{55}
\contentsline {subsection}{\numberline {12.2}Infla\IeC {\v c}n\IeC {\'a} te\IeC {\'o}ria}{57}
\contentsline {section}{\numberline {13}Dodatky}{79}
\contentsline {subsection}{\numberline {13.1}Hubblov z\IeC {\'a}kon}{79}
\contentsline {subsection}{\numberline {13.2}Exaktn\IeC {\'e} dynamick\IeC {\'e} rie\IeC {\v s}enia}{82}
```

---

### Post by slaanco on 2007-03-24
ok, everything fixed

---

### Post by Steveire on 2007-03-24
how?

---

### Post by slaanco on 2007-03-24
I used to many different styles \section{} \section*{} (I messed up with these two types) in the included files, but when i fixed it it worked really nice.

---

