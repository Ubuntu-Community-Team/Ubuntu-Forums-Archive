---
title: "Data DVD mounts ok but not displayed on desktop or under Computer"
date: 2008-03-13
forum: Desktop Environments
---

### Post by dangermouse28 on 2008-03-13
In 5 years of Linux use, I've not seen this before!

I've burned a data DVD and stuck it back in to check it's ok. What I find is that it's not displayed on the desktop or under Computer places but if I go to /media I find cdrom and cdrom0 folders. The cdrom folder is linked to cdrom0. I can access the contents of the DVD here fine.

My /etc/fstab is below.


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=7272736a-d508-4dcf-95b0-0aabc4fe7f6f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=0ef1a357-1d17-4466-981c-a8f7d03e0179 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

The biggest pain is having to use the terminal to unmount and eject the thing!
Any ideas anyone?

---

