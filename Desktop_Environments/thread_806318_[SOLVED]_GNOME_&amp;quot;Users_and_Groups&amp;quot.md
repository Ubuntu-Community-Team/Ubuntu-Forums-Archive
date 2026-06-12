---
title: "[SOLVED] GNOME &amp;quot;Users and Groups&amp;quot; won't unlock"
date: 2008-05-24
forum: Desktop Environments
---

### Post by Steve413z on 2008-05-24
If i goto the gnome, "users and groups" options, and click "unlock" it just freezes, I can't modify anything through the GUI, i have to use the command line, anyone know how to fix this?

---

### Post by Steve413z on 2008-05-25
alright, i think i might have solved the problem

sudo usermod -G admin [YOUR USER NAME]
sudo usermod -G root [YOUR USER NAME]

restart x

---

