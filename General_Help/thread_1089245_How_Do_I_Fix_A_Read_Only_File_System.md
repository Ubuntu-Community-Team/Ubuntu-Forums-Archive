---
title: "How Do I Fix A Read Only File System"
date: 2009-03-06
forum: General Help
---

### Post by Mr Fredrick on 2009-03-06
Hi All,

One of the messages that are printed to the screen during the start-up boot sequence states that my file system is "Read Only".

Is this a problem and if it is how can I trouble shoot / fix it?

Thanks in advance,

MrFred

Note: I don't have the Ubuntu LiveCD.

---

### Post by taurus on 2009-03-06
Can you post the outputs of these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by Mr Fredrick on 2009-03-06
Hi Taurus,

Here are the results:

```

peter@peter-laptop:~$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           9       72261   de  Dell Utility
/dev/sda2   *          10        2690    21535132+   7  HPFS/NTFS
/dev/sda3            6426       10842    35479552+  83  Linux
/dev/sda4           10843       11499     5277352+  82  Linux swap / Solaris
peter@peter-laptop:~$

```

```

peter@peter-laptop:~$ cat /etc/fstab
proc            /proc           proc    defaults        0       0
UUID=a50754d8-3591-4365-9ae4-c9bc603ef829 /               ext3    defaults,errors=remount-ro,relatime 0       1
UUID=07D7-0818  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
UUID=40ACD4A2ACD493AE /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
UUID=efc78d4d-c9de-4659-acdc-ce037ccb89c5   none   swap   sw   0   0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
peter@peter-laptop:~$ 

```


```

peter@peter-laptop:~$ sudo blkid
[sudo] password for peter: 
/dev/sda1: SEC_TYPE="msdos" UUID="07D7-0818" TYPE="vfat" 
/dev/sda2: UUID="40ACD4A2ACD493AE" TYPE="ntfs" 
/dev/sda3: UUID="a50754d8-3591-4365-9ae4-c9bc603ef829" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: TYPE="swap" UUID="efc78d4d-c9de-4659-acdc-ce037ccb89c5" 
peter@peter-laptop:~$

```

```

peter@peter-laptop:~$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/sda3              34G  7.4G   25G  24% /
tmpfs                1012M     0 1012M   0% /lib/init/rw
varrun               1012M  108K 1012M   1% /var/run
varlock              1012M     0 1012M   0% /var/lock
udev                 1012M  2.8M 1009M   1% /dev
tmpfs                1012M  108K 1012M   1% /dev/shm
/dev/sda1              71M  7.7M   63M  11% /media/sda1
/dev/sda2              21G   13G  8.3G  60% /media/sda2
peter@peter-laptop:~$

```

Thanks for the help!

---

### Post by taurus on 2009-03-06
> **Mr Fredrick said:**
> Hi Taurus,

Here are the results:

```

peter@peter-laptop:~$ cat /etc/fstab
proc            /proc           proc    defaults        0       0
UUID=a50754d8-3591-4365-9ae4-c9bc603ef829 /               ext3    **[COLOR="Red"]defaults,[/COLOR]**errors=remount-ro,relatime 0       1
UUID=07D7-0818  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       **[COLOR="Red"]1[/COLOR]**
UUID=40ACD4A2ACD493AE /media/sda2     ntfs    defaults,umask=007,gid=46 0       **[COLOR="Red"]1[/COLOR]**
UUID=efc78d4d-c9de-4659-acdc-ce037ccb89c5   none   swap   sw   0   0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
peter@peter-laptop:~$ 

```

```

peter@peter-laptop:~$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/sda3              34G  7.4G   25G  24% /
tmpfs                1012M     0 1012M   0% /lib/init/rw
varrun               1012M  108K 1012M   1% /var/run
varlock              1012M     0 1012M   0% /var/lock
udev                 1012M  2.8M 1009M   1% /dev
tmpfs                1012M  108K 1012M   1% /dev/shm
/dev/sda1              71M  7.7M   63M  11% /media/sda1
/dev/sda2              21G   13G  8.3G  60% /media/sda2
peter@peter-laptop:~$

```

Thanks for the help!

It's probably nothing but on my machine, I don't have the **defaults** for /.

Also, I would recommend you replace the 1 to 0 for the two entries for windows (or recovery partition--vfat--and windows partition--ntfs).

Then save it and reboot.

---

