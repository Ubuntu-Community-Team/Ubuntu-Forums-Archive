---
title: "remove default menu entries"
date: 2012-06-19
forum: Desktop Environments
---

### Post by cccc on 2012-06-19
hi

Howto remove some default menu entries in LXDE?

---

### Post by seppalta on 2012-06-19
Install and use Lxmed to control Menu:  [http://sourceforge.net/projects/lxmed/.]("http://sourceforge.net/projects/lxmed/")
Otherwise, delete the desktop file associated with the application.  Most desktop files are in **/usr/share/applications**.   Lxmed is a java application and requires a good java to run.
[http://douwil7.100webspace.net/linux/Tuning.html#9](http://douwil7.100webspace.net/linux/Tuning.html#9)

---

### Post by cccc on 2012-06-19
Sorry, but java is not installed, this is a really small thin client installation.
Knows someone where can I find this menu file to delete some entries manually?

---

### Post by black veils on 2012-06-20
> **seppalta said:**
> delete the desktop file associated with the application.  Most desktop files are in **/usr/share/applications**


i dont think deleting is the best way, because you can lose it as an option in places you need it, generally it is best to do the following:

1.  open the **terminal** and type ```
gksudo pcmanfm
``` press the **Enter** key. this will open your file manager with root privileges, be careful.


2. go to filesystem, locate **/usr/share/applications**


3.  right-click the chosen menu entry file, open with leafpad or whatever text editor is on Lubuntu.


4.  add this line to the end of the file ```
NoDisplay=true
``` then save.

---

### Post by cccc on 2012-06-20
Thx a lot, that's what I want and it works well now.

---

