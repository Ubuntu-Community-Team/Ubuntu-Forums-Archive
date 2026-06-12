---
title: "Help me with the initrd, please!"
date: 2005-07-05
forum: Desktop Environments
---

### Post by Morimando on 2005-07-05
Okay. I'll try to explain as good as i can. I have a SATA-harddisk installed into my computer, for which Ubuntu didn't set to load the module via the initrd. So i decided to use mkinitrd and solve this annoying problem, but:
I have copied the necessary files (reiserfs.ko and sata_sil.ko) to /lib/modules/kernelversion/initrd. Also i have changed /etc/mkinitrd/modules and included the names of the modules (without the .ko) one module a line.
Now i expected mkinitrd to include the specified modules into the initrd and to load them at boottime, so that i won't get the annoying error that special device sdaX couldn't be found any more... wrong! 
It just doesn't seem to load the modules i want! So i mounted the initrd via
```
mount -t cramfs -o loop /boot/initrd.img /initrd
```
and looked at "loadmodules" where i found out that
 
a) the modules i specified are in the list (at the top) so they SHOULD be loaded
b) there are many more modules i DIDN'T specify (and don't need either)
c) it loads the module siimage.ko which conflicts with sata_sil and is obviously the wrong driver for use with my Silicon Image 3112A SATA controller (as it's basically an IDE driver manipulated to somewhat support the chipset)

So where do the modules i didn't specify come from and where do i eliminate them, and how do i make sure the initrd is built EXACTLY like i want it - none more, none less??
Please answer fast, i want to start my Ubuntu again!

---

### Post by alastair on 2005-07-05
It might be an idea to check the man page for :

mkinitrd
mkinitrd.conf

Modules listed in "/etc/mkinitrd/modules" are not automatically loaded it seems - use a script (/etc/mkinitrd/scripts) or the "MODULES" option in the .conf file (dep,all etc.)

Make sure that the right initrd file is used with the right kernel in the GRUB file. Consider making the new output initrd file a different name (e.g. initrd.img-2.6.10-test) and editing the GRUB config file explicitly (then updating : update-grub - see "man update-grub" though).

Hope something there helps.

---

### Post by Morimando on 2005-07-05
read all the man pages thoroughly before posting here ;)
But i did find out... i hadn't inserted the scsi_mod and some other scsi-relevant module it needed. Damn ^^

---

