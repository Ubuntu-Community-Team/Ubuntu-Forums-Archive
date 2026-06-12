---
title: "Startup-manager - delete unwanted entries??"
date: 2010-01-08
forum: Desktop Environments
---

### Post by zollen on 2010-01-08
I have been using startup-manager for setting the default OS, but is there an option for deleting any unwanted entries?? If no, where is the config file so I can delete the startup entries manually?

---

### Post by bluelamp999 on 2010-01-08
You can use Ubuntu Tweak (available in Ubuntu Software Centre.)

Select Add/Remove>Package Cleaner>Clean Kernel to remove older kernels from your system, they will also be removed from the GRUB startup menu.

**N.B.** You won't have the option to load the older kernel(s) after this option!

If you wish to keep the older kernel(s), look up how to edit the GRUB config file - there are threads on this topic.

---

### Post by zollen on 2010-01-09
> **bluelamp999 said:**
> You can use Ubuntu Tweak (available in Ubuntu Software Centre.)

Select Add/Remove>Package Cleaner>Clean Kernel to remove older kernels from your system, they will also be removed from the GRUB startup menu.

**N.B.** You won't have the option to load the older kernel(s) after this option!

If you wish to keep the older kernel(s), look up how to edit the GRUB config file - there are threads on this topic.

I see no Add/Remove option in Ubuntu Software Center, would you be able to provide step-by-step instructions of accessing the Add/Remove option?

I have ubuntu 9.10 (karmic), GNOME 2.28.1 and kernel 2.6.31-17. I would like to remove all older version of kernels.

I also do not have /boot/grub/grub.conf or /boot/grub/menu.lst. Where is the grub menu config file?

root@MYBOX:/boot$find . -name *.conf
root@MYBOX:/boot$ find . -name *.lst
./grub/partmap.lst
./grub/handler.lst
./grub/parttool.lst
./grub/moddep.lst
./grub/command.lst
./grub/fs.lst

---

### Post by bluelamp999 on 2010-01-09
It might be better if you take a look at this thread - [http://ubuntuforums.org/showthread.php?t=1374935](http://ubuntuforums.org/showthread.php?t=1374935)

And this one - [http://ubuntuforums.org/showthread.php?t=1374935](http://ubuntuforums.org/showthread.php?t=1374935)

Good Luck!

Btw, 'Ubuntu Tweak' is an application that performs all sort of housekeeping stuff on your system, have a Google!

---

