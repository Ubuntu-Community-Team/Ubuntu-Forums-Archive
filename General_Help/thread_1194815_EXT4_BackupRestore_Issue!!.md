---
title: "EXT4 Backup/Restore Issue!!"
date: 2009-06-23
forum: General Help
---

### Post by cottfcfan on 2009-06-23
If like me you`re constantly pratting with linux till you screw it up, a good restore tool is a must. On EXT3 i used PING which IMO is the best backup tool for ext3.
 Now i`m using EXT4 though, its not yet compatible, so i started using clonezilla.
 PROBLEM!!
When restoring an EXT4 partition, GRUB is not restored properly,
(some type of compatibility problem) so you cannot boot back into your OS.
 I googled the problem, and tried everything, all the usual stuff to restore grub. Nothing worked. In the end new install.
 My advice is when installing on EXT4, keep Boot on its own EXT3 partition, it saves a lot of time and work if you need a restore.
 
ps. I would be interested if anyone else has a solution to this problem?

---

### Post by jimnwal on 2012-07-06
I have two machines one NTSF partition and EXT4 partitions on the hard drives on both machines.  One machine has Windows XP and Ubuntu 12.04--the other has Windows 7 and Ubuntu 12.04.  I find that Acronis True Image 12 will backup the partitions and restore if I use bootable (Acronis) media (CD).  However, the backups of the EXT4 partitions fail using the program within Widows XP.  The EXT4 backups made within Windows 7 will validate as good but restore fails!  The restore works for all partitions if the restore is done outside of Windows, however the restored drive will not boot unless the Grub is repaired using a Live CD and Internet connection.  [COLOR=#800000]

sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update[/COLOR]
[COLOR=#800000]sudo apt-get install -y boot-repair && boot-repair[/COLOR]  

The good thing about using Acronis is that you can expect compression of about 40% and as long as you do not  backup sector by sector or back up free space, you can back up to almost anything that has enough space for the data.  The bad thing is that Acronis is not free.

---

### Post by lisati on 2012-07-06
Old thread closed, a lot can change in three years.
Please start a new thread.

---

