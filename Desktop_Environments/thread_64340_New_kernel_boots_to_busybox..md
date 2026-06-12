---
title: "New kernel boots to busybox."
date: 2005-09-10
forum: Desktop Environments
---

### Post by valadil on 2005-09-10
I'm trying to build a new kernel for my laptop and not having much luck.

Just to test things out and deal with this scientifically I did the following:
  download and install kernel-image-2.6.10
  run it (it runs fine)
  download and install linux-tree-2.6.10 (I had been using vanilla sources but had the same problems)
  make menuconfig in the kernel source directory with ubuntu patches installed
  load alternate config file from /boot/config-2.6.10-5-386 (which I ran so I know works)
  make-kpkg ... (note that I'm using initrd here)
  try to boot

Try to boot is where things always fail.  Grub does come up, but when I try to boot my new kernel I get the error that /dev/hda2 does not exist and then I get dumped into a busybox ash shell.  There aren't any hds in /dev.  I've got no idea whats wrong here.  Becuase I've tried vanilla kernels and ubuntu patched kernels from configs that do work I'm inclined to think that theres something wrong with something else I'm doing.  I'm gonna try not doing an initrd image, but I don't really think that will make a difference.

---

### Post by mlomker on 2005-09-10
Good luck, I made many attempts to get a 2.6.10 kernel to boot on my laptop.  For whatever reason, I've had no problem compiling 2.6.13 kernels (I use the ck patch).

---

### Post by valadil on 2005-09-10
Actually I had no trouble making 2.6.10 boot in hoary.  Since coming to breezy though things haven't been good.  I even rolled back gcc to 3.3.  The reason I'm going with 2.6.10 is I have a patch for that particular kernel that makes the nvidia driver get along with my laptop.  I haven't found the patch for any other kernels and my lappy is kinda bitchy when it comes to nvidia drivers.

---

