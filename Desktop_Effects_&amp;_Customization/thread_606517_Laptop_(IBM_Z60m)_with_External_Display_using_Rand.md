---
title: "Laptop (IBM Z60m) with External Display using RandR 1.2"
date: 2007-11-08
forum: Desktop Effects &amp; Customization
---

### Post by TooEZ on 2007-11-08
G'day,

I have been trying for days to configure my work laptop to dual display (not clone) like I used to with XP (this is my last hurdle before I totally ditch XP). I need to be able to run VMware on one screen and Firefox/Terminal Server Client in the other... 

Hardware Setup:
IBM Thinkpad Z60m with a Radeon Mobility X600 - Resolution of 1280x800
HP L1925 Display (Home)  - Resolution of 1280x1024
Lenovo 19" Display (Work) - Resolution of 1280x1024

I have followed a bunch of threads here and search high and low but I have not been able to do it. 

I have followed these guides so far:
[http://wiki.debian.org/XStrikeForce/HowToRandR12]("http://wiki.debian.org/XStrikeForce/HowToRandR12")

The problem is after I add the Virtual 2560x1024 in the Screen section of my xorg.conf. As soon as I restart an error comes up saying "Ubuntu is running in low-graphics mode".

My xorg.conf:

```
# xorg.conf (xorg X Window System server configuration file)
Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc M24 1P [Radeon Mobility X600]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc M24 1P [Radeon Mobility X600]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x800"
#              Virtual           2560x1024
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection
```

xRandR:
```
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1200
VGA-0 connected (normal left inverted right)
   1280x1024      59.9  
   1152x864       75.0  
   1024x768       75.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  
DVI-0 connected 1280x800+0+0 (normal left inverted right) 0mm x 0mm
   1280x800       60.0* 
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
LVDS connected 1280x800+0+0 (normal left inverted right) 0mm x 0mm
   1280x800       60.0*+   60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
S-video disconnected (normal left inverted right)

```

A little bribery has never hurt!!! I will give $1 to any person who helps me get this solved! 

Cheers

---

### Post by TooEZ on 2007-12-19
Bumping...

This has now been bothering me for weeks and I cant get it soved.  I am on holidays for a a week and i want to get this working 100% for when I get back to work...

HELP... I will give $5 to any person who helps me get this solved!

---

### Post by scottym on 2007-12-31
Give this a try:
[http://forlong.blogage.de/article/2007/10/2/Desktop-effects-by-default-in-Gutsy---how-Compiz-Fusion-enhances-Ubuntus-desktop-of-version-710](http://forlong.blogage.de/article/2007/10/2/Desktop-effects-by-default-in-Gutsy---how-Compiz-Fusion-enhances-Ubuntus-desktop-of-version-710)

---

### Post by topolino on 2008-01-02
Hi,

I think there is a mistake in your xorg.conf file. It should be:

Virtual         2560 1024

instead of

Virtual         2560x1024

Replace the 'x' by ' '.

Hope this helps,

---

