---
title: "Can't set NTSC-M to Video Out"
date: 2009-01-03
forum: General Help
---

### Post by Dan Paul Ciocan on 2009-01-03
Hi please help me. I have an ATI Radeon HD 4670 and I use Xubuntu 8.10. This is my xorg.conf:
```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
[COLOR="Red"]       Option      "TVFormat" "NTSC-M" # Added by me[/COLOR]
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
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
```
So, I used "aticonfig --initial" first. Then I added the NTSC-M option because I live in Canada. But when i run:
```
danpaul@xubuntu:~$ sudo aticonfig --tv-info
The TV Format is "[COLOR="Red"]PAL-B[/COLOR]"
The TV geometry is "87x40+0+0"
The horizontal position limits are [-145, 145]
The vertical position limits are [-52, 52] 
TV overscan mode is disabled
```
The TV format is PAL-B, so my TV don't work correctly. Please explain to me how to configure xorg.conf with the NTSC-M format. Thank you very much! Have a nice day! :)

---

