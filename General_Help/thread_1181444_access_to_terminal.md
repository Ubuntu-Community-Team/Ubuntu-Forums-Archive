---
title: "access to terminal"
date: 2009-06-07
forum: General Help
---

### Post by almagr on 2009-06-07
how can i access terminal, when all my desktop menus have dissapeared and f2 doesnt work?

---

### Post by UbuntuNerd on 2009-06-07
try Ctrl+Alt+f2 and to get back to your desktop Ctrl+Alt+f7

---

### Post by UbuntuNerd on 2009-06-07
try this command when you get there it should restore your panels and menus
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

---

### Post by CatKiller on 2009-06-08
Or you could right-click on the Desktop and create a launcher for gnome-terminal.

---

