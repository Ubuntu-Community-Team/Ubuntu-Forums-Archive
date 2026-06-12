---
title: "ubuntu 8.04 and auto drive mounting??"
date: 2008-05-10
forum: Desktop Environments
---

### Post by baking666 on 2008-05-10
Hello All :-)

I have links on my desktop that point to my data drive...in earlier versions of ubuntu my data drive (ext3) would mount at boot time and so my desktop links would become active as well.

But with 8.04 none of my other system or data partitions are auto mounted and so my links on my desktop are invalid :-(

I have to go to my computer icon on desktop and click on my data partition to mount it and then the links on my desktop become active....

My question is how do i auto mount partitions at boot time??

I've seen ref's to using entries in the mtab file and adding them to fstab but this doesn't work for me :-( I get permission problems when I try to open the partition ..which incidentally doesn't mount at bootup when I asked it too...well I think I did...here is the entry:

/dev/sda5 /media/MyData ext3 rw,auto,nosuid,nodev,uhelper=hal 0 0

I cut this from the mtab file and added 'auto' but no go :-(

In fact it seems as tho ubuntu has side stepped the fstab file somewhat and is using some custom method for dynamic drive mounting etc.....

If this is the case I'd like to set an option in the drive icon properties to auto mount on bootup :-)

---

### Post by Rocket2DMn on 2008-05-10
Try making the entry
```
/dev/sda5 /media/MyData ext3 defaults 0 0
```
Alternatively you can use UUIDs similar to as seen in entries earlier in the file, just check
```
sudo blkid
```
More info on fstab here: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

