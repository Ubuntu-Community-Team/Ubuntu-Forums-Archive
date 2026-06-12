---
title: "unity-greeter segfault"
date: 2013-03-12
forum: Desktop Environments
---

### Post by diskover on 2013-03-12
Hello,

I'm experiencing a problem that I can't resolve alone (Usually, I fix my issues from myself, and this is my first post on a ubuntu forum :) ) :
After an upgrade from 10.04 to 12.10, my session freeze (from 30 min to 2 hours after login). I have no other choice to hard reboot my machine in this case.

I found in /var/log/syslog many lines like these (time is just before complete hold)
```
Mar 12 10:23:27 jbouchet kernel: [ 1663.695834] unity-greeter[3579]: segfault at 18 ip 00007f70ab839616 sp 00007fff61aeaa80 error 4 in libxklavier.so.16.2.0[7f70ab829000+19000]
```

For information, I have an Nvidia Geforce GT 220, and run the "nouveau driver" provided by ubuntu community.

Have you any suggestion ?

---

### Post by diskover on 2013-03-13
Hi all,

Ubuntu-fr.org give me the answer to my problem : the "nouveau driver" isn't applicable in my case, so I must use Nvidia driver (nvidia-current-update).

Bye.

---

