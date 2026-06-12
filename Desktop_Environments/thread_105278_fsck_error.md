---
title: "fsck error"
date: 2005-12-18
forum: Desktop Environments
---

### Post by phiz on 2005-12-18
/home: recovering journal

fsck. ext3: unable to get superblack flags on /home

[FAIL]

[COLOR="Red"]fsck[/COLOR] failed please repair manually

Control -D will exit etc. 

Ubuntu also randomly goes into read-only mode sometimes causing me to have to reboot the system. Does anyone know the way to fix this problem? Thankyou.

---

### Post by poptones on 2005-12-18
It sounds like you are having catastrophic media failures (ie your hard drive is hosed). is this /home partition on your main drive along with the root partition? I'm guessing it is because you said you sometimes have to reboot due to the system becoming read only.

Mount with a live cd and run fsck -y on each of your partitions. I would strongly suggest you back up anything valuable asap and certainly before running that fsck.

I would also suggest you visit the website of your hard drive manufacturer (ie maxtor, seagate, wd) and download their bootable hard drive diagnostic tool. Use that to run a comprehensive test of your drive and see what it finds...

---

