---
title: "memory leak in evince document viewer?"
date: 2008-07-16
forum: Desktop Environments
---

### Post by logos34 on 2008-07-16
man, evince really eats up my memory:  it's using 27% (of 478 mb avail) just to read a 40 page pdf!  Yet when I close it and open the same doc in acroreader it only uses 12.7%!  It should be jsut the opposite, with gnome/linux apps being lighter.  Could it be a mem leak?  It's been this way for some time, can't figure it out,  BTW, I'm on 64-bit studio 8.04.

anyone with same prob?

---

### Post by lookaway on 2008-07-30
I just posted a thread at the beginner talk forum...Evince was using 1.1GB of memory when I was reading a simpe pdf file(150 pages)! I have 2 GB of memory...I mean, that's insane! A document viewer using half my memory!

---

### Post by mali2297 on 2008-07-30
It might be related to this [reported bug](https://bugs.launchpad.net/poppler/+bug/251898).

---

