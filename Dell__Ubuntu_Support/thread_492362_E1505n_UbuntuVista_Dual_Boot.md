---
title: "E1505n Ubuntu/Vista Dual Boot"
date: 2007-07-04
forum: Dell  Ubuntu Support
---

### Post by maldek on 2007-07-04
I have an E1505n, as I'm sure you gathered from the title, and would like to install Vista on a separate partition before I head to school this fall.  I shrank sda6 down with GParted and left 40.5 GB of empty space.  I then put in my Vista install disc, rebooted, and made it all the way to the partition options.  No matter what I do, when I select the new partition to install Vista (I did format it with Vista's partition tool) it says, "Windows is unable to find a system volume that meets its criteria for installation."

I did a little research into the error and it seems Vista can only install onto a primary partition, and you're only allowed to have two primaries on one disk.  I'm on a laptop so another hdd isn't an option, and with the way dell partitions their dellbuntus I think I'll have to reinstall Ubuntu and partition it differently before I can install Vista.

Does anyone know from experience if that's what is necessary?  If it is, will everything on my laptop still work after reinstalling Ubuntu such as the volume buttons and other small things like that?

---

### Post by metalheart on 2007-07-04
Do you have Dell MediaDirect recovery DVD with your PC? I used it and the instructions (selected option to create two partitions) from the box to repartition the disk. I then installed Vista and after that Ubuntu.

---

### Post by nigelt on 2007-07-04
Does this help?

[http://apcmag.com.au/node/5162/](http://apcmag.com.au/node/5162/)

---

### Post by maldek on 2007-07-04
> **metalheart said:**
> Do you have Dell MediaDirect recovery DVD with your PC? I used it and the instructions (selected option to create two partitions) from the box to repartition the disk. I then installed Vista and after that Ubuntu.

The only disc that came with my laptop was an Ubuntu 7.04 disc which I already had probably 5 copies of sitting around.  I use GParted for partitioning though, and it sounds like that's all the DVD you mention really does anyway.

---

