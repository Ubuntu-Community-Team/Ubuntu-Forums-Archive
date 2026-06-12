---
title: "problems installing programs from the add/remove menu"
date: 2009-01-01
forum: General Help
---

### Post by danny h on 2009-01-01
when i try to install anything off the add/remove section, i get 'E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

---

### Post by Tim Sharitt on 2009-01-01
You've probably had an install or upgrade interrupted. Open a terminal and run:
```
sudo dpkg --configure -a
```
Repost here if that give you an error message.

---

### Post by danny h on 2009-01-01
yep, it's definately because i didnt install the problem right, its because whenever i try installing java i end up getting 


[IMG]http://img390.imageshack.us/img390/8882/screenshotmi5.png[/IMG]


and i dont know what im suppose to do from there, so i just always end up pressing exit...

what am i suppose to do from step - anyone know?

---

### Post by adult swim on 2009-01-01
when you get to that screen, hit the tab key and it should make the OK highlighted.  then hit enter

---

### Post by danny h on 2009-01-01
thank you!

problem solved!

---

