---
title: "[SOLVED] Desktop problems"
date: 2008-10-27
forum: Desktop Environments
---

### Post by Cammy on 2008-10-27
I just upgraded from 7.04 to 8.04 (actually, it was a fresh install, and then I copied my old /home folder over) and I've run into a bit of a problem.

I have two panels on the top edge of my screen.  One is for my launcher, clock, trashcan, shutdown button, and the one below that is for my taskbar and window switcher.

Ever since my upgrade, I've had two problems.  1) When I boot up, the two panels are switched, so the lower one is on top, and vice versa.   And 2) when I launch an app, the titlebar of the app pops up under my panels, so I can't get to the close/minimize buttons without moving it.

But that's now the least of my problems.

In an attempt to fix the above, I renamed my Desktop and .gnome directories, and rebooted, figuring they'd be recreated from scratch when the OS noticed them missing.

That didn't work.  Now my /home/user directory IS my desktop, and renaming everything back does nothing.

Does anyone know how to fix this?

---

### Post by hictio on 2008-10-27
That's weird, to say the least, specially if you did a fresh install???? What gives.
Ok, the one thing I can think of, is that you forgot to rename some of the (then) current Gnome directories on your install.

You should rename:

.gnome
.gnome2
.gconf
.gconfd
.metacity


try that.

---

### Post by Cammy on 2008-10-27
Ok, I figured that part out!

In the file ~/.config/user-dirs.dirs there is a setting called XDG_DESKTOP_DIR.

It was set to "$HOME/", so I changed it to "$HOME/Desktop" and that fixed that mess.

WHEW!

Now I just need to figure out why my apps keep popping up underneath my panels, and why my panels won't keep their positions.

---

