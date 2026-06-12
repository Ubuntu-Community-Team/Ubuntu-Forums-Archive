---
title: "Cannot automount this HD"
date: 2009-04-19
forum: General Help
---

### Post by puner on 2009-04-19
Hello

No matter which version of ubuntu I install this HD never automounts. I always had to go to Places>New Volume to open the contents. So that means if I apply a wallpaper from New Volume, the next time I restart the computer, my wallpaper won't be as it was because New Volume did not automount. 

Same thing happens with adding music to Rhythm Box. I cant see my music in the library until I manually mount New Volume.

But ever since I installed 9.04 RC, I cant even manually mount the drive. I always get the error;

```

**Unable to mount Entertainment**

DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

``` 


```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbba6bba6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9ccf9ccf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       11030    88598443+   7  HPFS/NTFS
/dev/sdb2           11031       11279     2000092+  82  Linux swap / Solaris
/dev/sdb3           11280       14946    29455177+  83  Linux

Disk /dev/sdc: 10.2 GB, 10242892800 bytes
64 heads, 32 sectors/track, 9768 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x000e13df

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9767    10001392    7  HPFS/NTFS
```

---

### Post by kevstar31 on 2009-04-19
post the output of:
```
cat /etc/fstab
```

---

### Post by puner on 2009-04-19
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                    0  0  
# / was on /dev/sdb3 during installation
UUID=f4a64557-557c-430a-90c8-8f60c8ce7af2  /               ext3         relatime,errors=remount-ro  0  1  
# swap was on /dev/sdb2 during installation
UUID=611d0c53-61d3-4e16-98fd-8309a7f4440e  none            swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sdd                                   /media/floppy0  auto         rw,user,noauto,exec,utf8    0  0  
/dev/sdc1                                  /media/sdc1     ntfs         defaults                    0  0  
/dev/sdb1                                  /media/sdb1     ntfs         defaults                    0  0 
/dev/sda1				   /media/sda1     ntfs         defaults
```

---

### Post by anandamide on 2009-04-26
Ditto. One of my partitions (frustratingly, the one with all my photos, music and films on) doesn't mount at boot, and never has done.

Here's (a messy) fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=b77f53e9-4b83-4565-9336-290b40a813ee /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda1
UUID=18968AF0968ACE26 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=7CEA-C091  /media/disk        ntfs    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=4e78c283-95bd-4a30-a4e4-bd5cb03a56c2 none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

sda6 is the one I'm having problems with.

---

### Post by anandamide on 2009-05-02
Bump? I can't see what could be going wrong :-( . Although unlike puner I can at least manually mount (still).

---

### Post by danwood76 on 2009-05-02
@puner

Which volume are you trying to mount and have you made a mountpoint for it?
You should also note that because the drive is NTFS if it has errors marked in the journal it will not mount either (normally due to a bad shutodown). If you load up windows and check all disks you might have more chance of mounting.

@ Anandamide

Can you post the output of the following two commands:
```

sudo blkid # This will dump the UUIDs per disk
sudo fdisk -l # Will dump your partiiton makeup

```

---

### Post by anandamide on 2009-05-03
Thanks for the reply :-). Here ya go:

```

/dev/sda1: UUID="18968AF0968ACE26" TYPE="ntfs" 
/dev/sda2: UUID="b77f53e9-4b83-4565-9336-290b40a813ee" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="4e78c283-95bd-4a30-a4e4-bd5cb03a56c2" 
/dev/sda6: UUID="A6E00D07E00CDF83" TYPE="ntfs" 
philip@dendrite:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8625edcc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11588    93077148+   7  HPFS/NTFS
/dev/sda2           11589       23176    93080610   83  Linux
/dev/sda3           23177       38913   126407452+   5  Extended
/dev/sda5           37801       38913     8940141   82  Linux swap / Solaris
/dev/sda6           23177       37800   117467217    7  HPFS/NTFS

```

---

### Post by danwood76 on 2009-05-03
The UUID is wrong in your fstab.

Change this line:
```

UUID=7CEA-C091  /media/disk        ntfs    defaults,utf8,umask=007,gid=46 0       1

```
to this:
```

UUID=A6E00D07E00CDF83  /media/disk        ntfs    defaults,utf8,umask=007,gid=46 0       1

```
That should then work as long as the mountpoint is setup correctly.

---

### Post by Bigneil on 2009-05-03
i had a similar problem the other day, i didn't want to get all mixed up in typing clever gobbaldygook into the terminal because i dont really understand what it all means. but some one pointed me in the direction of 'NTFS configuration tool' which enabled me with a nice simple graphical interface to set up auto-mounting for my secondary internal drive.

---

### Post by anandamide on 2009-05-05
Thanks Dan, that's solved the problem easily!

Have a cigar!

---

