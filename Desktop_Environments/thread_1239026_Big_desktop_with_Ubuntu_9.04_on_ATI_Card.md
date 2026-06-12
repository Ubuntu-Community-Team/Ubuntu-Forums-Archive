---
title: "Big desktop with Ubuntu 9.04 on ATI Card"
date: 2009-08-13
forum: Desktop Environments
---

### Post by srimalj on 2009-08-13
Hi

Has anyone got big (large desktop) working with Ubuntu 9.04 with an ATI card?

(i,e a setup where you have 2 or more monitors and you have one seamless desktop where you can move windows across the monitors - i hope i'm using the right terminology)

This is my setup

$ lspci | grep -i vga
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3450

with 2 identical monitors.

I managed to get a dual head setup (at least i think thats what its called)..

using

# aticonfig--initial
# aticonfig--initial=dual-head


This is perfect except for the fact that both displays act as two separate workstations -- ie i cant move windows accros the two displays

Any idea/experience on how I can merge the 2 displays in to one big desktop?

Thanks in advance

Srimal.

---

### Post by alfalfa31 on 2009-11-06
I'm running 5 monitors, two 22" @ 1680x1050 and 3 17" @ 1280x1024, total usable width of 7200px (which is nuts, I know, but why not, right?). They're running on quad RadeonHD 3650's.  I'd be running 8 if I had either the desk space or the desire to go vertical.

```
-----------------------------------------------------------------------
|           |           |                |                |           | 
|           |           |                |                |           | 
|  17" 1    |  17" 2    |   22" 1        |    22" 2       |   17" 3   | 
|           |           |                |    Primary     |           | 
|           |           |                |                |           | 
------------------------|                |                |------------
                        ----------------------------------- 

```
I had to hand edit my xorg.conf file to make it go (which I've been doing for a while anyway).

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 4240 0
	Screen         "aticonfig-Screen[0]-1" 2560 0
	Screen         "aticonfig-Screen[1]-0" 1280 0
	Screen         "aticonfig-Screen[1]-1" 0 0
	Screen         "aticonfig-Screen[2]-0" RightOf "aticonfig-Screen[0]-0"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "on"
EndSection

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

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "PairModes" "1680x1050+1680x1050"
	Option	    "DesktopSetup" "horizontal,reverse"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-1"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]-0"
	Driver      "fglrx"
	Option	    "PairModes" "1280x1024+1280x1024"
	Option	    "DesktopSetup" "horizontal,reverse"
	BusID       "PCI:2:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]-1"
	Driver      "fglrx"
	BusID       "PCI:2:0:0"
	Screen      1
EndSection

Section "Device"
	Identifier  "aticonfig-Device[2]-0"
	Driver      "fglrx"
	BusID       "PCI:5:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
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
	EndSubSection
EndSection
```

If you enable xinerama it should get things running for you (which you can do in xorg.conf or in the Catalyst control center).  Problem is, I don't know what driver versions you're running and if you've upgraded to 9.10 (which was a pain for me).

---

