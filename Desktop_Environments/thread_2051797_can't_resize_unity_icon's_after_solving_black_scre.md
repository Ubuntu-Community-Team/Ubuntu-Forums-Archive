---
title: "can't resize unity icon's after solving black screen blink on login screen"
date: 2012-09-02
forum: Desktop Environments
---

### Post by alieblice on 2012-09-02
Hi
i cant resize unity icons from compiz after solving down problem actually none of the compiz setting for unity work .

 i had black screen blink on login  ((when i give my password , it was return me immediately to login screen again ))  that i solved it by removing these files 
 .Xauthority
.xsession-errors
.xsession-errors.old

---

### Post by stinkeye on 2012-09-02
Sounds like your in the ubuntu2d session.
```
echo $DESKTOP_SESSION
``` 

If your being dropped back to the **ubuntu2d** session when choosing the **ubuntu** session at login,
check your gfx drivers in additional drivers.

---

### Post by alieblice on 2012-09-02
thank's for reply . you were right . it was in unity2d .
i change it from login screen to unity3d and every thing works fine now.

---

