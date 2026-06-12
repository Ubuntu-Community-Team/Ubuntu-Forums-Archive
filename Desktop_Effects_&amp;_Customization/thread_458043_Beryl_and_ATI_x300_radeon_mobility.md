---
title: "Beryl and ATI x300 radeon mobility????"
date: 2007-05-29
forum: Desktop Effects &amp; Customization
---

### Post by shawnthecableguy on 2007-05-29
Hi there,

I had Beryl up and running with out a hitch and upgraded to fiesty....now no eye candy is working :(

I have tried everything to get it running, format/reinstall from scratch...tried every guide on here.

can someone please point me in the right direction?


Thanks:D

---

### Post by shawnthecableguy on 2007-05-30
Ok, I got it working, tried to play a movie and it died :(

reformatting again, would greatly appreciate and how-to or guide to installing beryl or similar on fiesty......

or any other tips :)

---

### Post by ilektron on 2007-06-24
I'm in the same boat.  I can't seem to get feisty working with fglrx, xgl and beryl on either of my computers with beryl.  I've tried every how to i could find.

---

### Post by llamakc on 2007-06-24
I use an X300SE with the radeon driver and AIGLX with no problem.

---

### Post by teddmeister2 on 2007-06-24
I also have beryl working fine with an x300 mobility card + aiglx + open source drivers.
I'll post my xorg.conf if that helps.

```

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
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
	Load	"dbe" #added
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
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
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. M22 [Radeon Mobility M300]"
	Driver		"ati" #changed from "fglrx"  #changed from "ati"
	BusID		"PCI:1:0:0"
	Option "DRI" "true" 
	Option "ColorTiling" "on" 
	Option "RenderAccel" "true"
	Option "BusType" "PCIE" #added 2007-06-18
	Option "EnablePageFlip" "true"
	Option "AccelMethod" "XAA"  #changed from "EXA"
	Option "XAANoOffscreenPixmaps" #changed from EXANoOffScreenPixmaps
	Option "TripleBuffer" "true"	#added 2007-04-09
	Option "AccelDFS" "true"	#added 2007-04-09 #may be useless with accelmethod xaa
	Option "GARTSize" "64"
	Option "DynamicClocks" "on" 	#power saving option
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. M22 [Radeon Mobility M300]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
	Option	"AIGLX"	"true"  #added
EndSection

Section "DRI"
	Mode	0660 #changed from 0666
EndSection

# below I am disabling composite for 3d desktop

 Section "Extensions"
 Option "Composite" "Enable"
 EndSection

```

Make sure you delete your fglrx stuff before you try to do anything with the other driver as that will cause problems.
-Bryan

---

### Post by BluewookieJim on 2007-06-24
I've got Beryl running on my notebook right now, a dell i6000d with an ATI x300 radeon mobility. If there is anything specific you want to see from my config, just let me know.

---

### Post by faight on 2007-06-25
hi,  I cant get Beryl to work properly on my dell latitude D610
It runs, just doesnt do any effects at all

I copied your xorg.conf to mine and it just messed up my video
I DIDNT delete my fglrx file as you told me to cause people in #ubuntu told me not to.
So I guess that is next thing on the agenda... I just hate deleting stuff...  feels like a "bandaid".


Here is my xorg.conf file:







# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"ATI RADEON MOBILITY X300"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-89
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI RADEON MOBILITY X300"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1792x1344"	"1680x1050"	"1600x1200"	"1440x900"	"1400x1050"	"1280x1024"	"1280x960"	"1280x854"	"1280x800"	"1280x768"	"1200x800"	"1152x864"	"1152x768"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1792x1344"	"1680x1050"	"1600x1200"	"1440x900"	"1400x1050"	"1280x1024"	"1280x960"	"1280x854"	"1280x800"	"1280x768"	"1200x800"	"1152x864"	"1152x768"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1792x1344"	"1680x1050"	"1600x1200"	"1440x900"	"1400x1050"	"1280x1024"	"1280x960"	"1280x854"	"1280x800"	"1280x768"	"1200x800"	"1152x864"	"1152x768"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1792x1344"	"1680x1050"	"1600x1200"	"1440x900"	"1400x1050"	"1280x1024"	"1280x960"	"1280x854"	"1280x800"	"1280x768"	"1200x800"	"1152x864"	"1152x768"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1792x1344"	"1680x1050"	"1600x1200"	"1440x900"	"1400x1050"	"1280x1024"	"1280x960"	"1280x854"	"1280x800"	"1280x768"	"1200x800"	"1152x864"	"1152x768"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1792x1344"	"1680x1050"	"1600x1200"	"1440x900"	"1400x1050"	"1280x1024"	"1280x960"	"1280x854"	"1280x800"	"1280x768"	"1200x800"	"1152x864"	"1152x768"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection











Thanks alot

---

### Post by wormser on 2007-06-25
> **BluewookieJim said:**
> I've got Beryl running on my notebook right now, a dell i6000d with an ATI x300 radeon mobility. If there is anything specific you want to see from my config, just let me know.

I am having issues with the ATI Technologies Inc M22 [Radeon Mobility M300].

BluewookieJim, I have the same laptop.  Can you post or pm me your xorg.conf.

---

### Post by swisscow on 2007-06-25
I can get it running using either XGL or the AIGLX but GoogleEarth which I use a lot just doesn't work. Any ideas?

---

### Post by faight on 2007-06-25
I forgot to mention, this was the page I was going off of but it sure didnt work for me:
I dont know why

[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

---

### Post by swisscow on 2007-06-25
I have used this one and it worked for me - the only thing I can suggest is check, check and check again!

Sorry I can't be any more help.

---

### Post by faight on 2007-06-25
Actually I noticed that guy's code is wrong.

He uses: 

Section "Device"
        Identifier        "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
        Driver                "radeon"
        BusID                "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
        Option "AGPMode" "4"
        Option "AGPFastWrite" "true"
        Option "DisableGLXRootClipping" "true"
        Option "AddARGBGLXVisuals" "true"
        Option "AllowGLXWithComposite" "true"
        Option "EnablePageFlip" "true"
EndSection



When the whole web page is geared towards the Radeon X300!  Not the R250!

---

### Post by wormser on 2007-06-25
> **faight said:**
> I forgot to mention, this was the page I was going off of but it sure didnt work for me:
I dont know why

[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

That guide got it working for me.  It does have a problem, the windows blur and do not return to a normal state.  I have a [thread here]("http://ubuntuforums.org/showthread.php?t=484405").

---

### Post by faight on 2007-06-26
Thanks for the link, I'll have to check it out!
I got it to Not crash for once
I had to remove the AGP parts cause the  X300 is NOT an AGP!
Also I dont think it knows what "X300" is.  It knows M22 though

---

### Post by wormser on 2007-06-26
> **faight said:**
> Thanks for the link, I'll have to check it out!
I got it to Not crash for once
I had to remove the AGP parts cause the  X300 is NOT an AGP!
Also I dont think it knows what "X300" is.  It knows M22 though

The following command will show you the details of your video hardware.

```
lspci | grep ATI
```

Just run threw that [tutorial]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon").  It is working for me but I still have an issue with windows getting scrambled.

---

### Post by rjz35 on 2007-06-27
It worked for me, beryl + Aixgl+Ati M300, i'll post my xorg.conf.
if anybody has any info on how to enhance my xorg.conf please tell me.

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
	Load	"dbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
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
	Identifier	"Generic Video Card"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option 		"DRI" "true" 
	Option 		"ColorTiling" "on" 
	Option 		"RenderAccel" "true"
	Option 		"BusType" "PCIE" #added 2007-06-18
	Option 		"EnablePageFlip" "true"
	Option 		"AccelMethod" "XAA"  #changed from "EXA"
	Option 		"XAANoOffscreenPixmaps" #changed from EXANoOffScreenPixmaps
	Option 		"TripleBuffer" "true"	#added 2007-04-09
	Option 		"AccelDFS" "true"	#added 2007-04-09 #may be useless with accelmethod xaa
	Option 		"GARTSize" "64"
	Option 		"DynamicClocks" "on" 	#power saving option

EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
        Option          "AIGLX"         "true"
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

Section "Extensions"
        Option "Composite" "Enable"
EndSection

---

