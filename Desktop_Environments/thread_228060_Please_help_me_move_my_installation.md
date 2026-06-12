---
title: "Please help me move my installation"
date: 2006-08-02
forum: Desktop Environments
---

### Post by apanloco on 2006-08-02
I need to move the whole root filesystem to another drive, and boot that one. Let's say I mount the new disc on /mnt/new. Is this OK:

cp -xR / /mnt/new/

Then /mnt/new/dev will be empty. Can Dapper boot a drive with an empty /dev/? (Gentoo can; it says there's a problem with /dev and tells you how to fill it with defaults. Will Dapper do the same?)

Thanks a lot,
BR/D

---

### Post by aysiu on 2006-08-02
Have you thought of using [PartImage](http://www.psychocats.net/ubuntu/partimage.html)?

---

### Post by Dubbayoo on 2006-08-02
I would try cpio.

[http://hacks.oreilly.com/pub/h/2504](http://hacks.oreilly.com/pub/h/2504)

---

### Post by apanloco on 2006-08-02
The problem is that my current installation is on a virtual RAID5 device, consisting of 4 harddrives, which I want to move to a single non-raided device. I have done a quick search and it seems that PartImage does not work correctly with Virtual devices like md and lvm. Otherwise, it would have been perfect.

BR/D

---

### Post by apanloco on 2006-08-02
cpio, perfect, thanks,

BR/D

---

### Post by apanloco on 2006-08-02
Should I run the cpio/find combination on /dev also? I think there are files in /dev that are vital to booting. I can't find an answer to that... Most files in dev should be dynamically created by udev, but all arn't right?

BR/D

---

