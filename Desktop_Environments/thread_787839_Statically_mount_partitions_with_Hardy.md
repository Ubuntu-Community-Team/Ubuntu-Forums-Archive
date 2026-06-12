---
title: "Statically mount partitions with Hardy"
date: 2008-05-09
forum: Desktop Environments
---

### Post by narcisgarcia on 2008-05-09
I'm using an installed Ubuntu GNU/Linux 8.04 (Hardy Heron) and the treatment on hard disk partition is now similar than Live-CD.

Unlike previous versions (when installed), the hard disk partitions aren't mounted by default. This can be seen as a "new feasible feature", but I haven't found an easy way for the Gnome's user to set static mounts.

---

### Post by vdawg on 2008-05-09
I had the same question

[http://ubuntuforums.org/showthread.php?t=778432](http://ubuntuforums.org/showthread.php?t=778432)

There is a simple solution:

you copy the entries for your drives from your /etc/mtab into your /etc/fstab and after rebooting your hdds will be mounted by default. Make sure that you backup your fstab and your mtab before messing around with this, and preferably unmount your drives also before making the changes and then reboot.

If you come across a solution that does not require the fstab mod., let me know :)

cheers!

---

### Post by wkulecz on 2008-05-09
Modifying /etc/fstab is why and how they mount where you want on boot.  If you do it manually or with some graphical tool doesn't really matter.

This is one of those things IMHO they should have just left alone.  Either way you can't make everybody happy, should have left this behavior unchanged across versions so people could know what to expect.  Different is not better, better is better!

--wally.

---

### Post by narcisgarcia on 2008-05-10
In my opinion, when somebody change a behavior like this, is needed to develop an alternative way for graphical users, or to leave this as a configurable option.

---

### Post by XemeX on 2008-05-10
Try to edit fstab according to the drives' UUIDs otherwise Hardy tends to change the order of optical devices, SATA and IDE drives each time you boot which is very annoying to me :(

---

