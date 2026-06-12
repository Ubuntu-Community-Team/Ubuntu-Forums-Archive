---
title: "Permissions Unchangable in extra HD?"
date: 2008-12-29
forum: General Help
---

### Post by sandman3838 on 2008-12-29
Hello

My system is a Dual Boot with Winxp and Ubuntu 8.10 each is on it's own HD.  I just did a fresh install of Ubuntu about two weeks ago and I'm the only user on this system.

My issue has to do with permissions with folders and files that I have saved to other HDs. Naturally if I right click on files or folders in your HOME directory, (properties/permissions) you can make adjustments.

The problem is with Files and Folders that I have saved to other HD like the ones I have just created.  

(These two are FAT32 32gb)
SDE1 /MEDIA/INBOX
SDE5 /MEDIA/LINUX_BKUP

(This one is NTFS-3G 80gb)
SDE6 /MEDIA/MICS

If I right click on files or folders that I have just saved or created in these partitions, (properties/permissions) you can't make adjustments.  Any permissions are unavailable to change.  For the owner it says ROOT?  Why when I'm the one that just created it?  :confused:

I suspect that my issue here lies in System/Administration/Users and Groups for the settings selected for myself as a user?

My original intent here has been to create a clean partition without any restrictions for sharing files between Winxp (NTFS) and Ubuntu (EXT3).

If it helps here is a break down of my HD partitions along with there current file format.

SDA1 /NEDIA/IDE_FILES NTFS-3G 
SDB1 /MEDIA/WIN_XP NTFS-3G
SDC1 / EXT3 
SDD1 /MEDIA/GAMES NTFS-3G 
SDE1 /MEDIA/INBOX VFAT 
SDE5 /MEDIA/LINUX_BKUP VFAT 
SDE6 /MEDIA/MICS NTFS-3G 

Thanks for all your help!:)

---

### Post by taurus on 2008-12-29
How do you mount those partitions?  Post the outputs of these commands from a terminal.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by wizard10000 on 2008-12-29
FAT32 doesn't support setting permissions on files or folders.  On the Linux side since root mounted the partition root owns the files :)

---

### Post by sandman3838 on 2008-12-29
Since posting this I have done some more reading from others on this.
Below is the information you requested and some extra?
I hope it helps?  Thank you!

MORE INFO THESE COMMANDS SHOWED:

sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
ls -la /media
id

******* sudo fdisk -l  

kevin@Larry-Ubuntu:~$ sudo fdisk -l
[sudo] password for kevin: 

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb329b329

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24792   199141708+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa411a411

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06e41ad8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       18662   149902483+  83  Linux
/dev/sdc2           18663       19457     6385837+   5  Extended
/dev/sdc5           18663       19457     6385806   82  Linux swap / Solaris

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x66305c95

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sde: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38e1d7dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1        4023    32314716    c  W95 FAT32 (LBA)
/dev/sde2            4024       19929   127764945    f  W95 Ext'd (LBA)
/dev/sde5            4024        8056    32395041    b  W95 FAT32
/dev/sde6            8057       19929    95369841    7  HPFS/NTFS
kevin@Larry-Ubuntu:~$ 

********  sudo blkid

kevin@Larry-Ubuntu:~$ sudo blkid
/dev/sda1: UUID="01C62F4B85E703C0" LABEL="IDE_FILES" TYPE="ntfs" 
/dev/sdb1: UUID="4A2CACCC2CACB47B" LABEL="WIN_XP" TYPE="ntfs" 
/dev/sdc1: UUID="c3000fbc-a66f-4d8e-9da7-a382d76964c8" TYPE="ext3" 
/dev/sdd1: UUID="01C724C13F7D1AC0" LABEL="SATA_GAMES" TYPE="ntfs" 
/dev/sde1: LABEL="INBOX" UUID="DCD9-EA27" TYPE="vfat" 
/dev/sdc5: TYPE="swap" UUID="e22175bd-2dbe-4e5f-a7fa-69914bfb7efe" 
/dev/sde5: LABEL="LINUX_BKUP" UUID="BCDA-49A5" TYPE="vfat" 
/dev/sde6: UUID="AC70DD8670DD57A2" LABEL="MICS" TYPE="ntfs" 
kevin@Larry-Ubuntu:~$

********   cat /etc/fstab

kevin@Larry-Ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdc1 :
UUID=c3000fbc-a66f-4d8e-9da7-a382d76964c8 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda1 :
UUID=01C62F4B85E703C0 /media/IDE_FILES_ ntfs-3g defaults,locale=en_US.UTF-8 0 0
# Entry for /dev/sde1 :
UUID=DCD9-EA27 /media/INBOX vfat defaults,utf8,umask=0 0 2
# Entry for /dev/sde5 :
UUID=BCDA-49A5 /media/LINUX_BKUP vfat defaults,utf8,umask=0 0 2
# Entry for /dev/sde6 :
UUID=AC70DD8670DD57A2 /media/MICS ntfs-3g defaults,locale=en_US.UTF-8 0 0
# Entry for /dev/sdd1 :
UUID=01C724C13F7D1AC0 /media/SATA_GAMES ntfs-3g defaults,locale=en_US.UTF-8 0 0
# Entry for /dev/sdb1 :
UUID=4A2CACCC2CACB47B /media/WIN_XP ntfs-3g defaults,locale=en_US.UTF-8 0 0
# Entry for /dev/sdc5 :
UUID=e22175bd-2dbe-4e5f-a7fa-69914bfb7efe none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
kevin@Larry-Ubuntu:~$ 

********  df -h  

kevin@Larry-Ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc1             141G   11G  124G   8% /
tmpfs                 1.8G     0  1.8G   0% /lib/init/rw
varrun                1.8G  308K  1.8G   1% /var/run
varlock               1.8G     0  1.8G   0% /var/lock
udev                  1.8G  2.9M  1.8G   1% /dev
tmpfs                 1.8G  104K  1.8G   1% /dev/shm
lrm                   1.8G  2.0M  1.8G   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sda1             190G  129G   61G  68% /media/IDE_FILES_
/dev/sde1              31G  192K   31G   1% /media/INBOX
/dev/sde5              31G   32K   31G   1% /media/LINUX_BKUP
/dev/sde6              91G   68M   91G   1% /media/MICS
/dev/sdd1             233G   95G  139G  41% /media/SATA_GAMES
/dev/sdb1             233G   33G  201G  15% /media/WIN_XP
kevin@Larry-Ubuntu:~$ 

*******  ls -la /media

kevin@Larry-Ubuntu:~$ ls -la /media
total 124
drwxr-xr-x 10 root root  4096 2008-12-29 09:40 .
drwxr-xr-x 20 root root  4096 2008-12-10 01:06 ..
lrwxrwxrwx  1 root root     6 2008-12-09 19:24 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2008-12-09 19:24 cdrom0
-rw-rw-rw-  1 root root    74 2008-12-29 10:14 .created_by_python-fstab
-rw-r--r--  1 root root     0 2008-12-29 09:40 .hal-mtab
drwxr-xr-x  2 root root  4096 2008-12-12 01:28 IDE_FILES
drwxrwxrwx  1 root root 12288 2008-12-27 21:09 IDE_FILES_
drwxrwxrwx  2 root root 32768 1969-12-31 18:00 INBOX
drwxrwxrwx  2 root root 32768 1969-12-31 18:00 LINUX_BKUP
drwxrwxrwx  1 root root  4096 2008-12-28 14:45 MICS
drwxrwxrwx  1 root root 12288 2008-12-27 15:03 SATA_GAMES
drwxrwxrwx  1 root root 12288 2008-12-27 15:03 WIN_XP
kevin@Larry-Ubuntu:~$ 

*********** ID  

kevin@Larry-Ubuntu:~$ id
uid=1000(kevin) gid=1000(kevin) groups=0(root),4(adm),20(dialout),24(cdrom),29(audio),46(plugdev),106(fuse),108(lpadmin),114(netdev),123(admin),124(sambashare),1000(kevin)
kevin@Larry-Ubuntu:~$

---

### Post by albinootje on 2008-12-29
> **sandman3838 said:**
> 
uid=1000(kevin) gid=1000(kevin) groups=0(root),4(adm),20(dialout),24(cdrom),29(audio),46(plugdev),106(fuse),108(lpadmin),114(netdev),123(admin),124(sambashare),1000(kevin)


You can use your uid and gid in the mount options for /etc/fstab to enhance your permissions on those partitions.
Check :
```

man mount 

```
Or find examples on the net.

---

### Post by sandman3838 on 2008-12-29
You can also right clicking on them and select Mount or Un-mount drive or use System - Administration - Disk Manager!

Getting them Mounted or not is not the issue. It's access to permissions for the files and folders on the drive.

---

### Post by albinootje on 2008-12-29
> **sandman3838 said:**
> You can also right clicking on them and select Mount or Un-mount drive or use System - Administration - Disk Manager!

Getting them Mounted or not is not the issue. It's access to permissions for the files and folders on the drive.

I mentioned *adding* the uid=1000,gid=1000 mount options to give you more permission rights while mounting the partitions.

umask=000 as a mount option can also help.

Can you test that by editing /etc/fstab and see the difference after unmounting and mounting again ?

---

### Post by sandman3838 on 2008-12-29
Hello Thanks for the help!

FSTAB displays:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/sdc1 :
UUID=c3000fbc-a66f-4d8e-9da7-a382d76964c8	/	ext3	relatime,errors=remount-ro	0	1
#Entry for /dev/sda1 :
UUID=01C62F4B85E703C0	/media/IDE_FILES_	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/sde1 :
UUID=DCD9-EA27	/media/INBOX_	vfat	defaults,utf8,umask=0	0	2
#Entry for /dev/sde5 :
UUID=BCDA-49A5	/media/LINUX_BKUP	vfat	defaults,utf8,umask=0	0	2
#Entry for /dev/sde6 :
UUID=AC70DD8670DD57A2	/media/MICS	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/sdd1 :
UUID=01C724C13F7D1AC0	/media/SATA_GAMES	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/sdb1 :
UUID=4A2CACCC2CACB47B	/media/WIN_XP	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/sdc5 :
UUID=e22175bd-2dbe-4e5f-a7fa-69914bfb7efe	none	swap	sw	0	0
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0

********* 

Where should I add:
uid=1000,gid=1000 mount options

Also, it looks like what your changing here is uid=userid and gid=groupid.

If I remember correctly this is also offered in Administration-User and Groups when you select Properties on Root or Myself.  At the moment Root=0  and Kevin=1000

Are we talking the same thing here?

---

### Post by albinootje on 2008-12-29
> **sandman3838 said:**
> 

Where should I add:
uid=1000,gid=1000 mount options

For example :
UUID=01C724C13F7D1AC0 /media/SATA_GAMES ntfs-3g defaults,locale=en_US.UTF-8,uid=1000,gid=1000 0 0

> 
Also, it looks like what your changing here is uid=userid and gid=groupid.

If I remember correctly this is also offered in Administration-User and Groups when you select Properties on Root or Myself.  At the moment Root=0  and Kevin=1000

Are we talking the same thing here?

Correct.
The first user created during installation of Ubuntu gets uid 1000, and root always has uid 0.

---

### Post by sandman3838 on 2008-12-29
Here is what I came up with after your suggestion!
However FSTAB is a read only!

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>

proc /proc proc defaults 0 0
#Entry for /dev/sdc1 :
UUID=c3000fbc-a66f-4d8e-9da7-a382d76964c8 / ext3 relatime,errors=remount-ro 0 1
#Entry for /dev/sda1 :
UUID=01C62F4B85E703C0 /media/IDE_FILES_ ntfs-3g defaults,locale=en_US.UTF-8 0 0
#Entry for /dev/sde1 :
UUID=DCD9-EA27 /media/INBOX_ vfat defaults,utf8,uid=1000,gid=1000 umask=0 0 2
#Entry for /dev/sde5 :
UUID=BCDA-49A5 /media/LINUX_BKUP vfat defaults,utf8,uid=1000,gid=1000 umask=0 0 2
#Entry for /dev/sde6 :
UUID=AC70DD8670DD57A2 /media/MICS ntfs-3g defaults,locale=en_US.UTF-8,uid=1000,gid=1000 0 0
#Entry for /dev/sdd1 :
UUID=01C724C13F7D1AC0 /media/SATA_GAMES ntfs-3g defaults,locale=en_US.UTF-8 0 0
#Entry for /dev/sdb1 :
UUID=4A2CACCC2CACB47B /media/WIN_XP ntfs-3g defaults,locale=en_US.UTF-8 0 0
#Entry for /dev/sdc5 :
UUID=e22175bd-2dbe-4e5f-a7fa-69914bfb7efe none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

---

### Post by albinootje on 2008-12-29
> **sandman3838 said:**
> 
However FSTAB is a read only!


Did you try with sudo ?
```

sudo gedit /etc/fstab

```

---

### Post by sandman3838 on 2008-12-29
WOW!
That did it!
I applied "uid=1000,gid=1000" to the other HD as well.  Except for the Linux HD!  I was scared to touch it!  :)

I can now edit without issue, at least any that I can see so far.
If I Right click - Properties - Permissions on a folder that I have created I can now access the Permission options.  See Screen Shot!

Odd, I can see why Ubuntu would restrict file and HD access to the File Systems or Hidden folders in the HOME folder but get this difficult just to access HD outside of Ubuntu is strange?  Keep in mind I'm coming at this from a Win perspective.  There I would just log on as Administrator and I was able to read issue or change anything.

Here with Ubuntu I couldn't access permissions from file or folder properties to items outside of Ubuntu?  It seems like this could be a lot easier?

While were here!  If you had noticed two of the HD partitions were Fat32 or VFAT.  I read somewhere that this format was prefered to share files to and from my Winxp and Ubuntu.  Is this correct?

Also, I read that when creating Fat32/Vfat I needed to create this from Winxp and I did but was limited to 32 gb size while with Ununtu Vfat could have used up the whole HD.  Did I do the right thing here by letting Winxp create the partitions?

Thanks for your help!

---

### Post by albinootje on 2008-12-29
> **sandman3838 said:**
>  While were here!  If you had noticed two of the HD partitions were Fat32 or VFAT.  I read somewhere that this format was prefered to share files to and from my Winxp and Ubuntu.  Is this correct?

A quick reply to this question :

FAT32 is often called vfat in Linux.

FAT32 has a 4 Gb file size limit, and it will give you less free space compared to NTFS, but FAT32 can be very handy when you want to share files with Windows- and Mac-users.

If you only want to share between Linux and Windows then NTFS could be a better choice.

Concerning your other questions, perhaps you can mark this thread as SOLVED, and start a new thread about formatting FAT32 partitions in Linux or Windows etc.

---

### Post by sandman3838 on 2008-12-30
It's working fine!
I'll change the Partitions to NTFS!

---

