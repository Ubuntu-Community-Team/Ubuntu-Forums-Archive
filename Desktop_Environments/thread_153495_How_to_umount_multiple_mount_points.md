---
title: "How to umount multiple mount points"
date: 2006-04-01
forum: Desktop Environments
---

### Post by wik on 2006-04-01
Hi,

I mounted my USB external hard disk in several points 

now each time I plug in my usb disk, there are two mount points that appear one in /media/usb-disk and another /media/usb-disk1

and two icons on the mount panel on top of the desktop.

I wish to remove the second mount point.

I appreciate the help.

regards

---

### Post by audax321 on 2006-04-01
Assuming you editted your /etc/fstab file, all you have to do is remove all mention of the second mount point from that file. You edit it using this command:

sudo gedit /etc/fstab

If you didn't edit that file, reboot. If you did edit the file and but removed all instances of the second mount point now, reboot anyway to make sure the drive is not mounted any more.

Then just remove the second mount point by deleting the folder:

sudo rmdir /media/usb-disk1

:D 

P.S. You can also skip the reboot and just unmount using:
sudo umount /media/usb-disk1
but the reboot just ensures it is actually unmount and you don't end up deleting stuff on the USB drive (though you could just pull the drive out :) )

---

### Post by wik on 2006-04-01
thanx for your reply;

I already checked /fstab and there was nothing mentioned there about the usb drive mount

and I already tried deleting /media/usb-disk1 and unmounting it, and I did unpluged the USB external hard drive and it goes away.

But when I pluged it again, the two mount points appear again, I think the mount point info is stored somewhere and I need to edit it .

regards

---

