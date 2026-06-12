---
title: "howto rename and give other icons to mounted usb drives?"
date: 2005-01-13
forum: Desktop Environments
---

### Post by nico on 2005-01-13
Hey,
I have an external usb drive with 5 partitions on them and an iPod. Now when Ubuntu detects them, they are nicely put on the Gnome desktop, but with their /dev names, eg sda1, sda2, sda3,..., sdb2. Now I have seen on a lot of screenshots of other people their desktop, where the devices have names and other icons (like the ipod icon and the usbdrive icon). Is there a place where I can configure this? 

Can I just put extra entries in /etc/fstab and give the partitions other mount points as the default? How do I know then what options to give in fstab for these partitions?

How do I unmount my iPod? Right-clicking and choosing unmount, gives an error that the device is still busy.

Thanks

---

### Post by shadow on 2006-01-05
Hi, sorry about the bump but I wondered if anybody had a solution to this?

I can't believe it's so difficult to rename an ipod.

---

### Post by nico on 2006-01-05
Sorry I never found out, I just switched to Apple :cool:

---

### Post by robenroute on 2006-02-20
Hi there, I've just converted a few FAT32 partitions to ext3 and now they show on my desktop as "11.7 GB Volume" and "29.3 GB Volume". This seems rather odd to me, since two other partitions (on the same external Firewire drive) do have proper names.

A hint in the right direction (for changing the desktop labels) would be much appreciated. Thanks.

Rob

---

### Post by dpaint4 on 2006-03-16
Hey this never got answered and I want to know too. My Windows install named my ipod 'DPAINT4'S IPOD' and I believe I need to have it just named 'ipod' in order to work with all the programs people are using to synch it.

How can I rename the thing? Wish it was renaming anything else.

---

### Post by NeroSpectre on 2007-05-31
You may have already found this, but try this:

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

The mtools info on this site came from this blog, which is also a good source of info:

[http://ubuntu.wordpress.com/2006/03/01/editing-fat32-partition-labels-using-mtools/](http://ubuntu.wordpress.com/2006/03/01/editing-fat32-partition-labels-using-mtools/)

---

