---
title: "want to share Windows partition on Samba unable to change permissions"
date: 2011-12-12
forum: Desktop Environments
---

### Post by jamesbon on 2011-12-12
I have a windows partition which I Can easily access via nautilus gui.Without manually mounting the partition.When I click on the hard disk icon it automatically gets mounted at /media.

```
 sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x711e302a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   163839999    81816576    7  HPFS/NTFS/exFAT
/dev/sda3       163840000   368639999   102400000    7  HPFS/NTFS/exFAT
/dev/sda4       368640000   625139711   128249856    f  W95 Ext'd (LBA)
/dev/sda5       368642048   625139711   128248832    7  HPFS/NTFS/exFAT

```

Here is my /etc/fstab file 

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
~                                                                          
```

and following are entries of smb.conf
```

[hell]
   comment = Winows files
   read only = yes
   locking = no
   browseable = yes
   path = /media/New\ Volume
   guest ok = yes
   public = yes

```

The client machine tried to connect but it failed to mount the Windows partition from the server.
Upon digging a further I noticed the permissions of volume in /media for others and group are 00
The permissions I see are 

```
deel@ubuntu:/media$ ls -l
total 16
drwx------ 1 deel deel 16384 2011-11-16 10:33 New Volume  

```

So assuming that samba client process does not have read permissions to above I tried to change the permissions at server.
```

deel@ubuntu:/media$ sudo chmod 755 New\ Volume/  

```
But now they did not changed
```

deel@ubuntu:/media$ ls -l  

total 16
drwx------ 1 deel deel 16384 2011-11-16 10:33 New Volume

```If you notice in above even after changing permissions the permissions have not changed. What could be the reason and how can I share the windows partition on samba server to my network?

---

### Post by oldtimer7777 on 2011-12-12
Just to be sure, did you install:
sudo apt-get install ntfs-3g
> **jamesbon said:**
> I have a windows partition which I Can easily access via nautilus gui.Without manually mounting the partition.When I click on the hard disk icon it automatically gets mounted at /media.

```
 sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x711e302a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   163839999    81816576    7  HPFS/NTFS/exFAT
/dev/sda3       163840000   368639999   102400000    7  HPFS/NTFS/exFAT
/dev/sda4       368640000   625139711   128249856    f  W95 Ext'd (LBA)
/dev/sda5       368642048   625139711   128248832    7  HPFS/NTFS/exFAT

```Here is my /etc/fstab file 

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
~                                                                          
```and following are entries of smb.conf
```

[hell]
   comment = Winows files
   read only = yes
   locking = no
   browseable = yes
   path = /media/New\ Volume
   guest ok = yes
   public = yes

```The client machine tried to connect but it failed to mount the Windows partition from the server.
Upon digging a further I noticed the permissions of volume in /media for others and group are 00
The permissions I see are 

```
deel@ubuntu:/media$ ls -l
total 16
drwx------ 1 deel deel 16384 2011-11-16 10:33 New Volume  

```So assuming that samba client process does not have read permissions to above I tried to change the permissions at server.
```

deel@ubuntu:/media$ sudo chmod 755 New\ Volume/  

```But now they did not changed
```

deel@ubuntu:/media$ ls -l  

total 16
drwx------ 1 deel deel 16384 2011-11-16 10:33 New Volume

```If you notice in above even after changing permissions the permissions have not changed. What could be the reason and how can I share the windows partition on samba server to my network?

---

### Post by jamesbon on 2011-12-12
yes

---

### Post by Morbius1 on 2011-12-12
When you mount an ntfs partition from nautilus it mounts with you being the only one that can access it. That's by design. You can't do a chmod or chown on an ntfs partition since there are no linux permissions or ownership "bits" to set but there is an easy way out of this problem.

Change this:
> [hell]
   comment = Winows files
   read only = yes
   locking = no
   browseable = yes
   path = /media/New\ Volume
   guest ok = yes
   public = yesTo this
> [hell]
    comment = Winows files
    read only = yes
    locking = no
    browseable = yes
    path = /media/New\ Volume
    guest ok = yes
[COLOR=Blue]**force user = deel**[/COLOR]
    public = yesThen restart samba:
```
sudo service smbd restart
```The remote "guest" will be converted to "deel" for that share and therefore will have access to the directory but still be controlled by the "read only = yes" restriction in the share definition.

---

### Post by jamesbon on 2011-12-14
> **Morbius1 said:**
> When you mount an ntfs partition from nautilus it mounts with you being the only one that can access it. That's by design. You can't do a chmod or chown on an ntfs partition since there are no linux permissions or ownership "bits" to set but there is an easy way out of this problem.
Thanks for clearing this out.

> **Morbius1 said:**
> 
The remote "guest" will be converted to "deel" for that share and therefore will have access to the directory but still be controlled by the "read only = yes" restriction in the share definition.

This is a good suggestion.

---

