---
title: "Add/Remove Programs"
date: 2006-09-14
forum: Desktop Environments
---

### Post by Old Pink on 2006-09-14
"Add/Remove Programs" used to be at the bottom of the "Applications" menu but it's vanished, and isn't available on edit menus.

I want it back.

---

### Post by aysiu on 2006-09-14
Add it as a new menu item. The command for that menu item is ```
gksudo gnome-app-install
```

If you want to make sure it is installed, go to the terminal and paste in this command ```
sudo aptitude update && sudo aptitude install gnome-app-install
```

---

### Post by Old Pink on 2006-09-14
One of the first helpful people I've come accross here. Thanks. :)

---

