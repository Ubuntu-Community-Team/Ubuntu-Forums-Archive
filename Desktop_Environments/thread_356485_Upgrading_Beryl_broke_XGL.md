---
title: "Upgrading Beryl broke XGL"
date: 2007-02-08
forum: Desktop Environments
---

### Post by bornakke on 2007-02-08
Did, like everybody else, the Beryl upgrad from 1.99.2 to 1.9999 the other day. However in my case i seems to be my XGL session which has been broken. Beryl doesn't seem to be the problem since uninstalling Beryl doesn't fix the problem. 

Running gnome without XGL shows no problems using glxinfo (or gears):

> display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI


I, however, get no hardwear rendering when I log into my XGL session:
> 
name of display: :1.0
display: :1  screen: 0
direct rendering: No
server glx vendor string: SGI


Also the following new errors are shown in the xorg.0.log :
> 
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32


I'm using ATI 9000 mobility, which shouldn't support Aiglx, which is why i'm thinking that the error might have something to do with the computer trying to use Aiglx. 

I have tried downgrading, upgrading and removing Beryl and Xserver-xgl, but it doesn't seem to have any effect what so ever on my problem! I also tried setting the XGL session up again 

Ubuntu is still very new to me, so any help or Idears of how to ”reinstall” XGL would be be more than gladly appreciated!


My Xorg.conf information is:
> 
[...]
Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection
[...]
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection
[...]
Section "DRI"
	Mode	0666
EndSection


---

### Post by bornakke on 2007-02-09
Found that my Xorg.conf file where missing 
> 
load "Glcore"


However now a new error is showing:

(EE) Failed to load /usr/lib/xorg/modules/extensions/libGLcore.so
(EE) Failed to load module "GLcore" (loader failed, 7)

Seems to be connected to libgl1-mesa-dri, but I haven't been able to find any information how to fix this. Have tried to reinstall the file, but without luck!

Any one who have and Idear of where I should start out looking? :confused:

---

### Post by shareMenaPeace on 2007-02-09
Maybe just by reinstalling you can fix this? (See my signature).

---

### Post by PriceChild on 2007-02-09
Don't reinstall,

try ```
LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa /usr/bin/beryl
```Until we fix the packages.

---

### Post by PriceChild on 2007-02-09
Don't reinstall,

try ```
LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa /usr/bin/beryl
```Until we fix the packages.

---

### Post by bornakke on 2007-02-10
Thanks a lot! Now I have a place to work from ([http://ubuntuforums.org/showthread.php?t=352350](http://ubuntuforums.org/showthread.php?t=352350))

---

