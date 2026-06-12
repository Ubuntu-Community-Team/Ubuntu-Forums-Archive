---
title: "Gnome volume icons placement on desktop"
date: 2008-02-07
forum: Desktop Environments
---

### Post by jazzor on 2008-02-07
This might be an odd request but does anyone know how to force the Gnome desktop to display harddisks first before other removable volumes (such as cdroms and usb sticks)? Currently, if i start my computer with a cd in the drive, the cdrom icon comes up first, but if i take the cdrom out, the icon is gone (unmounted), but leaves an annoying gap between the icons of the harddisk volumes.

---

### Post by jan quark on 2008-02-08
try this

run 
```

gksudo gconf-editor
```

navigate to > apps > nautilus > desktop

here you can add by clicking on the box what should be visible on the desktop
I had just to drag and drop the computer and home and cdrom symbols to the place I wanted them to appear

tell me if this helps

---

