---
title: "Western Digital 160Gb drive only has 1 93.2GB partition in UBuntu"
date: 2009-06-22
forum: General Help
---

### Post by SypsG on 2009-06-22
If this post is all jumbled together, it's not my fault. The thread entry widget is dorking up my posts.  This is weird. I didn't do anything to it, but just noticed that it is only showing 93.2GB. It used to show up as "PASSPORT", but now it shows up as "93.2GB Media" on my Ubuntu 8.04 system. Recently had a crash with multiple lost inodes, dereferenced files, etc. The really weird thing is that it doesn't look like anything is wrong with the data on it, but the name and the capacity are incorrect now.  Thoughts?   root@IbexSTVA:/home/gsypsomos/Desktop/VMWare Win2k3 Files?# parted /dev/sdb GNU Parted 1.8.9 Using /dev/sdb Welcome to GNU Parted! Type 'help' to view a list of commands. (parted) print Model: WD 1600BEV External (scsi) Disk /dev/sdb: 160GB Sector size (logical/physical): 512B/512B Partition Table: msdos  Number  Start   End     Size    Type     File system  Flags  1      32.3kB  93.2GB  93.2GB  primary  fat32        lba

---

