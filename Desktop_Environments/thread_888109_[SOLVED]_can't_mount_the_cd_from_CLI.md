---
title: "[SOLVED] can't mount the cd from CLI"
date: 2008-08-12
forum: Desktop Environments
---

### Post by cherva on 2008-08-12
I recently discovered that /dev/hdc and /dev/cdrom are gone.
Which file in /dev should I use now ? 
When I insert a cd it automounts, so the cd is ok :)

---

### Post by logos34 on 2008-08-12
it's probably now using /dev/scd0

check with

ls -l /dev/cd*

---

### Post by sisco311 on 2008-08-12
```
lshw -C disk
```should list the device name.

---

### Post by cherva on 2008-08-12
> **logos34 said:**
> it's probably now using /dev/scd0

check with

ls -l /dev/cd*
Found it :) somehow it is now cdrom4 which is a link to scd0 :)

---

### Post by sisco311 on 2008-08-12
Cool!
If your thread is solved, please mark it solved by selecting 
**Mark this thread as solved** from the **Thead Tools**.

---

