---
title: "Partition paths change at boot"
date: 2008-09-30
forum: Desktop Environments
---

### Post by nife87 on 2008-09-30
Maybe this is an easy question to answer, but I have not been able to find a proper solution for it, so here goes.

I have 3 hard drives installed in my desktop, 2 SATA and 1 IDE, and the Ubuntu installation lies on one of the SATA drives.
To automatically mount the two other drives at boot, I edited fstab and added the necessary lines, where /dev/sda1 is the Ubuntu SATA (ext3), /dev/sdb1 is the other SATA (ntfs), and /dev/sdc1 is the IDE (ntfs).
This works fine in perhaps 2-3 boots, but the next time I boot, the partition paths have suddenly changed?
All three partition paths can change, as I have noticed, so sometimes the 2 extra drives have just switched folder paths, but other times only 1 of them will mount, since the other now points to the Ubuntu drive!
This is one possible other (odd and anoying) configuration, where USATA stands for Ubuntu SATA:
USATA /dev/sdb1
SATA /dev/sdc1
IDE /dev/sda1

Does anyone know how I can solve this? Since it would be nice it the drives would "stay" where they should be for each boot, as otherwise I have to mount one or the both of them manually quite often.
I am running Ubuntu 8.04.1 on a Gigabyte P35-DS3R motherboard (perhaps some silly option in the BIOS that I have misread?). I do not believe the ports, which the two SATA drives are attached to, play a role, since also the IDE change its path just as often as the SATA.

---

### Post by nife87 on 2008-10-01
Bump...

I really need help with this, since I cannot find anyone else with similar issues (but if anyone knows of someone, please redirect me).

---

### Post by sisco311 on 2008-10-01
EDIT:

link:[http://www.cyberciti.biz/faq/linux-finding-using-uuids-to-update-fstab/]("http://www.cyberciti.biz/faq/linux-finding-using-uuids-to-update-fstab/")

mount the partitions by uuid.

to find the uuid of a partition type:
```
sudo vol_id --uuid /dev/sd**XY**
```in a terminal.

edit your fstab and change /dev/sd**XY** to UUID=*the uuid you get from the above command*

Example:
> UUID=92f2be35-c311-4924-877a-d4cc263a7f9d /media/data           ntfs    defaults,umask=007,gid=46        0       0

---

### Post by nife87 on 2008-10-01
Thanks, it works perfectly!

---

### Post by sisco311 on 2008-10-01
Cool!

Please mark the thread solved by selecting 
**Mark this thread as solved** from the [COLOR="Red"]**Thread Tools**[/COLOR].

---

