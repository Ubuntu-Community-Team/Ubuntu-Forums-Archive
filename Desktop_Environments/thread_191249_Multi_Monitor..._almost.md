---
title: "Multi Monitor... almost"
date: 2006-06-07
forum: Desktop Environments
---

### Post by Caracarn on 2006-06-07
I am attempting to get multi monitor support running on my ATI Radeon 9600 XT. My two monitors are plugged into the 1 AGP card via the analog and digital connectors.

I currently have the fglrx drivers installed and I followed the HowTo at

[http://gentoo-wiki.com/HOWTO_Dual_Monitors](http://gentoo-wiki.com/HOWTO_Dual_Monitors)

More specifically I entered the following commands

```
aticonfig --initial=dual-head --dtop=horizontal --screen-layout=right --iagp=off -v
/etc/init.d/xdm restart
```

Ubuntu didnt like the --iagp=off -v part of the command, so I dropped it, and it seemed to work ok.
It also didnt like the second command as it didnt know what xdm was, so I skipped that as I assumed it was just doing a restart of Gnome.

I rebooted my PC and at first it seemed to work, I logged in and the rotating cursor was sitting between the two screens. Unfortunately when I actually tried to move the cursor over to the second screen it wont move past about 1cm into the second screen. I can actually see the cursor on the second screen I just can't move across any further than that 1cm wide vertical strip.

I thought it might be a resolution problem with xorg.conf so I tried playing around with, but it either didnt make any difference or gave me an Xserver error and wouldnt load the gui until I removed the changes. I am a bit of a Linux newbie so any assistance in fixing this problem is appreciated.

Here is the video part of the xorg.conf

```
Section "Monitor"
	Identifier   "IBM 6332 E74"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
	Driver      "ati"
	BusID       "PCI:2:5:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "DesktopSetup" "horizontal"
	BusID       "PCI:2:5:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	BusID       "PCI:2:5:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
	Monitor    "IBM 6332 E74"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

```

---

