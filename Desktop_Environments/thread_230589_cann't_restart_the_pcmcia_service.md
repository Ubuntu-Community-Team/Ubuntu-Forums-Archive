---
title: "cann't restart the pcmcia service"
date: 2006-08-06
forum: Desktop Environments
---

### Post by zjcim on 2006-08-06
```
joey@ubuntu:~$ sudo /etc/init.d/pcmcia restart
 * Linux >= 2.6.13-rc1 requires pcmciautils instead of pcmcia-cs
```

my kernel is 2.6.15-26-386

---

### Post by ciscosurfer on 2006-08-06
Try installing pcmciautils```
sudo aptitude update && sudo aptitude install pcmciautils
```Does that do the trick?

---

