---
title: "[SOLVED] GeomView and Ubuntu 7.10"
date: 2008-03-11
forum: Education &amp; Science
---

### Post by youcancallmeal on 2008-03-11
Hi all,

I have installed GeomView on Ubuntu 7.10 with the command:

sudo apt-get install geomview.

But when I try to start geomview I get the following error:
[I]
/usr/lib/geomview/gvx: Symbol `_XmStrings' has different size in shared object, consider re-linking
InstCreate: Undefined option: 7951040
Geomview: internal error: Segmentation violation; dump core now [/I]

What should I do to solve this problem?

Thanks in advance.

---

### Post by gnuman on 2008-03-15
Since no one has responded, you may want to start here:

[http://www.geomview.org./FAQ/](http://www.geomview.org./FAQ/)

On the support page you can find a link to the mailing list archive.  There is some discussion of the segmentation fault on there (do a key word search):

[http://www.geomview.org./support/](http://www.geomview.org./support/)

Good luck!

---

### Post by Dr.Byte on 2008-03-20
Well look for a newer version of geomview For example at :

[http://http://archive.ubuntu.com/ubuntu/pool/universe/g/geomview/]("http://http://archive.ubuntu.com/ubuntu/pool/universe/g/geomview/")

After instalation of the geomview_1.9.4_amd.deb and libgeomview-dedv_1.9.4_1.9.4-1_amd64.deb packages everything works pretty fine at my computer.

---

### Post by youcancallmeal on 2008-03-27
Thanks for the help.

I gave up on getting it to work in the 64 bit version (and yes I tried the newest version of GeomView). But it works fine with the 32 bit version  so I consider this problem as "solved".

---

