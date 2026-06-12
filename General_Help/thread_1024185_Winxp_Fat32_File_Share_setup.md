---
title: "Winxp Fat32 File Share setup?"
date: 2008-12-28
forum: General Help
---

### Post by sandman3838 on 2008-12-28
Hello

I have a Ubuntu 810 Permissions issue to ask of you all for the two VFAT or Fat32 partitions listed below.

SDE1 /MEDIA/INBOX
SDE5 /MEDIA/LINUX_BKUP

I would like to set-up the two VFAT partitions without all the permissions options begin turned on. I read somewhere that VFAT/FAT32 was prefered to get around some of the permission issues between WinXP NTFS and Linux file sharing. The two VFAT partitions are at 32mb each and they were created in WInXP.

Interesting, Winxp Fat32 size was limited to 32mb, while Ubuntu seemed to have the possibility to use the entire 160gb hd? 

Frist, VFAT INBOX SDE1 here I would like to set-up for sharing information with WINXP.

Second, VFAT LINUX_BKUP SDE5 for this I just wanted to backup certain folders from my home directory.


SDA1 /NEDIA/IDE_FILES NTFS-3G (IDE)
SDB1 /MEDIA/WIN_XP NTFS (SATA)
SDC1 / EXT3 (SATA)
SDD1 /MEDIA/GAMES NTFS-3G (SATA)
SDE1 /MEDIA/INBOX VFAT (SATA)
SDE5 /MEDIA/LINUX_BKUP VFAT (SATA)
SDE6 /MEDIA/MICS NTFS (SATA)

Is there a program that you could recommend or perhaps terminal commands that I can run that will affect the target partitions only?

Thank you for your time and help.

---

### Post by sandman3838 on 2008-12-28
Does this Help?

~$ cat /etc/mtab
/dev/sdb1 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.27-9-generic/volatile tmpfs rw,mode=755 0 0
/dev/sde1 /media/IDE_FILES_ fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sdd1 /media/INBOX vfat rw,utf8,umask=0 0 0
/dev/sdd5 /media/LINUX_BKUP vfat rw,utf8,umask=0 0 0
/dev/sdd6 /media/MICS fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sdc1 /media/SATA_GAMES fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sda1 /media/WIN_XP fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/kevin/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=kevin 0 0

---

### Post by sandman3838 on 2008-12-28
Here is an update!

In theory...
One should be able to right click and select Properties on:

SDE1 /MEDIA/INBOX
SDE5 /MEDIA/LINUX_BKUP

Or any folder or file within?

Then select Permissions and make the appropriate changed to Group - Owners - Others.

I can't!  It's all Grayed out?

What am I missing?

---

