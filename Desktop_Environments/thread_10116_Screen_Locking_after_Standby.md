---
title: "Screen Locking after Standby"
date: 2005-01-05
forum: Desktop Environments
---

### Post by alue on 2005-01-05
I have Warty installed on an IBM Thinkpad X22.  When I close the lid of the machine while the computer is on, the machine goes into standby, as it should.  When I open the lid again and allow the computer to wake up, however, I get a dialog box saying:

XScreenSaver 4.16
This display is locked.

And there are prompts for my username and password.

Basically, the display locks everytime the computer wakes from standby, and I don't want this to happen.  Computer > Desktop Preferences > Screensaver > Display Modes > Lock Screen After is unchecked.  How can I prevent the display from locking?

Alan

---

### Post by alue on 2005-01-05
Well there seems to be two issues:

(1) xscreensaver is locking the screen even though the control panel indicates that it won't; and

(2) xscreensaver is turns on when the computer comes back from standby.

The first issues appears to be a bug.  The second should be resolved from a power management control.  Does ubuntu have power management utilities?

Alan

---

