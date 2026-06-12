---
title: "xrandr - how to set default monitor?"
date: 2011-06-06
forum: Desktop Environments
---

### Post by Kalpinsh on 2011-06-06
I have a laptop and also an external monitor. The external monitor phisically is to the right of my laptop on my desk. I would like the external monitor to be the default monitor. Grandr and arandr (xrandr with GUI) does not help.

VGA1 - external monitor, LVDS1 - laptop monitor. 
xrandr --output VGA1 --mode 1280x1024 --pos 1280x0
xrandr --output LVDS1 --mode 1280x1024  --pos 0x0

These commands set my external monitor to right for 1280 pixels. I assume that the monitor that is positioned at 0x0 is the main monitor. How to set VGA1 the default or how to position LVDS1 to the left for MINUS 1280 pxs?

Please help!

---

### Post by FormatSeize on 2011-06-06
> **Kalpinsh said:**
> I have a laptop and also an external monitor. The external monitor phisically is to the right of my laptop on my desk. I would like the external monitor to be the default monitor.
I'm unsure how much technology has come along since the beginning of 2010, but it is likely that you are trying to do an impossible task. Laptops, at least from what I had been told, won't let you default to a different monitor outside of it's own monitor that's already attached to it, and will simply override any attemp at doing so. 
 
This could for no other reason that That's The Way It Is, or it could be some sort of fool-proofing, in that someone can't change the default monitor one day, forget, and grab the laptop and go somewhere only to realize (when it's far to late) that the default monitor is at home.

---

### Post by Toz on 2011-06-06
> **Kalpinsh said:**
> I have a laptop and also an external monitor. The external monitor phisically is to the right of my laptop on my desk. I would like the external monitor to be the default monitor. Grandr and arandr (xrandr with GUI) does not help.

VGA1 - external monitor, LVDS1 - laptop monitor. 
xrandr --output VGA1 --mode 1280x1024 --pos 1280x0
xrandr --output LVDS1 --mode 1280x1024  --pos 0x0

These commands set my external monitor to right for 1280 pixels. I assume that the monitor that is positioned at 0x0 is the main monitor. How to set VGA1 the default or how to position LVDS1 to the left for MINUS 1280 pxs?

Please help!

According to: [https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution") you can place the monitor to the left of the laptop using the > --left-of parameter. Or you can use the > --primary parameter to identify the primary monitor.

---

### Post by Kalpinsh on 2011-06-07
> **FormatSeize said:**
> I'm unsure how much technology has come along since the beginning of 2010, but it is likely that you are trying to do an impossible task. Laptops, at least from what I had been told, won't let you default to a different monitor outside of it's own monitor that's already attached to it, and will simply override any attemp at doing so. 
 
This could for no other reason that That's The Way It Is, or it could be some sort of fool-proofing, in that someone can't change the default monitor one day, forget, and grab the laptop and go somewhere only to realize (when it's far to late) that the default monitor is at home.

No it is possible to set the external monitor as the default. The default monitor will be the one which is positioned at 0x0. The problem is that I can not position laptop monitor to the left - do not know how to "--pos minus1280x0) - only to the right but phisically the external monitor is to the right on my desk.

> **Toz said:**
> According to: [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) you can place the monitor to the left of the laptop using the  parameter. Or you can use the  parameter to identify the primary monitor.

Thanks but these will not work for me.

Any other ideas?

---

### Post by Toz on 2011-06-07
Does:```
xrandr --output VGA1 --primary
```not make VGA1 primary and set at 0x0?

Or: ```
xrandr --output VGA1 --left-of LVDS1
```not do the same?

What happens when you issue those commands?

---

### Post by Kalpinsh on 2011-06-08
> **Toz said:**
> ```
xrandr --output VGA1 --primary
```
This command does nothing.
> **Toz said:**
> 
```
xrandr --output VGA1 --left-of LVDS1
```
This does set the external monitor as the default BUT it is like i would position LVDS1(laptop monitor) for 1280px (one full screen length unit) to the right. Logically the external(VGA1) monitor is to left BUT phisically it on the right side of my desktop. In order to move my cursor from VGA1 (on my desk to the right) I need to move it to the right side and it will show up in my laptop monitor from the left side. Wrong order - I hope you understand me.

There was one time when I somehow managed to fool the xrandr by using both grandr and arandr apps (xrandr with GUI) to reach my goal. But at the next reboot it somehow switched back. I did not save that config. I have not managed to repeated that but if I could then I would save that config and apply it at every reboot.

Maybe it is just a syntax problem - how to tell to xrandr "--pos -1280x0" the minus sign.

---

### Post by Toz on 2011-06-08
Ok. Lets see if I'm understanding this. What about:

1. Set VGA1 as primary:
```
xrandr --output VGA1 --primary
```
2. Place it to the right of LVDS1
```
xrandr --output VGA1 --right-of LVDS1
```

Therefore, as primary it should be 0x0. If you move cursor off right of VGA1 it should show up on left side of LVDS1 (which is physically at the right of VGA1).

---

### Post by Kalpinsh on 2011-06-09
> **Toz said:**
> Ok. Lets see if I'm understanding this. What about:

1. Set VGA1 as primary:
```
xrandr --output VGA1 --primary
```2. Place it to the right of LVDS1
```
xrandr --output VGA1 --right-of LVDS1
```Therefore, as primary it should be 0x0. If you move cursor off right of VGA1 it should show up on left side of LVDS1 (which is physically at the right of VGA1).

Thanks but I already tried these. Currently I have laptop monitor (to the left on the desk) as the default and the external monitor extends my desktop. After these commands nothing changes.

---

