---
title: "Gnome +nvidia + LCD TV"
date: 2008-06-20
forum: Desktop Environments
---

### Post by etikette on 2008-06-20
Hello,

I bought a shiny new LCT TV today.
The TV also supports VGA Input (1680x1050@60Hz), so i connected my pc to the tv and booted into ubuntu.

At first everything seemed to work until gdm started. The tv went black and showed a "No Input Present" message.
I switched the display driver from "nvidia" to "nv" which fixed the issue with gdm and i was able to access the desktop from then on.

But even after hours of fiddling around i could not find a way to get the original nvidia driver to work.
The first problem was that i couldn't get the driver to display 1680x1050 at 60Hz (was always at 50Hz).

Adding **Option "DynamicTwinView" "False"** to xorg.conf fixed that problem but i still got a black screen.

I don't know what else to try to get the official nvidia driver to work, so I'll ask you guys for help or further ideas.
Any help would be appreciated.

System infos:
OS: Ubuntu 8.04
Graphics card: 7900 with latest nvidia driver
TV: LG 22LS4D 

xorg.conf
```

Section "InputDevice"
       Identifier      "Generic Keyboard"
       Driver          "kbd"
       Option          "XkbRules"      "xorg"
       Option          "XkbModel"      "pc105"
       Option          "XkbLayout"     "de"
EndSection

Section "InputDevice"
       Identifier      "Configured Mouse"
       Driver          "mouse"
       Option          "CorePointer"
EndSection

Section "Device"
       Identifier      "Configured Video Device"
       Boardname       "NVIDIA GeForce 7 Series"
       Busid           "PCI:5:0:0"
       Driver          "nvidia"
       Screen  0
       Option          "DynamicTwinView"       "False"
       Option          "NoLogo"        "True"
       Vendorname      "NVIDIA"
EndSection

Section "Monitor"
       Identifier      "Configured Monitor"
       Vendorname      "Generic LCD Display"
       Modelname       "LCD Panel 1680x1050"
       Horizsync       31      -       84
       Vertrefresh     57.0    -       75.0
       Option          "DPMS"
 modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828
-hsync +vsync
 modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054
1087 -hsync +vsync
       Gamma   1.0
EndSection

Section "Screen"
       Identifier      "Default Screen"
       Monitor         "Configured Monitor"
       Device          "Configured Video Device"
       Defaultdepth    24
       Option          "DynamicTwinView"       "False"
       SubSection "Display"
               Option          "DynamicTwinView"       "False"
               Depth   24
               Modes           "1680x1050@60"  "1600x1024@60"  "1440x900@60"   "1280x800@60"   "1280x720@60"   "1280x768@60"   "800x600@60"
       EndSubSection
EndSection

Section "ServerLayout"
       Identifier      "Default Layout"
 screen 0 "Default Screen" 0 0
EndSection
Section "Module"
       Load            "glx"
       Load            "v4l"
EndSection
Section "ServerFlags"
EndSection

```

---

### Post by mattchesters on 2008-07-28
I'm having the same issue with the same TV. Stuck at 800 x 600 at the moment.

---

### Post by mattchesters on 2008-07-28
This is depressing :( I've been working hours to try and find out why its not working any higher than 800x600. Used many different drivers for my nvidia FX 5200. Played about with xorg.conf more times than I can remember.

Does anyone have a solution? Can anyone spot an error in the xorg.conf? Please, any help much appreciated!

---

### Post by mattchesters on 2008-07-28
:guitar: Its working! After playing with the code from etikette, I managed to get my FX 5200 to work with the tv but only at 50hz, It may not be the full 60 but its nice to be out of 800x600, thank you!

Sorry for sort-of hijacking the thread etikette.

EDIT: My screen resolutions settings are saying its running at 60. etikette try changing all the resolution list to @50

---

