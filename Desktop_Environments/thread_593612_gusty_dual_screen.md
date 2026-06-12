---
title: "gusty dual screen"
date: 2007-10-27
forum: Desktop Environments
---

### Post by yon2501 on 2007-10-27
ok so ive just switched up to gusty and i cant seem to get dual monitors working properly with the screens and graphics tool. is there any way i can disable this tool and get nvidia control pannel. i used nvidia cp before on fiesty and i know my way around it prety well and id just rather use that. if not the problem im havint with the screens and graphics tool is that whenever i enter dual sceen mode the monitor on my laptop looks like its in zoom desktop mode and only a small portion of my desktop is on the other screen. any help would be much appreciated.

---

### Post by boast on 2007-10-27
just do, sudo X -configure  (i believe thats it)

then edit xorg.conf and put nvidia drivers. And then just use nvidia-settings, and avoid opening "screens and graphics"

---

### Post by yon2501 on 2007-10-27
well this cant be good 
```
Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.

```

---

