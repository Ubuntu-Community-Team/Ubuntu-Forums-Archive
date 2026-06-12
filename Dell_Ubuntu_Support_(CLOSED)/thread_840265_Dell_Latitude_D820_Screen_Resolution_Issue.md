---
title: "Dell Latitude D820 Screen Resolution Issue"
date: 2008-06-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by aldavewebbs on 2008-06-25
Dear all,

I have been experiencing problems with my Dell Latitude's screen resolution on Ubuntu 8.04 after playing around with xrandr... 

Please can someone help as my screen resolution is stuck in 640x480 at the moment and it's driving me crazy not being able to sort it!

details of  sudo pico /etc/X11/xorg.conf below:

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "uk"
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
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Modes "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "1x1"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Synaptics Touchpad"
EndSection

xrandr -q:
Screen 0: minimum 800 x 600, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 

Help me! Doesn't look I have any drivers installed for card now...
Many Thanks.
ADW
ps. I am new to Ubuntu so please be fragile!

---

### Post by twbks on 2008-06-27
Try reconfiguring the xserver-xorg package by running ```
 sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by aldavewebbs on 2008-07-01
> **twbks said:**
> Try reconfiguring the xserver-xorg package by running ```
 sudo dpkg-reconfigure -phigh xserver-xorg
```

Receiving this message when I attempt the above: !?!

adw@adw-laptop:~$ sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080701131416

---

