---
title: "[debian] dpkg-reconfigure command does not work"
date: 2008-11-08
forum: Debian
---

### Post by hanzj on 2008-11-08
As per [http://wiki.debian.org/BootProcessSpeedup](http://wiki.debian.org/BootProcessSpeedup)```

aptitude install dash
dpkg-reconfigure dash
```


i tried running the dpkg-reconfigure dash command, but I get > 
bash: dpkg-reconfigure: command not found

---

### Post by basenvironment on 2008-11-08
did you run it as root?

---

### Post by hanzj on 2008-11-08
Yes, I tried running it sudo.

---

### Post by bwhite82 on 2008-11-08
dpkg-reconfigure is in the package 'debconf'. Do you have it installed?

---

### Post by wolfen69 on 2008-11-08
> **hanzj said:**
> Yes, I tried running it sudo.

do you have sudo enabled? type: ```
su
``` to become root then do the command.

---

### Post by K.Mandla on 2008-11-09
Moved to Debian subforum.

---

