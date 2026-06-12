---
title: "/etc/cron.hourly/ is empty"
date: 2005-05-17
forum: Desktop Environments
---

### Post by stepore on 2005-05-17
just checking, should /etc/cron.hourly/ be empty?

root@ubuntu-shine:/home/shine # ls -la /etc/cron.hourly/
total 16
drwxr-xr-x    2 root root 4096 2005-04-08 19:24 .
drwxr-xr-x  123 root root 8192 2005-05-16 23:01 ..
-rw-r--r--    1 root root  102 2004-09-03 13:37 .placeholder

cheers,
jb

---

### Post by camp on 2005-05-17
Hi there,

Probably not the most elaborated answer... but mine is empty too.   ;-) 

/JC

---

### Post by JonahRowley on 2005-05-17
Nothing is scheduled to run hourly from **/etc/cron.hourly/**.  This is nothing to be alarmed about.

---

### Post by stepore on 2005-05-17
[QUOTE=JonahRowley]Nothing is scheduled to run hourly from **/etc/cron.hourly/**.  This is nothing to be alarmed about.[/QUOTE]
 just checking. i'm used to something running hourly when i was running mandrake.

cheers.

---

