---
title: "Ubuntu 9.04 trihead configuration"
date: 2009-05-05
forum: Desktop Environments
---

### Post by keyboardgnome on 2009-05-05
Greetings,

So I'll cut to the chase, I have a trihead configuration that uses two USB to VGA video adapters and an integrated on board Intel video adapter. So far, I'm able to get desktops on all displays without a problem. What I would like to do is have my desktop stretched across all desktops so that I can move windows, terminals, firefox, etc around.

The problem is that the integrated motherboard's video adapter is an Intel 82945G/GZ, and from researching it other folks say to use xrandr and not xinerama. Unfortunately, I cant do this as there's only one video out on the integrated board, and I have two other adapters.

If I try to use the 'driver "intel"' option in xorg with xinerama, x11 crashes hard. Using the i810 driver doesnt yield a picture on the display that is attached to that card.

Below is my xorg.conf from trying various solutions and combinations. Anyone have any idea's as to why this isn't working? I'll post some X error's shortly.

Thanks in advance.

```
Section "Device"
	Identifier	"Configured Video Device"
	BusID "PCI:0:2:0"
	Driver "intel"
	#Driver "i810"
	#Option      "VideoRam"       "8192"
	#Option      "DevicePresence" "true"
	#Option "NoAccel" "yes" 
	#Option "AccelMethod" "XAA"
	#added below
	#Option "AccelMethod" "exa"
	#Option "MigrationHeuristic" "greedy"
	Screen 0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "Device"
 Identifier "Device[SISUSBVGA]"
 VendorName "SiS" # Value does not matter
 BoardName "SiS" # Value does not matter
 Driver "sisusb"
EndSection

Section "Monitor"
 Identifier "Monitor[SISUSBVGA]"
 VendorName "Monitor Vendor" # value does not matter
 ModelName "Monitor Model" # value does not matter
 VertRefresh 50-75
 HorizSync 30-90
EndSection

Section "Screen"
 Identifier "Screen[SISUSBVGA]"
 Device "Device[SISUSBVGA]"
 Monitor "Monitor[SISUSBVGA]"
 DefaultDepth 16
 SubSection "Display"
  Depth 16
  Modes "1280x1024" "1024x768" "800x600" "640x480"
 EndSubSection
 SubSection "Display"
  Depth 8
  Modes "1280x1024" "1024x768" "800x600" "640x480"
 EndSubSection
 SubSection "Display"
  Depth 24
  Modes "1280x1024" "1024x768" "800x600" "640x480"
 EndSubSection
EndSection

Section "Device"
 Identifier "Device[SISUSBVGA]2"
 VendorName "SiS" # Value does not matter
 BoardName "SiS" # Value does not matter
 Driver "sisusb"
EndSection

Section "Monitor"
 Identifier "Monitor[SISUSBVGA]2"
 VendorName "Monitor Vendor" # value does not matter
 ModelName "Monitor Model" # value does not matter
 VertRefresh 50-75
 HorizSync 30-90
EndSection

Section "Screen"
 Identifier "Screen[SISUSBVGA]2"
 Device "Device[SISUSBVGA]2"
 Monitor "Monitor[SISUSBVGA]2"
 DefaultDepth 16
 SubSection "Display"
  Depth 16
  Modes "1280x1024" "1024x768" "800x600" "640x480"
 EndSubSection
 SubSection "Display"
  Depth 8
  Modes "1280x1024" "1024x768" "800x600" "640x480"
 EndSubSection
 SubSection "Display"
  Depth 24
  Modes "1280x1024" "1024x768" "800x600" "640x480"
 EndSubSection
EndSection


Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 0	"Default Screen"
	Screen 1	"Screen[SISUSBVGA]" RightOf "Default Screen"
	Screen 1        "Screen[SISUSBVGA]2" LeftOf "Default Screen"
	#Option         "Xinerama" "true"
	#Option 		"Clone" "off"
EndSection

```

---

### Post by keyboardgnome on 2009-05-05
Debug info:

Errors and Warnings for the intel driver
```
grep EE /var/log/Xorg.0.log.intel 
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) intel(0): Failed to init memory manager 
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) Falling back to old probe method for sisusb
(WW) intel(0): libpciaccess reported 0 rom size, guessing 64kB
(WW) intel(0): ESR is 0x00000001, instruction error
(WW) intel(0): PRB0_CTL (0x0001f001) indicates ring buffer enabled
(WW) intel(0): Existing errors found in hardware state.

```

Warnings and errors for the i810 driver
```
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) Falling back to old probe method for sisusb
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER

```


Warnings and errors for even the vesa driver:
```

	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) Falling back to old probe method for sisusb

```

Yup, that's right.... vesa doesnt work either. It seems to complain the same way that the intel driver does in regards to memory related issues. 

I've tried new combinations of the following of the Device for intel:

```
	#Option 	"NoAccel" "true"
	#Option "DRI" "false" 
	#Option "AccelMethod" "UXA"
	#Option "AccelMethod" "XAA"
	#added below
	#Option "AccelMethod" "exa"

```

None seem to work. Yes, I do uncomment them when I try them one at a time. :) And recomment out the previous lines too....

---

### Post by keyboardgnome on 2009-05-06
Any ideas?

---

### Post by keyboardgnome on 2009-05-11
>whistles<

I think what I need to use is Xinerama, however the driver for the intel card is now intentionally not using it anymore. Is there anything else out there that is like Xinerama that is supported?

---

### Post by jwmuelle on 2009-11-23
did you ever find a solution to this?  

I'm running laptop with tri-head config.  Laptop display and integrated VGA are able to work as a single desktop across the 2 displays (because they're on the same video card, I assume) but I can't combine the 3rd screen, which is connected via USB2VGA adapter (Tritton).  That one only seems to work as a separate desktop, the same issue you reported.

Also, I see you posted at 9.04.  I'm running 9.10.  Are you using gnome or KDE?  I'm forced to use gnome with my config.  When using KDE (with/without kdm & kwin) I get lots of poor results on the 3rd screen... like X crashes, mouse moving to USB2VGA screen and unable to move back...


jw

---

