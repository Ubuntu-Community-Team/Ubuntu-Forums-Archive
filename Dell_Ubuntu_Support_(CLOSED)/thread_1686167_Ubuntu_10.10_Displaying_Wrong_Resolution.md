---
title: "Ubuntu 10.10 Displaying Wrong Resolution"
date: 2011-02-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Mr_PS3 on 2011-02-11
About two days ago I successfully installed Linux Ubuntu 10.10 on my Dell Studio 1558. Today when I hooked up my laptop to an external monitor, I noticed I didn't have the same resolution as I did before. I booted back into my Windows partition and check my resolution. It said 1920x1080. The problem is that I am not able to switch to this 1920x1080 resolution. I tried using xrandr and editing the xorg.conf
Here is my xorg.conf file:
```
Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[2]-0" 0 0
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "0-LVDS"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1440x900"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "Default Device"
	Driver      "fglrx"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[2]-0"
	Driver      "fglrx"
	Option	    "Monitor-LVDS" "0-LVDS"
	BusID       "PCI:2:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
	SubSection "Display"
		Virtual   1920 1080
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[2]-0"
	Device     "amdcccle-Device[2]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

How do I get the resolution to 1920x1080?

---

### Post by Mr_PS3 on 2011-02-12
Nevermind I figured it out on my own. I realized I only changed the Section "Screen" setting instead of the Section "Monitor" setting. I now have my desktop at 1920x1080 resolution.

---

