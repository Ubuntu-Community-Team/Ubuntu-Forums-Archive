---
title: "[SOLVED] Old Nvidia+Compiz=bust"
date: 2008-03-04
forum: Desktop Effects &amp; Customization
---

### Post by saxuntu on 2008-03-04
I have an old Geforce 2 MX 200 card. I did a fresh reinstall of gutsy to find compiz on by default. However the tops of the windows were cutoff (the bar with the min,max, and close buttons) and i couldn't drag the windows. Any ideas? I turned off desktop affects and everything is fine. I reinstalled comp-fus and still no luck. My wife's laptop runs it fine and i really like the eye candy.

---

### Post by overdrank on 2008-03-04
> **saxuntu said:**
> I have an old Geforce 2 MX 200 card. I did a fresh reinstall of gutsy to find compiz on by default. However the tops of the windows were cutoff (the bar with the min,max, and close buttons) and i couldn't drag the windows. Any ideas? I turned off desktop affects and everything is fine. I reinstalled comp-fus and still no luck. My wife's laptop runs it fine and i really like the eye candy.

Hi and you may try this command ```
sudo nvidia-xconfig --allow-glx-with-composite
```
If this does not correct the issue then post back with your contents of the xorg

---

### Post by saxuntu on 2008-03-06
It's 12:11 am and i'm on the laptop. I'll try it out tomorrow, well, this evening. Thanks for the help.

---

### Post by saxuntu on 2008-03-06
tried. gnome had problems booting. rebooted and still busted.
> Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen      0  "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "DELL P780"
    VendorName     "Dell"
    ModelName      "Dell P780"
    HorizSync       30.0 - 85.0
    VertRefresh     48.0 - 120.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
    ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
    ModeLine       "640x480@85" 36.0 640 696 752 832 480 481 484 509 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
    ModeLine       "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
    ModeLine       "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
    ModeLine       "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync +vsync interlace
    ModeLine       "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
    ModeLine       "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@75" 129.9 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
    ModeLine       "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
    ModeLine       "1400x1050@75" 155.8 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
    ModeLine       "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
EndSection

Section "Monitor"
 #      
    Identifier     "monitor1"
    VendorName     "Plug 'n' Play"
    ModelName      "Plug 'n' Play"
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV11DDR [GeForce2 MX200]"
    Driver         "nvidia"
    BoardName      "nv"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
 #      
    Identifier     "device1"
    Driver         "nvidia"
    BoardName      "nv"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV11DDR [GeForce2 MX200]"
    Monitor        "DELL P780"
    DefaultDepth    24
    Option         "AllowGLXWithComposite" "True"
    SubSection     "Display"
        Virtual     1792 1344
        Depth       24
        Modes      "1024x768@75" "1024x768@70" "1024x768@85" "1024x768@60" "832x624@75" "1024x768@43" "800x600@60" "1152x864@75" "800x600@85" "1280x1024@75" "800x600@75" "1280x960@60" "800x600@72" "1280x1024@60" "800x600@56" "1280x960@75" "640x480@85" "1400x1050@60" "640x480@75" "1400x1050@75" "640x480@72" "1600x1200@65" "640x480@60" "1600x1200@60" "1792x1344@60"
    EndSubSection
EndSection

Section "Screen"
 #      
    Identifier     "screen1"
    Device         "device1"
    Monitor        "monitor1"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "640x480@60"
    EndSubSection
EndSection

This is xorg.conf there was also .1, .2, .3, .4

---

### Post by overdrank on 2008-03-06
> **saxuntu said:**
> tried. gnome had problems booting. rebooted and still busted.

This is xorg.conf there was also .1, .2, .3, .4

HI and you can try to add 
Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"
To you device section in the xorg, example below

```
Section "Device"
Identifier "nVidia Corporation NV11DDR [GeForce2 MX200]"
Driver "nvidia"
BoardName "nv"
BusID "PCI:1:0:0"
Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"
Screen 0
EndSection
```
But first backup your xorg with this 
To copy Xorg
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```
To restore backup
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
You can edit the xorg with this command ```
gksudo gedit /etc/X11/xorg.conf
``` Then save the file and restart x with the ctrl, alt, backspace keys or restart the system.

---

### Post by saxuntu on 2008-03-07
If we were in the same room I could kiss you. The options on the xorg.conf worked. Thanks.

---

### Post by overdrank on 2008-03-07
> **saxuntu said:**
> If we were in the same room I could kiss you. The options on the xorg.conf worked. Thanks.

:shock::oops: a simple thanks will do lol:)

---

