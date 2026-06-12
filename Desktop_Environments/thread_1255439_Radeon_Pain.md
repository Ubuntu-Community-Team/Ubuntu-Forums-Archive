---
title: "Radeon Pain"
date: 2009-09-01
forum: Desktop Environments
---

### Post by Bobboau on 2009-09-01
ok, I have been fighting with this for two days straight so sorry if I'm a little incoherent.

I have an ATI radeon, made by visiontek

lspci -nn | grep VGA
retuns
03:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV 630 XT AGP [Radeon HD 2600 XT AGP] [1002:9586]


I can not get it to work properly in a clean kubuntu install.
useing anything but vesa results in a black screen on reboot. vesa sucks, so I've been trying to get the radeon driver to work.
when I try it though I get the afore mentioned black screen with a little bit of garbage at the top, I can ctrl-alt fn to a terminal, but if I try to get back to f7 it will lock up typicaly.

glxinfo |grep vendor
returns
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa Project

or it does right now, if I try to run that command line with the radeon drivers I get ''failed to open the display' or something to that effect.

my xorg.conf I most recently tried

```

Section "Device"
        Identifier      "RadeonX"
        Driver          "ati"
        BusID           "PCI:3:0:0"
        Option          "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-72
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "RadeonX"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1440x900" "1024x768"
        EndSubSection
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection

```

I would post the x log but it's for my current (vesa) session

my eyes feel like they are on fire, please help

---

### Post by Bobboau on 2009-09-01
ok, quick update, I removed the 1440 resolution and now it 'sorta' works, I get a desktop but it's still extreemly slow, and I can't get any special effects working

---

