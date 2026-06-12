---
title: "Transparent Upon Maximize"
date: 2008-01-05
forum: Desktop Effects &amp; Customization
---

### Post by acary on 2008-01-05
When I enable desktop effects in 7.10, I have this problem with some applications. Specifically, when I minimize windows and then maximize them, the borders for the window show up, but the body of the window is transparent (the desktop image displays). I have to hit F5 to make page reappear. Sometimes I just click a link and parts of the window go funky.

I am currently using the open driver. When I ran the restricted driver manager, it didn't work and botched my setup. When I used Envy, that permitted the upgrade, but (if memory serves; it's been a few weeks) I had new problems with the "Desktop effects could not be enabled" error messages.

I have an ATI Radeon X300 video (128 MB), 1GB RAM, 2.x GHz processor, so I should have plenty of power.

Any ideas?  Below is my xorg.conf file.  If any other files are needed, please ask.  Thanks.

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
EndSection

---

### Post by Hannibal-King on 2008-01-05
I had a problem similar to yours.. It was caused by one of the eye candy features in Compiz Fusion..
For me, it helped to disable Minimize Effect in Compiz Manager..

---

