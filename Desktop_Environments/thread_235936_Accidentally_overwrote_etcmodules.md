---
title: "Accidentally overwrote /etc/modules"
date: 2006-08-13
forum: Desktop Environments
---

### Post by jonnnny on 2006-08-13
Hey, I just installed a fresh Dapper installation, but then almost immediately I accidentally overwrote /etc/modules (don't ask how :( )
I don't want to reboot in case something screws up, but if anyone can give me the default content for the file, I would really appreciate it.

Or is there some way I could recover what it was before? I already closed the text editor (gedit).

Thanks!

---

### Post by Illusionistx on 2006-08-14
all mine has is 
```

lp
psmouse

```

hope that helps a little

---

### Post by nanotube on 2006-08-14
mine is:

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse
sbp2
sr_mod
i8k
fglrx

```

the i8k i added manually to enable hardware sensors on my dell laptop, the fglrx i added manually when i installed the ati proprietary driver. everything else was there "by default".

good luck :)

---

