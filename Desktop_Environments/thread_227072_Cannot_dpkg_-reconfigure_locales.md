---
title: "Cannot dpkg -reconfigure locales"
date: 2006-08-01
forum: Desktop Environments
---

### Post by hkl8324 on 2006-08-01
I got the following 

hkl8324@hkl8324-laptop:~$ sudo dpkg -reconfigure locales
dpkg: conflicting actions --control and --remove

Any suggestions?

---

### Post by ardchoille on 2006-08-01
You have a space where there shouldn't be one. The proper command is:

```

sudo dpkg-reconfigure locales

```

You have a space between dpkg and -reconfigure, try it without the space.

---

