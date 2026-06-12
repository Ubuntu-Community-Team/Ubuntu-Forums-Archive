---
title: "xorg with Warty?"
date: 2005-03-08
forum: Desktop Environments
---

### Post by fackamato on 2005-03-08
Is anyone using xorg with warty? Does it work worse/as good,bad/better than xfree? I'm using an nvidia card.

Would xorg work just out of the box with the apt-get install command?

---

### Post by jdong on 2005-03-08
Don't try installing X.org on Warty -- it simply doesn't work.

Hoary will be out in a month -- it'll have X.org 6.8.2

---

### Post by Qdlaty on 2005-03-08
At the moment I find Hoary enough stable to recomand it to anyone who have need to use X.Org.
You need only to change warty into hoary in your sources.list and do update and dist-upgrade and you will be x.org user (with Gnome 2.10)

---

### Post by fackamato on 2005-03-08
Thanks for the answers. Any opinions on xorg speed vs xfree speed? I mean 2D speed, without fancy transparencies and such. For example now, moving around the gnome terminal isn't perfectly smooth. :) (g3ti200/p4 3.1smp)

---

### Post by rosslaird on 2005-03-08
Hm, let's see... Open a console, move it around. Nope, not entirely smooth, even with the latest x.org (and latest gnome ). It seems to redraw the backdrop about very -- what, tenth of a second? It does get a little smoother when I use the xcompgr, but that still crashes way too often. Xfce console windows are pretty smooth, though.

Ross

---

