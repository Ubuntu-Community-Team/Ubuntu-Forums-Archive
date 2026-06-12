---
title: "Ubuntu fails when booting"
date: 2009-02-10
forum: General Help
---

### Post by michael1384 on 2009-02-10
Whenever I turn my computer on I get this:
> 	*checking file systems...
1016
fsck 1.41.3 (12-Oct-2008 )
/dev/sdb5 is mounted. e2fsck: Cannot continue, aborting.


fsck dies with exit status 8
										[fail]
	*File system check failed.
A log is being saves in /var/log/fsck/checkfs if that location is writable.
Please repair the file system manually.
	*A maintenance shell will now be started.
Control-D will terminate this shell and resume system boot.
bash: no job control in this shell
root@michael-desktop:~#


Usually I press control-D and get on with my life, but I just want to know if this is bad and how do I solve this problem?

---

### Post by taurus on 2009-02-10
You need to fsck your /dev/sdb5.

```
fsck /dev/sdb5
```

---

### Post by michael1384 on 2009-02-10
Now I am not privaleged to mount sdb5.

Or any USB disk

---

### Post by taurus on 2009-02-10
What are the outputs of these commands from a terminal?

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by Slim Odds on 2009-02-10
> **taurus said:**
> You need to fsck your /dev/sdb5.

```
fsck /dev/sdb5
```

His fsck failed because /dev/sdb5 was mounted.

---

### Post by michael1384 on 2009-02-10
```
sudo fdisk -l:
```

Produces this:

```

Disk /dev/sda: 1091 MB, 1091371008 bytes
64 heads, 63 sectors/track, 528 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x4aa55d6a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2         528     1062432    5  Extended
/dev/sda5               2         528     1062400+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xea448bcb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       11260    90445918+   7  HPFS/NTFS
/dev/sdb2           11261       14593    26772322+   f  W95 Ext'd (LBA)
/dev/sdb5           11261       14593    26772291   83  Linux

Disk /dev/sdc: 264 MB, 264634368 bytes
16 heads, 32 sectors/track, 1009 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1010      258416    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(1023, 15, 32) logical=(1009, 7, 32)

```

```
Sudo blkid
```

Produces this:

```
/dev/ramzswap0: TYPE="swap" 
/dev/sda5: TYPE="swap" UUID="52995a96-894f-48d2-90f1-6a4a90f9ba82" 
/dev/sdb1: UUID="26AC7D34AC7CFF9B" LABEL="HARDISK" TYPE="ntfs" 
/dev/sdb5: UUID="2913f55b-b03d-4e87-89be-97031e4d8f9f" TYPE="ext2" 
/dev/sdc1: SEC_TYPE="msdos" LABEL="USB DISK" UUID="0461-E031" TYPE="vfat" 

```

```
cat /etc/fstab
```

Produces this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
/dev/sdb5	/	ext2	relatime,errors=remount-ro	0	1
#Entry for /dev/sdb1 :
UUID=26AC7D34AC7CFF9B	/media/Programs	ntfs-3g	defaults,locale=en_GB.UTF-8	00
/dev/sdb5	/media/windows_	ext2	defaults	0	2
#Entry for /dev/sda5 :
UUID=52995a96-894f-48d2-90f1-6a4a90f9ba82	none	swap	sw	0	0
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0
/dev/sdc1	/media/Misc	ntfs-3g	defaults	0	0



```

```
df -h
```

Produces this:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb5              26G  3.7G   21G  16% /
tmpfs                 220M     0  220M   0% /lib/init/rw
varrun                220M  208K  220M   1% /var/run
varlock               220M     0  220M   0% /var/lock
udev                  220M  3.2M  217M   2% /dev
tmpfs                 220M  272K  220M   1% /dev/shm
lrm                   220M  2.0M  218M   1% /lib/modules/2.6.27-11-generic/volatile

```

Based on what I saw after typing those commands, I think sdb5 is the partition on which Ubuntu is installed. It won't let me access my Windows partition now.

---

### Post by taurus on 2009-02-10
Since /dev/sdb5 is your root partition, you have to run the fsck from the LiveCD.  Boot up the LiveCD.  Then, open a terminal and run

```
sudo fsck /dev/sdb5
```
Did you shutdown your windows cleanly the last time you used it?  There should be a space between the last two zeros in /etc/fstab for your ntfs partition.

```
UUID=26AC7D34AC7CFF9B	/media/Programs	ntfs-3g	defaults,locale=en_GB.UTF-8	**[COLOR="Red"]0 0[/COLOR]**
```

By the way, /dev/sdc1 is fat32/vfat but somehow you try to mount it with ntfs-3g in /etc/fstab!

```
/dev/sdc1 	/media/Misc	**[COLOR="Red"]ntfs-3g[/COLOR]**	defaults	0	0
```
Replace the **ntfs-3g** with **vfat** for /dev/sdc1.

---

### Post by michael1384 on 2009-02-10
How do I go about doing that?

---

### Post by taurus on 2009-02-10
Doing what?  Run fsck or edit /etc/fstab?

To edit /etc/fstab on root partition, /dev/sdb5, you first need to mount it

Applications -> Accessories -> Terminal
```
sudo mkdir /media/ubuntu
sudo mount -t ext2 /dev/sdb5 /media/ubuntu
```
and then edit /etc/fstab.

```
gksudo gedit /media/ubuntu/etc/fstab
```

---

### Post by michael1384 on 2009-02-11
I've done everything you suggested. I still get the error when it boots.

I still don't have permission to mount any usb storage volumes.

---

