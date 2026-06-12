---
title: "GRUB Problem"
date: 2007-06-27
forum: Dell  Ubuntu Support
---

### Post by dude1701 on 2007-06-27
Ok, i just used the live CD in 7.04 to remove my ubuntu partition since i wanted to try another linux OS, and after i deleted the partition, i tried to boot back into win, and i kept getting:

GRUB Loading stage1.5.

GRUB Loading, Please wait...
Error 22

I didn't touch my NTFS file sys that had windows on it at all, so what else could cause this problem?

---

### Post by Sonofmoog on 2007-06-27
> **dude1701 said:**
> I didn't touch my NTFS file sys that had windows on it at all, so what else could cause this problem?

GRUB was loaded into the MBR of /dev/hda.  There are any number of ways of getting rid of it.   If you're looking for a Windows solution, load the Recovery Console, and type FIXBOOT at the prompt.  

There is more info here:  [http://support.microsoft.com/kb/307654](http://support.microsoft.com/kb/307654)

Others here can better advise you about Linux solutions involving the LiveCD ..

---

### Post by pissedoffdude on 2007-06-27
Use your windows cd to boot into the recovery console. Once in the recovery console type ```
FIXMBR
``` followed by a ```
FIXBOOT
``` If you do not have a windows cd then you may want to try super grub disk [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

### Post by Sonofmoog on 2007-06-28
> **pissedoffdude said:**
> [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

Now, *that *is the best tutorial on GRUB I have ever read ..

---

