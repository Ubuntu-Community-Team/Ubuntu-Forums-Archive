---
title: "install gcc-3.2.2 ubuntu jaunty 32"
date: 2009-06-17
forum: General Help
---

### Post by vreemde eend on 2009-06-17
Hi,

I need to install gcc-3.2.2 to compile the IBM powerpc evaluation kit (PEK 2.0). I downloaded the source and compiled:

../configure --prefix=/usr/local/gcc-3.2.2 --enable-version-specific-runtime-libs
sudo make bootstrap

But if I run "make -k check", the test fails with a segmentation error. I however can run "make install" without errors.

Somebody knows an easier solution to install gcc-3.2.x?

thanks,

pieter

---

