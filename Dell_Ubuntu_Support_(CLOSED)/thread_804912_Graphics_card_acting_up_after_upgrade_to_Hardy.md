---
title: "Graphics card acting up after upgrade to Hardy"
date: 2008-05-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by brettbed on 2008-05-23
I have a Dell Latitude D610 with an ATI Radeon Mobile X300 which ran great under Gutsy with Compiz.

Now that I upgraded to Hardy I can't use any special effects without the screen becoming all choppy and slow to respond.

Checkout the screenshot of me trying to scroll on ESPN. It does with simple text too.

I have tried getting the driver from the ATI Radeon site but that doesn't work either.

Do I have to edit my xorg.conf file?

WTF

---

### Post by brettbed on 2008-05-23
Here is my xorg.conf:

Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizEdgeScroll" "0"
	Option	    "SHMConfig" "true"
	Option	    "MinSpeed" "0.5"
	Option	    "MaxSpeed" "0.8"
	Option	    "AccelFactor" "0.042"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc M22 [Mobility Radeon X300]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc M22 [Mobility Radeon X300]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Modes    "1400x1050"
	EndSubSection
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection

---

### Post by TimGS on 2008-05-23
Look at 
[http://ubuntuforums.org/showthread.php?t=792988&highlight=hardy+ati](http://ubuntuforums.org/showthread.php?t=792988&highlight=hardy+ati)

---

