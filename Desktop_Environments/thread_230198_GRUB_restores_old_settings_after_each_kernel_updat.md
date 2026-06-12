---
title: "GRUB restores old settings after each kernel update"
date: 2006-08-05
forum: Desktop Environments
---

### Post by theo444 on 2006-08-05
Hi, I'm currently running Ubuntu 6.06 on two computers that I have.  Originally it was only on one of the computers.  After getting the first computer set up with all the software that I wanted I used a disk cloning software to clone my tweaked out Ubuntu installation to my second computer.

However, the problem is that my first computer has four hard drives.  On this computer I installed Ubuntu to the fourth hard drive.  When I cloned this drive to the second computer, I had to reconfigure GRUB.  The second computer has only two drives, with Ubuntu being on the first drive.  Before I had reconfigured GRUB, I got the following error message when I would try to boot into Ubuntu:

```
Booting 'Ubuntu, kernel 2.6.15-26-k7'
root (hd3,0)
Error 21: Selected disk does not exist
Press any key to continue...
```

So I booted to the Ubuntu live CD and reconfigured GRUB by replacing "(hd3,0)" with "(hd0,0)" in the /boot/grub/menu.lst file and then I synced those changes with the bootloader.

This worked fine and I had no problems at all booting into Ubuntu until I installed a kernel update.  For some reason, the old GRUB settings in the menu.lst file are restored.  After each kernel update the setting (hd0,0) is restored back to (hd3,0), like it is on my first computer.  

For now I've been manually editing the menu.lst file to correct this problem, but I can't keep doing this after every kernel update.  If anyone  has any ideas of a permanant solution to prevent this from happening again, I'd greatly appreciate your feedback.

Thanks!

---

### Post by Phasmagon on 2006-08-05
You have to change the default root device to the drive you want in the automagic options in menu.lst. This options control the configuration of new kernels. The part you want is:

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

do not uncomment. Just replace hd1 with the drive that your ubuntu root is installed.

---

### Post by theo444 on 2006-08-05
Thank you, Phasmagon! It worked, even after I installed the latest kernel update!

---

