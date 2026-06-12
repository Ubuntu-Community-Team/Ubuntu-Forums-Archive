---
title: "XFCE nm-applet shows up twice in panel"
date: 2006-12-02
forum: Desktop Environments
---

### Post by .t. on 2006-12-02
I guess this is something to do with my XFCE and GNOME sessions overlapping, but it's quite annoying to have two nm-applet instances in the XFCE systray. I've looked in /etc/xdg/autostart and ~/.config/autostart, but cannot find where nm-applet is being called twice. Anyone got any info?

---

### Post by .t. on 2006-12-02
Fixed: delete the contents of ~/.cache/sessions to restore your session to a fresh state.

---

