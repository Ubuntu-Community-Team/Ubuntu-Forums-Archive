---
title: "kernel error"
date: 2009-03-04
forum: General Help
---

### Post by manish117 on 2009-03-04
Hi,
I was trying adhoc networking using AODV protocol for my lab using a virtual image of ubuntu, reference taken from...
[http://my.opera.com/subjam/blog/show.dml/472834](http://my.opera.com/subjam/blog/show.dml/472834)

I cant get pass through compiling AODV protocol, probably got to do with Step 1 which says "apt-get install kernel-source-2.6.8 kernel-headers-2.6-386" as there is kernel-source-2.6.8 available to download. I get the following error while compiling...
...
grep: /lib/modules/2.6.27-7-server/build/Makefile: No such file or directory
cc1: error: /lib/modules/2.6.27-7-server/build/include/linux/modversions.h: No such file or directory
kaodv-mod.c:22:27: error: linux/version.h: No such file or directory
kaodv-mod.c:23:41: error: missing binary operator before token "("
kaodv-mod.c:29:26: error: linux/module.h: No such file or directory
...and so on....

Needed some help please...
thanks in advance!!

---

