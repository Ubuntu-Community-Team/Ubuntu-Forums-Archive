---
title: "Wacom Intuos tablet and dualhead"
date: 2006-06-22
forum: Desktop Environments
---

### Post by igm on 2006-06-22
Hi there, 

I managed to install my ATI fglrx drivers with dualhead, as well as my Wacom Intuos tablet. 

Here's my problem: 

When I move my cursor around (with the pen), it jumps from one screen to the other when I horizontally cross the center of a screen. I can only access the outer halfs of each screen. Well, it's not exactly the center where the cursor jumps. I have one 1920x1200 and one 1600x1200 display. On the 1920er display, I can access slightly more than one half - it's slightly less on the other.

Is there a way to restrict the tablet to one screen?

Thanks,
Ingo



Here is my /etc/X11/xorg.conf:

```
 
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	Screen         "aticonfig-Screen[1]" RightOf "aticonfig-Screen[0]"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "de"
	Option	    "XkbVariant" "nodeadkeys"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mouse0" # was "/dev/input/mice", changed for wacom
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/event7"          # Change to 
	Option	    "Type" "stylus"
	#Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/event7"          # Change to 
	Option	    "Type" "eraser"
	#Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/event7"          # Change to 
	Option	    "Type" "cursor"
	#Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1920x1200"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1920x1200"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1920x1200"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1920x1200"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1920x1200"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1920x1200"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

```

---

### Post by AtZeuS on 2006-06-24
Hi,

I had the same problem, so i looked at the linux wacom project documetation at [http://linuxwacom.sourceforge.net/index.php/howto/inputdev](http://linuxwacom.sourceforge.net/index.php/howto/inputdev)

The dirt:

Option "ScreenNo" "n"
                   In a multi-monitor environment, specifies the screen number
                   in which the cursor can move.

Try adding that 
Option "ScreenNo" "0" to each wacom device in your xorg.conf. Works great here :)

Cheers!

---

### Post by igm on 2006-06-26
Ah, thanks. I missed that one, although ScreenNo 1 does not work, cannot use my tablet at all. With ScreenNo 0, I can use it on display 1. Strange.

Thanks again,
Ingo

---

