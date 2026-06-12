---
title: "corrupted ext3 file system"
date: 2009-06-05
forum: General Help
---

### Post by ccipriano on 2009-06-05
I have a dual boot machine that I'm now having a problem with.  So I had a windows partition go bad and I ended up reinstalling windows on that partition.  This obviously screwed up GRUB so on my way to restoring it I ran into a couple of problems.  This somehow screwed up one of my other partitions that had an ext3 file system on it.  I have read a lot of threads so far but I can find one that really replicates my issue.

So where I am at so far:

Looked at this thread: [http://ubuntuforums.org/showthread.php?t=1154829](http://ubuntuforums.org/showthread.php?t=1154829)

Here is my corresponding output from that thread.
```
root@ubuntu:~# fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3c48033a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1567    12582912   27  Unknown
/dev/sda2   *        1567       27681   209763328    7  HPFS/NTFS
/dev/sda3           27682       38450    86501992+   5  Extended
/dev/sda4           38451       38914     3717120   12  Compaq diagnostics
/dev/sda5           38202       38450     2000092+  82  Linux swap / Solaris

Disk /dev/sdc: 2008 MB, 2008023040 bytes
16 heads, 32 sectors/track, 7660 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              16        7660     1956928    e  W95 FAT16 (LBA)
root@ubuntu:~# sudo fdisk -lu

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3c48033a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    25167871    12582912   27  Unknown
/dev/sda2   *    25167872   444694527   209763328    7  HPFS/NTFS
/dev/sda3       444695265   617699249    86501992+   5  Extended
/dev/sda4       617705472   625139711     3717120   12  Compaq diagnostics
/dev/sda5       613699065   617699249     2000092+  82  Linux swap / Solaris


```

testdisk does work and I can see all of my files, but I am hoping to get to the point where I can mount the drive again.  This is what testdisk says:

```
TestDisk 6.11.1, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 320 GB / 298 GiB - CHS 38914 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0  32 33  1566 160  2   25165824 [PQSERVICE]
P HPFS - NTFS           1566 160  3 27680 243 19  419526656
P Linux                27681   2  1 38199 254 62  168987608
L Linux Swap           38201   0  1 38449 254 46    4000168
L HPFS - NTFS          38450  98 49 38913  37 36    7434240







Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
EXT3 Large file Sparse superblock, 86 GB / 80 GiB

```here is some more things I have tried

```
root@ubuntu:~# fsck /dev/sda3
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda3
Could this be a zero-length partition?

```It is worth noting that testdisk says that the partition is ext3 and this says ext2.

```
root@ubuntu:~# debugfs /dev/sda3 -w
debugfs 1.41.3 (12-Oct-2008)
/dev/sda3: Attempt to read block from filesystem resulted in short read while opening filesystem
``````
root@ubuntu:~# mount -t ext3 /dev/sda3 /mnt/root/
mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


``````
root@ubuntu:~# dmesg | tail
[29738.630919] sd 7:0:0:0: [sdc] Write Protect is off
[29738.630924] sd 7:0:0:0: [sdc] Mode Sense: 23 00 00 00
[29738.630927] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[29738.630933]  sdc: sdc1
[29738.674678] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[29738.674790] sd 7:0:0:0: Attached scsi generic sg3 type 0
[30366.375896] usb 8-4: USB disconnect, address 2
[31987.064741] attempt to access beyond end of device
[31987.064752] sda3: rw=0, want=4, limit=2
[31987.064756] EXT3-fs: unable to read superblock

```
Hopefully this provides enough information for someone to give me some help.  Let me know if any other information is needed.

---

### Post by logos34 on 2009-06-06
no, sda3 is the extended partition--it's just a shell or wrapper for logical paritions (here, sda5 and sda6)

Looks like sda1 is/was your linux / partition, despite what testdisk says. Maybe a "deeper search" will yield sda1 as linux (83).  

Run fsck on sda1.  It should read type '83' (ext2/3).  '82' is swap.

does 

sudo sfdisk -l 

show anyhting different?

---

### Post by ccipriano on 2009-06-06
```
root@ubuntu:~# sfdisk -l

Disk /dev/sda: 38913 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0+   1566-   1567-  12582912   27  Unknown
/dev/sda2   *   1566+  27680-  26115- 209763328    7  HPFS/NTFS
/dev/sda3      27681   38449   10769   86501992+   5  Extended
/dev/sda4      38450+  38913-    463-   3717120   12  Compaq diagnostics
/dev/sda5      38201   38449     249    2000092+  82  Linux swap / Solaris

```


I think the testDrive output was from the deeper search but I am running it again right now to double check.

---

### Post by ccipriano on 2009-06-06
Using testDisk I was able to retrieve some of my old grub information however I am still unable to fix sda3 to the point where I could mount it.

If it helps this is what was in my menu.lst

```
title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        83e6ce6f-bf7d-44e0-be58-b7296c20e337
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=83e6ce6f-bf7d-44e0-be58-b7296c20e337 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        83e6ce6f-bf7d-44e0-be58-b7296c20e337
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=83e6ce6f-bf7d-44e0-be58-b7296c20e337 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.27-11-generic
uuid        83e6ce6f-bf7d-44e0-be58-b7296c20e337
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=83e6ce6f-bf7d-44e0-be58-b7296c20e337 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
uuid        83e6ce6f-bf7d-44e0-be58-b7296c20e337
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=83e6ce6f-bf7d-44e0-be58-b7296c20e337 ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 9.04, memtest86+
uuid        83e6ce6f-bf7d-44e0-be58-b7296c20e337
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Restorer DO NOT LOAD
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista
root        (hd0,1)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title        Microsoft Windows XP Embedded
root        (hd0,3)
savedefault
makeactive
chainloader    +1

```

---

### Post by ccipriano on 2009-06-06
I got it working but I figured I would describe how I did in order to help anyone else out who runs into this type of problem.

After doing a deep search in testdisk I was able to write the partition table to disk and on reboot I was able to mount the drive.  I can't believe it was this simple after all the other stuff I tried.

To restore grub after this I simply followed this guide  [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Overwriting%20the%20Windows%20bootloader](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Overwriting%20the%20Windows%20bootloader)

---

### Post by logos34 on 2009-06-06
> **ccipriano said:**
> 
After doing a deep search in testdisk I was able to write the partition table 

yep.  often have to dig down a few levels to find the right layout.

So which one was it, sda1 or was / inside the extended partition (what fdisk was showing as empty space ahead of swap?

---

### Post by ccipriano on 2009-06-06
I think it was inside the ext partition.  The sda thing may be something that came factory installed on my harddrive as some weird factory reset thing but I am not exactly sure.

---

### Post by -kg- on 2009-06-06
> **ccipriano said:**
> Using testDisk I was able to retrieve some of my old grub information however I am still unable to fix sda3 to the point where I could mount it.



You aren't going to be able to mount sda3.  sda3 is an Extended partition and cannot be mounted.  Only formatted Primary (such as sda1 and sda2) or Logical partitions (which are partitions contained within the Extended partition) are mountable.

See the link, "How To Partition," in my signature block for a more detailed description.

<edit> I really should *_carefully read_* all the posts in a thread before I post! #-o

---

