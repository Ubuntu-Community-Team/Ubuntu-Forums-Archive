---
title: "Ubuntu live CD for maintance (HD backup)"
date: 2008-12-16
forum: General Help
---

### Post by slon45 on 2008-12-16
One of my HDs died so I decided to use an alternative (call it C). Unfortunately, it still has an OS on it and some files I would like to keep. I have a drive (call it D) with a bit of space on it that can hold the documents I want to keep before I do a fresh install onto it. Unfortunately, the OS there is corrupt and really cannot boot. So, I booted up using a Ubuntu liveCD that I had (it's what I'm using now). I was very happy to see that I could see both C and D! Unfortunately, whenever I try to mount them using the linux GUI, it says it cannot mount because access is denied since NTFS is in use.

Yes, it has NTFS. However, only C has the corrupt OS on it. D is just an NTFS disk used for storage; it has no OS on it. So, how can I mount both C and D to transfer some files from C to D?

It also says it indicates an unclean shutdown of the disk. Yeah, because the system is screwed up and barely, if ever, starts. Of course I can't shut it down. If I could, I would just go into windows and copy the files I need.

---

### Post by chrisamiller on 2008-12-16
If your NTFS volume is dirty (because it wasn't shut down properly), then you're going to need to repair the filesystem before trying to mount it with NTFS-3g under Ubuntu. There are several windows-centric boot disks/liveCDs that will do what you need.  Here's a start:

[http://www.google.com/search?hl=en&q=+boot+disk+ntfs+repair&btnG=Search](http://www.google.com/search?hl=en&q=+boot+disk+ntfs+repair&btnG=Search)

---

### Post by jerome1232 on 2008-12-16
You could use ntfsfix, just (while on live cd) install ntfsprogs and then run ntfsfix on the partitions.

Of course change /dev/sdxx to your real partitions, if you need help with figuring out which drive is which post the output of 'sudo fdisk -l' that's a small letter L not the number 1

```
sudo apt-get install ntfsfix
sudo ntfsfix /dev/sda1
sudo ntfsfix /dev/sdb1
```

---

### Post by slon45 on 2008-12-16
I got lucky, started the windows installation and shut it down. Now all drives are accessible except for one. Then again, that drive wasn't accessible to begin with, except with my laptop. Anyone know why? It is a 1TB treckstor external drive connected via USB. It's new. And I was able to access it via a laptop, but not my desktop. It would be an enormous help since it is totally clean. Anyone have any idea?

---

### Post by slon45 on 2008-12-16
One more thing. I wanted to delete some files from one of the non-system drives. I click delete and the file disappears, but the drive is no less occupied. I deleted a 6-gig file I didn't need, I check the drive free space, and it is still the same. My trash bin appears empty.

Found it. It was a hidden folder located on the drive from which I deleted the files.

---

### Post by slon45 on 2008-12-16
Okay, Windows is running again on the other HD. Unfortunately, I still cannot detect the 1TB external HD. Feels like my USB port is dead or something.

---

### Post by jerome1232 on 2008-12-16
With the drive plugged in can you post the output of
```
lsusb
sudo fdisk -l
```

---

