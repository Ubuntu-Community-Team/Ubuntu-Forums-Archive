---
title: "Microsoft LifeCam Doesn't Work After Reboot"
date: 2011-07-18
forum: Desktop Environments
---

### Post by Grakul on 2011-07-18
Hi, All

I have a Microsoft LifeCam webcam. It works great under Ubuntu 10.04... Until I reboot. After the reboot, Cheese reports no device connected. I have to get down behind my PC, unplug the webcam and plug it in again. Then it works... until the next reboot.

Anybody have any idea why?

Cheers
Grakul

---

### Post by smurphy_it on 2011-07-18
I'd check your logs for errors.  
```
sudo cat /var/log/syslog
```

---

