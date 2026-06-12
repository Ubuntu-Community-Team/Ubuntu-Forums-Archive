---
title: "Unable to mount new volume error"
date: 2009-03-05
forum: General Help
---

### Post by spectrumvoid on 2009-03-05
Hi all. I'm trying to mount my external hard drive, and this is the error message. I'm using ubuntu 8.04.

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdd1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
clicking on the 'Safely Remove Hardware' icon in the Windows
taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
your own responsibility. For example type on the command line:

mount -t ntfs-3g /dev/sdd1 /media/New Volume/ -o force

Or add the option to the relevant row in the /etc/fstab file:
/dev/sdd1/ media/New Volume ntfs-3g force 0 0 

This is my fstab file
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=94712ba4-438c-468a-b6e1-8ea0adaa34ed /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=abb6c599-ccd9-4c8b-99c7-18cbf0e28881 none            swap    sw              0       0
/dev/sdc1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

I tried adding the line in but an error message pops up saying I don't have permission. I type su- in the terminal, nothing happen. 

Please help :)

---

### Post by pastalavista on 2009-03-05
to edit system files use sudo in terminal (Applications > Accessories > Terminal) type:```
sudo gedit /etc/fstab
```or gksu:```
gksu gedit /etc/fstab
```
when you are asked for your password, it won't appear to respond but just type it and hit <enter>

sudo and gksu (for graphical applications like gedit or nautilus) give you the power (root administrator) to destroy your system, so be careful using them.. always make a backup of any file you need them for before you change it.

---

