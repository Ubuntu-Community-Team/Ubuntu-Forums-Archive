---
title: "how to test for broken hdd?"
date: 2006-07-03
forum: Desktop Environments
---

### Post by frup on 2006-07-03
this morning i got this wierd error when booting my computer... now hdd1 seems to be unmounted... i cant mount it manually in the disks gui

its there in fstab.. but all the files on hdd1 are gone.. i tried copying some files over to where the mount would be.. aprox 30GB... it told me there was not enough space... considering my hda1 only has 25gb free i am guessing it is trying to copy to there...

on turning on the computer the hard drive is recognised on the IDE thing.. the disks tool also sees it.. the disks gui says it is mounted to /ext3 (tthe mount point) but all the files from it are gone :(

how can i sort out what is going wrong/fix the problem

---

### Post by maxbaggi on 2006-07-04
Hi frup,
Could you please post the output of the following commands:
```
sudo fdisk -l
```
and,
```
df -T -h
```

also what exactly are your using Ubuntu or Kubuntu?

---

### Post by frup on 2006-07-04
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4664    37463548+  83  Linux
/dev/hda2            4665        4865     1614532+   5  Extended
/dev/hda5            4665        4865     1614501   82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
16 heads, 63 sectors/track, 155061 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1      155061    78150712+  83  Linux

Disk /dev/hdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        9728    78140128+   7  HPFS/NTFS

**funny that should be ext3!!!**

Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/hda1     ext3     36G  8.7G   25G  26% /
varrun       tmpfs    379M  128K  379M   1% /var/run
varlock      tmpfs    379M  4.0K  379M   1% /var/lock
udev         tmpfs    379M  124K  379M   1% /dev
devshm       tmpfs    379M     0  379M   0% /dev/shm
lrm          tmpfs    379M   19M  361M   5% /lib/modules/2.6.15-25-386/volatile
/dev/hdb1 reiserfs     75G   31G   44G  42% /Linspire/reiserFS
/dev/hdd1     ext2     74G   26G   45G  37% /tmp/disks-conf-hdd1



i am using ubuntu

---

### Post by frup on 2006-07-04
hey thanks that allowed me to find the data

/dev/hdd1 ext2 74G 26G 45G 37% /tmp/disks-conf-hdd1

:S im still confused about this.. dont want to mess anything up, why is this saying ext2 and this saying /dev/hdd1 * 1 9728 78140128+ 7 HPFS/NTFS and my fstab which i did has it as ext3 which i am positive i formated it as... until 2 weeks ago this was my windows partition. it was a dead installation which i havent used since january so i formated it (i was only keeping it for the .exe programs incase wine suddenly released an update which could run one so i could test it :D)

---

### Post by maxbaggi on 2006-07-04
Hi frup,
I don't know why the two commands are showing different file systems... maybe hdd1 was not formatted properly.  You could try formatting it again.  There are various GUI tools available like gparted that can do the job.  Please do not forget to backup your data before formatting.
One other thing... why is hdd1 mounted on "/tmp/disks-conf-hdd1"?  I don't think it is wise to mount anything in /tmp folder.

---

### Post by frup on 2006-07-04
This morning on boot ... something went wrong.. sort of like the fsck check.. i used to have it mounted at a folder /ext3 ... i did not mount it to /tmp it did it itself.. i dont know why. i also dont seem to be able to move it from there.

---

### Post by pjbgravely on 2006-07-04
In a terminal:

sudo umount /dev/hdd1 

sudo fsck /dev/hdd1

if there are problems it will tell you how to fix it.
After fixing try:

sudo mount /dev/hdd1


ext3 is really ext2 with a journal added, and most ext2 utilities will work with it. It may have lost the journal, and is now ext2 if so you can convert it back without reformatting it.

Paul

---

### Post by frup on 2006-07-04
what i dont understand is how this happened... i literally havent touched anything.. it was working fine last night.. i was just on the internet and using gimp... then this morning its all X'd. It wasnt like i turned it off wrong or anything  either.

i will try unmounting it and fscking it now.

---

### Post by frup on 2006-07-04
fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
/dev/hdd1: clean, 6671/9781248 files, 7005515/19535032 blocks

laurent@ubuntu:~$ sudo mount /dev/hdd1
mount: wrong fs type, bad option, bad superblock on /dev/hdd1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


laurent@ubuntu:~$ dmesg | tail
[17179627.948000] NET: Registered protocol family 31
[17179627.948000] Bluetooth: HCI device and connection manager initialized
[17179627.948000] Bluetooth: HCI socket layer initialized
[17179628.016000] Bluetooth: L2CAP ver 2.8
[17179628.016000] Bluetooth: L2CAP socket layer initialized
[17179628.076000] Bluetooth: RFCOMM socket layer initialized
[17179628.076000] Bluetooth: RFCOMM TTY layer initialized
[17179628.076000] Bluetooth: RFCOMM ver 1.7
[17180387.556000] Warning: /proc/ide/hd?/settings interface is obsolete, and will be removed soon!
[17188861.064000] ext3: No journal on filesystem on hdd1

---

### Post by frup on 2006-07-04
[17188861.064000] ext3: No journal on filesystem on hdd1

so no journal on the drive, how do i reimplement it?

---

### Post by pjbgravely on 2006-07-04
I have never seen the journal lost before but I have done it on purpose, that is the only way to re-size. You may have a mechanical problem with the drive. You may want to mount it first by changing the file system type to ext2, just to make sure everything is still there, and making a backup if you need to. This command should create the journal. 

sudo tune2fs -j /dev/hdd1


Paul

---

