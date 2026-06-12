---
title: "/home and /var mounting in / even though on own partitions?"
date: 2006-07-04
forum: Desktop Environments
---

### Post by timczer on 2006-07-04
My / partition is showing 96% full.  If I use baobab and look at all the directories, it only appears to be 5 gigs our so (of 12 gigs available).  My home directory is mounted on a seperate partition (hdb5) and has 5.5g, as is my /var directory (hdb6), about 1g.  The only way I could be out of space is if these two directories are being included as part of /. 

 If they are being mounted on their own partitions, why would it show me being out of space?  This just happened today.  I made some changes to the disks today, to free up room.  I moved two partitions (hdb9, hdb10) off the back of the drive all these partitions are on, but didn't move the home or var directories.  They were part of the extended partition that also held the two partitions I moved to a different disk.  There are also two partitions between home and var (hdb7, hdb8)and the two I moved that seem to be mounting fine.  

How do I get the system to show the drive space correctly?

---

### Post by taurus on 2006-07-04
What does your /etc/fstab look like and what is the output of this command?
```

more /etc/fstab <-- to view your /etc/fstab...
df -h <-- for disk space...

```

---

### Post by timczer on 2006-07-04
Here is the fstab output.  It is the same as I was using before this problem started.


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb3       /               reiserfs defaults        0       1
/dev/hdb1       /boot           ext2    defaults        0       2
/dev/hdb5       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda2       /media/hda2     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda3       /media/hda3    freebsd    defaults	 0       1
#/dev/hda5       /media/hda5     ext3    defaults        0       2
#/dev/hda6       /media/hda6     ext2    defaults        0       2
#/dev/hda7       /media/hda7     ext2    defaults        0       2
/dev/hdb6       /var            ext3    defaults        0       2
/dev/hdb2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd1	/media/vmware	ext3	defaults	0	0
/dev/hdd2	/media/vmware2	ext2	defaults	0	0
/dev/hdd3	/media/vmware3	ext2	defaults	0	0
# /dev/hda7	/media/oldhome	ext2	defaults,errors=remount-ro,usr_xattr	0	1
/dev/hdb7	/media/music	vfat	defaults,umask=000,user	0	0
/dev/hdb8	/media/media_files ext3	defaults	0	0

output of df -h

tim@tim-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb3              12G   12G  464M  97% /
varrun                474M  156K  474M   1% /var/run
varlock               474M  4.0K  474M   1% /var/lock
udev                  474M  200K  474M   1% /dev
devshm                474M     0  474M   0% /dev/shm
lrm                   474M   18M  456M   4% /lib/modules/2.6.15-25-k7/volatile
/dev/hdb1              96M   28M   64M  31% /boot
/dev/hdb5              20G  4.9G   14G  27% /home
/dev/hda1              25G   12G   13G  49% /media/hda1
/dev/hda2              26G  3.5G   23G  14% /media/hda2
/dev/hdb6             9.7G  1.1G  8.2G  12% /var
/dev/hdd1             9.7G  8.5G  816M  92% /media/vmware
/dev/hdd2             9.9G  129M  9.2G   2% /media/vmware2
/dev/hdd3             9.7G  8.2G  1.1G  89% /media/vmware3
/dev/hdb7              20G  8.6G   11G  44% /media/music
/dev/hdb8              72G   22G   47G  33% /media/media_files
/dev/sda1              38G  6.9G   31G  19% /media/QUE!$M3 40G

Here is the output of baobab showing each directory in /.

If you add up the memory used, outside of home and var, it is only about 5.5g.

---

### Post by timczer on 2006-07-04
I don't think this made a difference, but I also installed vmserver a couple of days ago.  I think I set it up correctly, setup seperate partitions for it to install the other operating systems.  

Going directory by directory in /, I cannot find any files large enough to have taken up all the room on my root partition.

---

### Post by vigleik on 2006-07-04
Try filelight (sudo apt-get install filelight). It will give you a graphical representation of what's taking up all the space.

Vigleik

---

### Post by timczer on 2006-07-04
When I run filelight, it appears to show only 3.1g used on /.  Even adding /proc, /sys /dev, and /root back it is another 1.2g.  Total would be a little over 4 gigs.  

Could there be something holding memory open, but not showing as a file in a directory?  How can I tell?

---

### Post by pksings on 2006-07-04
DId you move the contents of the original locations to the new locations or copy them?

This is the method I would move filesystems with and why.

boot into single user mode. Un-mount the filesystems you wish to move if at all possible. ( with some it is not possible such as /usr ).  make new target dirs with different names.  Use the mv command to move whatever, wherever.  Delete the old directories, rename the different named ones you previously made and copied to the correct names or make new ones if necessary for stubs to mount the moved ones on. 

to move /usr I used tar to create a tar file of the whole thing in "relative" form. (./usr) Then extracted that tar file into my new /usr2,  Check to make sure everything is there. Change fstab to represent the new arrangement so that the correct partition will mount,  Copy the mount command into your working directory, Then string three commands together, "mv /usr /usr-old; mkdir /usr; ./mount /usr"   Worked for me..

A common mistake is to mount over a "full" directory which hides it's contents so that the filesystem still shows full but you can't see the files or delete them.

PK

---

### Post by timczer on 2006-07-04
What I moved was not part of the Ubuntu operating system.  I had FC5 on two partitions (boot and root) in the hdb9 and hdb10 partitions.  I moved these to another drive completely, then deleted the partitions.  I didn't move /home or /var at all.  They are part of the same LVM as the two moved partitions as well as two other partitions within the LVM (hdb7 and hdb8).  

This is the fdisk output before the change of partitions:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9756    78365038+   7  HPFS/NTFS
/dev/hda2            9757       13151    27270337+   c  W95 FAT32 (LBA)
/dev/hda3           13152       15701    20482528+  a5  FreeBSD
Partition 3 does not end on cylinder boundary.
/dev/hda4           15702       19458    30172590+   5  Extended
Partition 4 does not end on cylinder boundary.
/dev/hda5   *       15702       15766      522081   83  Linux
/dev/hda6           15767       16668     7245283+  83  Linux
/dev/hda7           16669       19458    22405162+  83  Linux

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1          13      104391   83  Linux
/dev/hdb2              14         140     1020127+  82  Linux swap / Solaris
/dev/hdb3             141        1670    12289725   83  Linux
/dev/hdb4            1671       20178   148665510    5  Extended
/dev/hdb5            1671        4220    20482843+  83  Linux
/dev/hdb6            4221        5494    10233373+  83  Linux
/dev/hdb7            5495        8044    20482843+  83  Linux
/dev/hdb8            8045       17588    76662148+  83  Linux
/dev/hdb9           17589       20165    20699721   83  Linux
/dev/hdb10          20166       20178      104391   83  


And this is the fdisk after I moved the partitions:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3180    25543318+   7  HPFS/NTFS
/dev/hda2            3181        6575    27270337+   c  W95 FAT32 (LBA)
/dev/hda3            6576        9152    20699752+  83  Linux
/dev/hda4            9153       19457    82774912+   5  Extended
/dev/hda5            9153        9165      104391   83  Linux
/dev/hda6            9166       11882    21824271   83  Linux
/dev/hda7   *       11883       14314    19535008+  83  Linux

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1          13      104391   83  Linux
/dev/hdb2              14         140     1020127+  82  Linux swap / Solaris
/dev/hdb3             141        1670    12289725   83  Linux
/dev/hdb4            1671       20178   148665510    5  Extended
/dev/hdb5            1671        4220    20482843+  83  Linux
/dev/hdb6            4221        5494    10233373+  83  Linux
/dev/hdb7            5495        8044    20482843+  83  Linux
/dev/hdb8            8045       17588    76662148+  83  Linux

Disk /dev/hdd: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        1285    10321731   83  Linux
/dev/hdd2            1286        2586    10450282+  83  Linux
/dev/hdd3            2630        3915    10329795   83  Linux


It doesn't appear anything changed with the /home partition (hdb5) or the /var partition (hdb6).  

I am only guessing that home and var are being counted against /, because the sizes are about right to account for the difference.  

If I go through gparted or look at the gnome-system-monitor, it shows the root partition as 96% full, with 11.3 gigs used.  If I use a file manager or baobab or filelight, it only shows about 4.5 gigs in all the other directories of /.  How do I figure out what is taking up memory?

---

### Post by timczer on 2006-07-04
If I run sudo du -sh /* it lists home and var under /.  If they are in their own partitions, would they show up under / with this command?

---

