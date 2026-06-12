---
title: "X.org crashes with SMP kernel..."
date: 2006-07-04
forum: Desktop Environments
---

### Post by st00ner on 2006-07-04
Problem Resolved

---

### Post by ajgreeny on 2006-07-04
Does xorg crash if you try to start it after logging in to the terminal using "startx", or is it just on bootup?  Have you tried booting into your previous kernel at bootup?  Hit Esc at grub if the menu doesn't appear and then chose the previous kernel, which should still be listed.  If that doesn't work, then for some reason your xorg.conf must have changed and will need dealing with.

---

### Post by st00ner on 2006-07-04
Problem Resolved

---

