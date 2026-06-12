---
title: "Asrock MB K8NF6G-VSTA hardware support"
date: 2007-05-16
forum: Development CD/DVD Image Testing
---

### Post by juantovarm on 2007-05-16
Something very interesting and weird happened, in feisty herd 4 (32bit) the audio on the Asrock MB K8NF6G-VSTA is supported, in the official release (64bit or 32 bit) it isn't. Would it be possible to have support in 7.10?

chipset NVIDIA® GeForce 6100 / nForce 405
audio 7.1 CH Windows® Vista™ Basic Level HD Audio (ALC861VD/ALC883 Audio Codec)
lan Realtek PHY RTL8201CL 

Thanks

---

### Post by Loïc2 on 2007-05-25
My Asrock MB K8NF6G-VSTA audio is supported in Feisty final, whether by upgrade from Herd5 or scratch install.

I only tried with i386, since I've got a Sempron without amd64 support.

Did you try booting a live cd? Do the sound still works if you boot a Herd 4 cd (or with another distribution/OS)?

---

### Post by Loïc2 on 2007-05-25
Also you might want to check if you did any changes to your system since Herd 4 (bios updates, etc...)

---

### Post by juantovarm on 2007-05-25
same pc, same bios, same everything. It worked perfectly with herd 4 but not with the final release, live cd or otherwise.... well i will propably have to do some compiling

---

