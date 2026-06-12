---
title: "Restore .img backup file"
date: 2009-02-16
forum: General Help
---

### Post by martin_legion on 2009-02-16
Hi there. 
I have an .img file containing the backup of a complete primary partition of a windows server 2003. I made the image with a software called SelfImage, but I want to learn how to restore it with linux.

I was thinking about restoring it into a secondary hard drive I have in my computer. I guess I should unmount it, then "burn" the img file, and then, put the newpartition in grub and see if it boots, or just put the hard drive in another computer as primary and, again, see if it boots.

The img file is 160 GB (it's not compressed with gzip), so... I'd like to know what to do before I start, so I don't waste a couple of long hours just to see that I did it wrong or something...

Let's say the img is in /media/hd1/file.img and I want to "burn" it into /dev/hdb1 (or /dev/hdb ?).
I guess I could do it with dd, but what parameters should I use...

Any help would be apreciated.
Thanks!

---

### Post by Tim Sharitt on 2009-02-16
If it's a regular disk image (which it may not be) you could write it to a partition with dd (this will erase everything on the partition you are writing to).

```
sudo dd if=/path/file.img of=/dev/sdb1
```

You may want to try to mount it first to make sure you get something meaningful written to the partition.

```
mount -o loop /path/file.img /directory_to_mount_at
```

---

