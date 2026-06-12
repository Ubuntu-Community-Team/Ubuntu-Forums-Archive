---
title: "kde goes black"
date: 2008-09-03
forum: Desktop Environments
---

### Post by radu_radu on 2008-09-03
Hello all,

I got this weird problem:

KDE will load via KDM, and even Compiz-Fusion loads, but then, after a couple of seconds, the screen goes black, only the mouse cursor stays on top and can be moved. Before going black, KDE was responsive, I could launch the menu, apps, but not for long. I can fallback to a tty. Also, Gnome or Fluxbox work just fine (compiz included). 
I run fglrx as video driver.

This is my xorg.conf:
```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizEdgeScroll" "0"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Virtual 1280 800
	EndSubSection
EndSection

Section "Extensions"
       Option      "Composite" "On"
EndSection


```

And here ->[HTML]http://rapidshare.com/files/142389960/logs.tar.bz2.html[/HTML] you can find my /var/log/Xorg.log

Any idea where KDE dumps its logs? Or how to get debug info from KDE?

---

