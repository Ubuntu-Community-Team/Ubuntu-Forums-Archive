---
title: "removed package and now launch bars are gone"
date: 2009-02-11
forum: Desktop Environments
---

### Post by zarawesome on 2009-02-11
I tried to remove some packages to make space for the gigantic TeX environment and now my navigation bars or launch bars or task bars or whatever are gone. All I have is the wallpaper and a couple of icons. I tried removing .gconf and .gnome and .gnome2 and .gconfd to no avail. An answer to any of the following questions would be nice:

1) How do I launch graphical applications without my taskbar?

2) How do I get my taskbar back? I don't remember what packages I uninstalled. Do I need them?

---

### Post by UbuntuNerd on 2009-02-11
hit Alt + F2 and type this commands all at once and hit run:
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

---

### Post by zarawesome on 2009-02-12
Alt+F2 doesn't work either.

---

### Post by UbuntuNerd on 2009-02-13
can you hit "Control+Alt+f1" and see what happens, to go back to your GUI hit "Alt+f7"

---

