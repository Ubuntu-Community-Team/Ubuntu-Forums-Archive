---
title: "Ubuntu Dual Boot how to with another linux distro?"
date: 2009-05-25
forum: Desktop Environments
---

### Post by smirnoff76 on 2009-05-25
I have been looking for a tutorial / howto on how to install ubuntu with another linux distro (in this case Sabayon) on the same fixed disk but have not been able to find one, does anyone know of any tutorials / howto's on this subject?

Thanks

---

### Post by sedawk on 2009-05-25
There are two important things:

* Make sure you know how to install the second linux without destroying
  the existing partitions and killing any existing data (including
  your first linux). E.g. select manual installation and manual
  partitioning)

* After installation there is a risk your old Linux will not boot anymore
 (if the installer didn't detect and integrate it). When both versions
 are based on grub that is easy to repair, e.g. you have to add entries
 for the old linux to grub's menu.lst and to copy the required kernel
 and initrd from the "old" /boot to the /boot of the new linux (without
 overwriting files - e.g. rename kernel and initrd as needed).

You will find lots of threads hear about people having trouble after
installating the second linux (cannot boot ..., grub error ...).

---

