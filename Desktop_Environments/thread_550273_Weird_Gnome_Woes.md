---
title: "Weird Gnome Woes"
date: 2007-09-13
forum: Desktop Environments
---

### Post by greviant on 2007-09-13
X locked up on me, so I killed it with a Ctrl+Alt+Backspace.  GDM loaded fine, and I logged in.  Everything looked like it was going alright, except I had a window with the message:

"Your session only lasted less than 10 seconds.  If yu have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace.  Try loggin in with one of the failsafe sessions to see if you can fix this problem."

If I close this window, or click "OK" my session ends.

I am not out of disk space.  Almost everything works, minus things that attempt to talk to the session manager, for instance, if I try to run gnome-session-properties I get this error:

"(gnome-session-properties:7904): GnomeUI-WARNING **: While connecting to session manager:
Could not open network socket.
could not connect to the session manager"

I have no idea what could have caused this to happen suddenly.

---

### Post by dabeej on 2007-09-13
Something similar happened to me. I left and came back and my screen was garbled. Killed X the same way. Network issues. Rebooted. Everything works fine. Weird.

---

### Post by greviant on 2007-09-13
Rebooting did nothing to fix the issue

---

