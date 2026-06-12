---
title: "[SOLVED] Missing windows border in Gutsy"
date: 2007-10-14
forum: Desktop Effects &amp; Customization
---

### Post by Flashgordon20 on 2007-10-14
Hello,
I am using the Gutsy RC1. Every time I enable visual effects in the appearance settings, the window borders disappear on all my open windows. Any suggestions for a fix? If it's relevant, my video card specs  are as follows:
> *-display:0
             description: VGA compatible controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 03
             size: 256MB
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             configuration: latency=0
             resources: iomemory:dff00000-dff7ffff ioport:eff8-efff iomemory:c0000000-cfffffff iomemory:dfec0000-dfefffff irq:16

I have had Beryl running in the past with no issues. Thanks for any help.

---

### Post by kshane on 2007-10-14
Have you tried changing the window borders settings to see if others may work?  I had a similar problem, but I never concentrated on fixing it as I have since gone back to feisty until ATI releases their new driver...

Kevin

---

### Post by FredB on 2007-10-14
Can you post your xorg.conf ?

Maybe a line to add in it to have borders displayed. Just guessing, of course.

---

### Post by Flashgordon20 on 2007-10-14
Yes, no matter which boirder I choose, I still have the same issue.

---

### Post by Flashgordon20 on 2007-10-14
> **FredB said:**
> Can you post your xorg.conf ?

Maybe a line to add in it to have borders displayed. Just guessing, of course.

How do I do this? Sorry, I'm new!

---

### Post by Flashgordon20 on 2007-10-14
> **FredB said:**
> Can you post your xorg.conf ?

Maybe a line to add in it to have borders displayed. Just guessing, of course.

Never mind. found it. What section wouldl I add line in and what would it say? 

 > 
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
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
        Load    "dbe"
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
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by rybu on 2007-10-14
I have a similar problem.  Borders appear fine on my 1st display, but not on the 2nd. 

I posted my question on the Compiz forum:

[http://forum.compiz-fusion.org/showthread.php?t=4741](http://forum.compiz-fusion.org/showthread.php?t=4741)

---

### Post by Flashgordon20 on 2007-10-14
Thank You. I will continue to watch your thread and post to it if I come up with anything. Someone else is having the same issue at this thread: [http://ubuntuforums.org/showthread.php?t=575882](http://ubuntuforums.org/showthread.php?t=575882). I am watching that one too. Hopefully one of us finds a solution.

---

### Post by Flashgordon20 on 2007-10-16
Solved by doing this [http://ubuntuforums.org/showpost.php?p=3540917&postcount=13](http://ubuntuforums.org/showpost.php?p=3540917&postcount=13)

---

