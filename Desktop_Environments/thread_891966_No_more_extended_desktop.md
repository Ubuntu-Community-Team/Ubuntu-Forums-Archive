---
title: "No more extended desktop"
date: 2008-08-16
forum: Desktop Environments
---

### Post by jis on 2008-08-16
By these commands I used to get extended desktop for Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03):

 xrandr --output VGA  --mode 1280x960
 xrandr --output LVDS --auto
 xrandr --output VGA --above LVDS

Now the last command tells:
xrandr: screen cannot be larger than 1280x1280 (desired size 1280x1760)

What's wrong? I am using Xubuntu 8.04.

---

### Post by jis on 2008-08-16
After log out and log in, I can get extended desktop. Previous session was started with no external monitor.

---

