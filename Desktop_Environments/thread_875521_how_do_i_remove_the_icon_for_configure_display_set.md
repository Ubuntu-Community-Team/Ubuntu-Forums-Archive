---
title: "how do i remove the icon for configure display settings from the notification area?"
date: 2008-07-30
forum: Desktop Environments
---

### Post by kef_kf on 2008-07-30
when i right click on it and choose "Configure Display Settings", it launches gnome-display-properties.
screenshots are below.

---

### Post by linux_tech on 2008-07-30
Does it show up in system monitor?

---

### Post by kef_kf on 2008-07-31
i believe it doesnt.

---

### Post by imronak on 2008-07-31
Right Click on it, does it have a "Remove from panel" option ??

---

### Post by kef_kf on 2008-07-31
nope, there is a greyed out "Screen Rotation" option and another option labeled "Configure Display Settings" that brings up the gnome-display-properties menu (updated screenshots in the first post).

---

### Post by kef_kf on 2008-08-01
bump

---

### Post by sfarestam on 2008-12-12
I struggled with this as well and finally discovered that the culprit is gnome-settings-daemon (how logical is that...?). To disable it, launch gconf-editor and disable /apps/gnome_settings_daemon/xrandr/show_notification_icon.

---

