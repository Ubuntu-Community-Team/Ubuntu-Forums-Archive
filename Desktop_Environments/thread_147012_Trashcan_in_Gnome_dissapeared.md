---
title: "Trashcan in Gnome dissapeared"
date: 2006-03-19
forum: Desktop Environments
---

### Post by Roxxor on 2006-03-19
My trashcan has dissappeared. It isn't in the right corner (down) any more. How can I get it back?


EDIT: I solved it.

---

### Post by Ramses de Norre on 2006-03-19
gconf-editor /apps/nautilus/desktop
Check trash_icon_visible and define a name for it.

---

### Post by Aewheros on 2006-03-19
Or if you meant it disappeared from the panel, just right click the panel and select *add to panel*. You will be provided with a collection of useful stuff to add, including the thrash can.

---

