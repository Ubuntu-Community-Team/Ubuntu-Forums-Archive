---
title: "Error message when i try to update :/"
date: 2009-02-17
forum: General Help
---

### Post by Nikeman121 on 2009-02-17
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.




anyone know how to fix?

---

### Post by drs305 on 2009-02-17
You must run this with administrative privileges (sudo):

```
sudo dpkg --configure -a
```
Enter your password when asked - you won't see it. Hit ENTER once you have typed it in.

---

