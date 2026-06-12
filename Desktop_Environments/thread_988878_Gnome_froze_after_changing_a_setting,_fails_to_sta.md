---
title: "Gnome froze after changing a setting, fails to start--how to fix from cmd line?"
date: 2008-11-21
forum: Desktop Environments
---

### Post by joe42 on 2008-11-21
I was idly playing around with some of the appearance settings in gnome--the window background color in the customize theme window, to be precise--and gnome stopped responding...  I logged out via ctrl-alt-del, logged back in, and gnome fails to start--I see the Ubuntu light tan colored background and some gray box in the upper left which appears to take text input according to the cursor... Useless information probably.

I can still log in with other window managers ("failsafe" gnome, alas, doesn't work), so is there a way I can revert gnome's settings when not in gnome?

The other option I can think of is creating a new user (I'm using one now, and gnome works fine) and moving all of my junk to the new user.  I'd rather fix the current account, though...

Thanks very much, in advance.

---

### Post by joe42 on 2008-11-21
I tried:
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
in my home directory, logged back in with gnome, and got no changes...

Any other ideas?

---

### Post by joe42 on 2008-11-21
I got impatient, so I'm just moving all of my old things to this new user account, then I'll delete the old one and rename this one to what the old one was.  Seems to be working so far.

Thanks, anyway.

---

