---
title: "Ext3 – bad for Solid State Drives?"
date: 2009-02-17
forum: General Help
---

### Post by cyclone5uk on 2009-02-17
Everyone knows that flash-based SSD’s only have a finite number of writes before the Flash-memory cells die. Admittedly, many thousands – but we are always told that limiting the number of writes is generally a good idea and will ultimately make your SSD last longer.

I was told that because Ext3 is a journaling file system it is not as healthy for an SSD as Ext2 would be.

I am about to get a brand new SSD for my netbook and want to set up the most SSD-healthy install I can.

I was wondering what other people though of this? Does the journaling really create enough writes to make it significant?

---

### Post by biovore on 2009-02-17
For normal users..  I don't really think it matters.

---

### Post by sdennie on 2009-02-17
By default, ext3 commits the journal to disk every 5 seconds.  That's a lot of small independent writes.  You can still use ext3 but, you will want to tune it to be more appropriate for an SSD that is not vulnerable to data loss from a power outage.  This guide should get you moving in the right direction: [  HOWTO: Decrease disk activity]("http://ubuntuforums.org/showthread.php?t=839998")

---

### Post by dcstar on 2009-02-18
> **cyclone5uk said:**
> Everyone knows that flash-based SSD&#8217;s only have a finite number of writes before the Flash-memory cells die. Admittedly, many thousands &#8211; but we are always told that limiting the number of writes is generally a good idea and will ultimately make your SSD last longer.

I was told that because Ext3 is a journaling file system it is not as healthy for an SSD as Ext2 would be.

I am about to get a brand new SSD for my netbook and want to set up the most SSD-healthy install I can.

I was wondering what other people though of this? Does the journaling really create enough writes to make it significant?

The following options in your fstab file will reduce writes to any EXT2/3 filesystem:

```
noatime,nodiratime
```

IMHO a journaling filesystem is more valuable for mechanical drives where cached and unwritten data takes time to get to the physical media and this can be interrupted by a power outage, with a solid state drive this risk factor should be reduced - especially if you have a battery powered device. If your netbook has a battery, use EXT2 with those fstab options.

Be aware that each SSD "write" (of even a small size) can involve a significant area of the memory on the SSD chip(s) depending on their design. A small file write of a few bytes could actually trigger off a physical write of an area many (many) times that magnitude.

---

### Post by sdennie on 2009-02-18
> **dcstar said:**
> The following options in your fstab file will reduce writes to any EXT2/3 filesystem:

```
noatime,nodiratime
```


This shouldn't be needed in Hardy and later releases.  The kernel is configured to default supported fs types to use relatime:

$ grep RELATIME /boot/config-`uname -r`
CONFIG_DEFAULT_RELATIME=y
CONFIG_DEFAULT_RELATIME_VAL=1

Relatime is very similar to noatime but only updates atime when ctime or mtime are updated.  It also implies the same behavior for directories (so, no need for nodiratime).

> 
IMHO a journaling filesystem is more valuable for mechanical drives where cached and unwritten data takes time to get to the physical media and this can be interrupted by a power outage, with a solid state drive this risk factor should be reduced - especially if you have a battery powered device. If your netbook has a battery, use EXT2 with those fstab options.


I generally agree.  I haven't compared performance between ext2/ext3/ext4 but, it still may be worth using a journaled filesystem with very slow journal commits if, for instance, the performance of ext4 is significantly better than ext2 (which it probably is).

Edit:
Actually, it appears the RELATIME behavior I described above only applies to Hardy.  Strange.

---

### Post by CKDewey on 2009-02-18
"With current technologies write endurance is not a factor you should be worrying about when deploying flash SSDs for server acceleration applications - even in a university or other analytics intensive environment. "

- [http://www.storagesearch.com/ssdmyths-endurance.html](http://www.storagesearch.com/ssdmyths-endurance.html)

Short answer: A modern SSD will outlast the useful lifetime of its host (especially a netbook).

--
Tom

---

### Post by HavocXphere on 2009-02-18
I read in some or other kernel changelog that they did some work to make it more suitable for SSD. If there was a serious issue with the SSD life they would have fixed it with those optimisations.

I'd treat it like a wear&tear issue with car tires: Accept it as a fact of life.

Besides...by the time your SSD goes bad, the world will have moved onto 5TB drivers & you'll probably replace it before it goes bad anyway.

---

### Post by cyclone5uk on 2009-02-25
Thanks for the info - that's all really helpfull stuff.

---

