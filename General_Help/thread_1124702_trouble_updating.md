---
title: "trouble updating"
date: 2009-04-13
forum: General Help
---

### Post by tuss4 on 2009-04-13
Recently my friends version of Ubuntu (8.10) is not updating, as it should, when the dialogue comes up, after he enters his password, and error message with this code pops up: 

```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

---

### Post by tuss4 on 2009-04-13
*bump*

---

### Post by taurus on 2009-04-13
Close down the update manager.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by tuss4 on 2009-04-13
thank you will try it as soon as I see my friend again.

---

