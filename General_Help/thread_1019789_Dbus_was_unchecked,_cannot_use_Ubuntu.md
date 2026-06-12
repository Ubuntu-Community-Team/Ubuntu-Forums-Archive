---
title: "Dbus was unchecked, cannot use Ubuntu"
date: 2008-12-23
forum: General Help
---

### Post by gjbnh1701 on 2008-12-23
While trying to fix a persistent repeating keyboard problem, I came across a post someplace that mention 2 services that might be the problem. After unchecking the Dbus Service in the Service Settings Manager in Gnome, Ubuntu pretty much stopped working. If I boot via Failsafe more, I drop to a root terminal, restart both dbus and hal, I can get to the desktop via GDM, where the settings manager refuses to accept my root password to unlock the Services applet. I am at a lost on how to fix. What file must I edit to fix it so DBUS starts at startup again?? Thanks!

---

### Post by gjbnh1701 on 2008-12-23
Well after 8 hours I have solved this. Gnome Services Settings removes the symlink to s12dbus. The solution is to copy s12dbus from /etc/rec3.d to /etc/rc.2. Ubuntu nows boots properly. Dlus must run in order for hal to start properly. That said, the Services settings applet should disable, not delete a service.

---

