---
title: "Lost my external ext3 partition"
date: 2008-12-31
forum: General Help
---

### Post by cd-r80 on 2008-12-31
Hi! My external drive was read by my friends WinXP & Ext2IFS program. The drive has two partitions NTFS / EXT3. Things were copied from EXT3. Ext2IFS was set read only. When I came back & plugged my drive I found only NTFS partition on File manager. EXT3 was disappeared. There was no power failure. How to start to find my partition? Does it matter if HD jumper settings has changed?

---

### Post by dexter on 2008-12-31
You could check if the ext3 partition still exists using gparted.

---

### Post by cd-r80 on 2009-01-01
Hmmm. yes Gparted shows only /dev/sda 30G unallocated. It is a 160Gdrive. But my filemanager finds 62G NTFS. Fdisk /dev/sda  finds the partitions Ok.?


dmesg:
16.120000] usbcore: registered new interface driver hiddev
[   16.184000] attempt to access beyond end of device
[   16.184000] sda: rw=0, want=122880961, limit=66055248
[   16.184000] Buffer I/O error on device sda1, logical block 61440448
[   16.184000] attempt to access beyond end of device
[   16.184000] sda: rw=0, want=122880963, limit=66055248
[   16.184000] Buffer I/O error on device sda1, logical block 61440449

---

### Post by cd-r80 on 2009-01-01
I found the problem. The jumper setting was changed on hd. I corrected it as a master.

---

