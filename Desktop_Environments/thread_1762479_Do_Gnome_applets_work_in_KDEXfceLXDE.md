---
title: "Do Gnome applets work in KDE/Xfce/LXDE?"
date: 2011-05-19
forum: Desktop Environments
---

### Post by jre6 on 2011-05-19
Do Gnome applets like nm-applet work in KDE/Xfce/LXDE?

Or maybe Fluxbox/openbox?

---

### Post by mcduck on 2011-05-19
nm-applet works, since it's not exactly an applet, regardless of the name. :)

(not sure about KDE, but it definitely has no problems with XFCE/LXDE/OpenBox, as long as you have some way of displaying notification icons.)

Actual gnome applets require gnome-panel, although if I remember right the panel in XFCE has an applet that can serve as host for gnome-panel applets.

---

### Post by Copper Bezel on 2011-05-19
Right, we're really talking about Indicator Applets or Notification Area items, not panel applets. XFCE4-Panel can indeed support Gnome panel applets via xfapplet, but more importantly, anything that displays an indicator icon should appear in any other DE, so long as it's running. The only exceptions would be indicator applet items that aren't really indicator applet icons, like the session and message indicators.

---

