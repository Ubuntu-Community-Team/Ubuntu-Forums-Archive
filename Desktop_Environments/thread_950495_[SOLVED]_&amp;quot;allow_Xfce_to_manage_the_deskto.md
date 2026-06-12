---
title: "[SOLVED] &amp;quot;allow Xfce to manage the desktop&amp;quot; becomes unchecked during startup"
date: 2008-10-17
forum: Desktop Environments
---

### Post by tgyorgyi on 2008-10-17
During startup, the Xfce destop appears for a second, then it changes to a Gnome desktop. If I go to Desktop management in Settings, "allow Xfce..." box is unchecked. Upon checking, the Xfce desktop returns, but when I restart the computer, the same things happens as before.

Any suggestions?

Thnx in advance.

---

### Post by psyBSD on 2008-10-17
nautilus (the gnome desktop-managing application) somehow got trapped in your session-file.

If you run nautilus --quit from a terminal, and then log-out and save your session. The gnome-desktop won't come back and kill the xfce desktop.

---

