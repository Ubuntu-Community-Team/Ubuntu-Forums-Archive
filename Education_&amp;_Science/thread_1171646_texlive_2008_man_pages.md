---
title: "texlive 2008 man pages"
date: 2009-05-27
forum: Education &amp; Science
---

### Post by PGScooter on 2009-05-27
Hi,

The command ```
man pdflatex
``` does not work. I added the path to my PATH environment variable so the commands are recognized, but I did not find any information on how to install/find the man pages.

Thanks!

---

### Post by meborc on 2009-05-28
hmm... i installed texlive packages and i have man latex, pdflatex, pdfcslatex etc...

can't help you... but why install man pages anyway? they are not much of a help... a quik google will help more than man pages

---

### Post by PGScooter on 2009-05-28
hi meborc,

I often work without internet available. Also, it makes me think something else could be wrong with my tex installation.

---

### Post by meborc on 2009-05-28
try installing the "texlive" package from synaptic

---

### Post by unutbu on 2009-05-28
The pdflatex manpage is part of the texlive-base-bin package:
```

% locate pdflatex | grep man
/usr/share/man/man1/pdflatex.1.gz
% dpkg -S /usr/share/man/man1/pdflatex.1.gz
texlive-base-bin: /usr/share/man/man1/pdflatex.1.gz
```

---

### Post by PGScooter on 2009-05-29
meborc and unutbu, thank you for your help!

I searched for pdflatex and found a man file. Then, I added that path to the path that the man command searches.

see ```
man man
``` and ```
man manpath
```

In my case, I put the following lines in my .bashrc: ```

MANPATH=":/usr/local/texlive/2008/texmf/doc/man/"
export MANPATH

```

---

