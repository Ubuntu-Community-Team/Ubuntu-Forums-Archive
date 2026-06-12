---
title: "Startx segmentation fault on Toshiba Satellite C40D"
date: 2014-01-19
forum: Desktop Environments
---

### Post by alexander.s.farley on 2014-01-19
I've just attempted a dual-boot install of Ubuntu 13.10 and Win8.1. Had some issues with UEFI which now seem to be resolved. 

Problem: I am not able to boot into a desktop environment. Running 'startx' causes a segmentation fault at address 0x8.

/etc/default/grub contains the line:
GRUB_CMDLINE_LINUX_DEFAULT="text"

Previously, this line was GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" but I found that this resulted in a blinking cursor after selecting Ubuntu in the GRUB2 prompt. "text" at least allows me to boot into a terminal. 

Hardware background: Toshiba Satellite C40D laptop, Win 8 installed from factory. 'lspci' indicates:
VGA compatible controller: Advanced Micro Devices, INC. [AMD/ATI] Kabini [Radeon HD 8400]

When booting from a LiveUSB, the desktop mode started without any issues, so there exists some setting under which the graphics are recognized - I just don't know what happened in between testing Ubuntu without installing, and after installing, but somehow the graphics are apparently no longer recognized. Choosing Ubuntu Recovery Mode from Grub, followed by failsafeX, results in:
Loading Extension GLX
(EE)
Fatal server error: 
(EE) no screens found(EE)

Can anyone point me where to look next?

---

### Post by squakie on 2014-04-08
Sorry - I didn't see this thread until now.  If  you are still having the problem please changing the line to be as follows:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

---

