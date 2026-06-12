---
title: "where to get build-essentials? no wireless yet."
date: 2006-06-19
forum: Desktop Environments
---

### Post by dbcalo on 2006-06-19
ok. trying to get all the necessary build essentials to compile the kernel to get my wireless card working, but i cant to that until i have all the packages to compile it. so... is there an easier way short of downloading the whole dvd?

---

### Post by aysiu on 2006-06-19
Both CDs have *build-essential* on them, even though it's not installed by default.

Pop in either CD and then paste these commands: ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by dbcalo on 2006-06-20
ok. have done this but no kernel config is working. xconfig, gconfig, menuconfig, etc. don't have all the dependencies. are these on the disc as well?

---

### Post by aysiu on 2006-06-20
I doubt it, but you can check with Synaptic or Adept.

[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

