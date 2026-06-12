---
title: "[SOLVED] Optical Drive mounting read only"
date: 2008-12-26
forum: General Help
---

### Post by cmittle on 2008-12-26
I recently managed to salvage a DVD RW from my sisters computer.  Today I installed it in place of one of the two optical drives in my server in the hopes of being able to burn dvd's from it rather than booting up my desktop.  When I put in a blank DVD to burn K3b says no medium present.  If I put in a disc with information on it it will auto mount and show up just like it's supposed to.  Can someone please help me figure out why it is not recognizing blank media?

Thanks,
Cory

---

### Post by Rocket2DMn on 2008-12-27
Can you please post the output of the following commands:
```
sudo fdisk -l
cat /etc/fstab
sudo blkid
mount
```
If you can point out the specific optical drive from the listing in any of those commands, that would be very helpful.

---

### Post by cmittle on 2008-12-28
This is part of the response from sudo lshw pertaining to the drive in question;
```

 *-cdrom:0
                description: DVD reader
                product: DVD+RW SOHW-802S
                vendor: LITE-ON
                physical id: 2
                bus info: scsi@1:0.0.0
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: UPP6
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=open

```


sudo fdisk -l 
```

Disk /dev/sda: 650.1 GB, 650136969216 bytes
255 heads, 63 sectors/track, 79041 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeac23097

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1860    14940418+  83  Linux
/dev/sda2           78799       79041     1951897+  82  Linux swap / Solaris
/dev/sda3            1861       78798   618004485   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux

```

cat /etc/fstab;
```


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=03559223-7cc1-4d59-a0af-f6da5f14521c /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda3
UUID=db1d939d-5a7f-4862-b60c-b97638e442fa /home           ext3    defaults        0       2
# /dev/hda2
UUID=23906a83-4191-493c-94df-d06fd4a857a0 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sdb1	/media/160gdisk	auto	


```

sudo blkid;
```


/dev/sda1: UUID="03559223-7cc1-4d59-a0af-f6da5f14521c" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sda2: TYPE="swap" UUID="23906a83-4191-493c-94df-d06fd4a857a0" 
/dev/sda3: UUID="db1d939d-5a7f-4862-b60c-b97638e442fa" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="9344607d-209f-445b-ba74-60b616e3920e" TYPE="ext3" 

```

mount;
```



/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-21-generic/volatile type tmpfs (rw)
/dev/sda3 on /home type ext3 (rw)
/dev/sdb1 on /media/160gdisk type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)

```

---

### Post by Rocket2DMn on 2008-12-28
OK, there are two incorrect lines in your fstab file
```
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
```
Neither of them have a partition (ex: hdc1 instead of hdc).
We will fix that, but I want to see if that other drive pops up as a /dev/scd# device as well (scd usually references an optical drive, whereas hd* or sd* usually reference hard disks or flash drives).
Please post the output of
```
ls -l /dev/scd*
```
You may have /dev/scd0 and /dev/scd1
Those devices will replace /dev/hdc and /dev/hdd in your fstab file such that the new entries look like this:
```
/dev/scd0        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
```
To edit fstab, run
```
gksudo gedit /etc/fstab
```

---

### Post by cmittle on 2008-12-29
I have determined what is wrong with this drive.  It's the silly DVD+ format instead of the more commonplace DVD- format.  I just happen to have a few DVD+ blanks laying around, popped it in and sure enough it recognizes this empty media.  

I think I will have to continue using my desktop for cd burning for now.  

It seems like the drives work normally entered as hdd and hdc.  Do you know of any particular problems that may arise from that versus being entered as scd0 and scd1?

Cory

---

### Post by Rocket2DMn on 2008-12-29
I think what is probably happening is that the discs are automounting, not based on what is in fstab.  You can check this by commenting out those two lines in fstab by adding a # at the front of them.  If the discs still mount as before, then it is simply automounting - and if that works fine, then good!  You should use whatever configuration works best.
Again, the two lines currently in fstab are meaningless because they aren't associated with a particular partition.

---

### Post by cmittle on 2008-12-29
Sorry to waste your time with a silly mistake like misunderstanding what the drive was telling me.  I really appreciate the help trying to resolve the issue, and I'm sure I will be back reading this thread again sometime to remember the commands you showed me.

Thanks,
Cory

---

### Post by Rocket2DMn on 2008-12-29
You're not wasting my time, this is why I (and others in the community) are here!

---

