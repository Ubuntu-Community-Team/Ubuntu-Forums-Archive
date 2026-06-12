---
title: "ATI proprietary drivers"
date: 2005-04-22
forum: Gaming &amp; Leisure
---

### Post by dalegribble on 2005-04-22
I wanted to see what experience people have had with the proprietary ATI driver vs. the xorg-fglrx driver in Ubuntu.  I was using the xorg-fglrx drivers and was able to use opengl, but in particular World of Warcraft kept crashing on me.  I decided to try the proprietary drivers, and received the following error when running "sudo sh make.sh" in /lib/modules/fglrx/build_mod/

Warning: could not find /lib/modules/fglrx/build_mod/2.6.x/.libfglrx_ip.a.GCC3.cmd for /lib/modules/fglrx/build_mod/2.6.x/libfglrx_ip.a.GCC3

I wonder if this is just specific to Ubuntu?  ATI is still not displaying in the vendor id of glxinfo.  I've installed the kernel headers and source...Any help would be greatly appreciated :D

Xorg.0.log
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:0 found

BTW, PCI:1:0:0 is the correct BusID

---

### Post by jdodson on 2005-04-22
follow the steps in the guide to get 3D proprietary drivers working for your ATI card: [http://ubuntuforums.org/showthread.php?t=25723](http://ubuntuforums.org/showthread.php?t=25723)

---

### Post by dalegribble on 2005-04-22
This is really a great guide for getting the xorg-fglrx package installed.  However, I want to try the drivers you download from the ATI website.  Does anyone have any information on this error:

Warning: could not find /lib/modules/fglrx/build_mod/2.6.x/.libfglrx_ip.a.GCC3.cmd for /lib/modules/fglrx/build_mod/2.6.x/libfglrx_ip.a.GCC3

Or has anyone even installed the ATI drivers from their website w/ 3D support?

---

### Post by jdodson on 2005-04-22
[QUOTE=dalegribble]This is really a great guide for getting the xorg-fglrx package installed.  However, I want to try the drivers you download from the ATI website.  Does anyone have any information on this error:

Warning: could not find /lib/modules/fglrx/build_mod/2.6.x/.libfglrx_ip.a.GCC3.cmd for /lib/modules/fglrx/build_mod/2.6.x/libfglrx_ip.a.GCC3

Or has anyone even installed the ATI drivers from their website w/ 3D support?[/QUOTE]

i recommend using the drivers in ubuntu, however people are doing what you are requiring, check this guide here: [http://ubuntuforums.org/showthread.php?t=24557](http://ubuntuforums.org/showthread.php?t=24557)

---

