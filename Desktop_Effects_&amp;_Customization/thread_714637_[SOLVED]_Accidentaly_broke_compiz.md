---
title: "[SOLVED] Accidentaly broke compiz"
date: 2008-03-04
forum: Desktop Effects &amp; Customization
---

### Post by dynamethod on 2008-03-04
Well, i had compiz running fine boefre, but i decided to install ccsm, sorry i cant type much because its painfully slow atm, but my taskbars dont appear anymore, i dont have any visual effects at all anymore, and had to open up firefox with alt+f1 then type in firfox, please help!i cant access anything without alt+f1

heres my xorg settings, though i have not touched them at all, and everything use to be fine before i installed ccsm!

```
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
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc R420 JK [Radeon X800]"
        Driver          "fglrx"
        Busid           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc R420 JK [Radeon X800]"
        Monitor         "SyncMaster"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1280x1024"     "1280x960"      "1152x864"     "1024x768"       "832x624"       "800x600"       "720x400"       "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
EndSection
Section "Module"
        Load            "glx"
EndSection
Section "Extensions"
        Option          "Composite"     "1"
EndSection

```

---

### Post by dynamethod on 2008-03-04
Please someone out there help, cause there s absolutly nothing i can do with this os as it is now, theres absolutly nothing on the desktop dexcept for the wallpaper itself

---

### Post by dynamethod on 2008-03-04
i got it fixed, i had to run killall gnome-panel and then compiz --replace

---

