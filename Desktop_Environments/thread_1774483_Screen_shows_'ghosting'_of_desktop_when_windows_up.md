---
title: "Screen shows 'ghosting' of desktop when windows update"
date: 2011-06-03
forum: Desktop Environments
---

### Post by rickyrockrat on 2011-06-03
I've just discovered a workaround for a very disturbing issue where every time text scrolls in a terminal window or windows are switched, it looks like for just a few milliseconds, the whole desktop is displayed skewed off to the right on Lucid.  I've discovered a way for it to go away.

In my .Xautorun file (or just shortly after the desktop appears, in a terminal window, do this):
xrandr --output DVI1 --mode 1600x1200 -o normal
xrandr --output DVI1 --mode 1920x1200 -o normal

The first resolution is just one down from my max, and the last one is my maximum resolution.

As a side note: I've also seen a 'lockup' where Xorg goes to 100%, but most of the time I can still log in over ssh. Don't know if it's related.  I've tested this with both LXDE and XFCE4 on Lucid, so I don't believe it's a window manager issue.

Cheers!

---

