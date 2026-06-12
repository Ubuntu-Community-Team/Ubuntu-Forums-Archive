---
title: "new HDD"
date: 2008-12-13
forum: General Help
---

### Post by punkrkr52 on 2008-12-13
I'm running ibex, and I'm about to get a new hard drive. I wanted to know if there was any way I can more or less transfer my existing install to the new hdd. As in keep all my settings and scripts. Or would I have to do it all from scratch again?

---

### Post by logos34 on 2008-12-13
assuming the new drive is as big or bigger than the current one, you can simply use the **dd command**, which will copy the entire disk + mbr to the new one.

Working from the live cd you'd do this:

> [http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

Cloning an entire hard disk:

**dd if=/dev/sda of=/dev/sdb bs=4096 conv=notrunc,noerror**

/dev/sda is the source. /dev/sdb is the target. Do not reverse the intended source and target. It happens. Notrunc means 'do not truncate the output file'. Noerror means to keep going if there is an error. Normally dd stops at any error.

Then, if there's any unallocated space on the new drive, use >System>admin>partition editor to grow / to take up the rest of the disk (might have to delete /swap first to get it out of the way, then make a new one at end of disk), or else turn the space into a data partition.  Reboot into the new drive, and once you're satisfied all is well, wipe the old one.  *Don't try to mount the old partition because it will cause system confusion since it has the same UUID #.

---

### Post by punkrkr52 on 2008-12-14
Fantastic thank you.

---

