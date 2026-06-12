---
title: "Find size of all deb files"
date: 2008-02-18
forum: Desktop Environments
---

### Post by lsutiger on 2008-02-18
I am looking to find out how much space all the debs in my /var/cache/apt/archive folder is taking up.

Is there any stock CLI command I can use? 

I have tried different combinations of ls and locate but never get the desired result.

Thanx in advance.


Also, all of those files should be ok to delete correct?

---

### Post by yabbadabbadont on 2008-02-18
```
du -sh /var/cache/apt/archive
```

;)

(and yes, they are safe to delete)

---

### Post by lsutiger on 2008-02-18
Thanx!

Went through a few man pages while I was at it on other commands. I will conquer this one day!

---

