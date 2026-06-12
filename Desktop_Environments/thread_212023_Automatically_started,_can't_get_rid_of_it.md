---
title: "Automatically started, can't get rid of it"
date: 2006-07-09
forum: Desktop Environments
---

### Post by HAARP on 2006-07-09
My RAID-array won't work properly. Kay then, I'd like to try raidtools instead of mdadm.

The problem is, mdadm is being started automatically. Right after the kernel loads, but before init starts. I deinstalled the package already, deleted its config files, but it's still being started.
Where are the entries?


I've discovered there are some multiple-disk (md) modules in **/lib/modules/2.6.15-25-k7/kernel/drivers/md**.
Can I just delete this directory and hope it won't load?

---

### Post by mlind on 2006-07-09
> **HAARP said:**
> My RAID-array won't work properly. Kay then, I'd like to try raidtools instead of mdadm.

The problem is, mdadm is being started automatically. Right after the kernel loads, but before init starts. I deinstalled the package already, deleted its config files, but it's still being started.
Where are the entries?


I've discovered there are some multiple-disk (md) modules in **/lib/modules/2.6.15-25-k7/kernel/drivers/md**.
Can I just delete this directory and hope it won't load?

NO!!

Use module blacklisting feature. Add unwanted module to /etc/modprobe.d/blacklist like this
```

blacklist *name_of_badmodule*

```

---

### Post by HAARP on 2006-07-09
Kay, that's why I asked ;)

I blacklisted every single module in md, but it's still being loaded. So it's not the modules which are responsible for it.
It's being loaded right after the kernel boots, but before init loads. But HOW?

---

### Post by mlind on 2006-07-09
What md modules do load?

---

### Post by HAARP on 2006-07-09
md_mod
raid0
dm_mod
dm_mirror

Also, my array is started twice (RAID0), md0 and md1. I don't get why...
It works fine until I write some data on it. After rebooting the partitions and partition tables randomly dissapear on both drives and the array becomes unusable till I re-partitionate the drives and initialize the array again.
That's why I want to try raidtools2, but I can't get rid of mdadm..

The modules are still loaded, regardless of the blacklisting.

---

### Post by HAARP on 2006-07-10
*bump* :-$ 

Seriously, You need more threads in the forum overview per page. Threads get buried too fast :rolleyes:

---

### Post by mlind on 2006-07-10
So you tried adding these entries to /etc/modprobe.d/blaclist ?
```

blacklist md_mod
blacklist raid0
blacklist dm_mod
blacklist dm_mirror

```

Does /etc/mdadm contain some configuration files?
Does /etc/init.d/mdadm-raid get invoked on startup sequence?

---

### Post by HAARP on 2006-07-10
Yep, it's all blacklisted.

**/etc/mdadm** is empty. It never created any configuration files in there.
**/etc/init.d/mdadm*** doesn't exist.

The module/application/whatever is started even before init, so it wouldn't matter anyway. I just can't seem to find out HOW :-s

---

### Post by HAARP on 2006-07-12
After the kernel update yesterday, it's gone now.

---

### Post by mlind on 2006-07-12
> **HAARP said:**
> After the kernel update yesterday, it's gone now.

Good to know. You should remove those blaclisted entries you already didn't.

---

### Post by HAARP on 2006-07-12
Already done. Thanks.

---

