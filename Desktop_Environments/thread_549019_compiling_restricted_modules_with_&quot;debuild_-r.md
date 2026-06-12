---
title: "compiling restricted modules with &quot;debuild -rfakeroot&quot; fail"
date: 2007-09-12
forum: Desktop Environments
---

### Post by je_457 on 2007-09-12
version: Ubuntu 7.04

I only needed to change 1 setting in the kernel (CONFIG_USB_SUSPEND off) so that my scanner can work.

I followed the instructions on [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile) to compile kernel.

The process went fine, but now had a broken VMplayer. This is "restricted" module, so I followed the instructions for restricted modules. This include:

[FONT="Courier New"][B]   cd linux-restricted-modules-2.6.20-2.6.20
   debuild -rfakeroot[/B][/FONT]

the "sudo debuild -rfakeroot" fail with the following error:

[FONT="Courier New"]Now signing changes and any dsc files...
 signfile linux-restricted-modules-2.6.20_2.6.20.5-16.29.dsc Tim Gardner <tim.gardner@canonical.com>
gpg: [COLOR="Red"]skipped "Tim Gardner <tim.gardner@canonical.com>": secret key not available[/COLOR]
gpg: [stdin]: clearsign failed: secret key not available
debsign: gpg error occurred!  Aborting....
debuild: fatal error at line 1155:
running debsign failed[/FONT]

Any advise on how to fix this (without getting a PHD in Computer Science)

---

