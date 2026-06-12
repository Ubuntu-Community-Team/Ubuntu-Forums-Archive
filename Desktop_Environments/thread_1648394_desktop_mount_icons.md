---
title: "desktop mount icons"
date: 2010-12-18
forum: Desktop Environments
---

### Post by emilemma on 2010-12-18
is there some way to move the icons for mounted disks from the desktop to a panel thereby keeping the desktop nice & clean?

thanks:D

---

### Post by PhantmKllr on 2010-12-18
> **emilemma said:**
> is there some way to move the icons for mounted disks from the desktop to a panel thereby keeping the desktop nice & clean?

thanks:D
In Gnome? I don't think that's possible.

---

### Post by Krytarik on 2010-12-18
I don't know a way to add the "volumes" you know to a panel, however if the mounted volumes don't change heavily each day you could create launchers for them invoking the nautilus command.

To remove the "volumes" from the desktop, press Alt+F2, enter:
```
gconf-editor
```
and untick "/apps/nautilus/desktop/volumes_visible".

---

### Post by emilemma on 2010-12-18
thanks very much.....

---

