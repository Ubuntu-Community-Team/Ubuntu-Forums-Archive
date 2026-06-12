---
title: "KDE4 Control Center in Gnome?"
date: 2009-05-17
forum: General Help
---

### Post by Kimm on 2009-05-17
Does anyone know how I can access the KDE4 control center from gnome? (and possibly which package its in). I know that it was called kcontrol in KDE3, but that seems to have changed.

The reason I want the KDE4 Control center is that I want to set the KDE theme to GTK+ (and no, the qtconfig tool wount work on KDE apps).

Help anyone? :)

---

### Post by 67GTA on 2009-05-17
It is ```
systemsettings
``` also the ```
gtk-qt-engine-kde4
``` package lets you control gtk looks from within KDE if you need it.

---

### Post by Kimm on 2009-05-17
> **67GTA said:**
> It is ```
systemsettings
``` also the ```
gtk-qt-engine-kde4
``` package lets you control gtk looks from within KDE if you need it.

Thank you for replying! I installed systemsettings, but now when I run it the window is empty, so I cant set the theme, do I need to install something besides this?

---

### Post by 67GTA on 2009-05-17
What version of Ubuntu are you running?

---

### Post by Kimm on 2009-05-17
> **67GTA said:**
> What version of Ubuntu are you running?

Jaunty. :)

---

### Post by 67GTA on 2009-05-17
Install ```
kdebase-workspace-bin
``` Run ```
kbuildsycoca4
``` in a terminal and log out and back in. That should populate the settings screen.

---

### Post by Kimm on 2009-05-17
Many thanks! That worked! :)

---

