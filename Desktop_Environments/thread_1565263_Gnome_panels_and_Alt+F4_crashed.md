---
title: "Gnome panels and Alt+F4 crashed"
date: 2010-08-31
forum: Desktop Environments
---

### Post by r00too on 2010-08-31
Ubuntu 10.04 i386

This happened once before (with an earlier version of Ubuntu) when I overlapped two desktop panels, and somehow I triggered it again.

All panels froze, and remained frozen even after a restart. In addition, Alt+F4 doesn't work. If it did, I'm assuming I could go into the config editor and delete the problematic panel(s).

Luckily I can access the file system. I would greatly appreciate it anybody had any ideas of what to do.

- Joseph

---

### Post by hhh on 2010-08-31
What happens if you restart gnome-panel?

```
pkill gnome-panel
```

-edit- There's this too, it resets gnome-panels back to default settings (logout and login afterwards)...

```
gconftool-2 --recursive-unset /apps/panel
```

Found that here...
[http://ubuntuforums.org/showthread.php?p=9758337](http://ubuntuforums.org/showthread.php?p=9758337)

HTH

---

### Post by r00too on 2010-08-31
Those worked perfectly. Thank you so much.

---

### Post by hhh on 2010-08-31
Sweet, np!

---

