---
title: "Need Help with Partimage questions"
date: 2006-08-23
forum: Desktop Environments
---

### Post by Gerry Atric on 2006-08-23
Apologies for reposting this. Previously posted in Beginners Forum but didnt get ant answers and it is especially relevant after the X server problems we have all been having.

I am looking for advice in regards to using Partimage to back up the Dapper 6.06 installation to another partition and then restore it to the original hard disk partition. I am using the System Rescue Disk. Could a knowledgeable person please check the following and correct mistakes/offer solutions/

1.When backing up with the System Rescue Disk it is necessary to mount the partition that is being used to store/receive the backup image, into memory.
2.Is this the case when restoring the backed up image, does the partition that is to Receive the stored backup image need to be mounted into memory to receive the backed up image?

Save: Dapper system is on part sdb8 Spare storage partition is on part sdb5
#mount /dev/sdb5 /mnt/temp1
#mkdir /mnt/temp1/Backup Name
#cd /mnt/temp1/Backup Name

#partimage -b -z1 -o save /dev/sdb8 Backup Name.sdb8.partimg.gz

Restore: Spare partition image storage is part sdb5 image is to be restored to part sdb8
#mount /dev/sdb8 /mnt/temp1
#mkdir /mnt/temp1/Backup Name
#cd /mnt/temp1/Backup Name

#partimage -e restore /dev/sdb8 Backup Name.sdb8.partimg.gz.000

3.When backing up the MBR and Partition Table on a dual boot system with XP, is it a good idea to back up the MBR and the Part record of both the Ubuntu system partition and also the XP system partition?
4.I believe that the following #dd code saves the MBR and part Table from the first partition of the identified disk only.

Save:
e.g. Dapper install is on sdb8 (first partition of the sdb disk) and XP install is on sda1(first partition of tht sda disk) Would it be wise to save both if the XP system is on sda1 and the Dapper system is on sdb8

#dd if=/dev/sda of=Backup Name.sda.mbr count=1 bs=512 and
#dd if=/dev/sdb of=Backup Name.sdb.mbr count=1 bs=512 and
#sfdisk -d /dev/sda > Backup Name.sda.pt and
#sfdisk -d /dev/sdb > Backup Name.sdb.pt

Restore:

#dd if=Backup Name.sda.mbr of=/dev/sda and
#dd if=Backup Name.sdb.mbr of=/dev/sdb and
#sfdisk /dev/sda < Backup Name.sda.pt and
#sfdisk /dev/sdb < Backup Name.sdb.pt

3. When restoring should the MBR and Part Table be restored before or after the installation image? Does the backup image of the partition also store the MBR and Partition Table?

4. If asked to unmount sdb8 how do you identify the partition to write to in a restore.

5. I have managed to save an image but all attempts to restore that image have so far failed.

---

