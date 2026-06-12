---
title: "How much memory (Hard drive) is good for dual boot."
date: 2009-05-26
forum: General Help
---

### Post by raj11 on 2009-05-26
Hi all...

I have been using window vista and ubuntu through wubi installation. I wants to remove ubuntu from the wubi installation and wants to install it in a real partition alongwith vista. I have few questions.

(1) How much memory is good for dual boot. I have read that 10 GB is enough to install ubuntu. Is it good to install it in a 10 -12 gb partition or is it advisable to keep more space. suppose i wants to install more programs in future in ubuntu, is there any problem of running out of space? 

(2) Is it possible to access ubuntu files (files in documents, music, pictures folder in ubuntu) from the window. currently in wubi installation, I can access window files in ubuntu but i cannot access ubuntu files from the window.

(3)Which file system is good for ubuntu 9.04. ext 3 or ext 4.

---

### Post by mosaic2s on 2009-05-26
What do you use the system for?

10gb is good enough for regular use of computer like e-mail, browsing, office work. Data can be shared both ways.

Ext3 is tried and tested. so support is easily available. Stick to this if the use is critical or time bound.

---

### Post by Legace on 2009-05-26
If you have enough space on your harddrive, go with a larger size so that you won't face any issues regarding free space in the future. Otherwise, 10GB should be enough.
-> If you run out of free space on Ubuntu, you can always use GParted to resize partitions in the future :)

If you want to access Ubuntu files from Windows, I suggest you create the following type of partitions:

- Windows Vista (NTFS)
- a second partition (NTFS)
- Ubuntu partition (EXT3 or EXT4)
- Swap partition (swap)

This way, you could save documents/music/videos on the second NTFS partition, and access data from both operating systems :)

By the way, I have been using EXT4 for a couple of months without a single problem. Unless you do something important on your PC, go with EXT4. :)

---

