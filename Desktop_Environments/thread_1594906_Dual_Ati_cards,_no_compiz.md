---
title: "Dual Ati cards, no compiz"
date: 2010-10-12
forum: Desktop Environments
---

### Post by skrribble on 2010-10-12
I'm using a Radeon HD 5450 and a Radeon HD 4350 with proprietary drivers.  Got Xinerama working using a combo of ATI Catalyst control center and previous knowledge of xorg.conf from trying to get ati cards working before.  Had compiz working with one monitor on one card, but no compiz with one monitor on each card.

xorg.conf:
```
Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "Left Screen" 0 0
	Screen         "Right Screen" 1600 0
	Option	       "Xinerama" "true"
EndSection

Section "Monitor"
	Identifier   "Left"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1600x900"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "Right"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1600x900"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "Radeon HD 5450"
	Driver      "fglrx"
	Option	    "Monitor-DFP2" "0-DFP2"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "Radeon HD 4350"
	Driver      "fglrx"
	Option	    "Monitor-DFP2" "1-DFP2"
	BusID       "PCI:4:0:0"
EndSection

Section "Screen"
	Identifier "Left Screen"
	Device     "Radeon HD 5450"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Right Screen"
	Device     "Radeon HD 4350"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

also:
```
glxinfo | grep rendering
direct rendering: Yes

```
and 
```
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 5450
OpenGL version string: 4.0.10237 Compatibility Profile Context

```

any ideas?? it kind of looks like its still trying to use one card for the whole screen to me, but i cant seem to figure it out... thanks in advance for any help

---

### Post by skrribble on 2010-10-13
nothing?? If anyone could help me get it working without Xinerama (separate x session on each screen) I would be very thankful for that too, but cant seem to get it to work myself.  I really just want 2 monitors, each with compiz.  Being able to drag windows between the two would be nice, but if not possible i understand....

---

### Post by sambolinux on 2010-10-14
compiz isn't working on my system with a single card, dual monitor either. Me thinks there is a problem with compiz or with ati drivers(my card by the way is a 4670 1gb ddr3).

---

### Post by sambolinux on 2010-10-14
compiz isn't working on my system with a single card, dual monitor either. Me thinks there is a problem with compiz or with ati drivers(my card by the way is a 4670 1gb ddr3).It work fine in lucid but not with maverick.
```
 sambo@my-ubuntu-maverick:~$ glxinfo | grep rendering 
direct rendering: Yes 
direct rendering: Yes
``` 
```
sambo@my-ubuntu-maverick:~$ fglrxinfo 
display: :0.1  screen: 0
 OpenGL vendor string: ATI Technologies Inc.
 OpenGL renderer string: ATI Radeon HD 4600 Series
 OpenGL version string: 3.3.10237 Compatibility Profile Context   
 display: :0.1  screen: 1 
OpenGL vendor string: ATI Technologies Inc. 
OpenGL renderer string: ATI Radeon HD 4600 Series 
OpenGL version string: 3.3.10237 Compatibility Profile Context  
```

---

