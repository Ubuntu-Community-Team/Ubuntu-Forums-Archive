---
title: "first time ubuntu user [help with monitor drivers]"
date: 2007-12-23
forum: Desktop Environments
---

### Post by CodingNinja on 2007-12-23
hi

this is my first time playing around with ubuntu.  I have a 22inch Hanns-G monitor model # HG216D.  I am unable to get any resolution higher than 1024 X 768 so everything looks sooo bad!!

I've tried a couple of things said in this forum but to no avail.  

My graphics card is 128MB nVidia GeForce 8300 GS  

and following is my X11.org file

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
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
	Driver		"nv"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-80
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

Please, I'd appreciate any help

---

### Post by ijason on 2007-12-23
i would recommend, first making a backup copy of your /etc/X11/**xorg.conf**, and then in the section where you have the resolutions defined, :

> SubSection "Display"
Depth 1
Modes "1600x1200" "1024x768" "800x600" "640x480"
EndSubSection

try adding one without the Depth variable. i've never seen a Depth option, although, i'm mostly familiar with laptop displays. but it might be a solution, try adding this :

> SubSection "Display"
Modes "1600x1200" "1024x768" "800x600" "640x480"
EndSubSection

then restart the windows manager.

---

### Post by ijason on 2007-12-23
also, it doesn't look like you've added drivers for your video card. have you checked to see if things perform better using the 'restricted drivers'? 

luckily, nVidia cards are much better supported than ATi cards, so you should be able to find a good how-to on the forum for updating the drivers for your video card if the restricted drivers don't solve the problem.

---

### Post by CodingNinja on 2007-12-23
i went to system-administration-restricted driver manager and it says your hardware does not need any restricted drivers.  So i assumed that drivers for my video card are already there.  

How can i find out if i have drivers for my video card or not?

I'll look for a how-to on updating the drivers but if you come across something usefull..please post it. 

Also I've just removed the depth from the .conf file. Going to retsrt now...lets hope it works

---

### Post by forceofnature on 2007-12-23
I edited my xorg.conf after reading this just adding the 1280x1024 helped me.  Hope you get your video driver set up right.

---

### Post by RegularSlinky on 2008-01-12
Hello. I have the same monitor and managed to get it working under Ubuntu 7.10 using the default LCD 1680x1050 monitor settings. First of all you'll have to get your graphics drivers working, then you just select the default monitor from the list of ones there as there are no Hanns-G ones. You don't need to go into the system and edit any files anywhere. You may have to log out and log back in again to get it working.

This seems to work fine for me. You may still get poor quality looking text, but this is a rendering problem that can be fixed by changing the Appearance -> Fonts to sub-pixel rendering for LCD screens.

I'm viewing using a VGA cable and it's okay. It's clearer in Windows, which I think is something to do with fonts, not the monitor. It may be clearer with an HDMI cable (but my card doesn't support that).

Cheers. :)

---

