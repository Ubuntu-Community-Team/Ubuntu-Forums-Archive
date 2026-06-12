---
title: "Pendrive Problem......"
date: 2009-02-17
forum: General Help
---

### Post by priate12 on 2009-02-17
Hi

How to Format Pendrive in UBUNTU (any version) ....

---

### Post by albandy on 2009-02-17
in wich file format?

by console
For example, for FAT32
sudo mkfs -F32 /dev/sdc1    (ensure sdc is your pendrive)

by graphical interface:
with gparted (in system administration as partition editor)

If you don't have installed gparted: sudo apt-get install gparted

---

### Post by priate12 on 2009-02-17
thanks ddude for reply ....

dude its NTFS file system ......

---

### Post by albandy on 2009-02-17
sudo mkntfs /dev/sdc1 (if /dev/sdc is your pendrive)

if you don't have the mkntfs command install the ntfsprogs

sudo apt-get install ntfsprogs

---

