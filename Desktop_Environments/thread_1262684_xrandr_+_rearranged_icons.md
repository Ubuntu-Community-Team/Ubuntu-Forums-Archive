---
title: "xrandr + rearranged icons"
date: 2009-09-10
forum: Desktop Environments
---

### Post by realn on 2009-09-10
Kubuntu 8.04 on laptop connected to an external monitor.
If I turn on the monitor, with this command

xrandr  --output VGA --auto

 the icons are rearranged on my desktop in a very ugly way ( I mean no logic whatsoever), even if I check the "lock in place" option.

The only configuration in which they are NOT rearranged is by setting  the VGA monitor as the the leftmost screen AND with the LCD on

xrandr --output LVDS --auto --right-of VGA

However, if I turn off the LCD

xrandr --output LVDS --off

the icons are scrambled again

My question is: WHY are the icons scrambled when either:

1) LCD display is off
or
2) VGA monitor is not the leftmost screen?

Please help me with this, I don't want the LCD on at all.
Thanks!

---

### Post by realn on 2009-09-10
It seems like I found something: I never tried to rearrange the icons on the VGA display. I did, and it seems that the settings for the icons are saved separately for the LCD and for the VGA. So, the result is:
when the VGA monitor is on (with either LCD ON or OFF) the icons are displayed accordingly to the "VGA settings".
When the VGA monitor is OFF, the icons are displayed with the "LCD settings".
Can anyone tell me where the icon settings are stored (so that I can copy the original LCD positions to the VGA settings, such that I won't have to move them by hand)

Thanks a bunch!

---

### Post by realn on 2009-09-10
/home/corneliu/.kde/share/apps/kdesktop/IconPositions

---

