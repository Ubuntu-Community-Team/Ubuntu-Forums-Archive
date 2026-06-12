---
title: "How can I stop mounted media from appearing on the desktop?"
date: 2006-09-05
forum: Desktop Environments
---

### Post by NakedGreekStatue on 2006-09-05
I have my windows NTFS share mounted on startup and often have a dvd inseted, and when these icons show up they mess up my very customized desktop. How can I have these media still mount but not put an icon on the desktop?

---

### Post by PWill on 2006-09-05
Go to Applications > System Tools > Configuration Editor
if it is not there, open a terminal, and type "gconf-editor" and press enter.  Click on the "apps" arrow. Go down to "nautilus" and click its arrow. Then select "desktop"
Uncheck the box next to "volumes_visible" ;)

---

