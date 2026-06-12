---
title: "removing all icons in GNOME"
date: 2009-12-09
forum: Desktop Environments
---

### Post by akashiraffee on 2009-12-09
Anyone know how you can stop gnome from automatically putting an icon on the desktop for mounted filesystems?  I don't use desktop icons and don't want to see them!

There is nothing in ~/Desktop to erase.

I'm flipping thru the help browser but not finding anything...

---

### Post by sisco311 on 2009-12-09
Press Alt+F2 and run:
```
gconf-editor
```

go to apps -> nautilus -> desktop and deselect the volumes_visible check box

---

### Post by akashiraffee on 2009-12-09
Thanks!

---

