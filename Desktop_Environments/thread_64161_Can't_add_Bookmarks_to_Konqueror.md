---
title: "Can't add Bookmarks to Konqueror"
date: 2005-09-10
forum: Desktop Environments
---

### Post by adwait on 2005-09-10
Hello!

Well, KDM crashed and I couldn't do anything so I had to hard reboot. Well, Konqueror was open then, and after the computer started, the booksmarks are gone. Also, I tried to add bookmarks but they just don't get added.........any idea?

---

### Post by GML3G0 on 2005-10-05
I have the same problem... Anyone?

---

### Post by cwaldbieser on 2005-10-05
[QUOTE=adwait]Hello!
Well, KDM crashed and I couldn't do anything so I had to hard reboot. Well, Konqueror was open then, and after the computer started, the booksmarks are gone. Also, I tried to add bookmarks but they just don't get added.........any idea?[/QUOTE]
The bookmarks are normally stored in ~/.kde/share/apps/konqueror/bookmarks.xml.  Maybe you could rename that file to a backup and see if starting from scratch would work?  Maybe the file had permissions changed somehow?

---

### Post by GML3G0 on 2005-10-05
I just fixed it by deleting that bookmarks.xml cache file and starting the bookmarks from scratch.

---

