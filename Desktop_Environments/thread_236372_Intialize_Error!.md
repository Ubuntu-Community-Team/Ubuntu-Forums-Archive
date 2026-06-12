---
title: "Intialize Error!"
date: 2006-08-14
forum: Desktop Environments
---

### Post by moonliter on 2006-08-14
I am getting this error when I start ubuntu:

```
INTERNAL ERROR FAILED TO INTIALIZE HAL!
```

Can I fix this problem?

---

### Post by moonliter on 2006-08-21
Can anyone help mw with this?

---

### Post by ntwrkguy on 2006-08-22
I started to get this too today...

---

### Post by Ashtray on 2006-09-02
Same problems here (after my upgrade to edgy).

//edit
After commenting out some mount points in my /etc/fstab the error was gone!

---

### Post by Ashtray on 2006-09-03
*kick

i noticed an upgrade process backed up the fstab as fstab.pre-uuid and changed the fstab in a wrong way. Placing back the fstab solves this.

//Note: This all happens AFTER **upgrading** to EDGY.

//Note2: going to freshly install edgy knot1 CD, too much haggle getting stuff working.

---

