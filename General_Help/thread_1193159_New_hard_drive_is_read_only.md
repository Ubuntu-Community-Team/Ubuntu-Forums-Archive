---
title: "New hard drive is read only"
date: 2009-06-21
forum: General Help
---

### Post by silentbrad on 2009-06-21
I just installed Ubuntu today, so this is all new to me, but why can't I save to my additional hard drive? I've partitioned, formatted, and mounted the drive, but when I try to save files to it, it says "Permission denied". I've done the partition/format/mount twice now, once with Terminal and once with Partition Editor. Both times gave me the same error message. Any help would be appreciated.

---

### Post by merlinus on 2009-06-21
```

sudo fdisk -l

```will show the partition.

You can then change ownership:

```

sudo chown -R username:username /media/sdb1

```Substitute the actual mountpoint for /media/sdb1 and username with your username.

```

df -h

```will show the mountpoint if you do not remember it.

---

### Post by silentbrad on 2009-06-21
Awesome. That worked perfectly. Thanks dude.

---

