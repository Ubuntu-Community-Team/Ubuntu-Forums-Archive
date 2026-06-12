---
title: "Load module at startup"
date: 2009-04-10
forum: General Help
---

### Post by Nonno Bassotto on 2009-04-10
I've been playing around to make my wireless work. Among other things I blacklisted the module zd1211rw and tried ndiswrapper. Now everything works well with the original driver zd1211rw, except that I have to load it manually at each startup with
```

sudo modprobe zd1211rw

```

How can I add it permanently to the loaded modules? I guess I have to put something somewhere in /etc/modprobe.d/ but I don't know exactly what. By the way, under /etc/modprobe.d/ I can still find /etc/modprobe.d/ndiswrapper, even though I completely removed ndriwrapper and all related tools.

---

### Post by Nonno Bassotto on 2009-05-06
Bump

---

