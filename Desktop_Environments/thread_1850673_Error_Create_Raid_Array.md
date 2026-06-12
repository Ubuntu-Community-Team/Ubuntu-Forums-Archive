---
title: "Error Create Raid Array"
date: 2011-09-27
forum: Desktop Environments
---

### Post by F35 on 2011-09-27
I am using the gui "Disk Utility".  It looks simple enough.  Disk Utility shows the 3 2TB drives I want to build into 1 Raid 5 disk.  However, when I go to FILE | CREATE RAID and am presented with all the drives, the 3 drives are grayed out and the message says "no free space".   I have attempted to format the drive, format the partion, delete the partions, mount, unmount.  But in the end, I get Error Creating Raid Array.  Looks so easy to use the disk utility gui and get this setup.   What am I missing?  Wrong format for the drives?  What?

---

### Post by sarkiss on 2013-01-03
I was having similar issues and the only way I could proceed was to  delete all existing partitions and let *Disk Utility* create one. But  the partition that *Disk Utility* created was giving *WARNING: The partition is misaligned by xxx bytes *messages similar to the one described at [http://askubuntu.com/questions/30071/the-partition-is-misaligned-error-in-disk-utility-should-i-repartition](http://askubuntu.com/questions/30071/the-partition-is-misaligned-error-in-disk-utility-should-i-repartition)

You can still create RAID using mdadm command line utility as described [here]("https://raid.wiki.kernel.org/index.php/RAID_setup"). However, if you need a GUI, the only other option I could find is [Webmin]("http://www.webmin.com/"). I tried it and I'm very happy; see [Using Webmin for Linux RAID]("https://plus.google.com/u/0/106416594206743737486/posts/2MwKjSoivBR"). I don't know why Webmin is not concluded in the standard Ubuntu or CentOS distribution, but it has RPM and Debian packages available.

Hope this helps.
[]("http://askubuntu.com/questions/30071/the-partition-is-misaligned-error-in-disk-utility-should-i-repartition")

---

### Post by F35 on 2013-01-12
Thanks, sarkiss, for the tip.  I may give webmin a try, especially since it might notify me of raid issues...hadn't been able to figure that out using mdadm.  

Since my original issue, I have learned how to use mdadm.  It wasn't that difficult, it is just when I first started considering RAID, it seemed like a gui like "Disk Utility" would work.  "Disk Utility" was just too problematic and I switched.

---

### Post by rubylaser on 2013-01-13
> **F35 said:**
> Thanks, sarkiss, for the tip.  I may give webmin a try, especially since it might notify me of raid issues...hadn't been able to figure that out using mdadm.  

Since my original issue, I have learned how to use mdadm.  It wasn't that difficult, it is just when I first started considering RAID, it seemed like a gui like "Disk Utility" would work.  "Disk Utility" was just too problematic and I switched.

If you don't mind using the command line, mdadm can easily be setup from partitioning (properly aligned), to [mdadm]("http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm"), to [SMART alerting]("http://zackreed.me/articles/45-how-do-i-know-if-my-hard-drive-is-failing"), [setting up a UPS]("http://zackreed.me/articles/40-ups-protect-your-files"), and [spinning down idle disks]("http://zackreed.me/articles/60-spin-down-idle-hard-disks").  I have all of these topics covered on [my site]("http://zackreed.me/").

---

