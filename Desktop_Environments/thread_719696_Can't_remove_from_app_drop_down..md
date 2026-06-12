---
title: "Can't remove from app drop down."
date: 2008-03-09
forum: Desktop Environments
---

### Post by prcoy on 2008-03-09
I cant remove wine from App dropdown. Any help?

---

### Post by soldats on 2008-03-09
Is this Xubuntu? If so look in /usr/share/applications where all the .desktop icons are. If the WINE icon is there make it *wine*.desktop.bak and save. it should automatically remove it from the menu. You may in turn add it again by removing the .bak at any time.

---

### Post by prcoy on 2008-03-09
Nope. This is Ubuntu 7.10 and no wine icon was in usr/share/applications. I uninstalled wine but the icons remain.

---

### Post by prcoy on 2008-03-09
Found it: Right clicked on 'Applications' then 'Edit Menus" and unchecked 'wine'. Too easy, I guess. :)

---

