---
title: "error message i received when attempting to install updates"
date: 2009-04-20
forum: General Help
---

### Post by RebeccaHowarth on 2009-04-20
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


What does this mean, and how do I fix it?

---

### Post by Peter09 on 2009-04-20
Its all in the error message. The package manager was interrupted and needs to be reset. In a terminal do the following

```
sudo dpkg --configure -a
```

---

