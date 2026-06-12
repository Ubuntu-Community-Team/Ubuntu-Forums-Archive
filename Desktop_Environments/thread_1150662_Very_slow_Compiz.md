---
title: "Very slow Compiz"
date: 2009-05-06
forum: Desktop Environments
---

### Post by Krtek007 on 2009-05-06
Hi all,
please I have following problem:
After release update from Ubutnu 8.10 to Ubuntu 9.04 compiz is very slow. I tested glxgears and I have about 1200fps.

But when I display window from bottom panel to desktop it takes very long time. The bigger window the more time. Also window resizing is very slow. All other efects works fine and without problems.

My HW is
CPU: Athlon 4350e
GPU: ATI Radeon 3650
RAM: 4GB (3,2GB)
OS: Ubuntu 9.04 32-bit


It's very disturbing. Please help!

---

### Post by lesodk on 2009-05-06
same here.
Raden 3650

---

### Post by lesodk on 2009-05-07
Try download the patch

[http://svn.pardus.org.tr/viewcvs/tags/2008/desktop/freedesktop/xorg/xorg-server/files/ubuntu/107_fedora_dont_backfill_bg_none.patch?root=pardus&view=log](http://svn.pardus.org.tr/viewcvs/tags/2008/desktop/freedesktop/xorg/xorg-server/files/ubuntu/107_fedora_dont_backfill_bg_none.patch?root=pardus&view=log)

and run 

sudo patch -p0 107_fedora_dont_backfill_bg_none.patch

(got it from
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186)
)

---

### Post by Krtek007 on 2009-05-16
Thank you, I used one of links in recommended thread. 
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186/comments/86](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186/comments/86)

complete thread is there
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186?comments=all](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186?comments=all)

I tried PPA patch and it works!

Thank you

---

