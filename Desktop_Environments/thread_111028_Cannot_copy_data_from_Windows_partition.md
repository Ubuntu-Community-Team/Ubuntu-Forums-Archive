---
title: "Cannot copy data from Windows partition"
date: 2006-01-01
forum: Desktop Environments
---

### Post by diffuser78 on 2006-01-01
I have a duat boot with Ubuntu and Win XP. I recently purchased an external hard drive and have formatted it using FAT32. I want all my data from windows partition on the new hard drive. When I try in Ubuntu it just wont copy it.

Am i missing on something ? What is the right way of opening win xp in ubuntu and copying stuff from win to either ubuntu or new hdd.

Thanks guys

---

### Post by zoiks on 2006-01-01
It could be a permission problem.  You may have to perform the copy as root or have the ntfs and vfat partitions remounted with general user access.  Also, why do you want "all" of your xp data on a vfat partition?  You aren't planning on going from ntfs to vfat in XP are you?  (I don't think that's a good idea)

---

### Post by aysiu on 2006-01-01
See the fourth link of my sig--same instructions apply for partitions and external hard drives.

---

### Post by diffuser78 on 2006-01-01
[QUOTE=zoiks]It could be a permission problem.  You may have to perform the copy as root or have the ntfs and vfat partitions remounted with general user access.  Also, why do you want "all" of your xp data on a vfat partition?  You aren't planning on going from ntfs to vfat in XP are you?  (I don't think that's a good idea)[/QUOTE]

NO I am making my external HDD as vfat so that i can write it to using both win xp and ubuntu. I have certain media files on my win partition and I need to take a back up on my external HDD. 

Thanks for your help though!!1

---

### Post by tedk on 2006-01-01
When I installed Ubuntu Breezy, my Windows partitions (described below they are C:, BootMagic, and F:) appeared as icons on my desktop, apparently mounted by default. 

I'm using PartitionMagic and  have four primary partitions (the BootMagic partition (FAT), C: (NTFS), /boot (ext3, where GRUB is), and an extended parition that contains F: (FAT32), swap, / (ext3), and /home (ext3)).

I can copy from F: without being root. I can access C: and the BootMagic partition as root and routinely copy from C: and chown, chgrp to a non-root user. 

This is the one internal drive not an external one. I don't think I really needed the F:. This partitioning scheme is one left over when I dual booted Red Hat 9 a while back; I  just recently moved to Ubuntu.

 -Ted

---

### Post by diffuser78 on 2006-01-02
[QUOTE=aysiu]See the fourth link of my sig--same instructions apply for partitions and external hard drives.[/QUOTE]

Your tutorials are nice and very easy to implement.

---

