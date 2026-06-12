---
title: "Kernel Version"
date: 2009-01-30
forum: General Help
---

### Post by Niksko on 2009-01-30
Where can I get information about the fifth number in the kernel version. For example, the version I got today was 2.6.27-11.27 . What is the fifth number? I can find no mention of it on the wikipedia page about linux kernel versions. Is it just an Ubuntu specific number or something like that?

-Nik

---

### Post by blazemore on 2009-01-30
I think it's the name of the Ubuntu package.
Does uname -r give you that, or did you find it somewhere else?
The official kernel revision ends in 11.

---

### Post by LowSky on 2009-01-30
I just google the  whole kernel number reported and it seems to be a Ubuntu derivitive of the 2.6.27-11 recently released

the 27 could be for the day it was released. I know I downloaded it on Jan 27, 2009....

---

### Post by Niksko on 2009-01-30
uname -r gives me 2.6.27-11

Maybe it's the day. Anyone else have any ideas?

---

### Post by sdennie on 2009-01-31
Have a look at /usr/share/doc/linux-image-`uname -r`.  It's the changelog that you want.

---

### Post by Niksko on 2009-01-31
Thanks for that. So it's basically a subversion number that security and bugfixes.

Thanks again

-Nik

---

### Post by Nepherte on 2009-01-31
Everything before the '-' is an official version number, in this case the version kernel developpers gave to the package. Everything after the '-' is an internal version number used by the ubuntu packagers.

---

### Post by q.dinar on 2010-12-02
how ubuntu kernel version is related to vanilla linux version?
about current versions, for example:
vanilla linux is 2.6.31.14 , ubuntu linux is 2.6.31-22.69 . how -22.69 is related to .14 ? does it mean that there is vanilla linux 2.6.31.22 and the ubuntu linux 2.6.31-22.69 is made from it?
(now i see in kernel.org:
stable: 2.6.31.14
nearest higher version there is:
stable: 2.6.32.26)

---

### Post by Bluesan on 2010-12-02
```
uname --help
```

lists all of the uname options

---

