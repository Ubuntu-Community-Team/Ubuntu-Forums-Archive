---
title: "kubuntu 10.10 dual monitor messes up desktop"
date: 2011-03-08
forum: Desktop Environments
---

### Post by josvanr on 2011-03-08
hi

I use 

xrandr --output LVDS1 --scale 1.2x1.2

to enlarge the 'resolution' of my laptop monitor. This works fine. 
Then, when I connect an external monitor, I use

xrandr --output VGA1 --auto --right-of LVDS1 

On ubuntu/gnome this worked fine. Now I switched to kubuntu 10.10
and kde4, and the 2 screens seem to be positioned and scaled
well, but the desktop is messed up. 

The panel and desktop are
 displayed on the  external monitor. The laptop screen shows part
of the desktop but is black mostly. Also I can't drag windows from the 
external monitor back to the laptop monitor. As mouse pointer   hits 
the edge of the external monitor (and desktop) while dragging 
the window, it stops there.  The mouse *can* be moved to the 
laptop screen (also on the black part) and also the part of the window
that is over the edge of the desktop is displayed in the black part of 
the laptop screen. But I can't handle the window (ie drag it furhter on
the laptop screen) when the mouse pointer is in the black part
of the laptop screen. 

It looks as if the kde4 desktop works on the external monitor. On the 
laptop it just displays the part that happens to overlap with the laptop
screen. But the desktop doesn't actually expand to the laptop screen, 
rendering it partly useless. I tried to fiddle with 
the 'monitor' settings but that doesn't help. 

Is kde4 able to handle this situation properly, or should I just forget
about it for now (and move back to gnome)

josvanr

---

### Post by josvanr on 2011-03-09
PS it seems to work normally if I don't initially scale the screen to 
a different size than standard. Apparently, the kde desktop doesn't 
scale up, at least when connecting the second monitor..

josvanr

---

