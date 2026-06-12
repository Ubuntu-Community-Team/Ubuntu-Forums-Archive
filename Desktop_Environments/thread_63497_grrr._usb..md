---
title: "grrr. usb."
date: 2005-09-08
forum: Desktop Environments
---

### Post by celluloid on 2005-09-08
Hey guys. 
After help from some of you here I got my Iriver H300 to mount nicely using the 'gnome-volume-manger&' command in the terminal.

Now, after a few days of working nicely, it's all gone again. This time it seems as though my computer running Hoary and XFCE4 is not seeing the device at all.

Upon mounting i get the error:

Mounting /media/h300
mount: special device /dev/sda does not exist
Mount failed

Done
There was one error.

Running 'fdisk -l' gives me this :
grant@ubuntu:~$ fdisk -l
grant@ubuntu:~$

And running 'sudo fdisk -l' gives me this:

grant@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 4303 MB, 4303272960 bytes
255 heads, 63 sectors/track, 523 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         523     4200966   83  Linux

Disk /dev/hdc: 853 MB, 853622784 bytes
255 heads, 63 sectors/track, 103 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1         103      827316   82  Linux swap / Solaris


I'm very confused about what has happened.
Can anyone help me here?
The device which was /dev/sda1 was mouting to /media/H300

---

