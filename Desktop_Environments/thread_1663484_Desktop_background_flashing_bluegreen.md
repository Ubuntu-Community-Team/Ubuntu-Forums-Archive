---
title: "Desktop background flashing blue/green"
date: 2011-01-09
forum: Desktop Environments
---

### Post by jleaker on 2011-01-09
This is odd.  My wallpaper, regardless of what is chosen, flashes to blue/green (like an old Win95 desktop color) every 10-15 seconds.  It stays that way for a second, then goes back to what is set.  Also, it seems to 'fade in' to the blue/green, then fades back to the chosen wallpaper (albeit a very fast fade).  Icons on the desktop are unaffected.

I've tried disabling all desktop effects, and it still does it.  The only way to stop it is to reboot, which seems to fix the problem for 24 hours or so, then it starts again.

Does anyone have any idea what is causing this?  This is really annoying.

---

### Post by Krytarik on 2011-01-09
Try removing/renaming:
~/.gconf/desktop/gnome/background
~/.gnome2/backgrounds.xml

Though it doesn't make really sense, since the behaviour only starts after a while.
I haven't any other clue at the moment.

---

