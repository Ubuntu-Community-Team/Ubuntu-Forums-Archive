---
title: "minimize windows with double click - 14.04 Unity"
date: 2015-04-13
forum: Desktop Environments
---

### Post by rawlins02 on 2015-04-13
New installation. Can't figure out how to minimize a window, with either one or two clicks. I prefer double click on titlebar to minimize.

I have installed compizconfig-settings-manager and Unity tweak tool.  Looked at a number of how-to docs. After 15-20 minutes of trying, thought I'd ask here.

---

### Post by grahammechanical on 2015-04-13
In Ubuntu Unity a double click on an application's window title bar will maximise the window. Then a double click on the top panel will restore the application window to its previous size. There are three ways that I know of for minimising a window. I do not think that the developers have made it possible to change the double click on the window's title panel. It is part of the Unity design.

Regards.

---

### Post by rawlins02 on 2015-04-13
In 12.04 and versions before that I found a way to enable a double click to minimize. Hard to believe that functionality has been eliminated.

---

### Post by mc4man on 2015-04-15
use in a terminal - 
```
gsettings set org.gnome.desktop.wm.preferences action-double-click-titlebar 'minimize'
```

---

