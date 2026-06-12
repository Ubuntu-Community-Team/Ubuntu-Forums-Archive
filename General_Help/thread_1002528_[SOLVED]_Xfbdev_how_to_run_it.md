---
title: "[SOLVED] Xfbdev how to run it?"
date: 2008-12-05
forum: General Help
---

### Post by siddartha on 2008-12-05
I have installed the Xfbdev from the repositories, but I don't seem to find anywhere a list of command line options to control it.

---

### Post by siddartha on 2008-12-11
From [the Kdrive home page]("http://www.pps.jussieu.fr/~jch/software/kdrive.html") scroll down to the Download section (which is at the end of the page) and get [on the download page]("http://www.pps.jussieu.fr/~jch/software/kdrive/") where you will find [the Xvesa deb]("http://www.pps.jussieu.fr/~jch/software/kdrive/xvesa_0.20031107-2_all.deb"). Install that one and you also get a nice man page which is not as easy to see as it is in place where just typing man won't help.```
man -l /usr/X11R6/man/man1/Xvesa.1x.gz
```will save you. And there are the options finally as the Kdrive does not have a use for the xorg.config.

---

