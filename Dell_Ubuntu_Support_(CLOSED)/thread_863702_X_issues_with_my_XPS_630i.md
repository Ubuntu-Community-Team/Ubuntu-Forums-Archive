---
title: "X issues with my XPS 630i"
date: 2008-07-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by refuseresisted on 2008-07-18
Hi, I just received an XPS 630i at work. It's got 2 8800GT video cards, and I am currently using two monitors (one plugged into each card). Obviously I am not using SLI.

So far everything has been running fine with the exception of two problems:

On the second display, if I click a window's title bar and drag it immediately, the pointer gets moved offscreen to the right. I can drag the pointer far to the left and the window frame will show back up, but if I don't, I have to page to another desktop and back in order to see the window I moved.

If I wait a couple seconds before dragging it, this does not happen. The primary display is fine.

My second problem is related to gnome-screensaver. Sometimes it seems to lock up and I have to change to another vty and restart gdm in order to regain access to the X server.

I am using fluxbox as my WM, so I can't say whether these problems occur in the default gnome WM.

Does anyone have any suggestions? I'll post the relevant bits of my xorg.conf below.

Thanks.

Section "Device"
        Identifier      "8800 GT 1"
        Driver          "nvidia"
        Option          "NoLogo"        "True"
        BusID           "PCI:1:0:0"
EndSection

Section "Device"
        Identifier      "8800 GT 2"
        Driver          "nvidia"
        Option          "NoLogo"        "True"
        BusID           "PCI:2:0:0"
EndSection

Section "Monitor"
        Identifier      "L226WTQ 1"
        Option          "DPMS"
        HorizSync       30-83
        VertRefresh     56-75
EndSection

Section "Monitor"
        Identifier      "L226WTQ 2"
        Option          "DPMS"
        HorizSync       30-83
        VertRefresh     56-75
EndSection

Section "Screen"
        Identifier      "left"
        Monitor         "L226WTQ 1"
        Device          "8800 GT 1"
        Defaultdepth    24
EndSection

Section "Screen"
        Identifier      "right"
        Monitor         "L226WTQ 2"
        Device          "8800 GT 2"
        Defaultdepth    24
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "left"
        Screen          "right" RightOf "left"
        Option          "Xinerama" "on"
EndSection

---

### Post by refuseresisted on 2008-07-21
Monday bump! Anyone have any suggestions? This is pretty annoying :(

---

