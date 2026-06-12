---
title: "Need help with my xorg.conf on 6 monitors/ 3 video cards..."
date: 2008-11-04
forum: Desktop Environments
---

### Post by bgovoni on 2008-11-04
Ok, I've spent forever trying to tinker with this and get it all to work. I have 6 20" lcds connected to 1 built in dual head ati x600 and 2 pci dual head ati x1300's. The problem I am having is that I can't make the x1300's not clone the desktop. The x600 works just fine on turning off the clone. Can someone look at my config and tell me what I'm doing wrong. I've also had no luck with the flgrx driver. I can't even get it to clone with that one enabled. I've also attached a picture of the beast running vista. But we need to take care of that...

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[2]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[2]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Virtual	3360 1050
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-1"
	Device     "aticonfig-Device[0]-1"
	Monitor    "aticonfig-Monitor[0]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Virtual	3360 1050
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]-0"
	Device     "aticonfig-Device[1]-0"
	Monitor    "aticonfig-Monitor[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Virtual	3360 1050
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]-1"
	Device     "aticonfig-Device[1]-1"
	Monitor    "aticonfig-Monitor[1]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Virtual	3360 1050
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[2]-0"
	Device     "aticonfig-Device[2]-0"
	Monitor    "aticonfig-Monitor[2]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Virtual	3360 1050
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[2]-1"
	Device     "aticonfig-Device[2]-1"
	Monitor    "aticonfig-Monitor[2]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Virtual	3360 1050
	EndSubSection
EndSection


Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	Screen         "aticonfig-Screen[0]-1" RightOf "aticonfig-Screen[0]-0"
	Screen         "aticonfig-Screen[1]-0" RightOf "aticonfig-Screen[0]-1"
	Screen         "aticonfig-Screen[1]-1" RightOf "aticonfig-Screen[1]-0"
	Screen         "aticonfig-Screen[2]-0" RightOf "aticonfig-Screen[1]-1"
	Screen         "aticonfig-Screen[2]-1" RightOf "aticonfig-Screen[2]-0"
	Option	    "Clone" "off"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-1"
	Driver      "ati"
	BusID       "PCI:1:0:1"
	Screen      1
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]-0"
	Driver      "ati"
	BusID       "PCI:4:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]-1"
	Driver      "ati"
	BusID       "PCI:4:0:1"
	Screen      1
EndSection

Section "Device"
	Identifier  "aticonfig-Device[2]-0"
	Driver      "ati"
	BusID       "PCI:5:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[2]-1"
	Driver      "ati"
	BusID       "PCI:5:0:1"
	Screen      1
EndSection

---

