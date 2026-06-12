---
title: "dbus-send: what's wrong with this?"
date: 2010-10-27
forum: Desktop Environments
---

### Post by gharris999 on 2010-10-27
Trying:

# dbus-send --print-reply --dest=org.gnome.SessionManager /org/gnome/SessionManager org.gnome.SessionManager.Inhibit string:'session-inhibitor' uint32:0 string:'not_idle' uint32:15


..seems to work, as the command returns what looks like a valid inhibitor cookie.  But:

# dbus-send --print-reply --dest=org.gnome.SessionManager /org/gnome/SessionManager org.gnome.SessionManager.IsInhibited uint32:-1

..always returns FALSE.  That command returns TRUE when the Power Manager Inhibit applet is in use or when I run the test-inhibit.c program compiled from the gnome session manager source code.

Anyone have any idea why my 1st dbus-send command isn't working?

---

### Post by gharris999 on 2010-11-15
The simple answer is: it is working.  But gnome session manager "retires" the inhibition  when it sees that the calling process (in this case, dbus-send) has exited.  So: it looks like it's impossible to "toggle" a system-wide power savings inhibition using dbus-send.  That's too bad.  It makes scripting control of power management that much harder.

---

