---
title: "CDs almost never mount properly"
date: 2005-09-11
forum: Desktop Environments
---

### Post by orzechowskid on 2005-09-11
I put a CD in the drive and 3 times out of 4, nothing happens.  The drive doesn't even bother spinning up, never mind any icons appearing on my desktop.  I can bring up a console and type 'sudo mount -t auto /dev/cdrom /mnt/cdrom' , and nothing happens; the mount command just sits there doing nothing, and I can't send a Ctrl-C to the terminal to break it.  I don't think it's a problem with the CD drive, since it works fine when I boot into Windows.

Every once in a while though, mounting a CD will work properly, so I don't really know what's going on.  Anyone have any thoughts on what to look at?

thanks in advance.

- Dan

---

### Post by rafakl on 2005-09-11
I dont know if this can change anything, but what about enabling DMA for your CD??

sudo hdparm -d1 /dev/hdc   (or whatever name your cdrom has)

---

### Post by orzechowskid on 2005-09-12
hmm, I don't think that's it.  I just noticed that sometimes my digital camera fails to mount too, so I might have a lower-level problem that affects all block devices.  It's plugged in and I turn it on, and half the time it gets recognized as a mass storage device and half the time nothing at app happens.

Any thoughts?

---

