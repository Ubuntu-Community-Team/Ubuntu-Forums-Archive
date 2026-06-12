---
title: "NetworkManager from CVS"
date: 2005-10-19
forum: Desktop Environments
---

### Post by el toro on 2005-10-19
Hi all
NetworkManager from cvs compiles and installs fine but refuses to run nm-applet because of security policies regarding dbus.  I have tried uninstalling, reinstalling, forcing dbus to re-read its policies by running /etc/init.d/dbus restart and alternately by killing dbus, but it still gives me the same message.  From what I've gathered, it appears to possibly be a problem w/ redhat's at_console code, but I'm not sure about that.  So, in short, does anyone have NetworkManager from CVS (or even 0.5.0 from source) running on Breezy, and if so, how did you achieve this incredible feat?

---

### Post by el toro on 2005-10-21
sigh...(bumps)

---

### Post by bugmenot on 2005-10-22
[http://bootlab.org/~j/NetworkManager-breezy/](http://bootlab.org/~j/NetworkManager-breezy/)

Didn't test myself yet. But 0.4.1 used to work flawlessly.

---

### Post by el toro on 2005-10-22
Thx--j has packages for 0.5.1 up already and they're working great.

---

