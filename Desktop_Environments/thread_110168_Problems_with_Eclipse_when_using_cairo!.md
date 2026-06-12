---
title: "Problems with Eclipse when using cairo!"
date: 2005-12-30
forum: Desktop Environments
---

### Post by pablete on 2005-12-30
Hi!..
After installing Eclipse 3.1.0 (not using apt-get), When I want to run my application, I get an error saying that the cairo library could not be found. Then I modify the LD_LIBRARY_PATH and add a "./" to it, and just in case also copy that library (that comes with eclipse) to de jdk1.5/jre/lib/i386 directory.
With this changes, the error msg changed to this one:
java: cairo-surface.c:273: cairo_surface_reference: Assertion `surface->ref_count > 0' failed.

Since the library libcairo2 is distributed with ubuntu, my guess is that somehow eclipse is using cairo2 instead of cairo1. So I set the LD_PRELOAD variable to the libcairo.so.1. Unfortunately, this make the VM crash when I try to open Eclipse.. :( 

I'll really appreciate any help in this issue!!..
Thanks!!

---

