---
title: "No desktop after update"
date: 2012-06-11
forum: Desktop Environments
---

### Post by backwoodsman on 2012-06-11
This is a fresh install of Xubuntu 12.04.  Everything worked fine at first; problem started after I updated.  Now, the startup splash screen never goes away (the blue picture); the panel loads and works fine, but anything that appears on the screen where the desktop should be just stays there -- menu, windows, etc. -- after it's closed.  There are no desktop icons, and right-clicking on what should be the desktop does nothing.  If I logout and login, then all this is still the same except menu, windows, etc. go away when they're supposed to.  The system is perfectly functional except there's no desktop.

I reinstalled the display manager and everything with 'xorg' in the name, but I don't really have any idea what to try next.  Any help would be appreciated.

---

### Post by Toz on 2012-06-11
If xfdesktop is not running, try starting it up from Alt+F2 (or a terminal window) with:
```
xfdesktop
```

---

### Post by backwoodsman on 2012-06-12
Thanks for the reply, but... never mind.  User had a bunch of old config files in /home directory (on separate partition) from old installs.  Problem went away when I deleted all that stuff.  Seems odd that it worked before the update, though.

---

