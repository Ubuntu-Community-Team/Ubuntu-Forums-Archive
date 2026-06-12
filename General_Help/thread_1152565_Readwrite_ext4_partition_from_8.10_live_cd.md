---
title: "Read/write ext4 partition from 8.10 live cd?"
date: 2009-05-07
forum: General Help
---

### Post by frustphil on 2009-05-07
How? I have a grub 22 error and the only livecd I got here is 8.10. I tried to configure grub but it can't read ext4 partition. Is there a utility or a package that I should install so I can read ext4 partition?

---

### Post by Yellow Pasque on 2009-05-07
I think you need support for it in the kernel...

---

### Post by lensman3 on 2009-05-08
See if you can find a file called "ext4.ko", it lives in a directory under /lib.  Use the following command

find /lib -name "ext4.ko"

Then as root do "modprobe ext4". 

That should mount the ext4 driver.  Then you should be  able to do a normal mount of the partition.  Modprobe needs a sudo in front of it.  If you do a "/sbin/lsmod | grep ext4", the command will tell you if the module is already loaded.  Also look through "dmesg | more" to see if there is an error message about ext4.  Also after the modprobe above look at dmesg to see if module loaded correctly.

If the module ext4 doesn't exist on your machine, then you will have to compile a new kernel after you enable that module.

---

