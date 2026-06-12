---
title: "External monitor temporarily blanks when launching application"
date: 2008-09-14
forum: Desktop Environments
---

### Post by austinak49 on 2008-09-14
I am currently running a dual monitor setup with my laptop which has an integrated intel 915. So far everything works great even compiz. The only problem I am having is when I launch any application (calc, firefox, etc) the external LCD goes blank while the application starts up and I have no idea why. The Green LED stays lit while going black and I don't get signal lost messages. The laptop LCD doesn't flicker or anything. I'm a bit stumped on this one. Here is my xorg.conf thanks for any help in advance.

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

Section "Device"
        Identifier      "Intel 945G "
        Driver          "intel"
        Option "monitor-LVDS" "monLVDS"
        Option "monitor-VGA" "monVGA"
EndSection

Section "Monitor"
        Identifier      "monLVDS"
        Option "PreferredMode"  "1024x768"
        Option "Position" "0 0"
EndSection

Section "Monitor"
        Identifier      "monVGA"
        Option "PreferredMode"  "1024x768"
        Option "LeftOf"  "monLVDS"
        Option "Position" "-1600 -300"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 945G Integrated Graphics Controller"
        Monitor         "monLVDS"
        DefaultDepth    24
        SubSection "Display"
          Depth 24
          Modes "1024x768"
          Virtual 2048 768
        EndSubSection
EndSection

---

