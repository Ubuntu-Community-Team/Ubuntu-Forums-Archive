---
title: "External USB drive isnt being mounted on Ubuntu 16.04"
date: 2018-06-29
forum: Desktop Environments
---

### Post by deepakdeshp on 2018-06-29
[COLOR=#000000][FONT=&amp]Hello,[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]After plugging it my USB drive isnt getting detected and mounted.I am using Ubuntu 16.04[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Here is the output of the commands I tried. Is there anything else I could try? I feel that the drive has died.

[/FONT][/COLOR]```
  fsck from util-linux 2.27.1e2fsck 1.42.13 (17-May-2015)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb
Could this be a zero-length partition?
uma@uma ~ $ sudo -tntfs fsck /dev/sdb
fsck from util-linux 2.27.1
e2fsck 1.42.13 (17-May-2015)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb
Could this be a zero-length partition?
uma@uma ~ $ df -hT /dev/sdb
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  3.4G     0  3.4G   0% /dev
uma@uma ~ $ mount |grep sdb
uma@uma ~ $ sudo dd if=/dev/sdb of=/dev/null
dd: error reading '/dev/sdb': Input/output error
0+0 records in
0+0 records out
0 bytes copied, 0.347402 s, 0.0 kB/s
uma@uma ~ $ lsblk /dev/sdb
NAME MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sdb    8:16   0  1.8T  0 disk
uma@uma ~ $ sudo mount /dev/sdb /tmp
mount: /dev/sdb: can't read superblock
uma@uma ~ $ lsusb
Bus 002 Device 003: ID 064e:930b Suyin Corp.
Bus 002 Device 002: ID 0438:7900 Advanced Micro Devices, Inc.
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 0bc2:ab24 Seagate RSS LLC
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by Bashing-om on 2018-06-29
deepakdeshp; Humm ..

Not enough info to make a call.
What was the file system on the target drive ?

post back:
```

sudo parted -l

```
as 'fsck' does not do the Windows NTFS file system.

If it is in fact a linux - ext4 - file system .. maybe spare that superblock off ??

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]could be not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by deepakdeshp on 2018-06-29
parted -l doesnt detect the 2 TB usb Seagate drive. Moreover badblocks command reports all blocks as bad, I aborted the program after block 2100.

```
sudo parted -l[sudo] password for uma: 
Model: ATA HGST HTS545050A7 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system     Name                          Flags
 1      1049kB  683MB   682MB   ntfs            Basic data partition          hidden, diag
 2      683MB   955MB   273MB   fat32           EFI system partition          boot, esp
 3      955MB   1089MB  134MB                   Microsoft reserved partition  msftres
 4      1089MB  118GB   117GB   ntfs            Basic data partition          msftdata
 5      118GB   134GB   15.8GB  ext4
 7      134GB   293GB   159GB   ext4
10      293GB   466GB   173GB   ext4
 8      466GB   471GB   5352MB  linux-swap(v1)
 6      471GB   500GB   28.7GB  ntfs            Basic data partition          hidden, msftdata



```

---

### Post by ajgreeny on 2018-06-29
After booting up the machine to a full desktop GUI attach the USB disk then run ```
dmesg | tail -n 30
```

---

### Post by oldrocker99 on 2018-06-29
This has happened to me, and the cause was a bad USB cable. Try another cable, and your problem might be solved.

---

