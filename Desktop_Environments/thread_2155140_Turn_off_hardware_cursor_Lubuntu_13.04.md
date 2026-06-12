---
title: "Turn off hardware cursor Lubuntu 13.04"
date: 2013-06-17
forum: Desktop Environments
---

### Post by user_of_gnomes on 2013-06-17
I'm trying to execute the following instructions to see if I can figure out why the mouse cursor is missing from my Lubuntu installation (With an Nvidia NV10 videocard)

```

Open a terminal and type:

sudo gedit /etc/X11/xorg.conf

Locate the Section "Device" section and add the following line:

Option "HWCursor" "off"

So it looks similar to the following (your Section "Device" section may vary)

    Section "Device"
    Identifier "nVidia Corporation C51PV [GeForce 6150]"
    Driver "nv"
    BusID "0:5:0"
    Option "HWCursor" "off"
    EndSection


```

but there does not seem to be a /etc/X11/xorg.conf

What do I do?

---

### Post by user_of_gnomes on 2013-06-17
The bug is reproducable with NV10, NV11 and NV17 AGP videocards. Mouse pointer appears with NV34 videocard.

---

