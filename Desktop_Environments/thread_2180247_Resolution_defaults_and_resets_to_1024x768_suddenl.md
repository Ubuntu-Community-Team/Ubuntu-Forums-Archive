---
title: "Resolution defaults and resets to 1024x768 suddenly after 1 month"
date: 2013-10-12
forum: Desktop Environments
---

### Post by skyemoor on 2013-10-12
Ubuntu Studio 13.04
XFCE 4.10
Dell Inspiron
Dual boot with Win 7 Pro
Asus 23" monitor
In dock, no laptop screen in use

I've been using my Ubuntu Studio 13.04 fine for a few months, when I decided to boot into Windows for a few things. When I booted back into Studio, the screen resolution is now 1024x768. When I go into the Settings Manager and change it to 1920x1080, nothing happens the first time. When I go to set it again, it briefly changes into 1920x1080 but then a few seconds later changes back again. Repeatedly. I've even gone into Settings Editor to change this, but it reverts backs everytime.

The Settings Editor shows a number of monitors under default;

LVDS-0 Laptop (active)
x position 1280
1600x900

LVDS-1 (active)
x position 0

VGA-0 Asus 23" (active)
x position 0
1024x768

VGA-1 HSD 19" (not active) [this was a prior monitor no longer in use or even hooked up]
1920x1080



What can I do?

---

### Post by skyemoor on 2013-11-19
Still having this issue, any help will be greatly appreciated

---

### Post by papibe on 2013-11-19
Hi skyemoor.

Could you post the content of this file?
```
/var/log/Xorg.0.log
```
Please paste it here [paste.ubuntu.com]("http://paste.ubuntu.com/"), and then post back the link.

Regards.

---

