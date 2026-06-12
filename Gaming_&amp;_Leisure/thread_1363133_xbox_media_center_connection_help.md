---
title: "xbox media center connection help"
date: 2009-12-24
forum: Gaming &amp; Leisure
---

### Post by inversionce on 2009-12-24
Hey, I was wondering if there is any way I can connect my xbox 360 to my computer and stream videos, music and pictures. any help would be appreciated.

---

### Post by Qola on 2009-12-24
[Maybe this](http://vanvalkinburgh.org/blog/612).

---

### Post by inversionce on 2009-12-24
when I run   sudo aptitude install ushare  I get this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by Qola on 2009-12-24
> **inversionce said:**
> when I run   sudo aptitude install ushare  I get this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

Oh godddddd.

Copy this into Terminal.

```
sudo dpkg --configure -a
```

If it says something about lock, restart the pc and try that command again.

---

