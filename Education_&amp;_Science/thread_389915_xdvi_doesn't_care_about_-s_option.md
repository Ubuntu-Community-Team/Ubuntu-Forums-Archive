---
title: "xdvi doesn't care about -s option"
date: 2007-03-21
forum: Education &amp; Science
---

### Post by jazzgossen on 2007-03-21
I want xdvi to scale the output to my screen size per default, but it won't. I've tried adding 

xdvi.shrinkFactor: 0

to ~/.Xresources (the preferred way to do it), and I've also tried running

xdvi -s 0 my_document.dvi,

but xdvi still zooms in on the document as if I had shrinkFactor 1. Any ideas why?

---

