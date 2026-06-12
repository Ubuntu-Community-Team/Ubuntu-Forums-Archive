---
title: "Beryl problems on Xubuntu Edgo with Radeon"
date: 2006-11-19
forum: Desktop Environments
---

### Post by JC_Starter on 2006-11-19
Hi, 

i followed nearly all of the guides published on these forums, but i still don't manage to get a beryl running on a fresly installed Xubuntu 6.1 with Radeon 9600.

Here is some 'evidence' : 

$ glxinfo | grep vendor
libGL warning: 3D driver claims to not support visual 0x4b
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.

Typing in 'beryl' from a terminal session at start up gets me this error:

XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
libGL warning: 3D driver claims to not support visual 0x4b
initiating splash 
beryl : water : GL_ARB_fragment_program is missing


Starting beryl-manager then switching to beryl get me this error : 

XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: Another window manager is already running on screen: 0
beryl: No manageable screens found on display :0.0

Xorg.conf looks like this: 

Section "Device"
	Identifier	"Radeon 9600"
	Driver		"ati"
	BusID		"PCI:1:0:0"
        Option          "AGPMode"       "8"
        Option          "AccelMethod"   "EXA"
        Option          "ColorTiling"   "on"
        Option          "XAANoOffscreenPixmaps"
	Option          "DRI" "true" 
	Option          "EnablePageFlip" "true"
	Option          "RenderAccel" "true"
	Option          "AGPFastWrite" "on"
EndSection

Section "ServerLayout"
        Option          "AIGLX"         "true"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

Where am I making an error (or perhaps errors ):-D

---

### Post by pinworm on 2006-11-25
I think im having the exact same problem as you, ive been looking around, but havent been able to find a solution yet

---

### Post by pinworm on 2006-11-27
i dont know if this will be helpful to you at all, but i got beryl working enough to just test it out, you prob wouldnt want to run it like this.  you have to log in through a safe terminal session, and manually start up beryl-manager, if that runs ok, you should get window decorations around the terminal.  then start up xfce-panels,  and xfce-desktop and what ever else you need.  those might not be the exact names i dont remember.

---

### Post by drphilngood on 2006-11-27
Have you tried this thread?

[One thread to rule them all v2: Beryl & Official Compiz]("http://ubuntuforums.org/showthread.php?t=272104")

You can also try #ubuntu-xgl on irc.freenode.net.

Good luck!

---

### Post by mcduck on 2006-11-27
With a fairly new Ati card like 9600, you should be using Ati's proprietary drivers (fglrx) and XGL instead of open-source drivers (ati) and AIGLX.

---

### Post by pinworm on 2006-11-28
yea you may be right, from what i understand though aiglx is much more user freindly to get running, and you can change windows managers in the same session.  im not sure though what the other pro/cons are.

---

### Post by igknighted on 2006-11-28
I would avoid fglrx/xgl.  I used an x800 for a while and it worked perfectly, what if you try changing the 'ati' driver to 'radeon'?  'ati' never worked for me, but 'radeon' worked perfectly.

---

### Post by Billquinn1 on 2006-11-28
I had to comment out a couple of parts to make this work. I had to change to the Radeon driver also.

Section "Device" Identifier "ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
 Driver "radeon" 
BusID "PCI:1:0:0" 
Option "DRI" "true" 
Option "ColorTiling" "on" 
Option "EnablePageFlip" "true" 
Option "AccelMethod" "XAA" 
Option "XAANoOffscreenPixmaps" 
Option "GARTSize" "64" 
# Option "RenderAccel" "true" 
# Option "AGPMode" "2" 
# Option "AGPFastWrite" "on" 
EndSection


hope this helps

---

### Post by viz_e on 2006-12-12
Same problem here:
```
~$ beryl
XGL Absent, checking for NVIDIA
Nvidia Absent, checking for texture_from_pixmap
texture_from_pixmap Present
beryl: Another window manager is already running on screen: 0
beryl: No manageable screens found on display :0

```

Any news?

---

