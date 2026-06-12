---
title: "nfs and fstab"
date: 2005-10-28
forum: Desktop Environments
---

### Post by CharlieC on 2005-10-28
Still haveing trouble with nfs. I am trying to make my Ubuntu system an nfs client to my SUSE 10.0 machine. 
    I followed the directions on the help page. 
Here is the auto.master file:
# Sample auto.master file
# This is an automounter map and it has the following format
# key [ -mount-options-separated-by-comma ] location
# For details of the format look at autofs(5).
#/misc  /etc/auto.misc --timeout=60
#/misc  /etc/auto.misc
/net    /etc/auto.net
cc@linuxfour:/$

Here is my /etc/fstab
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

I understand there should be another line which I have tried:
linuxfour:/home/cc /linuxfour nfs user,exec,bg 0 0

It did not work. I am trying to share my /home/cc directory on this machine (linuxfour).
The suse10.0 sees the linuxfour machine, when I go to /mnt on it I get . .. linuxfour but not the share folder in other words it does not show anything in linuxfour.

Any idea what I am doing wrong?

Thanks
Charlie

---

