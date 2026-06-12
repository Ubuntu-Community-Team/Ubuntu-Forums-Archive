---
title: "Xfce window border problems after 10.04 to 12.04 upgrade"
date: 2013-03-03
forum: Desktop Environments
---

### Post by Overholt on 2013-03-03
I can't seem to find any reports exactly like this, so here goes.    After upgrading from xubuntu 10.04 to 12.04, window borders fail to appear in many (but not all) programs.  For example, when I launch a terminal, it goes fullscreen with no window border.  If I unselect view->"Show Window Borders", and then re-select it, they appear and I can resize the window.  xfwm4 is running.  clearing .caches does nothing.  xfwm4 --replace just returns everything to the original (broken) state, i.e. maximizes a terminal window and hides the border.  It happens even if I create a new user, so it seems not to be related to something lurking in my own config files.    Any ideas?

---

### Post by Frogs Hair on 2013-03-03
Hello and Welcome

You have a different version of XFCE in 12.04 and I was wondering if theme selection changed anything or if using F11 reverts the terminal window to normal size.

---

### Post by Toz on 2013-03-03
@Overholt, a couple of other things to consider:

1. Settings Manager -> Window Manager Tweaks -> Accessibility tab -> "Hide frame of windows when maximized" (this is the location of this option on 13.04 - may be in a different location in 12.04)

2. This bug report: [https://bugs.freedesktop.org/show_bug.cgi?id=54168]("https://bugs.freedesktop.org/show_bug.cgi?id=54168")

---

