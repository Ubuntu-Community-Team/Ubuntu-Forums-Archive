---
title: "Parallel TeXLive 2009 installation"
date: 2009-12-14
forum: Education &amp; Science
---

### Post by Garzo on 2009-12-14
I've just installed TeXLive 2009 into /opt/texlive/2009/ seeing as Ubuntu is stuck on 2007. The old Ubuntu repository packages are installed in the usual place (/usr/share/texmf-texlive). I'm trying to set my local path to use TexLive 2009, while keeping the repository packages as the main path. I think I've got everything straight as when I use 'latex -v' I get

```
pdfTeX 3.1415926-1.40.10-2.2 (TeX Live 2009)
kpathsea version 5.0.0
```

However, kpsewhich and texdoc aren't finding a thing. I edited /etc/profile and ~/.bashrc to try to set variables, but I'm worried I've made a texhash of it!

Any help,

Gareth.

---

### Post by dox_drum on 2010-01-28
If you are compiling from the terminal, try adding to the .bashrc the line
```
export TEXINPUTS=/path/to/texlive2009//:
```
Note the colon at the end, it means recursively.

If the problem is with the editor compilations, so you should change the options of it.

---

