---
title: "Lost Applications, Places and System Menu"
date: 2009-02-17
forum: Desktop Environments
---

### Post by namzuk on 2009-02-17
I lost the little "Applications, Places and System" menu in the upper left corner of my hardy heron screen when I inadvertently pulled it from the top panel.  I've tried and tried but can't get it back.  Please help

---

### Post by whoop on 2009-02-17
Right click (top) panel. Select "add to panel", Select "menu bar". click add

---

### Post by UbuntuNerd on 2009-02-17
if the solution provided above didn't solve your problem type this command in a terminal to restore your panels to default like they were before:
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```

---

