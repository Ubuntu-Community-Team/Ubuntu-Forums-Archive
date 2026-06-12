---
title: "Minimum recommended size for '/root' partition? Please help!"
date: 2009-04-09
forum: General Help
---

### Post by Pipps on 2009-04-09
I have reinstalled Ubuntu and noticed that the fresh installation occupies **2.50Gb** of disk space. This is great!

I have partitioned my local drive as follows:
- sda1 (primary) '/boot' 50.0Mb
- sda2 (primary) '/root' 10.0Gb (Contains '/', '/usr', '/tmp' etc)
- sda3 (primary) '/home' [all remaining disk space]
- sda4     -     '/swap' 2.0Gb (I have 1Gb of onboard RAM).

**Would it be ok to re-partition the 10.0Gb drive into a smaller 3.9Gb size?**

As my fresh Ubuntu installation is currently 2.50Gb, and as I will not ever install any more programmes or add other users, **is my installation size on disk ever like to increase in size in the future**?

---

### Post by askreet on 2009-04-09
You should leave room for log growth in /var.  If you're really not going to install any other programs, then that's probably okay.  I would go with 3GB.

I'm a bit confused, /root and / are different.  I think you mean to say / is 3.9G?  You don't need /root as a separate partition and most Ubuntu users never put anything there.

Also, Gb and GB arn't the same, though I'm sure you mean GB (Gigabytes) not Gb (Gigabits).

HTH,
askreet

---

### Post by Pipps on 2009-04-09
Thank you for the excellent advice!

1. I will stick to GBs in the future!

2. You're right - I meant '/' rather than '/root'.

May I ask, are there any other factors which would cause 'log growth' in /var?

---

### Post by askreet on 2009-04-09
It depends on what you're running.  For example, a heavily visited Apache server can generate 800M of access_log a month, or more.

---

### Post by Pipps on 2009-04-09
I don't even know what an Apache server is, so hopefully I should be ok then! :p

---

### Post by Slim Odds on 2009-04-09
You have to be careful, depending on the types of things that you intend to do with the computer.

As was mentioned, /var will grow some.

Also, /tmp can actually require a lot of space if you do things that need a lot of temporary space (like maybe encoding DVD's).

Also, 50MB for the boot partition may be a little small.

---

### Post by Pipps on 2009-04-09
My boot sector with running just Ubuntu is currently 29.0MB.

Is it likely to grow at any stage in the future as well?

---

### Post by Slim Odds on 2009-04-09
> **Pipps said:**
> My boot sector with running just Ubuntu is currently 29.0MB.

Is it likely to grow at any stage in the future as well?

Next time there is a kernel update, it will go there along with the old kernel.

You can delete the old kernel, but they leave it there as a backup in case you have problems with the new one.

I'd just make the /boot partition a little bigger. 100M would only be another 50M (that's not much).

---

### Post by Pipps on 2009-04-10
You're right. Another 50MB is nothing to fuss about!

Thanks for the advice!

---

