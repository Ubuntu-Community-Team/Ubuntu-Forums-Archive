---
title: "kile error dsfont.sty"
date: 2010-09-24
forum: Education &amp; Science
---

### Post by toffifeemann on 2010-09-24
hey,
i run kile 2.1 on my ubuntu 10.4
i used to have it on 9.10 and had several .tex files compiled and ready already... no that i installed it again it won't build the pdfs anymore giving me a first a warning and then an errormessage called, saying:
warning:
/usr/share/texmf-texlive/tex/latex/extsizes/extsizes.sty:0: It is better to use one of the extsizes classes, if you can.
error:
./vl1.tex:8:File 'dsfont.sty' not found. \usepackage

line 8 of my file says:
\usepackage{amsmath}

i hope you can help me, if you need more info let me know

---

### Post by toffifeemann on 2010-09-25
okay 
stupid of me, seems like it meant the line
\usepackage{dsfont}
so the doublestroke font, i dont know how to install that package, i have the file dsfont.sty but i dont know where to move it, anyone knows where it should go?

---

### Post by toffifeemann on 2010-09-26
hey, so the font was in the package "texlive-extra-fonts" available via synaptics

---

### Post by sophie27 on 2010-09-28
Hi,
does anyone know if it is possible to install doublestroke without installing all the texlive-extra fonts package? I mean, this package contains a lot of stuff which is not useful for me, but occupies a lot of memory in my netbook...can I install only what I need? 
THANX!

---

### Post by poyda on 2012-11-22
toffifeemann, the package is called texlive-fonts-extra
cheers

---

### Post by overdrank on 2012-11-22
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

