---
title: "[SOLVED] Full Re-install"
date: 2009-01-06
forum: General Help
---

### Post by Haruki-kun on 2009-01-06
I've decided I'm going to re-install Ubuntu 8.04 from scratch. My backup is already made. This computer has two partitions, one for Windows and one for Ubuntu. If possible, I'd like to leave the Windows Partition untouched.

How do I proceed to re-install the system without touching the Windows Partition?

---

### Post by gettinoriginal on 2009-01-06
When the Live CD brings you to the partitioning, select manual, and select the partition that currently is occupied by Ubuntu.  :P

---

### Post by Haruki-kun on 2009-01-06
OK, in the manual partition window I see:

/dev/sda1 ntfs (the Windows partition)
/dev/sda5 ext3 (The Ubuntu partition)
/dev/sda6 swap (the swap)

What should I do now?

---

### Post by fenian on 2009-01-06
Choose the /dev/sda5 partition.
Format to ext3
For the mount point choose  "/"

It will then erase and reformat the partition and the install will continue on that partition.

---

### Post by Sef on 2009-01-06
Read [Psychocats]("http://psychocats.net/ubuntu") to learn how to dual boot.  It is a pictoral howto.

---

### Post by Haruki-kun on 2009-01-06
Thanks a lot, everyone! It worked just fine. :D

---

