---
title: "Can't login to gnome. (Failsafe works)"
date: 2010-03-09
forum: Desktop Environments
---

### Post by Bryan76 on 2010-03-09
Here's my xsessions-errors.  I'm at a loss. :-\

```
/etc/gdm/Xsession: Beginning session setup...
/etc/X11/Xsession.d/40guidance-displayconfig_restore: 11: /usr/bin/displayconfig-restore: not found
No protocol specified
xhost:  unable to open display ":0.0"
imwheel: no process found
No protocol specified
xmodmap:  unable to open display ':0.0'
/etc/X11/Xsession.d/63xmodmap: 4: -k: not found
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
No protocol specified
/usr/bin/xmodmap:  unable to open display ':0.0'
No protocol specified
No protocol specified
XOpenDisplay() failed
Failure: Module initalization failed
No protocol specified

** (gnome-session:4336): WARNING **: Cannot open display: 

```

Any ideas?  The GDM graphical login comes up okay.

---

