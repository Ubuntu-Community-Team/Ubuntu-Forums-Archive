---
title: "Mount the external drives in specific directory"
date: 2009-04-03
forum: General Help
---

### Post by ravi.xolve on 2009-04-03
I use external hard disk it has several partitions. I want them to be always mounted in the specific directories.

Usually they are mounted by the order I click on their icons in GUI like dolphin and the directories named 'disk' or disk-* are created.

---

### Post by taurus on 2009-04-03
Try adding the entries in /etc/fstab to specify the mountpoints for those partitions.

---

### Post by kanikilu on 2009-04-03
You can either manually edit fstab, or if you want to try a GUI way of doing it, check out the pysdm package.

// Edit - Beat me again taurus ;)

BTW, for a basic guide on how to edit fstab, check out this tutorial:

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

It says it's meant for internal drives, though, and uses device names instead of UUID's. Since you say you want to do this with an external drive, I'd probably recommend doing it with UUID's. Here's a guide:

[http://linux.byexamples.com/archives/321/fstab-with-uuid/](http://linux.byexamples.com/archives/321/fstab-with-uuid/)

---

### Post by coffeecat on 2009-04-03
> **ravi.xolve said:**
> I use external hard disk it has several partitions. I want them to be always mounted in the specific directories.

The easiest way is the label the partitions. If you have a labelled partition, the automounter will create a mount folder with the same name, and an icon will appear on your desktop with the same name.

You can label partitions without reformatting them. For ext2/3 partitions, use 'e2label' at the terminal. For ntfs partitions, use 'ntfslabel' at the terminal (you need ntfsprogs installed). If they're FAT32 partitions, there is a way to do it in Linux, but I've forgotten. Easier, to use Windows.

---

### Post by ajgreeny on 2009-04-03
You can label any partition without formatting it using gparted, either from the live CD or by installing it in ubuntu if you wish.  Fat, ntfs, ext2 or ext3, reiser, they all can be labelled easily.  However if you want an external usb disk mounted somewhere other than /media, I have no idea how to do it as they are all automounted, as far as I'm aware in that folder.  Incidentally, if you mount in other folders than /media, there will be no icon for the drive on the desktop, unless you make one ,manualy, I think.

---

### Post by coffeecat on 2009-04-03
> **ajgreeny said:**
> You can label any partition without formatting it using gparted, either from the live CD or by installing it in ubuntu if you wish.  Fat, ntfs, ext2 or ext3, reiser, they all can be labelled easily.

Yes, I'd forgotten how far Gparted had come. Thanks.

> **ajgreeny said:**
>  Incidentally, if you mount in other folders than /media, there will be no icon for the drive on the desktop, unless you make one ,manualy, I think.

Yes, I believe that's true. Which is why I use /media even for internal partitions mounted through /etc/fstab. That way I get an icon on the desktop - which I prefer. My /mnt folder is always an empty desert.

---

### Post by ravi.xolve on 2009-04-08
Anything I can do with HAL?

---

