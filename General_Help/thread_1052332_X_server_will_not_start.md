---
title: "X server will not start"
date: 2009-01-27
forum: General Help
---

### Post by rmtebbot on 2009-01-27
Hello!

I am new to Ubuntu and (v 8.10). Stupidly fiddling around with fstab I changed something and when I rebooted the x server would not start (some internal error)

I believe this is because I changed fstab, and so the drive is read only. I can access the partition from ubuntu installed in windows but cannot change the file. How do I sort out the permissions?

Here is fstab, i assume the bold part is the issue:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=57c0e8f9-2bd6-4fd4-bcfc-5f715a62ce88 /               ext3    **relatime,errors=remount-ro.data=writeback.noatime** 0       1
# /dev/sda6
UUID=4ac2ff64-16d4-4fd2-bb24-10bc10a94467 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


my partition is /dev/sda5

Any help greatly appreciated!

---

### Post by ajgreeny on 2009-01-27
Try removing the **.data=writeback.noatime** from the line and see if that does the trick**.  **That's how mine is, anyway, so I know it can work with those words not present.

---

