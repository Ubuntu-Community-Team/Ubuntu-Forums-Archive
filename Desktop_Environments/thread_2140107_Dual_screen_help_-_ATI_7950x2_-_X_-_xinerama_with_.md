---
title: "Dual screen help - ATI 7950x2 - X - xinerama with OpenGL"
date: 2013-04-28
forum: Desktop Environments
---

### Post by 89serenity on 2013-04-28
Hey guys,


I am a long time Ubuntu user and today is the day I launch my first ticket! I have been struggling to get my setup to use dual monitors with OpenGL. The reason for posting in this thread is because I am having different issues with different desktops (Unity, Gnome3 and Plasma/KDE). 

** Setup **

My graphics hardware is 2x ATI 7950. I am using the latest ATI drivers (13.4) which were manually installed. I have 2x Asus 23" IPS monitors and each graphics card is using HDMI to connect to each screen. I am not using Crossfire on the graphics cards.

** Issues **

With KDE I am able to get full screen on both monitors and OpenGL compositing. However, I am not able to launch programs on screen 2, but I can interact with the desktop and add panels and so forth. If someone is able to tell me how to actually get say Konsole to run on screen 2 I will be happy with that. With xinerama I am able to get full screen on both monitors with all the joy that comes with xinerama such as moving between monitors. The issue is here that compositing is not available and I really do need it. 

I would be really happy if I ended up with 2 screens where I was not able to move programs between, but was able to launch applications on each independently, Preferably with Gnome 3 as it is the beans!

This is the first support ticket I have ever risen in all my years of computing, but I am just at a dead end on this one. I have attached my X config, please let me know what other logs/configs you require. 


Thanks in advance,

Chris

** xorg.conf (not using xinerama) **

Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Option "Xinerama" "off"
        Option "Clone" "off"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
        Screen         "aticonfig-Screen[1]-0" RightOf "aticonfig-Screen[0]-0"
EndSection


Section "Module"
EndSection


Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection


Section "Monitor"
        Identifier   "aticonfig-Monitor[1]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection


Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
EndSection


Section "Device"
        Identifier  "aticonfig-Device[1]-0"
        Driver      "fglrx"
        BusID       "PCI:2:0:0"
EndSection


Section "Screen"
        Identifier "aticonfig-Screen[0]-0"
        Device     "aticonfig-Device[0]-0"
        Monitor    "aticonfig-Monitor[0]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection


Section "Screen"
        Identifier "aticonfig-Screen[1]-0"
        Device     "aticonfig-Device[1]-0"
        Monitor    "aticonfig-Monitor[1]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

---

