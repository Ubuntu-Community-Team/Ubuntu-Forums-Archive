---
title: "Change UUID"
date: 2011-12-07
forum: Development CD/DVD Image Testing
---

### Post by caka2604 on 2011-12-07
I intend to do a iso setup file  ubuntu that mount hard drive as  read-only after installing (i'm working on  alternate CD and  remastersys). I try by adding the "ro" to the fstab,  put it at  "UUID:......" . But how to take over other machines, it is automatically  set to do so,  the UUID is different when use other machine ? Can  someone help me ?

---

### Post by Lars Noodén on 2011-12-08
If by other machines you mean hard drives or partitions, then yes the UUID is different for each partition.  You can see all the ones you have mounted using [blkid](http://manpages.ubuntu.com/manpages/precise/en/man8/blkid.8.html)

---

