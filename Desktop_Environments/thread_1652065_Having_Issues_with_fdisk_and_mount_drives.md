---
title: "Having Issues with fdisk and mount drives"
date: 2010-12-24
forum: Desktop Environments
---

### Post by Sugi on 2010-12-24
I am having issues with my sda drive within fdisk, and I think this is preventing my sdb drive from auto mounting.

> /de/sda1
Partition 1 does now end on cylinder boundary

But I read online that this caused by Window's 7 installation, which I am currently dual-booting.  Though, the problem is as of today my sdb won't mount correctly.

```
$ sudo mount /dev/sdb1 /mnt/sdb1
mount: /dev/sdb1 already mounted or /mnt/sdb1/ bus
```

The issue is sdb1 doesn't mount right away.  It's taking like 5 minutes to mount and every reboot this happens.  What is causing my sdb drive to take so long?

Reference:
Windows 7 Causes error does not end on cylinder boundary.
[http://prefetch.net/blog/index.php/2009/09/12/why-partition-x-does-now-end-on-cylinder-boundary-warnings-dont-matter/](http://prefetch.net/blog/index.php/2009/09/12/why-partition-x-does-now-end-on-cylinder-boundary-warnings-dont-matter/)

Sugi

---

### Post by Sugi on 2010-12-26
After the drive finally mounts it's self, it runs ok...  I am unsure of what is still causing this.

Sugi

---

