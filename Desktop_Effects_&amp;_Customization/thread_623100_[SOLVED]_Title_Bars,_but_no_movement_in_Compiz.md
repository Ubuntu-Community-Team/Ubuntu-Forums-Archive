---
title: "[SOLVED] Title Bars, but no movement in Compiz"
date: 2007-11-25
forum: Desktop Effects &amp; Customization
---

### Post by Aldanga on 2007-11-25
I just built a new PC a couple weeks ago. I installed Gutsy 64-Bit. (I have minimal knowledge of GNU/Linux. I've never really jumped into it; I've learned just enough to get me by.) After enabling Compiz, it worked great. Then I lost my title bars, but I got them back; but then I couldn't move the windows. I had enough problems with my install at the time so I reinstalled Ubuntu. Now I'm having the same issues.

I now have to use Metacity whenever I desire to move windows because Compiz won't let me. I do have Emerald installed. I've gone through most every thread I can find on the topic but can't find a solution, or anyone with my problem, for that matter.

I have an IGP. ATI Radeon Xpress 1250/690G.

Here's my Xorg.conf after I edited it [in bold] according to the compiz website instructions for ATI cards:

> # xorg.conf (xorg X Window System server configuration file)
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
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:5:0"
 [B]       Option		"DRI"			"true"
        Option		"ColorTiling"		"on"
        Option		"EnablePageFlip"	"true"
        Option		"AccelMethod" 		"EXA"
        Option		"XAANoOffscreenPixmaps"
        Option		"RenderAccel"		"true"
        Option 		"AGPMode" 		"x"
        Option		"AGPFastWrite"		"on"[/B]
EndSection

Section "Monitor"
	Identifier	"CMC 22 W"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"CMC 22 W"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1680x1680"	"1680x1050"	"1440x1440"	"1360x850"	"1280x1024"	"1280x960"	"1280x800"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
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
Section "Extensions"
	Option		"Composite"	"0"
EndSection

Any help is much appreciated.

---

### Post by Forlong on 2007-11-25
```
sudo apt-get install compizconfig-settings-manager
```
Go to *System &#8594; Preferences &#8594; Advanced Desktop Effects Settings* and make sure the **Move Window** plugin is enabled.

---

### Post by Aldanga on 2007-11-25
Holy cow. That's embarrassing. :oops:

Thank you. :)

---

### Post by Forlong on 2007-11-25
Not embarrassing at all. I dedicated an entry for this in the troubleshooting section of my how-to, because it's not too uncommon that people ask this.
And I have to acknowledge it's pretty confusing that there's actually a plugin for this.

---

