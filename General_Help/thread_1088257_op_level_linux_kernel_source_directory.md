---
title: "op level linux kernel source directory"
date: 2009-03-05
forum: General Help
---

### Post by jordanguyoflove on 2009-03-05
Hi, I am trying to build kernel and I get something wrong. It's 4 am I can't make any sense of it. Please help.

root@add-desktop:~# fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers
> 
We do not seem to be in a top level linux kernel source directory
tree. Since we are trying to make a kernel package, that does not make
sense.  Please change directory to a top level linux kernel source
directory, and try again. (If I am wrong, and this is indeed a top
level linux kernel source directory, then I have gotten sadly out of
date with current kernels, and you should upgrade kernel-package)
root@add-desktop:~# 

---

### Post by jordanguyoflove on 2009-03-05
sorry I was in the wrong directory.

My bad

---

