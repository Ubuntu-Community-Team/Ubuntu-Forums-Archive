---
title: "Top Panel settings - how to restore"
date: 2010-08-04
forum: Desktop Environments
---

### Post by kennethadammiller on 2010-08-04
I recently installed ubuntu, and I found that there was something in the top panel that I wanted to remove. I went to right-click->remove and when I did it went away, but it also took two other things: the volume applet that lets me control the volume, and the networking thing that has both empathy and evolution in it.

How do I restore these?
I want the panel to go back to the way it was before this error: does anyone know of a script that can be used to restore what's in the top panel?

---

### Post by sisco311 on 2010-08-04
Right click on the panel -> Add to panel... -> Indicator Applet.

To restore both panels:
```
gconftool-2 --recursive-unset /apps/panel
```
You may have to restart the panels:
```
killall -9 gnome-panel
```

---

### Post by mcduck on 2010-08-04
Actually it was most likely the Indicator Applet that was removed, since both the volume control and the messaging menu are in that applet, not in the Notification Area.

---

