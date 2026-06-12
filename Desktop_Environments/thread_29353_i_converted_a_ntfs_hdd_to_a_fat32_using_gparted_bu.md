---
title: "i converted a ntfs hdd to a fat32 using gparted but fdisk still shows as ntfs??"
date: 2005-04-24
forum: Desktop Environments
---

### Post by martinez9049 on 2005-04-24
i just converted a ntfs drive using gparted to fat32 so that i could use it with linux/windows. in gparted it shows the drive as fat32 but when i run fdisk -l it shows it as HPFS/NTFS. i rebooted the pc and it still shows the same thing. when i mount it i specify vfat and it mounts just fine. im just making sure that this is ok b/c the drive has all my important stuff on it. also, i edited the fstab file to make it mount in the beginning by adding 
/dev/sda1       /media/windows  vfat    umask=000       0       0
but it doesn't mount. at one point it told me that root was only able to mount that drive, it doesn't say that anymore, and i always have to mount it manually.

thanks,
ismael m

---

### Post by Nis on 2005-04-24
Bad idea trying to convert it.  If I remember correctly you cannot convert a NTFS drive to FAT32.  You can go the otherway (FAT32 to NTFS) however.  I would try mouting the drive like to said you could and copy all important data to another drive.  Then format the drive to FAT32 and copy the data you need back to it.  I've never been a big fan of converting file systems because there's too much that can go wrong when you mess with such a low level part of the system.

---

### Post by nad on 2005-04-24
Does windows recognize the drive now? I've seen this strangeness with drives that have been connected to a promise controller. Apparently some hidden flags get set and the only way to clear them is to overwrite the drives partition table. Something that you do _not_ want to do unless you absolutely know what you are doing.

If this is not your boot drive and windows and linux recognize it properly, it is probably ok. It would be safest to copy all of your data to another freshly partitioned and formatted drive.

As far as the fstab file, instead of the umask option use ' rw,user,noauto ' and leave the last two fields unfilled as they have no meaning for a vfat volume. This will give the volume read and write permissions to the one who mounts the volume. Now add a line to your .bashrc file in your home directory: mount /media/windows . This will auto mount the volume whenever you log in.

Dan M

---

### Post by martinez9049 on 2005-04-24
well as far as the conversion went i used gparted and it erased all the data too. but it wasn't like a format because it took a couple of seconds. is there a program that i could use to format it as a fat32?

---

### Post by nad on 2005-04-24
It seemd that parted just changed your file system type information. The data is still there. This is why you can see it with low level access. You can still recover the data if you wish and copy it to another drive.

As for formatting the drive with the filesystem of your choice: Once this is done any existing data will be harder to recover. The command: mkfs.vfat /dev/hd?  issued while the drive number ? is not mounted will create a vfat file system on that drive.

Dan M

---

### Post by martinez9049 on 2005-04-24
ok, i ran
$ mkfs.vfat /dev/sda1
and it showed mkfs version 2.11 and that's it. the drive is now empty but again, fdisk still shows it as ntfs. when i ran this code it took about half a second. whenever i ran windows and formatted a drive this big it usually took about 10-15 minutes. what am i doing wrong? i've already backed up the data on another drive so i don't care if the data is lost.

---

### Post by nad on 2005-04-24
Run the file system check program, unmounted again: e2fsck /dev/sda1

---

### Post by martinez9049 on 2005-04-25
ok i ran it and i got this. don't really know what this means.

e2fsck 1.35 (28-Feb-2004)
Couldn't find ext2 superblock, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sda1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


thanks,
ismael m

---

### Post by nad on 2005-04-25
Since this drives file system information is now trashed and you don't need anything on it, lets wipe any information currently stored at the very beginning. Make certain that the drive is not mounted, then issue the command:

dd bs=512 count=1 if=/dev/zero of=dev/sda

Copy this command exactly and double check it before pressing the enter key. You are about to do a direct disk write of zeroes to the first sector (512 bytes) of /dev/sda.

Now you can run fdisk and confirm that there is no partition table. If ntfs still shows up, it has placed information in the extended area. Rerun the previous command increasing the count number to 2 to write 1024 zeroes. This ought to really do it.

The drive is now ready to be partitioned and formatted. Please post your results.

---

### Post by fordfan753 on 2005-04-26
You have Windows...wouldn't it just be easier to use Partition Magic, or something along those lines, that way Windows will recognise it easier too. Partition Magic has a trial version, just look on the site...although I love Linux all my partitioning (except for stuff done while installing) is done through Partition Magic

---

### Post by martinez9049 on 2005-04-26
ok, i ran that command and i got this.

root@ubuntu:/home/ismael # dd bs=512 count=1 if=/dev/zero of=/dev/sda1
1+0 records in
1+0 records out
512 bytes transferred in 0.000874 seconds (585761 bytes/sec)

i ran fdisk -l and got this

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4664    37463548+  83  Linux
/dev/hda2            4665        4865     1614532+   5  Extended
/dev/hda5            4665        4865     1614501   82  Linux swap / Solaris

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24321   195358401    7  HPFS/NTFS

so i then changed the 1 to 2 and i still get the same thing in fdisk.

i don't have windows right now....i would've used partition magic long time ago or even the windows program is easy to use. i also don't feel like taking the drive out and putting it in another box that has windows to format it.

thanks,
ismael m


...i just noticed that when i start terminal it has this at the top:

mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ismael@ubuntu:~$

---

### Post by nad on 2005-04-26
[QUOTE=martinez9049]ok, i ran that command and i got this.

root@ubuntu:/home/ismael # dd bs=512 count=1 if=/dev/zero of=/dev/sda1
1+0 records in
1+0 records out
512 bytes transferred in 0.000874 seconds (585761 bytes/sec)

[/QUOTE]

dd bs=512 count=1 if=/dev/zero of=/dev/sda

Please rerun the command as above. Note that the command does not have a 1 after /dev/sda. You do not wish address the begining of the first partition when you want to overwrite your boot sector. You want to address the device itself.

---

### Post by martinez9049 on 2005-04-26
ok...i did that. and got this, which i think is right.

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4664    37463548+  83  Linux
/dev/hda2            4665        4865     1614532+   5  Extended
/dev/hda5            4665        4865     1614501   82  Linux swap / Solaris

Disk /dev/sda: 200.0 GB, 200049647616 bytes
64 heads, 32 sectors/track, 190782 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes

Disk /dev/sda doesn't contain a valid partition table


thanks,
ismael m

---

### Post by martinez9049 on 2005-04-28
ok, i used gparted to make a new partition. i did the default disktype of msdos and then i made a fat32 partition. when i run fdisk it shows the system as linux. i guess this is ok?

thanks,
ismael m

---

### Post by nad on 2005-04-28
To tell you the truth, I have never used gparted and I am not at a hoary system at the moment so I can't take a look. I imagine that the default disk type and file system would be native to linux. Please post the new parted ouput.

---

### Post by martinez9049 on 2005-04-28
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       24321   195358401   83  Linux


thanks,
ismael m

---

### Post by nad on 2005-04-28
This looks fine.

The output of: dosfsck -v /dev/sda1  ?

---

### Post by martinez9049 on 2005-04-28
dosfsck 2.11 (12 Mar 2005)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Checking we can access the last sector of the filesystem
Boot sector contents:
System ID "mkdosfs"
Media byte 0xf8 (hard disk)
       512 bytes per logical sector
     16384 bytes per cluster
        32 reserved sectors
First FAT starts at byte 16384 (sector 32)
         2 FATs, 32 bit entries
  48816128 bytes per FAT (= 95344 sectors)
Root directory start at cluster 2 (arbitrary size)
Data area starts at byte 97648640 (sector 190720)
  12203940 data clusters (199949352960 bytes)
32 sectors/track, 64 heads
         0 hidden sectors
 390716802 sectors total

...also, whenever i open a terminal now i get this message

mount: /dev/sda1 already mounted or /media/windows busy
mount: according to mtab, /dev/sda1 is already mounted on /media/windows
ismael@ubuntu:~$

i made changes to the fstab file and another file according to a guy who posted earlier in this thread and it's been doing this since i did that.

thanks,
ismael m

---

### Post by nad on 2005-04-28
Your file system is ready to go. Make a mount point for it and add an entry to your file system table, /etc/fstab, to describe it.

That guy was probably me. I had you add an entry to your .bashrc file to automatically mount this filesystem when you logged in. The message is inocuous. Every time you open a new terminal screen, the terminal reads your .bashrc file for configuration. If you wish to not see it, remove the mount line for this filesystem and edit fstab to indicate how you wish to mount it. Perhaps: /dev/sda1 mount_point vfat umask=0222 . The fifth and sixth fields have no meaning for a vfat file system.

---

### Post by martinez9049 on 2005-04-28
allright...thanks for all the help

ismael m

---

