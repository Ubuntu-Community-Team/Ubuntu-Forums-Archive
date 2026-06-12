---
title: "Where is the kernel-source-2.6.12 package?"
date: 2006-01-08
forum: General Help
---

### Post by bannerboy on 2006-01-08
where did the kernel-source-2.6.12 package go?

---

### Post by neoflight on 2006-01-08
u mean the location of source in ur computer...? by default it shud be here.

cd /usr/src/linux-source-2.6.12

---

### Post by lamego on 2006-01-08
By default it is NOT installed, the package is available on APT.
Just use the package manager and search for linux-source .

---

### Post by neoflight on 2006-01-08
right...sorry for the confusion. here is what i did.(for vpn stuff)...

# apt-get install linux-source-2.6.12
$ tar jxf /usr/src/linux-source-2.6.12.tar.bz2

The unpacked source tree then will be available in linux-source-2.6.12 directory.

---

### Post by bannerboy on 2006-01-08
thanks, I coulden't find it before, and how I have.

---

