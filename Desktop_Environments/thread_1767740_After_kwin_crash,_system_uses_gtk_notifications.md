---
title: "After kwin crash, system uses gtk notifications"
date: 2011-05-26
forum: Desktop Environments
---

### Post by a person on 2011-05-26
Occasionally, kwin will crash and recover itself, but afterwards, my system starts using GTK notifications (yellow popup bubbles with the pie graph countdown timer).  I've tried restarting knotify4 to no avail.

Anyone have an idea about this?

kde  4.6.2 on kubuntu 11.04

---

### Post by Zorael on 2011-05-30
Do you have **notification-daemon** or similar running at that point? Try killing it and see if knotify4 reasserts itself as the real provider of the org.freedesktop.Notifications dbus... address?

Else, try **[#kde on freenode](irc://irc.freenode.net/kde)**; they probably know the intricacies of the daemons at work.

---

### Post by a person on 2011-05-30
I've checked (and even restarted) kde's notification daemon, but I still get the gtk bubbles.  I've tried #kubuntu but there not really much help there.  I guess I can try #kde, but usually I get pointed back to #kubuntu.

---

