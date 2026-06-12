---
title: "Failed Userful install, can't recover desktop"
date: 2010-12-05
forum: Desktop Environments
---

### Post by zmef on 2010-12-05
Hi Fellow Ubuntu Users!

I recently bought a new television to hook up to my on board video card(intel I reckon) and wanted to set up a multiseat environment with Userful Desktop Multiplier. After realizing I need some more hardware in order to utilize Userful, I uninstalled it with the script they provide.

Here are my problems. When I login to Gnome in normal mode I get a black box across the bottom of both screens. Compiz does not work, and my monitors are no longer recognized. I also have no way to change how the monitors are used, cloned or multiview, or what have you.

When I login to gnome with the safe mode option, I don't have this problem. If I login as root the problems still persist though.

I have tried "fixing" the xorg.conf, but really don't know what I am doing with the recent changes to that. I updated to 10.10 from 10.04 in hopes that X would automagically fix my problems, no such luck.

Comments, questions, nasty remarks?

thanks in advance
 zmef

---

### Post by zmef on 2010-12-05
Okay, so here is where I am at now.I ran the copiz-check script and realized I was using the "fbdev" driver instead of the intel driver in xorg.conf. I changed that to intel and I no longer get that black box at the bottom of my screen. I still cannot change my resolution, use my television as a second monitor other than a "clone" of my main display, and I can't enable desktop effects via compiz.

Below is my current xorg.conf. I believe this is where my problems lie, but cannot identify them. Do you see any problems?

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#	InputDevice    "Mouse0" "CorePointer"
# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "dri"
	Load  "glx"
	Load  "extmod"
	Load  "record"
	Load  "dbe"
	Load  "dri2"
EndSection

# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#Section "InputDevice"
#	Identifier  "Keyboard0"
#	Driver      "kbd"
#EndSection

# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#Section "InputDevice"
#	Identifier  "Mouse0"
#	Driver      "mouse"
#	Option	    "Protocol" "auto"
#	Option	    "Device" "/dev/input/mice"
#	Option	    "ZAxisMapping" "4 5 6 7"
#EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "Rotate"             	# <str>
        #Option     "fbdev"              	# <str>
        #Option     "debug"              	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "4 Series Chipset Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

---

