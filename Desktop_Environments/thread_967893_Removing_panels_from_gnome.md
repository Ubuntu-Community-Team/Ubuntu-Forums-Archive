---
title: "Removing panels from gnome"
date: 2008-11-02
forum: Desktop Environments
---

### Post by ZankerH on 2008-11-02
I would like to remove my gnome panels since I use cairo-dock for the same functionality, but I can't remove gnome-panel because I need the gnome main menu and several other applets. However, when I right-click on a panel, the "remove panel" button is greyed out and I can't remove it. Is there any way I can get rid of the offending panel?

---

### Post by ZankerH on 2008-11-02
bump

---

### Post by ZankerH on 2008-11-02
bmup

---

### Post by Cammy on 2008-11-02
Alt+F2, then type gconf-editor

Go to: apps, panel, and somewhere in there (toplevel I think) is an option where you can unlock your panels.  Once you do this, you can remove them.

---

### Post by ZankerH on 2008-11-02
> **Cammy said:**
> Alt+F2, then type gconf-editor

Go to: apps, panel, and somewhere in there (toplevel I think) is an option where you can unlock your panels.  Once you do this, you can remove them.

Ah, thank you. 

I should note that I've found an intermediate solution in the meanwhile - I've banished the offending panel to the Compiz' widget layer.

---

### Post by fabounet on 2008-11-03
wth the new GMenu applet you don't need anymore the gnome-panel for the main menu ;-)

---

