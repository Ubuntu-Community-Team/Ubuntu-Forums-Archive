---
title: "Partition showing as device in Nautilus"
date: 2013-06-06
forum: Desktop Environments
---

### Post by Amorget on 2013-06-06
I just installed 13.04 on my latop and I did something that I hadn't done before, I mounted a partition in my home directory.  Why did I do this?  I wanted a seperate parition for Virtual machines but I wanted it mounted in my home directory to make it easy to get to and see.  The problem is that it is now showing as a device in Nautilus and I can easily Unmount it, which is a bad thing really.  Is there some way to hide it?  In searching the only thing I found was to mount it elsewhere and create a symbolic link, however the only examples used the mount command instead of the fstab, which is where I want to have it.

Any thoughts on how to get it out of the devices section?  Right now the partition is empty, so if I need to move it there won't be problems with Virtualbox losing anything.

here is my fstab:

> /dev/mapper/isw_bdcihjdhac_Volume0p6 /                                              ext4    errors=remount-ro 0       1
#/dev/mapper/isw_bdcihjdhac_Volume0p5            /boot                                         ext2    defaults        0       2
/dev/mapper/isw_bdcihjdhac_Volume0p7              /home                                       ext4    defaults        0       2
/dev/mapper/isw_bdcihjdhac_Volume0p8              /home/amorget/VirtualBox          ext4    defaults        0       2
/dev/mapper/isw_bdcihjdhac_Volume0p2              none                                         swap    sw              0       0
/dev/mapper/isw_bdcihjdhac_Volume0p2              none                                         swap    sw              0       0
UUID=0276f6eb-2277-4be4-8fd0-120673662932	/boot	                                         ext2	defaults	0	2

and attached is what I am seeing in Nautilus.  Notice the 268GB unlabled device, that is partition that is mounted to /home/amorget/VirtualBox

Thanks,
Douglas

---

### Post by vanadium on 2013-06-06
The partition that you mounted in your home directory does not appear in /etc/fstab? Did you mount it through the command line?

In fact, you already answered yourself: mount the partition everywhere except under /media/$USER or /home/$USER, and create a symlink (or use mount bind) in your home directory. When mounted in /etc/fstab, it will not be possible for a normal user to unmount.

---

### Post by Amorget on 2013-06-06
Hi, it is in the fstab, it is this line:  /dev/mapper/isw_bdcihjdhac_Volume0p8 /home/amorget/VirtualBox ext4 defaults 0 2

How can I create a symbolic link using fstab?  I don't want to manually mount it.

---

### Post by vanadium on 2013-06-06
Sorry, I am not familiar with this /dev/mapper construct. Just create a VirtualBox directory elsewhere, e.g. under /mnt.

A symbolic link is never created using fstab. It is something the user can do. With nautilus, you can create a link by pressing Ctrl+Shift and dragging the VirtualBox folder to your home directory (or where you want the link to be). Command line (if you would have created the mount point Virtualbox under /mnt:
```

ln -s /mnt/Virtualbox ~

```

---

### Post by Amorget on 2013-06-06
Thank you, that did what I wanted.

---

