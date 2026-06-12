---
title: "Can't see other hard disks?"
date: 2009-01-28
forum: General Help
---

### Post by stingerssx on 2009-01-28
So, I've been going back and forth with this whole Linux thing and here goes another attempt with another computer.


    This is an old dual 600mhz slot 1 processor computer that I installed an ATI Radeon 9200se vid card and has 384mb of pc100 SDRAM. I'm running 8.10 on it.

   So, yeah sure, I meet the minimum requirements, but the problem that I'm having with this one is that I have installed 3 HDDs. One is a 20gig with the OS mounted. Another one is an 18gig SCSI drive. And the third one is an 8gig from an XBOX. I have unlocked the XBOX drive, and I think that the mobo's BIOS needs to be updated to read the SCSI drive. But when installing (for the second time due to some problem with the xorg.conf file) I can see all 3 drives. Since the 20gig is the sda1 drive, I mounted the "/" on there.

   But with the os up and running, there are no other drives. Well, let me be more specific:  In "Computer" there is a icon for the SCSI drive but when I click on it, it says, "Can not mount drive". I don't see any other drives though. 

      Any thoughts? Open to all suggestions, And willing to answer any ?'s too.

      Thanks

---

### Post by heindsight on 2009-01-28
Please post the output of running the following commands in a terminal:
```
sudo fdisk -l
```
and
```
mount
```

---

### Post by munch3 on 2009-01-28
just format them from the BIOS :|
to ext3 or watever

---

### Post by heindsight on 2009-01-28
> **munch3 said:**
> just format them from the BIOS :|
to ext3 or watever

Say what!?!?

Lets first try to get a better idea of exactly what's going on before just reformatting! Besides, one doesn't format from the BIOS, if these other disks do need formatting it can be done from within ubuntu...

---

### Post by stingerssx on 2009-01-29
stinger@Dual-Slot1:~$ sudo fdisk -l

Disk /dev/sda: 20.4 GB, 20485785600 bytes
255 heads, 63 sectors/track, 2490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002f72b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2381    19125351   83  Linux
/dev/sda2            2382        2490      875542+   5  Extended
/dev/sda5            2382        2490      875511   82  Linux swap / Solaris

Disk /dev/sdb: 8004 MB, 8004132864 bytes
255 heads, 63 sectors/track, 973 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
stinger@Dual-Slot1:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/stinger/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=stinger)
tmpfs on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=0755)
stinger@Dual-Slot1:~$ 





For some reason ony showing sda. No sdb or any others.

---

### Post by heindsight on 2009-01-30
> **stingerssx said:**
> stinger@Dual-Slot1:~$ sudo fdisk -l
Disk /dev/sdb: 8004 MB, 8004132864 bytes
255 heads, 63 sectors/track, 973 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

It seems /dev/sdb is the disk you took from the xbox, but it doesn't seem to have a partition table on it. You'll have to create a new partition table on the disk.

You can do this using fdisk:
**Be very careful when using fdisk, if you specify the wrong disk you can cause serious damage!**
```
sudo fdisk /dev/sdb
```

Then inside fdisk, you need to use the n command to create a new partition. 
You'll be asked if you want to create an extended or primary partition. 
Choose p to create a primary partition.
You'll be prompted for a partition number, choose 1.
Next you'll be prompted to enter the first and last cylinders for the partition, just press Return both times to use the defaults (a partition covering the whole disk)
Now use the w command to write a new partition table to the disk and exit.

After doing this you should have a valid partition table on sdb, now you can create a filesystem on the newly created /dev/sdb1 by using mke2fs:
**Again, be careful, if you specify the wrong partition you will lose data**
```
sudo mke2fs -j /dev/sdb1
``` will create an ext3 filesystem on the partition.

Once you've got all this done, you can mount and start using your new filesystem.

I don't see any mention in the output you posted of your 18GB SCSI disk it seems ubuntu is not detecting this disk at all - I'm not sure what the reason for this is. Are you sure the disk is properly connected? Perhaps you do need to do something in your BIOS (like you mentioned) to be able to access this disk.

---

