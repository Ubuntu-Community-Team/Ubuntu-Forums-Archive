---
title: "Gutsy resolution stuck at lowest default"
date: 2008-03-30
forum: Desktop Environments
---

### Post by click170 on 2008-03-30
Does anybody have any insight into a resolution problem I'm encountering?

The resolution has been set to a comfortable level for some time now, and then last reboot it defaulted to 640x480 and I can't seem to change it.  The first thing I thought to check was that the other resolutions I had been using were still in the xorg.conf file, so I checked and they were.  

I've tried uninstalling the Nvidia restricted driver and reinstalling it, to no affect.  I've tried reconfiguring xorg by running `sudo dpkg-reconfigure xserver-xorg` but it seems I selected the wrong resolutions or something because when I restarted gdm my monitor wouldn't display anything because the resolution was out of range.  At this point I restored the old xorg.conf file which was giving me the default resolution of 640x480 and no more, something is better than nothing after all.

Below is my xorg.conf file, in case I missed something.  I'll post updates if anything changes.
Thanks for your help in advance.




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
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation C51 [GeForce 6150 LE]"
	Driver		"nvidia"
	Busid		"PCI:0:5:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"FPD2185W"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation C51 [GeForce 6150 LE]"
	Monitor		"FPD2185W"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1680x1680"	"1680x1050"	"1440x1440"	"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection

---

### Post by kbless7 on 2008-03-30
In the screen section delete all of the modes you don't want to use except for the one with the correct resolution

---

### Post by click170 on 2008-03-30
Just tried that.

I switched the Modes line to 
Modes     "1680x1050"

Then I logged out and logged back in, no affect.  I tried changing the resolution in the Screen Resolution tool but no luck, still stuck on 640x480.  At this point I tried rebooting the machine and repeating those steps, but no luck there either.

---

