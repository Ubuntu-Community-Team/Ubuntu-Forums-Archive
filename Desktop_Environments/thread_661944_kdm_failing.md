---
title: "kdm failing"
date: 2008-01-08
forum: Desktop Environments
---

### Post by kiiz on 2008-01-08
how can i reset kdm.some graphical programs refuse to run under kdm eg gdebi. it run only under console.

---

### Post by p_quarles on 2008-01-08
"Reset" as in reinstall it, or "reset" as in switch to another dm? 

Either way, the command is the same:
```
sudo dpkg-reconfigure kdm
```
If you want to reconfigure kdm, choose that as the default. This will also give you the option of switching the default to any other installed dms.

---

