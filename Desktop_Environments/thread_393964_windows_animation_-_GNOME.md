---
title: "windows animation - GNOME"
date: 2007-03-26
forum: Desktop Environments
---

### Post by g1psas on 2007-03-26
How to disable  windows animation in Ubuntu 6.10 (gnome) (e.g. window maximise, minimise) ? It realy makes my system slow

---

### Post by ArieT on 2007-03-26
Open up your gconf-editor  ("configuration editor" in Ubuntu), and then go to the key in apps -> metacity -> general called "reduced_resources" set it to TRUE and it will remove window animations and only show wire frames when moving/resizing.

---

