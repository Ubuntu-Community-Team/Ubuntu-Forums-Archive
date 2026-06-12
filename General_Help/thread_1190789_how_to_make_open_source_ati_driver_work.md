---
title: "how to make open source ati driver work?"
date: 2009-06-18
forum: General Help
---

### Post by fraud on 2009-06-18
Hey,
I'm currently at a loss, 'cause I read so many things, and can't get quake to work under jaunty.
Issues:
-my card is unsupported by ati (radeon x550)
-the xserver-xorg-video-ati and xserver-xorg-video-radeon are installed from the package manager
-I've read so many thing as to how to configure the xorg.conf, but after installing these 2 packages above, my xorg.conf stayed in its same default form:
```
Section "Device"
    Identifier    "Configured Video Device"

EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```
Question: how can I make this open source driver work?
Thanks!

---

### Post by fabiosl on 2009-06-18
Backup your xorg.conf file...
In the field ¨device¨ you should add the following line:
Driver        ¨radeon¨ 
(or any other driver that you are trying to use).

---

