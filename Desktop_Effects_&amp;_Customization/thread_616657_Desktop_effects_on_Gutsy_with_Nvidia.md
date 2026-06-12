---
title: "Desktop effects on Gutsy with Nvidia"
date: 2007-11-18
forum: Desktop Effects &amp; Customization
---

### Post by ram zu on 2007-11-18
Hi guys, sorry if this question is on duplicate but I've found lot of infor but almost related to ATI graphics or intel mobo.

I have a nvidia 5900 and a asus mobo with a AMD 64 processor. Everything working right with no problem.

I've been watching some videos of the desktop effects on gutsy and tryed myself to install them.

The first thing was to activate desktop effects on the "Appearance Preferences" but there was an error "Composite extension is not available" when I tried to select "extra".
Made a search in "synaptic Package Manager" about compiz and install some packages and then I could select "extra", but there was no button to click to select settings or activate the effects. I then install the "compiz gnome manager" and I now have an option in the System\preferences\GL desktop (but I feel that is something wrong here because there are some options but can't find the "keys" to activate the cube or other effects.)

Can anyone tell me what have I done wrong (I know I did) and how can I solve this?

Thankyou guys
and fly safe.

---

### Post by gsiliceo on 2007-11-18
In terminal
glxgears
Can you see some colored gears moving?

---

### Post by Forlong on 2007-11-18
Go to *System &#8594; Administration &#8594; Restricted Drivers Manager* and see if there's a driver available for you, if so: enable it and restart X. Then try again.

---

### Post by ram zu on 2007-11-18
yep

3 RGB gears runing.

In terminal:

18892 frames in 5.0 seconds = 3778.382 FPS
20031 frames in 5.0 seconds = 4006.124 FPS
40028 frames in 5.0 seconds = 7976.322 FPS
34202 frames in 5.0 seconds = 6863.212 FPS
...
CTRL+C

This test was made in a VNC terminal window (the server to far).

I've made some effects to work "compiz gnome manager".
Wasn't suppose to have "compizconfig-settings-manager" installed???

Forlong - The nvidia driver is active and running well

---

### Post by gsiliceo on 2007-11-18
Could you please post the contents of the file /etc/X11/xorg.conf

---

### Post by ram zu on 2007-11-18
> Section "ServerLayout"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
        Identifier      "Default Layout"
  screen 0 "Default Screen" 0 0
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
        Load            "glx"
        Load            "v4l"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "pt"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "stylus"
        Driver          "wacom"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier      "eraser"
        Driver          "wacom"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier      "cursor"
        Driver          "wacom"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier      "T710BH"
        Vendorname      "Generic CRT Display"
        Modelname       "Monitor 1280x1024"
        Horizsync       31.5-81.0
        Vertrefresh     50-75
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
        Gamma   1.0
EndSection

Section "Device"
        Identifier      "nVidia Corporation NV35 [GeForce FX 5900XT]"
        Boardname       "nv"
        Busid           "PCI:1:0:0"
        Driver          "nvidia"
        Screen  0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV35 [GeForce FX 5900XT]"
        Monitor         "T710BH"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Virtual 1600    1200
                Modes           "1280x1024@60"  "1280x960@75"   "1280x960@60"  "1400x1050@60"   "1280x1024@75"  "1600x1200@65"  "1152x864@75"   "1600x1200@60" "1024x768@60"    "1024x768@70"   "1024x768@75"   "832x624@75"    "800x600@60"   "800x600@75"     "800x600@72"    "800x600@56"    "640x480@75"    "640x480@72"   "640x480@60"
        EndSubSection
EndSection

Section "Extensions"
        Option          "Composite"     "Disable"
EndSection

Section "device" #    
        Identifier      "device1"
        Boardname       "nv"
        Busid           "PCI:1:0:0"
        Driver          "nvidia"
        Screen  1
EndSection
Section "screen" #    
        Identifier      "screen1"
        Device          "device1"
        Defaultdepth    24
        Monitor         "monitor1"
        SubSection "Display"
                Depth   24
                Modes           "640x480@60"    "640x480@72"    "640x480@75"   "640x480@85"     "800x600@56"    "800x600@72"    "800x600@75"    "800x600@85"   "800x600@60"     "832x624@75"    "1024x768@85"   "1024x768@75"   "1024x768@70"  "1024x768@60"    "1024x768@43"   "1152x864@75"   "1280x960@60"   "1280x1024@60" "1400x1050@60"
        EndSubSection
EndSection
Section "monitor" #    
        Identifier      "monitor1"
        Vendorname      "Plug 'n' Play"
        Modelname       "Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
        Gamma   1.0
EndSection
Section "ServerFlags"
EndSection

I'm about to check the Forlong howto.

---

### Post by gsiliceo on 2007-11-18
Look at the file, there is a part that says

Section "Extensions"
Option "Composite" "Disable"
EndSection

Replace "Disable" for "Enable"
Restart ubuntu

---

### Post by ram zu on 2007-11-18
Solved.

My bad was not watching first this:
[URL="https://help.ubuntu.com/community/CompositeManager/CompizFusion"]
https://help.ubuntu.com/community/CompositeManager/CompizFusion[/URL]

Thankyou all for your time and sorry for be such a dumb ****.
:)

P.S.: The only thing that i'm missing is the "Alternatively, for Ubuntu: System -> Preferences -> CompizConfig Settings Manager".
But I will make a reboot and I'll see.

---

