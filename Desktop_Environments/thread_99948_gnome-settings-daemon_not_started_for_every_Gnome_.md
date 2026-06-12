---
title: "gnome-settings-daemon not started for every Gnome session"
date: 2005-12-06
forum: Desktop Environments
---

### Post by jki on 2005-12-06
Hi!

Does anyone have any ideas about why gnome-settings-daemon is only started for the first one of simultaneous Gnome sessions by the same user?

The other sessions don't have ~/.Xresources merged, and they don't find the icon/gtk/metacity themes. When i start gnome-settings-daemon manually inside those sessions, that fixes all the problems. Until i login again, of course. :-)

If i [FONT="Courier New"]killall gnome-settings-daemon[/FONT], bonobo-activation-server starts it **in each session**, thus fixing the situation temporarily.

Thanks in advance!

---

