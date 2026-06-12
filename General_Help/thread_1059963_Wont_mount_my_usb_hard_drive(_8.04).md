---
title: "Wont mount my usb hard drive( 8.04)"
date: 2009-02-04
forum: General Help
---

### Post by zaphodbblx on 2009-02-04
I just realized that my usb hard drive has disappeared! it wont auto mount although it shows in my directory but just says "usb drive"(not the drives name) it wont manualy mount either. I got it to show the drive once in file viewer(by unplugging it a few times) but now it wont show..It worked the first few months flawlessly but now no go. any ideas?
it shows up when I lsub
Bus 008 Device 001: ID 0000:0000  
Bus 007 Device 005: ID 0d49:3210 Maxtor <--------------this is the bugger
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 413c:3012 Dell Computer Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 413c:2003 Dell Computer Corp. 
Bus 003 Device 001: ID 0000:0000  

the drive that won't show is the maxtor drive


it seems this happened sometime after an update, but I dont use the drive much( it has my mp3 collection on it) sO I just noticed it

I messed around a bit more and unplugged the drive for about an hour and now its back, but heres the fdisk output
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2               7         398     3148740    b  W95 FAT32
/dev/sda3   *         399       38535   306335452+  83  Linux
/dev/sda4           38536       38913     3036285    5  Extended
/dev/sda5           38536       38913     3036253+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: **********

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568641    7  HPFS/NTFS

I had done this before(even though I have NO idea what it means ) and this is the same output. could it be my usb drive was overheated?...like I say it showed up before but wouldnt mount

3 reboots and it's still there. even though its back if any one has guidence on how to fix this in the future I'd appreciate it!

---

### Post by taurus on 2009-02-04
Run this command first from a terminal.

```
lsusb
```
Then, post the output of this command.

```
sudo fdisk -l
```

---

