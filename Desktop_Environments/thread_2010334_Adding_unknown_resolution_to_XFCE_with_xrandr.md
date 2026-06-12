---
title: "Adding unknown resolution to XFCE with xrandr?"
date: 2012-06-25
forum: Desktop Environments
---

### Post by notrobb on 2012-06-25
I have a monitor (Samsung T220) that doesn't provide a correct EDID, so Operating Systems are never able to detect or provide the proper resolution (1680x1050). 

In Ubuntu 10.04 with gnome, I generated the mode line with cvt and had a short script that ran 

```
xrandr --newmode "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
xrandr --addmode VGA-1 1680x1050_60.00
```

This would add the mode, and allow me to go into System Settings > Display and choose it. 

Now with Ubuntu Studio 12.04 with XFCE, the xrandr commands complete without error and the new mode shows up in System Settings > Display. 

However, when I choose it, it immediately pops up the "This is your new resoultion, accept/reject?" window, but the display doesn't actually change, still looks crappy like 1024x768 or something.

Is there a different/better way to add a resolution in 12.04/xfce?

---

### Post by PCNetSpec on 2012-06-25
Have you tried adding the new modeline in /etc/X11/xorg.conf ?

[https://wiki.ubuntu.com/X/Config/Resolution/#Setting_xrandr_changes_persistently](https://wiki.ubuntu.com/X/Config/Resolution/#Setting_xrandr_changes_persistently)
and
[https://wiki.archlinux.org/index.php/Xrandr](https://wiki.archlinux.org/index.php/Xrandr)

---

