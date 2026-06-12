---
title: "Desktop Font Size"
date: 2009-06-18
forum: Desktop Environments
---

### Post by camper365 on 2009-06-18
Whenever I adjust my font size in System -> Appearance, it takes effect there, but whenever I log out or restart, my settings are set back to the default. The same happens with a terminal window. I adjusted the monospace setting in Appearance and the settings take effect in the terminal, but the same problem happens when I logout. If I adjust the settings in the terminal, the font size is the size I want until I log out and log back in.

---

### Post by camper365 on 2009-06-19
bump

---

### Post by days_of_ruin on 2009-06-19
Try making a new account and see if it has the same problem.

---

### Post by camper365 on 2009-06-20
the problem doesn't exists in a new user

---

### Post by days_of_ruin on 2009-06-20
So when you log in to the old account are there any popup warnings?

You could try deleting the current configuration for fonts:
```
rm -r .gconf/desktop/gnome/interface

```

---

### Post by camper365 on 2009-06-20
the only thing that pops up when i log in is pidgin and one of my applets is messed up and it asks me if I want it to be deleted, and I select delete, but it doesn't actually delete. Nothing related to the appearance

---

### Post by camper365 on 2009-06-21
idk what I did, but it's fixed

---

