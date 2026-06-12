---
title: "Cant change screen resolution to 1280x720"
date: 2009-08-21
forum: Desktop Environments
---

### Post by crhatigan on 2009-08-21
Im trying to change my screen resolution on 9.04 from 1024x768 to 1280x720 but there isnt a higher resolution when i go to the display screen and i tried changing it through terminal using xrandr -s 1280x720 command and it says not available. Any solutions?

---

### Post by ajgreeny on 2009-08-21
You could try manually editing your xorg.conf file after backing it up, of course.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorgbak.conf
gksudo gedit /etc/X11/xorg.conf
```
Now add your own required resolution figures in this pattern, with the refresh rates as well, if you know them.
```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
            HorizSync    30-80
            VertRefresh    50-75
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    SubSection "Display"
        Modes        "1280x720"
    EndSubSection
EndSection
```This all assumes that your display screen and video card are capable of providing that resolution, of course.

---

