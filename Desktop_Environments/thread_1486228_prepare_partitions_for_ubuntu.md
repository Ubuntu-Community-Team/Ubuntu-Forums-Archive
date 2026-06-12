---
title: "prepare partitions for ubuntu"
date: 2010-05-17
forum: Desktop Environments
---

### Post by cccc on 2010-05-17
hi

I'd like to prepare partitions for 10.04 Lucid Lynx using gparted on my home PC.
Which file system uses 10.04 Lucid Lynx ext3 or ext4?

BTW should I install the whole sytsem on one single partition or separate /var /home /tmp etc.?

---

### Post by portentum on 2010-05-17
You can install Ubuntu on either of those, and quite a few more. I stick with ext3, although I believe the default install option is now ext4.

I would recommend having separate / and /home partitions, simply because having a /home on its own means you don't lose anything you've saved there or old application/DE configurations if you have to reinstall for some reason. Splitting the filesystem up further than that is overkill for most users.

---

### Post by ajgreeny on 2010-05-17
> **portentum said:**
> You can install Ubuntu on either of those, and quite a few more. I stick with ext3, although I believe the default install option is now ext4.

I would recommend having separate / and /home partitions, simply because having a /home on its own means you don't lose anything you've saved there or old application/DE configurations if you have to reinstall for some reason. Splitting the filesystem up further than that is overkill for most users.
+1
The only difference is that I use ext4, not ext3 for my partitions and find it faster than ext3.  As far as I can make out there is no reason to stick with ext3 any more; the bugs that had caused files to be completely empty after a crash on any folder that was open seems to have been completely fixed.

---

### Post by cccc on 2010-05-18
> **ajgreeny said:**
> +1
the bugs that had caused files to be completely empty after a crash on any folder that was open seems to have been completely fixed.

This BUG was on ext3 or ext4?

---

### Post by 3rdalbum on 2010-05-18
> **cccc said:**
> This BUG was on ext3 or ext4?

It was on Ext4, but now it's no longer present so you don't need to worry about it.

---

