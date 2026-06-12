---
title: "Slow Gnome Start"
date: 2006-01-09
forum: Desktop Environments
---

### Post by boxy on 2006-01-09
Hey,

I just recently switched to Ubuntu 5.10 and i'm having problems with gnome when I login via GDM.  It takes at least 8 minutes to load Gnome,  I was recently trying to switch to ALSA instead of ESD and that fixed that problem but i couldn't get ALSA to work so now im back with ESD.  Any suggestions? :smile: 

Thanks.

---

### Post by boxy on 2006-01-09
Bump, common guys I **know** someone is just eager to help heh :p

Edit: btw here's my /etc/esound/esd.conf
```
[esd]
auto_spawn=0
spawn_options=-terminate -nobeeps -as 5
spawn_wait_ms=0
# default options are used in spawned and non-spawned mode
default_options=-as 5

```

---

