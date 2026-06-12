---
title: "Merge two partitions"
date: 2006-01-18
forum: General Help
---

### Post by rohrbold on 2006-01-18
Hello together,

I'm currently developing something and use VMWare for testing of multiple operating systems. Unfortunately disk space is rare on this machine. But I have an unused Partition with SuSE 10 which has about 10GB of allocated space that I do not really need any more. Does anybody know if it is possible and at no high risk to merge the SuSE partition to my existing Ubuntu / partition?
My /etc/fstab says the following:

proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /suse/home      ext3    defaults        0       2
/dev/hda1       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

So I don't need /dev/hda3 any more.
What can I do? Any suggestions?

Martin

---

### Post by slashem on 2006-01-19
Use a livecd and qparted/gparted. Take backups!!!!

---

