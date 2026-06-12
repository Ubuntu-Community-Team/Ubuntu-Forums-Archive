---
title: "I Can Not Control etc/fstab Eventhough i'm the Root"
date: 2009-01-20
forum: General Help
---

### Post by f.ben.isaac@gmail.com on 2009-01-20
I'm trying to let my ext3 recognized. I did this

sudo echo " /dev/sdb2 /media/BackTrack3 ext3 user,umask=002 0 0" >> /etc/fstab

but i get this:

bash: /etc/fstab: Permission denied

1. What should i do?

2. After i unmounted my dev/sdb2 manually by umount /dev/sdb2/,
i can not mount it manually. If i do sudo mount /dev/sdb2/, or
sudo mount /media/BackTrack3, i get this message:

mount: can't find /dev/sdb2 in etc/fstab or etc/mtab

What can i do?

3. Can you translate this in words:
 /dev/sdb2 /media/BackTrack3 ext3 user,umask=002 0 0

What this line says?

4. is every partition stored in fstab & mtab?

5. What is the difference between them?

---

### Post by taurus on 2009-01-20
Open a terminal and edit your /etc/fstab

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sdb2   /media/BackTrack3   ext3   defaults   0   2
```
Save it and close down gedit editing window.  Now, mount the new partition, /dev/sdb2, assuming your have already created the new mount point, /media/backTrack3.

---

### Post by f.ben.isaac@gmail.com on 2009-01-20
I deleted all my ext3 partition. I'm trying to partition it from ubuntu through fdisk. I did fdisk /dev/sdb/, i get reply unable to open dev/sdb/

I'm pretty sure my usb is on sdb, i did cat /proc/partitions to find it...

Why my fdisk can unable to open dev/sdb?

---

### Post by taurus on 2009-01-20
Post the output of this command from a terminal.

```
sudo fdisk -l
```

---

### Post by The Cog on 2009-01-20
You need root privs to use fdisk:
> sudo fdisk /dev/sdb

Your problem with 
sudo echo " /dev/sdb2 /media/BackTrack3 ext3 user,umask=002 0 0" >> /etc/fstab
is that the sudo is that it tries to open the pipe to fstab before opening a sudo process. The easiest way round this is:
> sudo -i
echo " /dev/sdb2 /media/BackTrack3 ext3 user,umask=002 0 0" >> /etc/fstab
but using an editor like this is easier (if you have a GUI):
> gksu gedit /etc/fstab

---

### Post by f.ben.isaac@gmail.com on 2009-01-20
```


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x36b18584

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            5100       10199    40961024    7  HPFS/NTFS
/dev/sda2           10199       15298    40960000    7  HPFS/NTFS
/dev/sda3   *       15298       30402   121316352    7  HPFS/NTFS
/dev/sda4               1        5100    40959968+   7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20ee4f6a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               4       13053   104824125    7  HPFS/NTFS



```

---

### Post by f.ben.isaac@gmail.com on 2009-01-20
> **The Cog said:**
> You need root privs to use fdisk:


Your problem with 
sudo echo " /dev/sdb2 /media/BackTrack3 ext3 user,umask=002 0 0" >> /etc/fstab
is that the sudo is that it tries to open the pipe to fstab before opening a sudo process. The easiest way round this is:

but using an editor like this is easier (if you have a GUI):

i already deleted my partition ext3, anyhow i will check it out later

---

### Post by taurus on 2009-01-20
> **f.ben.isaac@gmail.com said:**
> ```


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x36b18584

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            5100       10199    40961024    7  HPFS/NTFS
/dev/sda2           10199       15298    40960000    7  HPFS/NTFS
/dev/sda3   *       15298       30402   121316352    7  HPFS/NTFS
/dev/sda4               1        5100    40959968+   7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20ee4f6a

   Device Boot      Start         End      Blocks   Id  System
**[COLOR="Blue"]/dev/sdb1               4       13053   104824125    7  HPFS/NTFS[/COLOR]**


```

First, there is no /dev/sdb2.  You only have on partition on your second harddrive and it is ntfs filesystem.  Therefore, if you added the /dev/sdb1 line in /etc/fstab, you need to remove it.

Then, use ntfs-config to configure and mount /dev/sdb1.

```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

p.s.  Do you even have Ubuntu running on your machine (except from the LiveCD) since all your partitions are all ntfs?

---

### Post by f.ben.isaac@gmail.com on 2009-01-20
> **taurus said:**
> First, there is no /dev/sdb2.  You only have on partition on your second harddrive and it is ntfs filesystem.  Therefore, if you added the /dev/sdb1 line in /etc/fstab, you need to remove it.

Then, use ntfs-config to configure and mount /dev/sdb1.

```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

p.s.  Do you even have Ubuntu running on your machine (except from the LiveCD) since all your partitions are all ntfs?

sdb2 that was before i deleted my partition. Now, sdb2 does not show as i already deleted the ext2 partition.

I installed ubuntu on Windows. Ubuntu is in windows.

---

### Post by taurus on 2009-01-20
So you are using wubi.

---

### Post by f.ben.isaac@gmail.com on 2009-01-20
> **taurus said:**
> So you are using wubi.

Yes temporarily...

---

