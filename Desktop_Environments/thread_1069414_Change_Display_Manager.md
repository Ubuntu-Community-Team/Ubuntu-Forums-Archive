---
title: "Change Display Manager"
date: 2009-02-13
forum: Desktop Environments
---

### Post by notesetter on 2009-02-13
I'm a GNOME user. I just tried out KDE 4 and chose on first startup to change the display manager from GDM to the KDE one. How might I switch it back?

Thanks,

Dave

---

### Post by Darkshade on 2009-02-14
Open /etc/X11/default-display-manager with your favorite text editor and change ```
/usr/bin/kdm
``` to ```
/usr/sbin/gdm
```

---

### Post by notesetter on 2009-02-15
Many thanks.

---

