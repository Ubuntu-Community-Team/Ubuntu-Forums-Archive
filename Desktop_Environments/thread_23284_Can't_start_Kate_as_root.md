---
title: "Can't start Kate as root"
date: 2005-04-01
forum: Desktop Environments
---

### Post by timelord726 on 2005-04-01
For the life of me, I can't get Kate to start as root user (using sudo).  Here's the console output.

```
danny@danny-kubuntu:~$ sudo kate
Error: "/var/tmp/kdecache-danny" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
kate: ERROR: Communication problem with kate, it probably crashed.
``` 

What's going on?

Thanks!

---

### Post by J. S. Jackson on 2005-04-01
Same exact error here.

---

### Post by bailout on 2005-04-01
Same problem. I just use kwrite instead. I still get some errors on the konsole screen but it works.

---

### Post by apokryphos on 2005-04-01
It shouldn't really be doing that; I recommend someone filing a bug report, as it is in Main.

---

### Post by GoldBuggie on 2005-04-01
I've noticed that using "kdesu" instead of "sudo" works fine.

---

### Post by Pointwood on 2005-04-14
Yeah, I can confirm that problem:
> pointwood@milliways:/$ kate
kate: ERROR: Communication problem with kate, it probably crashed.

As GoldBuggie says, "kdesu kate", works.

---

