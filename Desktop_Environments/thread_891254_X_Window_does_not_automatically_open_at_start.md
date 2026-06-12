---
title: "X Window does not automatically open at start"
date: 2008-08-15
forum: Desktop Environments
---

### Post by themostunoriginalname on 2008-08-15
Currently, when I open my computer, it goes to the command line and I have to write startx to start it. Is there anyway to start it automatically again?

---

### Post by picpak on 2008-08-15
```
sudo update-rc.d gdm defaults
```

should do it.

---

### Post by themostunoriginalname on 2008-08-15
/etc/init.d/gdm does not exists

---

### Post by picpak on 2008-08-15
```
sudo apt-get install gdm
```

---

### Post by themostunoriginalname on 2008-08-15
works! Thanks!

---

