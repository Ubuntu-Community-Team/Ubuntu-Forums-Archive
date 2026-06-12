---
title: "Trouble w/ update manager"
date: 2009-04-03
forum: General Help
---

### Post by n00b_saibot on 2009-04-03
Every time I try to update, this comes up:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I am running ubuntu 8.10

---

### Post by ShaunG on 2009-04-03
Try doing as it says and run

```
sudo dpkg --configure -a
```

from a terminal. (Type alt+f2 and type in gnome-terminal to run a terminal.)

Then run

```
sudo apt-get update
```

to see if it fixed your problem.

---

