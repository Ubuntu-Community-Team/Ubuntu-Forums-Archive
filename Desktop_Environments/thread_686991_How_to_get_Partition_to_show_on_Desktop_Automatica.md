---
title: "How to get Partition to show on Desktop Automatically"
date: 2008-02-03
forum: Desktop Environments
---

### Post by aggiedvm on 2008-02-03
I have a VFAT partition that I am trying to use to keep "MY Documents" in.  I would like for this partition to be automatically mounted each time I log in and show on desktop as "My Documents" .  I can manually mount with mount command but have not been able to get fstab and mtab files just right to work properly.  I am trying to  mount /dev/sda6 to show as "My Documents" on desktop automatically with each login.

fdisk
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9a399a39

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3825    30724281    7  HPFS/NTFS
/dev/sda2            3826        4554     5855692+  83  Linux
/dev/sda3            4555        4676      979965   82  Linux swap / Solaris
/dev/sda4            4677       14593    79658302+   5  Extended
/dev/sda5            4677        4689      104391   83  Linux
/dev/sda6            4690       11701    56323858+   b  W95 FAT32
/dev/sda7           11702       14593    23229958+  8e  Linux LVM


fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=1b10dcda-808f-4c3b-82a9-741bcb4c4284 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=185C5D0F5C5CE950 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=f788ebb9-b5c3-4e13-88b0-d9e3ae048ef9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

#/dev/sda6	/media/My\ Documents	vfat	rw nosuid nodev uid=1000 fmask=0077 dmask=0077 codepage=cp437 iocharrset=iso8859-1 shartname=mixed usefree utf8

#/dev/sda6	/media/My\ Documents	vfat	rw nosuid nodev uid=1000 fmask=0077 dmask=0077 codepage=cp437 iocharrset=iso8859-1 shartname=mixed usefree utf8

EVERYTHING AFTER VFAT ON LAST LINE I COPIED FROM SOMEWHERE SO I DO NOT KNOW IF THIS IS CORRECT OR NOT.  THIS LINE IS COMMENTED OUT BECAUSE IT DOES NOT WORK WHEN RUN.

MTAB
/dev/sda2 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
/dev/sda1 /media/sda1 fuseblk rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096 0 0
securityfs /sys/kernel/security securityfs rw 0 0
/dev/scd0 /media/cdrom0 iso9660 ro,nosuid,nodev,user=aggiedvm 0 0
/dev/sda6 /media/disk vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree 0 0

EVERHTING HERE ON LAST LINE AFTER VFAT I ALSO COPIED FROM ANOTHER LINE AND I AM NOT SURE IF C0RRECT.

Any help would be appreciated.  I have tried for about 2 hours and I keep getting error message something to the effect that sda6 is not in mtab or fstab files.

Any help would be appreciated.

Ken

---

### Post by goodfella on 2008-02-04
Generally under Gnome the shortcut name of a mounted partition is the partitions label.  For example I have an external hard drive with a partition labeled external-backup.  On my desktop is an icon with the name external-backup.  This icon opens the partition labeled external-backup.  I can label the partition with e2label.  If the partition does not have a label, then I think the desktop icon is the name of the folder which the partition is mounted on.  Alternatively you can find out how to label fat23 partitions.

As far as your fstab goes try changing the line:
> 
#/dev/sda6 /media/My\ Documents vfat rw nosuid nodev uid=1000 fmask=0077 dmask=0077 codepage=cp437 iocharrset=iso8859-1 shartname=mixed usefree utf8

to:
> 
/dev/sda6 /media/My\040Documents vfat rw,nosuid,nodev,uid=1000,fmask=0077,dmask=0077,codepage=cp437,iocharrset=iso8859-1,shartname=mixed,usefree,utf8 0 2


You were missing the dump and pass option and also when suppling mount options you need to make them comma separated per the fstab man page.  Also the "\ " before "Documents" needs to be changed to \040 per the fstab man page.

One thing to remember is that the fstab file is formated as follows:
> 
<file system> <mount point> <type> <options> <dump> <pass>


Each column is delimited by a space which explains why you have to escape the space After "My" and before "Documents"

---

### Post by aggiedvm on 2008-02-04
Thanks for post.  I changed the line in fstab as described. The partition did not  mount automatically and when I try to mount manually by right clicking drive/mount drive I get the following error message:  [mntent]: line 15 in /etc/fstab is bad mount: can't find /media/My Documents in /etc/fstab or /etc/mtab.

Thanks,
Ken

---

### Post by aggiedvm on 2008-02-05
I found documentation that pointed out that the mtab file was dynamic file and not likely source of the problem.  I could mount the partition manually with no problem from the command line.  So I took out all of the extra commands in the fstab command line that was not in the manual command except rw and 0,2.  I then re-booted and the partition is mounted on boot-up.   Thanks for the help.

Ken

/dev/sda6 /media/My\040Documents vfat rw, 0 2

---

### Post by aggiedvm on 2008-02-05
One other problem.  Even though the rw (read-write) command is there in fstab, when I mount the partition this way it only gives read/write access to root.  I have tried manual command with chmod and the command runs but I still cannot modify the files.

aggiedvm@aggiedvm-laptop:~$ sudo chmod -R a+wrx /media/My\ Documents/

Any help would be appreciated.

Ken

---

### Post by aggiedvm on 2008-02-06
I have also tried changing ownership from root (who currently owns all of the files in this partition) to aggiedvm.  when I use the command and change this for /dev/sda6 it will show up as aggiedvm aggiedvm as ownwer.  However, the command will not change it for /media/My\ Documents.  The command runs but it does not change anything and I don't get an error message.  When I re-boot both places show root root as owner.

Any help would be appreciated.

Ken:(

---

