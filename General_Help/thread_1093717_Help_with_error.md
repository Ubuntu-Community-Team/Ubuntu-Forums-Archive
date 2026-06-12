---
title: "Help with error"
date: 2009-03-11
forum: General Help
---

### Post by Racnnut on 2009-03-11
I'm getting this error when I try to do a system update.  How do I access and correct this problem?

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by madverb on 2009-03-11
Open up a terminal and input:
```
dpkg --configure -a
```

---

### Post by pastalavista on 2009-03-11
make that ```
**sudo** dpkg --configure -a
```

:D

---

