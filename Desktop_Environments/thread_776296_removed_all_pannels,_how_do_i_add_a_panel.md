---
title: "removed all pannels, how do i add a panel"
date: 2008-04-30
forum: Desktop Environments
---

### Post by pedrotuga on 2008-04-30
this is embarrassing, but that's what just hapen to me... how do i fix that stupid mistake?

---

### Post by sisco311 on 2008-04-30
From a terminal delete the panels config files and restart the panel:
```
rm -fr ~/.config/xfce4/panel/
killall xfce4-panel
```press Alt+F2 and type: xfce4-panel

This will restore the default panels.

---

### Post by magnus0 on 2008-04-30
Try these commands, if you're on Gnome:
```

gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```

---

### Post by pedrotuga on 2008-04-30
thank you.
I used sisco's method and it worked fine.

---

