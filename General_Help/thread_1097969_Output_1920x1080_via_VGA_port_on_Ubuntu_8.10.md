---
title: "Output 1920x1080 via VGA port on Ubuntu 8.10"
date: 2009-03-16
forum: General Help
---

### Post by zuperzz on 2009-03-16
Hi,

I recently shifted over from Windows to Ubuntu and cannot believe how smoothly the transition occurred. The only problem I have facd using Ubuntu is that I am unable to connect my HP dv6833 laptop to my HDTV (Sony KDL-46W4100). 

Albeit my laptop is pretty crappy, before I switched over to linux, Windows Vista was able to recognize the HDTV as being a monitor of HD resolution (1920x1080) and would allow me to work with the TV as an awesome dual monitor! When I connect the TV to my laptop now (using the standard VGA cable) Ubuntu recognizes the TV as a monitor of resolution 1280x1024, which barely uses a third of my TV's screen space.

I would appreciate any help that could get this problem fixed and complete my transition to Ubuntu!

---

### Post by ThomasGHenry on 2009-06-09
bump

---

### Post by FloydPink on 2011-02-01
I have the same issue with my Vaio VGN-NR17G and Bravia KDL40EX500 LCD TV. Any solutions?

---

### Post by FloydPink on 2011-03-11
For someone who might have the same problem, here's how I resolved this issue: 
Manually added the full HD resolution (1920x1080) and then applied it onto the second monitor (which is the TV) using ```
xrandr
```. This page helped me do all this - [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

Here's the neat script that I am using right now to switch the display to TV:

```
#!/bin/bash
# This script switches the display to TV
xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr --addmode VGA-0 "1920x1080_60.00"
xrandr --output VGA-0 --mode "1920x1080_60.00"
xrandr --output LVDS --off
```

You should still go to the X/Config/Resolution page above to get the parameters in the script above.

Hope that would help someone...

---

