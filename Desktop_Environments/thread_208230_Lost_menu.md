---
title: "Lost menu"
date: 2006-07-03
forum: Desktop Environments
---

### Post by bigjack on 2006-07-03
As indicated for Kubuntu, the menu editor (xfce4-menueditor) doesn't work as expected, and might eat your menu. To restore the default menu: remove ~/.config/xfce4/desktop/menu.xml, log out from Xfce and then log in again.

How do I do this?  I have no idea where to go to remove the menu.xml.

---

### Post by lepre on 2006-07-04
copy this in terminal:

rm ~/.config/xfce4/desktop/menu.xml

then ctrl+alt+backspace (restarts X closing all app without prompt, save your work before!)

---

### Post by Taum on 2008-02-24
> **lepre said:**
> copy this in terminal:

rm ~/.config/xfce4/desktop/menu.xml

then ctrl+alt+backspace (restarts X closing all app without prompt, save your work before!)

That did not work for me.  Any other ideas?

---

### Post by smdofjmdsfjoiez on 2008-06-21
work for me 

thx!

---

