---
title: "Fsck forced on ntfs, why? How do I stop it?"
date: 2007-02-11
forum: Desktop Environments
---

### Post by Explosive_Cornflake on 2007-02-11
Hi all.
Hope this is the right place.
I've tried searching but can't find what I need. 
Running (K)Ubuntu 6.10
Anywho, my / was sda5 and /home was sda7. I had a NTFS on sda6. I got a free copy of vista so I installed it. I chopped sda6 upo a bit, and had a new blank ntfs as sda7, and home is now sda8. Mounting by UUID, this shouldn't have been a problem, which is the way fstab is doing things.
My problem is, everytime i boot an fsck is attempted and fails on sda7. It for some resons thinks it's ext2. (/ /home were ext3).
This still happens everytime i boot, (the control-d to continue screen on tty8), and i've removed all references to that partition.
Anyway, some useful info
fdisk -l
```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            2612        2872     2096482+  82  Linux swap / Solaris
/dev/sda3            2873       38913   289499332+   f  W95 Ext'd (LBA)
/dev/sda5            2873        5483    20972826   83  Linux
/dev/sda6            5484       23438   144223506    7  HPFS/NTFS
/dev/sda7           23439       26370    23548928    7  HPFS/NTFS
/dev/sda8           26371       38913   100751616   83  Linux

```
/etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system>         <mount point>           <type>  <options>       <dump>  <pass>

proc                    /proc                   proc    defaults        0       0

#******Local**********#
# /dev/sda5
UUID=cbf59a44-75f1-4286-bedc-b0b5f33e6157 /     ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=D2B02B56B02B3FF9   /media/xp               ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /dev/sda7
#UUID=DA5635CE5635AC5F   /media/vista           ntfs    defaults,nls=utf8,umask=007,gid=46,noauto 0       0
#home dir /dev/sda8
UUID=292ebcee-d52a-49df-999c-24e8a90a51cb       /home          ext3    defaults,errors=remount-ro 0       2
#Games, ntfs /sda6
UUID=12E2DF9D0E5A5D41 /media/Games              ntfs    defaults,nls=utf8,umask=007,gid=46 0    0
# /dev/sda2
UUID=734c0c67-8b93-4cc6-bb76-893d0765e798 none            swap    sw                            0       0
#****Special*****#
/dev/hdb                /media/cdrom0   udf,iso9660 user,noauto                                 0       0
/dev/hda                /media/cdrom1   udf,iso9660 user,noauto                                 0       0
/dev/                   /media/floppy0  auto    rw,user,noauto                                  0       0
/dev/sdc                /media/floppy1  auto    rw,user,noauto                                  0       0
#******Remote****#
#//192.168.3.200/Music  /media/Music    cifs    guest                                           0       0
#//192.168.3.200/Writeable /media/Writeable cifs        guest                                   0       0
192.168.3.200:/media/sda1/Video /media/Video nfs rw                                             0       0
192.168.3.200:/media/sdb1/Writeable /media/Writeable nfs rsize=8192,wsize=8192,timeo=14,intr    0       0
192.168.3.200:/media/hda3/Music /media/Music    nfs rsize=8192,wsize=8192,timeo=14,intr         0       0
192.168.3.2:/mnt/raid/ftp /media/Pollock/       nfs rsize=8192,wsize=8192,timeo=14,intr         0       0

```

and /var/log/fsck/checkfs
```
Log of fsck -C -R -A -a
Sun Feb 11 13:11:50 2007

fsck 1.39 (29-May-2006)
fsck.ext3: Bad magic number in super-block while trying to open /dev/sda7
/dev/sda7:
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 8

Sun Feb 11 13:11:50 2007
----------------

```

Does anyone know, what is calling this fsck, and how do I stop it?
Any help appricated,
Ciarán.

---

### Post by Explosive_Cornflake on 2007-02-12
Any ideas?

---

### Post by dcstar on 2007-02-12
> **Explosive_Cornflake said:**
> Any ideas?

Most likely you have changed the UUIDs when you installed the other O/S, and now your fstab file is not correct.

You need to verify the UUID of all of your partitions and fix your fstab file with the new data, do a forum search for the command to find these (I cannot remember how).

---

### Post by Explosive_Cornflake on 2007-02-13
UUID's are correct, I've verified them. /home wouldn't mount if it was wrong.

---

### Post by Explosive_Cornflake on 2007-03-12
I still have this issue.
I have no reference to sda7 UUID or otherwise.
```

ccoffey@Zoidberg:~$ ls /dev/disk/by-uuid/ -l | grep sda7
lrwxrwxrwx 1 root root 10 2007-03-12 03:38 DA5635CE5635AC5F -> ../../sda7
ccoffey@Zoidberg:~$ grep DA5635CE5635AC5F /etc/fstab | wc -l
0
ccoffey@Zoidberg:~$ grep sda7 /etc/fstab | wc -l
0

```
and i still get 
```
ccoffey@Zoidberg:~$ cat /var/log/fsck/checkfs
Log of fsck -C -R -A -a
Mon Mar 12 03:38:25 2007

fsck 1.39 (29-May-2006)
fsck.ext3: Bad magic number in super-block while trying to open /dev/sda7
/dev/sda7:
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 8

Mon Mar 12 03:38:25 2007
----------------
```
Can anyone shine any light on this?

---

