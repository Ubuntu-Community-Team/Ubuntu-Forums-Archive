---
title: "quick question, compiling kernel for another box"
date: 2009-02-20
forum: General Help
---

### Post by Til_Valhall_vi_drar! on 2009-02-20
Hi, i just have a little question, i have a diskless computer and a server with dhcp and tftpserver and all that.. i know how to build an initrd and i have a really god time doing this. my question is when im starting the diskless machine and it is loading the kernel nicely, but it tries to "mount root device (8,3)" or something like that, i noticed that when i builded bzImage i got a message "root device is (8,3)" or something like that, so, my question is, how do i compile the kernel without configuring it for this box? i can get it to mount an initrd fine and im getting a busybox shell on the diskless box, so it is working fine, but im wondering if the kernel has configured more than just the root device. I just want to compile it as best as possible. When im on it; when i type "make help\n" when im in the source directory of the kernel, i noticed that "make bzImage" is under the "Architecture for specific targets (x86):"

does this means that the kernel won't be compiled for amd64 (64bit) proccessors? both my diskless box and the box im compiling the kernel on has a 64bit cpu.

---

### Post by Til_Valhall_vi_drar! on 2009-02-21
bump

---

