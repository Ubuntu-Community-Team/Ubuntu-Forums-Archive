---
title: "Beryl fails, no composite extension, wit ATI Mobility Radeon 9000"
date: 2007-03-18
forum: Desktop Effects &amp; Customization
---

### Post by Austrian_Prototype on 2007-03-18
Hello everybody!

i can't get beryl to run with my ubuntu.

uname -r says the following:
markus@markus-laptop:~$ uname -r
2.6.17-11-386

fglrxinfo:

markus@markus-laptop:~$ fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY/RADEON 9000 DDR Generic
OpenGL version string: 1.3.1091 (X4.3.0-8.28.8)

It was quite a success for me to get the ATI openGL driver up and running :-)

When trying to start beryl, beryl says:

No composite extension
beryl: No composite extension


my xorg.conf looks like that:

Section "Device"
Identifier "ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
Driver "fglrx"
BusID "PCI:1:0:0"
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Extensions"
Option "Composite" "Disable"
EndSection

Do you have any clues??? I read somewhere that beryl wont run without composite-support, but I always read that people with the same Graphiccard get it done.
I tried both versions, beryl 1.99 and 2.0

Thanks in advance
Markus

---

### Post by Waappu on 2007-03-18
Hi

fglrx driver not support composite. If you want use that driver you need install XGL.
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL#Installing_Xgl_and_Beryl](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL#Installing_Xgl_and_Beryl)

Or uninstall that driver and use open source driver. I think it's better choise. Open source driver supports composite.
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX)
And if you are using Edgy you can upgrade your Xorg to get better performance
[http://ubuntuforums.org/showthread.php?t=373087](http://ubuntuforums.org/showthread.php?t=373087)

---

### Post by Austrian_Prototype on 2007-03-19
Hi,
Thanks for your help!

Unfortunately I now see that my chipset (R250) is not supported by the opensource driver (ati || radeon).
On the other hand, fglrx doesn't support composite, and with the xgl tutorial I can't get the xserver up and running.

Is there anybody who uses beryl or compiz with ATI Mobility Radeon 9000 R250 ??? 
Is there any hope for me?

Thx in advance 
 Markus

---

### Post by Waappu on 2007-03-19
Hi

See this post
[http://ubuntuforums.org/showthread.php?t=291464](http://ubuntuforums.org/showthread.php?t=291464)

---

### Post by Austrian_Prototype on 2007-03-20
thx! perfect match!!!!!

Double.-bookmarked this site :)

---

