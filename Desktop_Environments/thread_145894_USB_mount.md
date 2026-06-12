---
title: "USB mount"
date: 2006-03-17
forum: Desktop Environments
---

### Post by vidak on 2006-03-17
Where can I set the mounting options (eg. sync) of an USB-drive? When I plug an USBstick in, the konqueror-windows pops up (how can this feature get disabled?), and it looks like everything is fine, but umounting eats a lot of time, and after it nothing is changed on the drive. However, when mounting the drive manually with
sudo mount /dev/sda1 /foo/bar -o rw,sync
everything is OK - but it would be nice to see all these things done automatically...
I've tried to look at fstab, but there is nothing in there, and /etc/autofs doesn't exist...


Got any ideas?

---

### Post by Geffers on 2006-03-18
[QUOTE=vidak]Where can I set the mounting options (eg. sync) of an USB-drive? When I plug an USBstick in, the konqueror-windows pops up (how can this feature get disabled?), and it looks like everything is fine, but umounting eats a lot of time, and after it nothing is changed on the drive. However, when mounting the drive manually with
sudo mount /dev/sda1 /foo/bar -o rw,sync
everything is OK - but it would be nice to see all these things done automatically...
I've tried to look at fstab, but there is nothing in there, and /etc/autofs doesn't exist...


Got any ideas?[/QUOTE]

I get this sometimes, it says 'this feature not available' (or something similar) and then after a few moments it does disable.

Geffers

---

### Post by randcoop on 2006-03-18
fstab is, I think, the right place for this.  You can add a line to fstab for your USB drive.  Something like this would work:

/dev/sda1	/foo/bar	auto	rw,user,noauto	0	0

The first auto is in regard to the file system type.  The noauto refers to not automatically mounting the drive when the system starts.  user means that it should be mountable by the user (not just root), but in my experience it is inconsistent.  

The problem with this kind of thing is only that you might not always find sda1 assigned to this particular device (USB drive).  For example, if you plug in a different USB drive first, then yours, the second one will be assigned sdb1.

But if you're only using the one at a time, then this should work.

---

### Post by vidak on 2006-03-18
[QUOTE=randcoop]fstab is, I think, the right place for this.  You can add a line to fstab for your USB drive.  Something like this would work:

/dev/sda1	/foo/bar	auto	rw,user,noauto	0	0

The first auto is in regard to the file system type.  The noauto refers to not automatically mounting the drive when the system starts.  user means that it should be mountable by the user (not just root), but in my experience it is inconsistent.  

The problem with this kind of thing is only that you might not always find sda1 assigned to this particular device (USB drive).  For example, if you plug in a different USB drive first, then yours, the second one will be assigned sdb1.

But if you're only using the one at a time, then this should work.[/QUOTE]

sure, this would be the sane way to arrange the things here...:) however, the mounting is automatically done, without an entry in fstab... so there must be a configfile or whatever describing the way of mounting...
a friend suggested to look at the udev configs, but it didn't help me out... :(

---

### Post by randcoop on 2006-03-20
The automounting that you're talking about is set in ivman.  You can work there to change the auto process for mounting as media:/ and for starting konqueror automatically, etc.  Look in /etc/ivmconfigactions.xml

---

