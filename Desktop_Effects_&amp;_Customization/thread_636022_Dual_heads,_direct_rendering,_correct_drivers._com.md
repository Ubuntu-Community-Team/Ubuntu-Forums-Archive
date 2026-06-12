---
title: "Dual heads, direct rendering, correct drivers. compiz"
date: 2007-12-09
forum: Desktop Effects &amp; Customization
---

### Post by peterj on 2007-12-09
Hi,

I'll keep this short and sweet. after a long battle with graphics in which I tried several how-to's, I had to re-install. 

Now I'm trying to figure out how to set myself up with one good set of instructions. I've done a lot of reading but I can't figure out which how-to would be appropriate for my situation.

I have a Radeon x1300. I want to enable advanced desktop effects and use dual monitors. 

My xorg.conf is currently:
```
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
	Option		"Device"		"/dev/gpmdata"
	Option		"Protocol"		"IntelliMouse"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-90
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```

So do I use the ATI drivers through displayconfig-gtk,  do I get them direct from AVI? Do I stick with the open source ones? 

Then could someone please renew my faith in these forums and point me in the direction of a good straight forward how-to, suitable for my set-up?

I mean theres the 'big desktop', 'merged buffer' etc. But I know the x1300 is reknowned for problems and I can't find info on which to use for that particular card. 

I self-destructed my system over the past 48 hours as a result of my thread being completely ignored, Please don't make me do that again!

---

### Post by bro on 2007-12-10
Hi, 
if I understand well that you have an ati graphics card, I doubt if you will ever have dual monitor support. surely you don't have it now, so don't bother. 
Desktop effects work ugly and slowly with the latest ati driver that is supposed to support it fully. Therefore use the default proprietary driver that comes with Ubuntu (gutsy, feisty, edgy...) and install xgl. There are many good guides how to do this. In gutsy just installing xgl was enough for me.

---

### Post by Ub1476 on 2007-12-10
You wont have much luck with the current AIGXL drivers from ATI. I guess that maybe in Ubuntu's next release (April), it will work fine though. I think ATI just released their first drivers in October or something similar..

---

