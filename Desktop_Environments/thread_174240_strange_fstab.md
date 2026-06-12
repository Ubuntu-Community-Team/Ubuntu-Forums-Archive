---
title: "strange fstab"
date: 2006-05-11
forum: Desktop Environments
---

### Post by hldub on 2006-05-11
I have a pc in which I have 2 hard drives installed. I had windows & solaris on one and  ubuntu on the second. I cleared that solaris partitions and then installed ubuntu in its place. Everything went fine and I can now use the system. 

I want to meddle with fstab a bit (mount up the windows partition etc), nothing I haven't done before. When I took a look at the file I couldn't really follow it. Here a few of the lines that are throwin me off.

/dev/mapper/Ubuntu-root / ext3 defaults,errors=remount-ro 0 0
/dev/hda1 /boot ext3 defaults 0 2

I would expect to have found something more like
/dev/hdc2 / ext3 defaults,errors=remount-ro 0 1
/dev/hdc5 none swap sw 0 0

and then I would have addedd
/dev/hdc1 /home/hugo/windows ntfs ....

If anyone can explain these entries to me I would really appreciate it.

---

### Post by louis_nichols on 2006-05-11
The mapper/ubuntu-root thing means that that volume is a logical volume in an LVM. I use this and my fstab looks the same. It's not a problem, just a different way to use physical volumes.

You can still add other volumes as the usual, just as you wrote. Works like a peach :D There are advantages, too. Info [here]("http://www.tldp.org/HOWTO/LVM-HOWTO.html").

EDIT: as to WHY, your Ubuntu is installed on an LVM, it's a choice you made during the install process

---

