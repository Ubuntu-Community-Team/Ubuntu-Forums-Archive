---
title: "gnome menu corrupt.  crashes smeg &amp; alacarte."
date: 2005-12-16
forum: Desktop Environments
---

### Post by pcatiprodotnet on 2005-12-16
How do I fix a corrupt "start" menu?
It may be because I installed too many games; the games menu is Very long.
Is there any fix or manual way to add more menu items?
Thank you, -pc

---

### Post by aysiu on 2005-12-17
Have you tried Applications > System Tools > Applications Menu Editor?

---

### Post by pcatiprodotnet on 2005-12-17
> Have you tried Applications > System Tools > Applications Menu Editor?
Yes, "Applications Menu Editor" is smeg.  It crashes.

---

### Post by aysiu on 2005-12-17
Try this, then: ```
mv ~/.config/menus/applications.menu ~/.config/menus/applications.menu_backup
killall gnome-panel
smeg
``` Any luck?

---

