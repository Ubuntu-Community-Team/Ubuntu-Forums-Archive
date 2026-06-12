---
title: "Disk Mount problem"
date: 2008-12-12
forum: General Help
---

### Post by havencruise on 2008-12-12
Hi,
I recently installed ubuntu 8.04 on my system and also,i have an xp system running along with this. The problem i have is that i am unable to mount/view only one of 4 ntfs partitions i have.
I'm updating a picture so that the disk configuration on my system may be understood clearer.[IMG]http://i385.photobucket.com/albums/oo295/havencruise/untitled.jpg[/IMG]

I have 1 basic disk, and 1 dynamic disk. Ubuntu is installed in the first 8gb partition of disk0 in the image. In disk 1, i have windows in c:/. The thing to notice is that E:/ is spanned across two partitions:one of 41gb and the other of 15gb, and it shows up as a single partition in windows(my computer). In ubuntu, i am not able to mount this Movies partition. All the other partitions have been mounted except this. 
I would really like to mount this partition, as it has a lot of movies stored in it which i would like to watch from ubuntu itself.

---

### Post by havencruise on 2008-12-12
The fdisk -l and fstab outputs are as follows. : 
root@localhost:~# fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1044     8385898+  83  Linux
/dev/sda2            1045        3132    16771860    c  W95 FAT32 (LBA)
/dev/sda3            3133        9712    52853850    f  W95 Ext'd (LBA)
/dev/sda5            3133        6422    26426893+   b  W95 FAT32
/dev/sda6            6423        9712    26426893+   b  W95 FAT32

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe867e867

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1275    10241406   42  SFS
/dev/sdb2            1276       19457   146046915   42  SFS

Disk /dev/sdc: 262 MB, 262144000 bytes
16 heads, 32 sectors/track, 1000 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0xe116a12f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         999      255728    b  W95 FAT32
**************************************************************************
/etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=ae46976a-8cb9-4e12-bd0c-3fa89084fa11 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb2
UUID=30B7-7309  /media/hdb2     vfat    defaults,umask=007,gid=46 0       1
# /dev/hdb5
UUID=948F-9875  /media/hdb5     vfat    defaults,umask=007,gid=46 0       1
# /dev/hdb6
UUID=204C-B1E5  /media/hdb6     vfat    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=EA48D43D48D40A69 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1

/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sdb3	/mnt/Games	ntfs	defaults	0	0
/dev/sdb5	/mnt/Songs	ntfs	defaults	0	0

---

### Post by albinootje on 2008-12-12
Weird, can you post the output of :

mount

blkid 

And can you install gparted in Ubuntu, start it with sudo gparted, select /dev/sdb at the top right, and make a screenshot of that and post it here ?

---

### Post by havencruise on 2008-12-12
root@localhost:~# mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-22-generic/volatile type tmpfs (rw)
/dev/sda2 on /media/hdb2 type vfat (rw,umask=007,gid=46)
/dev/sda5 on /media/hdb5 type vfat (rw,umask=007,gid=46)
/dev/sda6 on /media/hdb6 type vfat (rw,umask=007,gid=46)
/dev/sdb1 on /media/sda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/sdb3 on /mnt/Games type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdb5 on /mnt/Songs type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/prashanth/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=prashanth)
/dev/sdc1 on /media/USB type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1001,utf8,umask=077,flush)
***************************************************************************
blkid:

/dev/sda1: UUID="ae46976a-8cb9-4e12-bd0c-3fa89084fa11" TYPE="ext3" 
/dev/sda5: LABEL="DOWNLOADS" UUID="948F-9875" TYPE="vfat" 
/dev/sdb1: UUID="EA48D43D48D40A69" LABEL="Windows" TYPE="ntfs" 
/dev/sdb3: UUID="42386CE5386CD985" LABEL="Apps & Games" TYPE="ntfs" 
/dev/sdb4: UUID="E420EE3720EE0FFA" LABEL="Movies" TYPE="ntfs" 
/dev/sdb5: UUID="3A40849440845891" LABEL="Songs" TYPE="ntfs" 
/dev/sdc1: LABEL="USB" UUID="A438-C322" TYPE="vfat" 
/dev/sda2: LABEL="VBOX" UUID="30B7-7309" TYPE="vfat" 
/dev/sda6: UUID="204C-B1E5" TYPE="vfat" 
**************************************************************************
Had this error show up when i started gparted
The kernel is unable to re-read the partitiontables on the following devices:
- /dev/sdb
Because of this you will only have limited access to these devices. Unmount all mounted partitions on a device to get full access.
**************************************************************************

---

### Post by havencruise on 2008-12-12
here's the screenshot..
[IMG]http://i385.photobucket.com/albums/oo295/havencruise/Screenshot.png[/IMG]

---

### Post by bikerharis on 2008-12-12
Hi all .. this is my first postr here.. I'm new to Ubuntu. I too have a problem with mounting drives. The problem is, The drives are not mounting automatically. I have to mount it manually each time when ubuntu starts. Please help..

---

### Post by havencruise on 2008-12-12
> **bikerharis said:**
> Hi all .. this is my first postr here.. I'm new to Ubuntu. I too have a problem with mounting drives. The problem is, The drives are not mounting automatically. I have to mount it manually each time when ubuntu starts. Please help..

You may want to look at this thread
[http://ubuntuforums.org/showthread.php?t=283131&highlight=mount+disks+automatically]("http://ubuntuforums.org/showthread.php?t=283131&highlight=mount+disks+automatically")

---

### Post by havencruise on 2008-12-12
> **albinootje said:**
> Weird, can you post the output of :

mount

blkid 

And can you install gparted in Ubuntu, start it with sudo gparted, select /dev/sdb at the top right, and make a screenshot of that and post it here ?

The gparted asked me to do a reboot. I did that, n now the other partitions which used to mount aren't mounting anymore, such D:/ and F:/ in the first picture.

---

### Post by albinootje on 2008-12-12
Can you boot with Windows, the ntfs-partitions are probably marked as "dirty".

And about your original question, it looks like Ubuntu has problems reading the partition table of /dev/sdb properly. :(
How did you create those partitions ? During the Windows-install or did you use some other software like Partition Magic ?

---

### Post by havencruise on 2008-12-12
> **albinootje said:**
> Can you boot with Windows, the ntfs-partitions are probably marked as "dirty".

And about your original question, it looks like Ubuntu has problems reading the partition table of /dev/sdb properly. :(
How did you create those partitions ? During the Windows-install or did you use some other software like Partition Magic ?

Yes i can boot with windows and access them properly too.. I created those partitions using windows disk manager(the one u get by right clicking "my computer" > manage > disk management).. Made it dynamic by right clicking on the drive(the place where it says "Disk 1" ) and saying Convert to Dynamic Disk.
After that u have options of selecting some unused spaces and merging them with other already formatted partitions. I had the 15gb partition as unused space, n i formatted that to a "spanned" partition of the (original) E:/ drive of 41.43 GB)

---

### Post by havencruise on 2008-12-12
> **albinootje said:**
> Can you boot with Windows, the ntfs-partitions are probably marked as "dirty".


About the "dirtiness" of the partitions, i was till now, able to mount all the other partitions of that disk, such as "Apps and Games" and "Songs"

---

### Post by havencruise on 2008-12-12
One more thing.. I uninstalled gparted, and searched for the drives using Device Manager.. this is what i found:
[IMG]http://i385.photobucket.com/albums/oo295/havencruise/Devicemanager.png[/IMG]

---

### Post by albinootje on 2008-12-12
What happens when you try to manually mount that Movies partition (which is /dev/sdb4) ?
Do you get to see errors in the terminal ?
Try also :
dmesg
after doing that.

---

### Post by cdtech on 2008-12-12
From what I understand the kernel has to have the LDM (Logical Disk Manager (Dynamic Disks)) support enabled. I'm not sure if this is done by default now, or if you have to recompile the kernel for the support.

---

### Post by havencruise on 2008-12-12
> **albinootje said:**
> What happens when you try to manually mount that Movies partition (which is /dev/sdb4) ?
Do you get to see errors in the terminal ?
Try also :
dmesg
after doing that.

Your're right.. /dev/sdb4 is Movies. But thats the 41GB partition. The 15GB partition is /dev/sdb2

Here's the output:

root@localhost:/mnt# mount /dev/sdb4 part
Failed to read last sector (118334915): Invalid argument
Perhaps the volume is a RAID/LDM but it wasn't setup yet, or the
wrong device was used, or the partition table is incorrect.
Failed to mount '/dev/sdb4': Invalid argument
The device '/dev/sdb4' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
**************************************************************************
I didn't ( or couldn't ) observe anything from dmesg..
All of the msgs seems to be the messages from startup itself.. Nothing from the mount.

---

### Post by havencruise on 2008-12-12
> **cdtech said:**
> From what I understand the kernel has to have the LDM (Logical Disk Manager (Dynamic Disks)) support enabled. I'm not sure if this is done by default now, or if you have to recompile the kernel for the support.

Yes, i thought of the same thing too. I tried looking for ldm in synaptic's search. Didn't find anything that relates to my problem. Perhaps you can do a search too and let me know the package name so that i may get it.

---

### Post by havencruise on 2008-12-12
I guess one should remember that "Movies" partition is spanned across two different spaces. One the 41GB space, and the other the 15GB space.

---

### Post by albinootje on 2008-12-12
What about copying your data to a usb-disk, and convert your spanned partitions into more normal partitions that Linux can read easily ?
After that copy the data back.

A quick search-engine search for ldm and linux doesn't show much info.

---

### Post by havencruise on 2008-12-12
> **albinootje said:**
> What about copying your data to a usb-disk, and convert your spanned partitions into more normal partitions that Linux can read easily ?
After that copy the data back.

A quick search-engine search for ldm and linux doesn't show much info.

lol.. :D .. thats the one thing i can't do :D .. i don't have a usb disk,nor do i have a portable usb drive of that capacity.. :) .. and there isn't enough free space on the disk to do that either. I found something though.. LVM2.. i searched for logical volume manager in "synaptic package manager" search. still not sure on how i need to use it :D

---

### Post by cdtech on 2008-12-12
If you insist on using LDM (for RAID) then you'll have to enable the filesystem option within the kernel code which enables linux to recognize and work with your LDM volumes (recompile).

---

### Post by havencruise on 2008-12-12
> **cdtech said:**
> If you insist on using LDM (for RAID) then you'll have to enable the filesystem option within the kernel code which enables linux to recognize and work with your LDM volumes (recompile).

I DO-NOT have a RAID disk :) .. I only have one dynamic disk and one basic disk. The dynamic disk has a spanned partition which needs to be recognized.. I doubt i need to recompile the kernel. I guess if i figure out how to use this LVM2 package, i can use it like any other partition

---

### Post by havencruise on 2008-12-12
Well, i've come to a part-conclusion that installing lvm2(search it in the synaptic package manager by the name logical volume manager) and testdisk packages has helped me mount the drives Songs and Apps&Games, but not the Movies. 
Although i still don't know what made them to mount, i still got them to be mounted. All i did was install those two packages, and gave the commands described here a trial : [https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall]("https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall") 
However the original problem still seems to be unsolved, and i hope someone finds a package for supporting dynamic drives like mine.

---

