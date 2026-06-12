---
title: "Disable/Abort periodic fsck?"
date: 2006-04-21
forum: Desktop Environments
---

### Post by aleitner on 2006-04-21
Hi all,

first of: thanks for the great distribution. You guys rock in so many ways!

I have a little itch though that I don't know how to scratch properly: every so and so often Ubuntu will perform a fsck on my main harddisk before regular bootup. Now, if you have to give a talk but you cannot because your computer decided to do a peridodic safety check that can be quite a problem. Of course one should prepare in time and then issues like this are not a problem. But you know how life is, somtimes you are in a hurry and you have to just play along.

Anyway, now I would see two ways out:
* A way to safely abort the check and delay it until next reboot.
* A way to disable the peridodic checks completely.

Can anybody point me towards any of these ways?

many thanks in advance,
Andreas

---

### Post by codejunkie on 2006-04-21
[QUOTE=aleitner]Hi all,

first of: thanks for the great distribution. You guys rock in so many ways!

I have a little itch though that I don't know how to scratch properly: every so and so often Ubuntu will perform a fsck on my main harddisk before regular bootup. Now, if you have to give a talk but you cannot because your computer decided to do a peridodic safety check that can be quite a problem. Of course one should prepare in time and then issues like this are not a problem. But you know how life is, somtimes you are in a hurry and you have to just play along.

Anyway, now I would see two ways out:
* A way to safely abort the check and delay it until next reboot.
* A way to disable the peridodic checks completely.

Can anybody point me towards any of these ways?

many thanks in advance,
Andreas[/QUOTE]
you can press ctrl+c to cancel some tasks when booting, but i've never tried this when it was checking root file system so i don't know if this will work.

you can disable it by editing the /etc/fstab file and change the line containing the root file system

example:
```
/dev/hdb3       /               ext3    defaults,errors=remount-ro 0       1
```
by changing the 1 at the end of the line to 0 will disable the check
```
/dev/hdb3       /               ext3    defaults,errors=remount-ro 0       0
```

---

### Post by dmizer on 2006-04-21
thank you.  this worked for me.  drives me nuts because i restart my box everyday for work (can't leave it run through the night).

---

