---
title: "Wheres home??"
date: 2008-07-03
forum: Desktop Environments
---

### Post by iluminati63 on 2008-07-03
Moving from Mandriva I noticed the absence of the Home icon on the desktop.
Is there an accepted way to place a linked icon to home??

---

### Post by unseend on 2008-07-03
Simply go to Places>Home and drag and n drop the Home icon to one of your panels or desktop. :D

---

### Post by rainwalker on 2008-07-03
Also, in gconf-editor you can check the box for /apps/nautilus/desktop/home_icon_visible

---

### Post by mcduck on 2008-07-04
> **rainwalker said:**
> Also, in gconf-editor you can check the box for /apps/nautilus/desktop/home_icon_visible

I recommend doing it this way. Icon enabled like this will automatically always use the theme you are using, and you can't accidentally remove it from the desktop (you can't drag it to trash like normal icons). Also when auto-arranging desktop icons these icons will be arranged first, before normal files/launchers.

---

