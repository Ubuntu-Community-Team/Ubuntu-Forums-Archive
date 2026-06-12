---
title: "Dapper Won't Boot"
date: 2006-07-04
forum: Desktop Environments
---

### Post by awtomlinson on 2006-07-04
All of a sudden, I can't boot into Dapper Drake.  My grub menu lists only the Windows XP partition.  When I boot with the Dapper install cd, I can see my Ubuntu partitions, but I can't mount them.  I receive the following error:  Unable to mount the selected volume.  error: device /dev/hdax is not removable.  error: could not execute pmount.  Can someone please help?

---

### Post by taurus on 2006-07-04
Did you upgrade your system, especially to the latest kernel, or something?  And if you want to mount your HD from a LiveCD, try (from a terminal)
```

sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/hdb1 /media/ubuntu
(assuming that your Ubuntu is on /dev/hdb1 and you use ext3 filesystem...)

```

---

### Post by awtomlinson on 2006-07-06
I always upgrade my system as soon as updates are available, but I don't remember if a kernel upgrade occurred recently.  At any rate, I am able to mount my hard drives when I use the live cd, but I still can't boot into Dapper, it is not even an option in Grub.  Someone please help!!

---

### Post by awtomlinson on 2006-07-07
Can someone please help me restore Ubuntu Dapper to my Grub boot menu?  Again, if I boot with the live cd, I can mount my Dapper partitions, but I am unable to boot into Dapper, only into XP.

---

