---
title: "Hiding partitions in Hardy"
date: 2008-06-23
forum: Desktop Environments
---

### Post by siennalizard on 2008-06-23
Dear all,

I have a recovery partition on my HP laptop, and disk mounter is helpfully identifying it and allowing me to mount it. The thing is, that I don't want to! I have checked my /etc/fstab, and it is not listed, only my proc, root, swap and DVD drives. Where is Ubuntu/Gnome finding this partition from? I would like to hide it.

Many thanks,
J.

---

### Post by pytheas22 on 2008-06-23
/etc/fstab only lists partitions that will be automatically mounted by the system.  So removing your partition from that file does not make it invisible to the system, and as far as I know there's no way to make it impossible to find by anyone who has root access.

You could try changing permissions to 000 for the device's entry in /dev, but I don't know if that would work.  Even if it did hide it from the disk mounter, you could still find it if you looked hard enough (e.g. with gparted possibly or with disaster-recovery tools that could look at the partition structure of your disk).

Is there a reason you want to hide it?  If you just don't want Ubuntu to do anything to it, then don't mount it and it won't.  If you're trying to prevent anyone from seeing data on the partition (all your top-secret recovery tools), you should use something like truecrypt.

---

### Post by siennalizard on 2008-06-23
Thanks for your help Pytheas.

I don't particularly want to hide the partition in any serious way, only to stop it appearing as a mountable volume to the Gnome VFS subsystem. At the moment, it shows up in the Disk Mounter applet, and I would rather it didn't. In Vista, for example, the partition does not even appear in My Computer. I'm trying to achieve the same effect.

Cheers,
J.

---

### Post by holiday on 2008-06-23
It's probably best to just get used to it. You know what it means, obviously, so you will treat it appropriately. 

It's easy to screw things up in Ubuntu, and then fixing them works out to be a Project. If you're in the mood, it can be an interesting project, but if you're trying to get something else done, it's best to try to understand what they're trying to do and go with that.

---

### Post by pytheas22 on 2008-06-24
I don't know of a way to make it not show up in the mounter applet.  Maybe you could try using a different applet that would give you more options--I think there are several out there with similar functionality.  Or you could write a custom launcher for the partitions you use; all the disk mounter does really is run a command like "mount /dev/xxx /media/xxx" so it wouldn't be much work.  You have to enter your password before the mounter will mount it anyway, right, so it would be hard to screw it up by accident?

I don't know how Vista hides the partition, but it could just be a file system that Vista doesn't recognize, so it pretends it doesn't exist.

---

