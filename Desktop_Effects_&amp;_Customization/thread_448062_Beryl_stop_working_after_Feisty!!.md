---
title: "Beryl stop working after Feisty!!"
date: 2007-05-18
forum: Desktop Effects &amp; Customization
---

### Post by abena on 2007-05-18
[I][FONT="Times New Roman"][COLOR="Purple"]Hi people, two days ago I decide to upgrade to Ubuntu Feisty, and after that, I've passed the whole two days trying to make beryl work, I've done everything, but nothing seems to work.


All what I get after doing Beryl on console is that all the borders disappear, and this is what I get:[/COLOR][/FONT][/I]

andrea@andrea-desktop:~$ beryl
************************************************** ************
* Beryl system compatiblity check *
************************************************** ************

Detected xserver : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension : passed (v0.3)
Checking for XDamage extension : passed
Checking for RandR extension : passed
Checking for XSync extension : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig : passed
Checking for GLX_EXT_texture_from_pixmap : passed
Checking for non power of two texture support : passed
Checking maximum texture size : passed (2048x204

Reloading options
libpng error: Read Error
Cancelado (core dumped)
andrea@andrea-desktop:~$



[COLOR="Purple"][I][FONT="Times New Roman"]I'm using a AtI Radeon X300 by the way!!!


Any Idea?!


Thanks!,[/FONT][/I][/COLOR]

---

### Post by dfreer on 2007-05-18
try this:
```
sudo apt-get install libpng12-0 libpng3
```
also, do you have direct rendering still enabled?
```
glxinfo | grep rendering
```
although I think ATI has another command that replaces glxinfo... not sure :(

---

### Post by abena on 2007-05-18
[I][COLOR="Red"][FONT="Times New Roman"]Hi dfreer, thanks for helping me!


Yes,  I do have direct rending, and about the libpng12-0 libpng3, should I add something to the sources.list, 'cause it says that can't find libpng3, and libpng12-0 is all ready installed.


Thanks again![/FONT][/COLOR][/I]

---

### Post by orb9220 on 2007-05-18
Same Problem with fix
[http://ubuntuforums.org/showthread.php?t=447317](http://ubuntuforums.org/showthread.php?t=447317)

---

### Post by dfreer on 2007-05-18
nah, i just threw the libpng3 in there for kicks, the main thing is that I saw that libpng error and wanted to make sure some version of libpng was installed.


try this out:
[http://forum.beryl-project.org/viewtopic.php?f=37&t=5675](http://forum.beryl-project.org/viewtopic.php?f=37&t=5675)
basically, go into beryl-manager, disable skydome, and reload window manager and window decorator in beryl-manager.

---

### Post by abena on 2007-05-18
[I][COLOR="Purple"][FONT="Times New Roman"]Thanks for your help orb9220, but i'm afraid it didn't work for me, i think this is possible because my video card is an ATI Raderon x300 and not an Envidia card... 

I really appreciate any other help!!![/FONT][/COLOR][/I]

---

### Post by dfreer on 2007-05-19
seems like orb9220's problem had a different error output then abena's. 

did you try the link I posted? removing any skydome images/caps images, or even disabling those options?

---

### Post by abena on 2007-05-19
*[COLOR="Red"][FONT="Times New Roman"]Yeah, I disable everything, and now this is what I get:[/FONT][/COLOR]*

```
andrea@andrea-desktop:~$ beryl-manager
andrea@andrea-desktop:~$ X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kwin: Fatal IO error: client killed
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```

:confused:

---

### Post by dfreer on 2007-05-19
Hmmm. after some googling, it sounds like ATI official drivers + AIGLX do not mix. are you using the official ATI drivers? (if you do not know just post your /etc/X11/xorg.conf file). You can supposedly use AIGLX with the open source ATI driver, but it isn't compatible with all ATI cards.
So if you are using the "fglrx" driver, use XGL or switch to the "Radeon" open-source driver.

EDIT: Also, after reading the thread title again, did beryl work BEFORE the upgrade to feisty?

---

### Post by abena on 2007-05-19
[COLOR="Red"]Yeap, it worked perfectly with the Ubuntu Edgy![/COLOR]


```
 
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "Files"
	
	# path to defoma fonts
	Fontpath	"/usr/share/X11/fonts/misc"
	Fontpath	"/usr/share/X11/fonts/cyrillic"
	Fontpath	"/usr/share/X11/fonts/100dpi/:unscaled"
	Fontpath	"/usr/share/X11/fonts/75dpi/:unscaled"
	Fontpath	"/usr/share/X11/fonts/Type1"
	Fontpath	"/usr/share/X11/fonts/100dpi"
	Fontpath	"/usr/share/X11/fonts/75dpi"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"type1"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"latam"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	
	# /dev/input/event
	# for USB
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/wacom"# Change to 
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	
	# /dev/input/event
	# for USB
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/wacom"# Change to 
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	
	# /dev/input/event
	# for USB
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/wacom"# Change to 
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Horizsync	28.0	-	57.0
	Vertrefresh	43.0	-	60.0
	Option		"DPMS"
EndSection

Section "Device"
	
	# AGREGADO POR MI
	#Option "AddARGBGLXVisuals" "True"
	#Option "RenderAccel" "True"
	#Option "AllowGLXWithComposite" "True"
	#Option "backingstore" "True"
	#Option "TripleBuffer" "True"
	#Option "DisableGLXRootClipping" "true"
	#Option "DamageEvents" "true"
	# FIN MIO
	Identifier	"ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)]"
	# yo
	Driver		"fglrx"
	Option		"UseFBDev"	"true"
	Option		"EnablePageFlip"
	Option		"ColorTiling"
	# fin
	
	#	Driver      "fglrx"
	#	Option	    "VideoOverlay" "on"
	#	Option	    "OpenGLOverlay" "off"
	Busid		"PCI:1:0:0"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"	"0x0"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"	"0x0"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"	"0x0"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"	"0x0"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"	"0x0"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"	"0x0"
	EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option		"Composite"	"0"
	Option		"Composite"	"0"
EndSection

Section "Extensions"
	Option		"Composite"	"0"
EndSection
```

---

