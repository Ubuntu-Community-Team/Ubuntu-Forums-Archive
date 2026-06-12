---
title: "Notification area vs Indicator Plugin precedence per app"
date: 2013-11-22
forum: Desktop Environments
---

### Post by memeplex on 2013-11-22
Hi, is it possible to configure the Indicator Plugin to reject specific applications in order them to show in the systray (Notification Area). For example, transmission-gtk.

Regards
--
Carlos

---

### Post by Frogs Hair on 2013-11-23
There are _some_ settings for panel applets in the dconf editor. I don't use Transmission and have never seen it in the system tray, but there may a true/false setting in the editor.

---

### Post by memeplex on 2013-11-23
Thank you Frogs Hair, I will take a look at that. I realize I don't fully understand how the notification area and the indicator plugin interrelate. For example, is there an order of precedence at the wm level or each application choses where to show itself? (supposing it supports both, indicator and systray). Moreover, how is it that some applications shows in both systray and indicator? (it comes to my mind the case of gmusicbrowser which, strictly, doesn't own an specific place in the indicator but resides inside the volume control).

---

### Post by memeplex on 2013-11-23
Apparently there is while/black listing functionality in the latest release of the xfce indicator plugin:

[http://mail.xfce.org/pipermail/xfce-announce/2013-June/000275.html](http://mail.xfce.org/pipermail/xfce-announce/2013-June/000275.html)

I'm contacting the developer now for some examples to get this working. I will let you know about any news, I know I'm not the only one dealing with this issue.

---

