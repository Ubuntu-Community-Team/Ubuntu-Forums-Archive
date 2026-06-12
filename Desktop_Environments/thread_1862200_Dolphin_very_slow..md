---
title: "Dolphin very slow."
date: 2011-10-16
forum: Desktop Environments
---

### Post by spazzm on 2011-10-16
**Problem:**
After upgrading to Oneiric I noticed that starting dolphin is very slow. From clicking the icon to the contents of my home directory is displayed takes over 70 seconds.

**Background:**
Upgraded from Natty over the network. The upgrade was interrupted during configuration, but recovered gracefully.

**Details:**
When starting dolphin from a console this message is displayed:
dolphin(5272)/kdecore (K*TimeZone*): KSystemTimeZones: ktimezoned initialize() D-Bus call failed:  "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

DBus is running as dbus-monitor shows lots of messages.

There is no extra disk activity or CPU load during while dolphin starts.



**Other symptoms:**
Right-clicking to bring up the context menu in dolphin is also very slow, about one minute.
KTorrent is also slow to start.
KTorrent does not move to system tray when closed.
[B]
Attempted resolutions:[/B]
Removed glib-networking. This had no effect.

Any suggestions?

---

### Post by spazzm on 2011-10-17
Tried a reinstall to no avail. Solution was to blow away the .kderc file and the .kde4 directory from my home directory.

Presumably they were left over from some ancient upgrade, causing problems. Now everything runs smoothly. :)

---

### Post by kellemes on 2011-10-18
> **spazzm said:**
> Tried a reinstall to no avail. Solution was to blow away the .kderc file and the .kde4 directory from my home directory.

Presumably they were left over from some ancient upgrade, causing problems. Now everything runs smoothly. :)

Thanks for the info.. Dolphin indeed tends to get slow over time.. now I know why. :popcorn:

---

