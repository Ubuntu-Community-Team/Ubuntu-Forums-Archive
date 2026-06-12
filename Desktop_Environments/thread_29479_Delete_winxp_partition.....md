---
title: "Delete winxp partition...."
date: 2005-04-24
forum: Desktop Environments
---

### Post by mirtux on 2005-04-24
Hi,
  i've now a dual boot system, win and a linux box. I would like to wipe out the first one since i do not longer need it. And i would like to use **/dev/hda1 **in which it is located for use as a storage mount for my system.

I need to reformat the partition to a new one and then mount in a new location (for example **/music**). How to do the first thing? The grub functionality will be modified by the **/dev/hda1 **format procedure?

Thanks in advance,
MC

---

### Post by nad on 2005-04-24
With the drive unmounted issue the command: mkfs.ext3 -L /music /dev/hda1  This will create an ext3 filesystem on the first partition of your first hard drive with the volume label /music. Other types of file systems are available to you. Personally, I use the xfs file system for large directories of large files. You may wish to research this. If you wish to use an xfs filesystem, replace ext3 in the command with xfs.

Now make a mount point for your new filesystem: mkdir /music  for example. and add a line to the file system table (/etc/fstab): /music /music ext3 rw,user,noauto 0 2  to reference it. Add a line to the end of the .bashrc file in your /home/ directory to auto mount when you log in: mount /music .

Edit /boot/grub/menu.lst to delete the lines referencing windows and it will not show up in your boot selection screen and you are done.

---

### Post by mirtux on 2005-04-25
Thank you very much, this is what i was searching for.....

Regards,
MC

---

