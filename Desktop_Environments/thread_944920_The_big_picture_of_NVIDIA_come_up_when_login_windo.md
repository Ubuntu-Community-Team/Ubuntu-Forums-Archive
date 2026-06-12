---
title: "The big picture of NVIDIA come up when login window."
date: 2008-10-11
forum: Desktop Environments
---

### Post by zccpop on 2008-10-11
I am not sure the reason is that I installed NVIDIA X SERVER settings.

When I login window, The big static picture about  NVIDIA come up every time. 

HOWTO remove it? Thank you..

---

### Post by jpkotta on 2008-10-11
It just sits there for about 2 sec?  That's the splash screen, and you can get rid of it by editing /etc/X11/xorg.conf
> Section "Screen"
...
Option "nologo" "true"
...
EndSection


It won't go away?  Then the driver is broken.

---

### Post by zccpop on 2008-10-13
It said:

> Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     1440 900
        Depth       24
        Modes      "1440x900@60" "1280x800@60" "1280x720@60" "1280x768@60" "800x600@60" "800x600@56"
    EndSubSection
EndSection


What should I change?

---

### Post by jpkotta on 2008-10-14
> Section "Screen"
Identifier "Default Screen"
Device "Configured Video Device"
Monitor "Configured Monitor"
DefaultDepth 24
[COLOR="Red"]Option "NoLogo" "true"[/COLOR]
SubSection "Display"
Virtual 1440 900
Depth 24
Modes "1440x900@60" "1280x800@60" "1280x720@60" "1280x768@60" "800x600@60" "800x600@56"
EndSubSection
EndSection
.

---

