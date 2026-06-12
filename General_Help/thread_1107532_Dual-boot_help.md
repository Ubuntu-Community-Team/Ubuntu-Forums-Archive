---
title: "Dual-boot help?"
date: 2009-03-26
forum: General Help
---

### Post by n3gative12 on 2009-03-26
So I decided to try out a windows 7 dual-boot on my computer, but after the installation windows took over my boot procedure. I tried fixing it by booting to  the disk and running grub setup, but now I can't get it to boot 7. this is what I have in my menu.lst file for windows 7:  ```
title		Windows 7
 root		(hd0,1)
 makeactive
 chainloader	+1
```
when I put (hd0,0) or (hd0,2) where (hd0,1) is, I get an error and it returns to the grub menu. When I leave it as it is above, booting to the windows 7 option just makes the computer completely reboot. Anybody know why this is/ how I can fix it?

---

### Post by n3gative12 on 2009-03-27
anybody?

---

### Post by fhydan on 2009-03-27
I'm having the exact same problem.

---

### Post by bumanie on 2009-03-27
Post output of > sudo fdisk -lu

---

### Post by n3gative12 on 2009-03-27
here is what I get:
```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x45004500

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   163846934    81923436   83  Linux
/dev/sda2       163846935   387712709   111932887+   7  HPFS/NTFS
/dev/sda3       387712710   390716864     1502077+   5  Extended
/dev/sda5       387712773   390716864     1502046   82  Linux swap / Solaris

```

---

