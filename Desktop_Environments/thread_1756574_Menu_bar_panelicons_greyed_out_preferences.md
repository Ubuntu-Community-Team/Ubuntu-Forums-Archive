---
title: "Menu bar panel/icons greyed out preferences"
date: 2011-05-12
forum: Desktop Environments
---

### Post by johntkucz on 2011-05-12
All panels are locked to top menu bar "move", "lock to menubar" and preferences are all greyed out when I right click on a top menu bar icon panel.

using 10.04 netbook edition. thanks.

---

### Post by Krytarik on 2011-05-12
The only way to modify the panel in the UNR is to manually edit the file "/var/lib/gconf/une.mandatory/%gconf-tree.xml". I guess you will get the point when you study the entries. These are system-wide settings. You need to gain root access to edit the file, like this:
```
gksu gedit /var/lib/gconf/une.mandatory/%gconf-tree.xml
```I had to do that to "free" the "Window Picker Applet". ;-)

Greetings.

---

