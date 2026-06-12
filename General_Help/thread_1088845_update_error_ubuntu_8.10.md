---
title: "update error ubuntu 8.10"
date: 2009-03-06
forum: General Help
---

### Post by clintsharlet on 2009-03-06
I now have a total of 55 updates for my computer, using ubuntu 8.10 and when I go to install the updates I receive this error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

how do I correct this??  I am a total newbie at this....

Thanks in advance
Clint

---

### Post by chriskin on 2009-03-06
probably running the command it asks you to run will solve the problem

have you tried it?

---

### Post by taurus on 2009-03-06
Close down the update manager.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by clintsharlet on 2009-03-06
Thanks Taurus, thanks very much... you fixed my problem!!  I am all new to this... but I like it!! greatly appreciated!


Clint..:D

---

