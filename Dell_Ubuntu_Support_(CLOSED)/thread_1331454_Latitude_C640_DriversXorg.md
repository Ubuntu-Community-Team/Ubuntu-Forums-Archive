---
title: "Latitude C640 Drivers/Xorg"
date: 2009-11-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jakj on 2009-11-19
I cannot get this machine to successfully load Xorg except in the Safe video mode I used in the installer. I have tried many solutions I found on the Internet to get drivers working, but any time I modify my xorg.conf to use the "radeon" driver, all I get is a black desktop with two white bars on top/bottom from when it starts to draw the trays and gets stuck, or it just stops on the burgundy-ish Ubuntu loading screen and won't do anything. I have to hard-reset the machine to get into recovery mode and restore the original xorg.conf. Same thing happens if I remove my xorg.conf entirely and let it autoconfigure.

This is the only way I can get X to start. I have copied xorg.conf files from other threads on the Ubuntu Forums and elsewhere on the Internet, but they don't work on mine.

$ cat /etc/X11/xorg.conf
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

---

