---
title: "[LaTeX] Picture environment"
date: 2007-07-31
forum: Education &amp; Science
---

### Post by herlock on 2007-07-31
Hello,

I would like to use the picture environment. But when i compile my latex file I have those errors:

> 
(/usr/share/texmf-tetex/tex/latex/amsfonts/amssymb.sty)
\@input{picture.aux}
(/usr/share/texmf-tetex/tex/plain/graphics/picture.tex
(/usr/share/texmf-tetex/tex/plain/graphics/miniltx.tex)
(/usr/share/texmf-tetex/tex/plain/graphics/autopict.sty
! Command \qbezier already defined.\MessageBreak Or name \end... illegal, see p
.192 of the manual.
\@latex@error #1#2->\errhelp {#2}\errmessage {#1}
                                                 
l.354 \newcommand\qbezier[2][0]{\bezier{#1}#2}


Any idea ?

Thank you :-)

---

### Post by henriette_holm on 2007-07-31
Just a suggestion. Try asking your question in a latex usenet group - or something similar. You'll properly find more help there.

/Henriette

---

### Post by yellowbread on 2007-10-12
Sounds like \qbezier is already defined somewhere, then you try to define it again. Try changing the name, or use \renewcommand instead. Metapost, if you have the time to learn it, gives much better results than the latex picture environment.

---

