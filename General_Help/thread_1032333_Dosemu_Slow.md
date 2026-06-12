---
title: "Dosemu Slow"
date: 2009-01-06
forum: General Help
---

### Post by wrgt on 2009-01-06
I'm currently running XP. I'm using our database program created by using Clipper. 

I wanted to migrate to Ubuntu and have set up the database program to run under Dosemu successfully. The problem is it's running slower than under XP.

I've tried changing the hogthreshold value from 1 (default) to 0 (all cpu power to dosemu) but nothing changed. 

```
c:\speed 0
```

Any suggestions?

---

### Post by Mike_Leash on 2010-06-21
try sudo sysctl -w vm.mmap_min_addr=0
to add it permanently add in /etc/sysctl.conf

vm.mmap_min_addr=0

---

