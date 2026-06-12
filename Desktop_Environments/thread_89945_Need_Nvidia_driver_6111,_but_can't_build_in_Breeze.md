---
title: "Need Nvidia driver 6111, but can't build in Breeze (2.6.12)"
date: 2005-11-13
forum: Desktop Environments
---

### Post by ariel on 2005-11-13
Hi all,

   I have a breeze installation with the latest nvidia driver (7676). However i need to downgrade to 6111. Reason is that this old version is the only one know to work OK with xcompmgr + Nvidia GeForce MX 400 which I have. All newer nvidia drivers freeze my box as soon as I launch xcompmgr.

   Why I want xcompmgr? because I want a supercool desktop with window & menu shadows and translucency.

   I have done quite a bit of research and found that the 6111 that nvidia offers doesn't build in kernels >= 2.6.8
   I also saw that some people developed patches for the 6111 source so that it can compile and I saw reports of people using the patched driver in new kernels with no problems. Unfortunately the patched version is no longer on line (it was here: [http://ngc891.blogdns.net/kernel/patches/NVIDIA-Linux-x86-1.0-6111-jp3.run](http://ngc891.blogdns.net/kernel/patches/NVIDIA-Linux-x86-1.0-6111-jp3.run))

   Apparently nvidia driver 6606 also works fine with this card & xcompmgr. Someone has the .deb packages or succeded patching the nvidia drivers to get them to build with kernel 2.6.12?
Thanks!


  So some good soul out there might have this patched version of 6111 or have a the actual patches and give me a clue on how to get this thing working?

Thanks a lot in advance.
Ariel

---

