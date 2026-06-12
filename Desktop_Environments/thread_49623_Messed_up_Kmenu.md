---
title: "Messed up Kmenu"
date: 2005-07-17
forum: Desktop Environments
---

### Post by oliwally on 2005-07-17
Ok, I've really done it this time - I've accidentally removed the 'System' sub-menu from my kmenu. Is there any way of restoring the whole thing in one hit? Or do I have to add it all back in one-by-one ?

---

### Post by SGC on 2005-07-17
To restore the orginal kmenu delete this file :
~/.config/menus/applications-kmenuedit.menu

---

### Post by oliwally on 2005-07-17
Wow, you people are just amazing - and fast in replying ! Thanks so much - worked like a charm.

---

### Post by Manny C on 2005-09-11
[QUOTE=SGC]To restore the orginal kmenu delete this file :
~/.config/menus/applications-kmenuedit.menu[/QUOTE]

Actually, it may be better to rename the file.

```
mv ~/.config/menus/applications-kmenuedit.menu ~/.config/menus/applications-kmenuedit.menu.bu
```

---

