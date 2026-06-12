---
title: "Roaming Power button"
date: 2009-08-26
forum: Desktop Environments
---

### Post by namluc on 2009-08-26
This is one of my pet gnome peeves, but it hasn't happened for a couple of months so i had forgotten about it. But it came back again today.

The power button likes to wander. It's home is in the far top right corner, but it prefers the center of the gnome panel. How do i make it stay put. 

All applets are and always are locked in position, as is the power button applet, however once it has moved once, no mattr what i do it keeps moving  jntil it gets bored

---

### Post by Andreas1 on 2009-08-26
try the following:
open gconf-editor, go to panel/applets/fast_user_switch_screen0 and check:

-locked
-panel_right_stick
-position = 0

then run "pkill gnome-panel" to restart the panel
then it should be the first applet from the right

i always found it weird of the gnome panel that you cannot rearrange its applets properly without using gconf

---

