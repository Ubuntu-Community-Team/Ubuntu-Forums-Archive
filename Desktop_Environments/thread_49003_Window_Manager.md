---
title: "Window Manager"
date: 2005-07-14
forum: Desktop Environments
---

### Post by trivialpackets on 2005-07-14
Is there a way that you can disable the default action that when you log into another window manager be it Gnome, KDE, XFCE or whatever, that it asks you if you want to make this change permanent?  It just annoys me a little, as when I log into another manager, it's typically just to mess around, and don't want to change it, but figure there must be a way to disable this action.

---

### Post by badrinarayan on 2005-07-14
Try uncommenting [FONT=Courier New]ShowLastSession=true[/FONT] (line 339 in mine) in **/etc/gdm/gdm.conf** This has the side effect of adding a "Last Session" to the menu.

Regards
Badri

---

### Post by trivialpackets on 2005-07-14
[QUOTE=badrinarayan]Try uncommenting [FONT=Courier New]ShowLastSession=true[/FONT] (line 339 in mine) in **/etc/gdm/gdm.conf** This has the side effect of adding a "Last Session" to the menu.

Regards
Badri[/QUOTE]
 Didn't work, but I'll look around that conf file and see if I can find something to make the difference.

---

### Post by badrinarayan on 2005-07-14
You will have to restart gdm
Try
```
sudo /etc/init.d/gdm restart

```
from a virtual console terminal (**Ctrl+Alt+F1** to get there)

Regards
Badri

---

### Post by trivialpackets on 2005-07-14
[QUOTE=badrinarayan]You will have to restart gdm
Try
```
sudo /etc/init.d/gdm restart

```
from a virtual console terminal (**Ctrl+Alt+F1** to get there)

Regards
Badri[/QUOTE]
 I tried this and did not get the desired result.  Any ideas as to why?

---

