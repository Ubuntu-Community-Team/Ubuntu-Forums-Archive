---
title: "Add/remove error"
date: 2009-04-05
forum: General Help
---

### Post by ghettoman962 on 2009-04-05
when i try to install something in add/remove i get this message: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report. 

i have no clue what this means please help

---

### Post by ShaunG on 2009-04-05
Open a terminal

Application -> Accessories -> Terminal

then run 

```
sudo dpkg --configure -a
sudo apt-get update
```

---

