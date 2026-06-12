---
title: "Ubuntu - no access to partition"
date: 2009-01-26
forum: General Help
---

### Post by kneewax on 2009-01-26
I am not sure quite what I did, I have been trying to revover data from an ntfs disk.  Somehow something I have done has screwed up the permissions on my data partition on my internal SATA drive.  

I can still mount the partition but I get the attached message box if I try to read or write to it.

Is there an easy way to allow my user account access to this disk again?

TA.

---

### Post by kneewax on 2009-01-26
Image attached this time (clearly I am having  a bad day!)

---

### Post by caljohnsmith on 2009-01-26
If your sda2 NTFS partition is mounted say on /media/sda2 for example, you could change the ownership of it to yourself with:
```
sudo chown $(whoami):$(whoami) /media/sda2
```
That will give you ownership of the folder. If you still don't have enough permissions to write to it, you can change the permissions with:
```
sudo chmod 755 /media/sda2
```
Then you should be able to read/write to that partition without any problems. Let me know how that goes or if you run into problems.

---

