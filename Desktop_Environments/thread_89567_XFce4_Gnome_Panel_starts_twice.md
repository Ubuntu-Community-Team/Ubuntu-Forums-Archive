---
title: "XFce4: Gnome Panel starts twice"
date: 2005-11-12
forum: Desktop Environments
---

### Post by samwyse on 2005-11-12
I wanted to run gnome-panel in xfce4 so I killed xftaskbar4 and xfce-panel. Then launched gnome-panel and quit using "save session". Now when logging in I get two gnome-panels started, the second instance gives an error complaining of the other instance.

Any idea how to fix?

---

### Post by aysiu on 2005-11-12
Can we assume you've tried killing all the Gnome panels, saving the session, logging back in, and starting only one Gnome panel?

---

### Post by samwyse on 2005-11-12
Yes, it shouldn't start twice. I now made a symbolic link in ~/Desktop/Autostart for gnome-panel as a workaround and avoid saving session (which I don't really need).

---

