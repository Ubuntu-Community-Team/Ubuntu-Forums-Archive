---
title: "X-Windows sees all my monitors, but gnome 3 does not"
date: 2013-10-10
forum: Desktop Environments
---

### Post by Scott_Schumacher on 2013-10-10
So, my xorg.conf looks like this:


Section "ServerLayout"
	Identifier     "Layout0"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
	Screen      2  "Screen2" LeftOf "Screen0"
	Screen      3  "Screen3" LeftOf "Screen2"
#	Option         "Xinerama" "1"
EndSection


Section "Monitor"
	Identifier  "Monitor0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection


Section "Monitor"
	Identifier  "Monitor1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection


Section "Monitor"
	Identifier  "Monitor2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection


Section "Monitor"
	Identifier  "Monitor3"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection


Section "Device"
	Identifier  "Device0"
	Driver      "fglrx"
	VendorName  "Advanced Micro Devices"
	BoardName   "GeForce 210"
	Option	    "UseFastTLS" "1"
	BusID       "PCI:1:0:0"
	Screen      0
EndSection


Section "Device"
	Identifier  "Device1"
	Driver      "fglrx"
	VendorName  "Advanced Micro Devices"
	BoardName   "GeForce 210"
	Option	    "UseFastTLS" "1"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection


Section "Device"
	Identifier  "Device2"
	Driver      "fglrx"
	VendorName  "Advanced Micro Devices"
	BoardName   "GeForce 210"
	Option	    "UseFastTLS" "1"
	BusID       "PCI:4:0:0"
	Screen      0
EndSection


Section "Device"
	Identifier  "Device3"
	Driver      "fglrx"
	VendorName  "Advanced Micro Devices"
	BoardName   "GeForce 210"
	Option	    "UseFastTLS" "1"
	BusID       "PCI:4:0:0"
	Screen      1
EndSection


Section "Screen"
	Identifier "Screen0"
	Device     "Device0"
	Monitor    "Monitor0"
	DefaultDepth     24
	SubSection "Display"
#		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


Section "Screen"
	Identifier "Screen1"
	Device     "Device1"
	Monitor    "Monitor1"
	DefaultDepth     24
	SubSection "Display"
#		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


Section "Screen"
	Identifier "Screen2"
	Device     "Device2"
	Monitor    "Monitor2"
	DefaultDepth     24
	SubSection "Display"
#		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


Section "Screen"
	Identifier "Screen3"
	Device     "Device3"
	Monitor    "Monitor3"
	DefaultDepth     24
	SubSection "Display"
#		Viewport   0 0
		Depth     24
	EndSubSection
EndSection



X-windows works, but gnome 3 only uses the first monitor

Any Ideas?

Thanks

---

