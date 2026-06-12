---
title: "2 monitors, different resolutions"
date: 2007-04-23
forum: Desktop Effects &amp; Customization
---

### Post by woland on 2007-04-23
I've stumbled upon several solutions for dual monitor setup. Suse Linux has a great GUI tool for easy managing the screen output setup, something that Ubuntu team *must* adopt.
However, I couldn't, both by wizards, GUI and hand modifications to make X to run dual monitors on different resolutions.

I've tried:
[LIST]
[*]Ubuntu Edgy on laptop with 1280x768 internal monitor and 1280x1024 external  LCD monitor.
[*]Suse with 1280x1024 LCD monitor and 1384x768 LCD TV
[/LIST]

Is there a way to make 2 monitors to run different resolutions on X, and if so How can I do it?

Is there a way to switch from single monitor to dual monitor setups in Ubuntu without restarting X?
Is there a GUI/shortcut, that can operated by a few clicks?

---

### Post by HaoTian on 2007-04-23
You'll need to let us know what kind of video card you're using.  I'm using an ATI Radeon x1600 and run two monitors of different resolution without difficulty on both Edgy and now Feisty.  (Laptop LCD at 1280x800 and LCD panel at 1280x1024). 

Here's the important sections from my xorg.conf file:

Section "Device"
	Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"

# --- The following was added for dual-head support:
	Option      "DesktopSetup" "horizontal"
	Option 	    "PairMode" "1280x800+1280x1024" # Pair mode resolutions
	Option	    "HSync2" "79"
	Option	    "VRefresh2" "75"
	Option 	    "DesktopSetup" "AUTO,AUTO"
EndSection

Section "Monitor"
	Identifier  "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display" 
		Modes	  "1280x800" "1280x1024"
                Viewport  0 0
                Depth     24
        EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice     "pad"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
    Option  "Composite" "Disable"  #make DRI work with fglrx.
EndSection

If you're using an ATI Card, make sure you have fglrx installed (check Synaptic Package Manager for files).

---

### Post by eponymous on 2007-04-23
my xorg file is gone because i'm on a new installation and haven't set up my dual display yet, but i can confirm that in feisty beta i had dual monitors running at 2 different resolutions.

i have an nVidia 8800 GTS, a 19" wide lcd at 1440x900 and a 19" CRT at 1280x1024. They have to be set up as two different X sessions 0 and 1. You can't do some things like drag a window from one to the other, but since they both have their own panels etc. this isn't really a big issue.

if you have nvidia their settings program pretty much handles this for you once your monitors are detected. just select seperate X sessions in the settings. sorry i can't be more specific.

---

### Post by Savage2007 on 2007-10-21
Fantastic! Thank you, thank you, thank you! I have tried about every way by googling solutions to this problem. I stumbled over yours today. I also have an X1600 mobile radeon card. 

This solution worked. Thanks again!

---

