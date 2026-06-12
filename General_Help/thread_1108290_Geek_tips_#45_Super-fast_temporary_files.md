---
title: "Geek tips #45: Super-fast temporary files"
date: 2009-03-27
forum: General Help
---

### Post by UranUtan on 2009-03-27
More Linux tips every geek should know
[http://www.tuxradar.com/content/more-linux-tips-every-geek-should-know](http://www.tuxradar.com/content/more-linux-tips-every-geek-should-know)

[COLOR="Red"]**Question:**[/COLOR] I would like to create this Ram disk (as suggested in the quote below) automatically each time Ubuntu boots. Can you please show how to do?

Thanks in advance

> #45: Super-fast temporary files

Remember the old days of RAM disks? Well, Linux has them too! If you've never tried them, a RAM disk is a virtual filesystem that runs entirely from your PC's main memory, which means it's lightning fast to read and write anything you want.

How much space you choose to allocate to your RAM disk is down to how much RAM you have and how much you plan to use it - if you have 1GB of RAM, you can easily spare 64MB for a ramdisk; if you have 2GB you can probably spare 256MB, and if you're lucky enough to have 4GB then you can easily stretch your RAM disk legs with 1GB.

Here's how to set up a 64MB disk - just change the 65536 for the size you want:

mkfs -t ext3 -q /dev/ram1 65536
mkdir -p /ramdisk
mount /dev/ram1 /ramdisk -o defaults,rw

Alternatively, a reader suggested you could also try using tmpfs, like this:

mkdir /ramdisk
mount none -t tmpfs -o size=256M /ramdisk

That will allocate 256MB of space to your RAM disk. If you skip the "-o size=256M" part, half your RAM will be used by default.

---

