---
title: "remove nautilus move to option"
date: 2010-08-17
forum: Desktop Environments
---

### Post by chaos_efphect on 2010-08-17
I just installed 10.04 on one of my computers and i LOVE the new look and feel expect for the right click nautils move/copy to. i wanted to know if anyone knew of a way to remove it? i tired doing some poking around on here but only found one post called "How to hide copy to / move to right click Nautilus menus?" but it did not work for me.

---

### Post by stinkeye on 2010-08-18
> **chaos_efphect said:**
> I just installed 10.04 on one of my computers and i LOVE the new look and feel expect for the right click nautils move/copy to. i wanted to know if anyone knew of a way to remove it? i tired doing some poking around on here but only found one post called "How to hide copy to / move to right click Nautilus menus?" but it did not work for me.

First make a backup of nautilus-directory-view-ui.xml
```
sudo cp /usr/share/nautilus/ui/nautilus-directory-view-ui.xml /usr/share/nautilus/ui/nautilus-directory-view-ui.xml.bak
```



```
gksudo gedit /usr/share/nautilus/ui/nautilus-directory-view-ui.xml
```

Search for **CopyToMenu** . You will find 2 instances.
Delete from **<menu action ="CopyToMenu">** to **</menu>**

Repeat for **MoveToMenu**

---

### Post by antistress on 2010-10-17
This is interesting, thanks.

Would it be possible to add new entries like being able to move to Download, Documents, Images, Music or Videos folder ?

---

### Post by Brama051 on 2011-07-08
> **antistress said:**
> This is interesting, thanks.

Would it be possible to add new entries like being able to move to Download, Documents, Images, Music or Videos folder ?
Yes, I'm also interested so please share you knowledge!

---

### Post by blawiz1 on 2011-10-16
> **Brama051 said:**
> Yes, I'm also interested so please share you knowledge!

use nautilus-actions-config-tool

---

