---
title: "apt-get and dpkg are stuck"
date: 2006-06-23
forum: Desktop Environments
---

### Post by LazyBoy on 2006-06-23
My pkg stuff is scrambled.  I can't add or remove anything.  How do I get out of this?

> 
$ sudo apt-get install c++
Reading package lists... Done
Building dependency tree... Done
E: The package sun-java5-bin needs to be reinstalled, but I can't find an archive for it.
$ sudo apt-get install sun-java5-bin
Reading package lists... Done
Building dependency tree... Done
E: The package sun-java5-bin needs to be reinstalled, but I can't find an archive for it.
$ sudo dpkg -i  sun-java5-bin
dpkg: error processing sun-java5-bin (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 sun-java5-bin
$ sudo dpkg -r  sun-java5-bin
dpkg: error processing sun-java5-bin (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 sun-java5-bin


Thanks,
LB

---

### Post by xXx 0wn3d xXx on 2006-06-23
Run:
> sudo dpkg --configure -a

---

### Post by LazyBoy on 2006-06-23
Thanks, but that doesn't do it.
LB

> 
$ sudo dpkg --configure -a
$ sudo apt-get install c++
Reading package lists... Done
Building dependency tree... Done
E: The package sun-java5-bin needs to be reinstalled, but I can't find an archive for it.


---

### Post by LazyBoy on 2006-06-23
I gave in and ran

> dpkg -r --force-remove-reinstreq sun-java5-bin

---

