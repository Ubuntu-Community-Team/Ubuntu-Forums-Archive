---
title: "[SOLVED] CD and DVD drive problem"
date: 2008-12-19
forum: General Help
---

### Post by greenco on 2008-12-19
I am not sure what has happened to my CD and DVD drives. When I put a CD into it and close the drawer it spins up, but I am not getting and icon on my desk top that shows the disk. Last week, it would put an icon on the desktop and open the CD to show me the contents. Is there a terminal command that I can run to fix this? I am running Ububtu 8.04.

Here is my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=45f66420-0aa1-4ad5-8539-001fc581dcbd /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=afb457c7-e8d5-4613-af07-531c3f6fe407 /home           ext3    relatime        0       2
# /dev/sda3
UUID=3ab89527-46fd-47ba-9150-e029080af56f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by greenco on 2008-12-19
Problem Solved!!

I found this on another forum and it fixed my problem.

Problem Solved.
Applications---->System Tools---->Configuration Editor---->apps---->
nautilus---->desktop----> check off (*) Volumes Visible.

---

