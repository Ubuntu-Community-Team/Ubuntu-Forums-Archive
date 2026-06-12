---
title: "Issue with Gnome panels- me being a noob?"
date: 2013-01-28
forum: Desktop Environments
---

### Post by TheWii552 on 2013-01-28
Hey guys, I've been using Ubuntu for a while now, but really didn't do much customization- and any that I DID do was in KDE. Now I'm figuring out Gnome- and basically experimenting with some stuff to start. I was messing around in the panel settings (for the bottom panel) and accidentally turned off the "expand" setting- and shortly after the properties window for the panel crashed. Now the panel is just a small panel with no "empty" space for me to get into the properties and edit the panel to make it big again. How can I get rid of this panel?

---

### Post by zombifier25 on 2013-01-28
It's probably easier to reset gnome-panel config:
```
dconf reset -f /org/gnome/gnome-panel/
```

---

### Post by TheWii552 on 2013-01-28
Ah, thanks. Worked fine!

---

