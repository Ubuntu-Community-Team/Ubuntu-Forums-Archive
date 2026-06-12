---
title: "installing mplayer + not working PS2 HP owt button mouse"
date: 2006-01-21
forum: Desktop Environments
---

### Post by koert.gielen on 2006-01-21
Hello,

I installed Brezzy Badger yesterday.

I few things don't work yet:

Mplayer:

root@ypc:/etc/X11# sudo apt-get install mplayer-386
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mplayer-386
root@ypc:/etc/X11# sudo apt-get install mplayer-fonts
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mplayer-fonts
root@ypc:/etc/X11# apt-get install mozilla-mplayer
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mozilla-mplayer

Mouse:

It is a HP Omnibook Laptop (Pentium II). The touchpad works alright. My (modified) xorg.conf:


Section "ServerLayout"
        IdentiSection "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "mouse"
        Option      "Protocol" "IMPS/2"
        Option      "Device" "/dev/psaux"
        Option      "Zaxismapping" "4 5"
        Option      "Emulate3buttons" "true"
EndSection

Anyone a clue?

Kind Regards,

Koert Gielen

---

