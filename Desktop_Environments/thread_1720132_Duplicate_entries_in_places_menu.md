---
title: "Duplicate entries in places menu"
date: 2011-04-02
forum: Desktop Environments
---

### Post by Bobhuber on 2011-04-02
I see this posted in several places in the past but no answers. If I use UUID in fstab to mount additional partitions I get duplicate entries for the partitions in the Places Menu.
I can solve the problem by mounting the partitions by Label ( /dev/sdb2  /mountpoint ) but half of the time grub2 will not mount the drive correctly using this method and will change the volume ID (sdb2 becomes sdf2) . ANY help would be appreciated.

---

### Post by Krytarik on 2011-04-02
I have the same behaviour at my system, at least when I tried it that way the last time, running Lucid 10.04, like stated.

But I can workaround that by putting the device specifications like this:
```
**/dev/disk/by-uuid/**107C-26F4  /media/Data     vfat    user,utf8,umask=007,uid=1000,gid=46 0       0

```Hope it works for you too!

Greetings.

---

### Post by Bobhuber on 2011-04-02
> **Krytarik said:**
> I have the same behaviour at my system, at least when I tried it that way the last time, running Lucid 10.04, like stated.

But I can workaround that by putting the device specifications like this:
```
/dev/disk/by-uuid/107C-26F4  /media/Data     vfat    user,utf8,umask=007,uid=1000,gid=46 0       0

```Hope it works for you too!

Greetings.
Thank you very much !! The /dev/disk/by-uuid did the trick.

---

