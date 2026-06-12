---
title: "Kubuntu Gutsy: what's wrong with my xorg.conf?"
date: 2007-11-10
forum: Desktop Environments
---

### Post by mibadt on 2007-11-10
Hi,
I'm on a dual boot PC (Gutsy/XP).  Whenever I boot into Kubuntu after working with XP, Kubuntu starts with a screen resolution too high.  Initially it began with  1856X 1392 (85 Hz). After I commented to virtual resolution in xorg.conf, it starts with  1400X 1050 (85 Hz).

I would like it to start always at 1024 X 768 (85 Hz).

How shall I modify my xorg.conf?

Thnaks

Michael Badt

----------my xorg.conf---------
Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbVariant"    "intl"
        Option          "XkbOptions"    "lv3:ralt_switch"
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
        Identifier      "nVidia Corporation NV44 [GeForce 6200 TurboCache(TM)]"
        Boardname       "NVIDIA GeForce 6 Series"
        Busid           "PCI:5:0:0"
        Driver          "nv"
        Screen  0
        Vendorname      "NVIDIA"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Vendorname      "MAG Technology Co., Ltd."
        Modelname       "MAG 786FD"

-------------

---

### Post by creeco on 2007-11-10
Just type in this command in any terminal, that usually works, if it doesnt post your new xorg.conf (after you typed the command below):
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` And reboot/restart your x server.

---

### Post by Henk Poley on 2007-11-10
Thanks for that fix, I had the same problem on my nVidia GeForce4 MX 420.

NB: I had to run restricted-manager-kde to get the propietary nvidia driver back in xorg.conf.

---

### Post by mibadt on 2007-11-10
Thanks,


I'll try this one!


Michael Badt

---

