---
title: "Multi Montior Interpid Ibex"
date: 2009-01-19
forum: General Help
---

### Post by Cpudan80 on 2009-01-19
Hello everyone:

I'm having trouble setting up dual monitors with Intrepid. Here's my setup:

Thinkpad T42 w/ ATI Mobility Radeon 7500 (yeah, it sucks)
Driver: "ati" as listed in xorg.conf
Laptop panel res: 1024x768 (max)

I have an external display connected (VGA, docked in docking station) that can support up to 1280x1024. I know the card is capable of doing dual-screen at different resolutions because it worked in Windows...

I'd like to have the 2nd monitor (to the left of the laptop) extend my desktop -- and have the 2nd monitor be at 1280x1024 res. 

Unfortunately, I don't know how to set it up -- so I was hoping someone would be able to walk me through it... I tried the screen resolution thing in gnome, but it didnt work right (it doesn't even list 1280x1024 for the external monitor...)

Thanks in advance!

Dan

---

### Post by blackened on 2009-01-19
Use xrandr instead.

[https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution")

---

### Post by Cpudan80 on 2009-01-20
Well -- unfortunately that didn't work.

When I try to set LVDS resolution to 1280x1024 with:

xrandr --addmode LVDS "1280x1024@60"

I get this error:

 X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  18 ()
  Serial number of failed request:  17
  Current serial number in output stream:  18

The modeline I added was:

modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync

Any ideas?

Dan

---

### Post by blackened on 2009-01-20
LVDS is your laptop display. I thought you were trying to change the resolution on your external monitor. If this is the case, then you should use:

```
xrandr --addmode VGA "1280x1024@60"
```

---

