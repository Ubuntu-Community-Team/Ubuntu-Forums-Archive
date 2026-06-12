---
title: "Dual Display on M-301Z (Ubuntu 10.04)"
date: 2011-06-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ceezax on 2011-06-22
Hello,

I have Dell Inspiron M-301z with Ubuntu 10.04 installed on it.


I have failed to display my screen desktop on an external monitor although it happened once the first time i connected the external monitor and after this, no luck even i have upgraded to Ubuntu 11 to get this working but also no luck. i have a DVI to VGA converter and the following (xorg.conf.fglrx-0)

----------------------------------------------------------------------------------------------------------------------------------
Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
	Option "AIGLX" "on"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

Section "Monitor"
	Identifier   "0-LVDS"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1366x768"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-DFP_EXTTMDS"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1366x768"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "Default Device"
	Driver      "fglrx"
	Option "XAANoOffscreenPixmaps" "on"
	Option "TexturedVideo" "off"
	Option "VideoOverlay" "off"
	Option "OpenGLOverlay" "off"
	Option "Textured2D" "on"
	Option "UseFastTLS" "1"
	Option "BackingStore" "on"
	EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	Option	    "Monitor-DFP_EXTTMDS" "0-DFP_EXTTMDS"
	Option	    "Monitor-LVDS" "0-LVDS"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-1"
	Driver      "fglrx"
	Option	    "Monitor-LVDS" "0-LVDS"
	BusID       "PCI:1:5:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-1"
	Device     "amdcccle-Device[1]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

----------------------------------------------------------------------------------------------------------------------------------

I will appreciate your help as this is urgent for me.

Thanks in advance

---

