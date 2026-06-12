---
title: "need some help with tex4ht cfg"
date: 2009-11-23
forum: Education &amp; Science
---

### Post by legioner123 on 2009-11-23
hello,

i really need some help with tex4ht.

tex4ht is a package for latex enviroment.
With tex4ht it is possible to convert files from .tex to .html.

i am trying to convert a .tex file to .html file with tex4ht.
Mathematical Formulas are converted to .png pictures (i think with imagemagic)
But after Convertation is the "alt" (alternative) attribute text of img Tag not good.
I tryed many times to find a possibility to set alternative text of images to the formel code from .tex file.
I only got some success with this code:
-------------
\newtoks\eqtoks 
\def\AltMath#1${\eqtoks{#1}% 
   \Picture*[\HCode{\the\eqtoks}]{ align="middle"}$#1$\EndPicture$} 
\Configure{$}{}{}{\expandafter\AltMath}  
------------

If i use this code in the .cfg file, then the alternative text for pictures in HTML is the .tex Code of the formula
Unfortanatly this only works with $$ formulas
With \[ \] formulas it doesnt work.

Thx for any help

---

