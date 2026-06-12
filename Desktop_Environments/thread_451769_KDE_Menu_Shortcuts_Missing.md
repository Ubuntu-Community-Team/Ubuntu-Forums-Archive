---
title: "KDE Menu Shortcuts Missing?"
date: 2007-05-22
forum: Desktop Environments
---

### Post by Megatog615 on 2007-05-22
When I installed KDE this morning, I realized that all my settings shortcuts went into "Lost and Found", and the Control Center is completely blank. Is there a way to reset the menus to all be in their default locations?

---

### Post by mitch.c on 2007-05-22
You could try:
```
$ kmenuedit menu reset
```
Or delete (or move) ~/.config/menus/applications-kmenuedit.menu and restart kicker:
```
$ dcop kicker kicker restart
```
YMMV.

-- 
Mitch

---

### Post by Megatog615 on 2007-05-23
The problem is, it's system-wide. I haven't edited the menu yet so that file doesn't exist.

---

