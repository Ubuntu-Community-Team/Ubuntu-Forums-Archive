---
title: "Remove Desktop HDD shortcut"
date: 2006-11-09
forum: Desktop Environments
---

### Post by ryurhrt on 2006-11-09
Ubuntu preinstall system auto mount all our drive if possible... i like this.... but an icon will be shown on the desktop for each drive it mounts... did any one know how to set ubuntu won appear the drive that it mount automately? because i like my desktop empty...

---

### Post by CatKiller on 2006-11-09
```
gconf-editor
```
/apps/nautilus/desktop/volumes_visible
untick the box

---

