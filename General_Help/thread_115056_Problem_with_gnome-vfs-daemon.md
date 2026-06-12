---
title: "Problem with gnome-vfs-daemon"
date: 2006-01-09
forum: General Help
---

### Post by naaman on 2006-01-09
When a user logs into GNOME, the desktop fails to fully load and "freezes", showing only the top and bottom panels and a blank background.  The panels are also blank.

The main issue is that the user has a /usr/lib/gnome-vfs2/gnome-vfs-daemon process running which cannot be killed.  It laughs in the face of a -9 and keeps on running.

Is there a way to kill a /usr/lib/gnome-vfs2/gnome-vfs-daemon process whilst other users are still logged into their gnome-sessions.  Otherwise, I will reboot the server tonight, which doesn't make Ubuntu look good.

Cheers,
Naaman.

---

