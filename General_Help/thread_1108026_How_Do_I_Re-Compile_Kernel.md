---
title: "How Do I Re-Compile Kernel"
date: 2009-03-27
forum: General Help
---

### Post by NuNn DaDdY on 2009-03-27
I have edited part of my kernel source and would like to recompile the kernel.  How would I do that?

---

### Post by HermanAB on 2009-03-27
Here is the recipe:

cd /usr/src/linux
make mrproper
make oldconfig
make bzImage
make modules
make modules_install
make install

Here is some more information:
[http://aeronetworks.ca/kernel-compile-howto.html](http://aeronetworks.ca/kernel-compile-howto.html)

Some googling will find more guides in no time.

---

