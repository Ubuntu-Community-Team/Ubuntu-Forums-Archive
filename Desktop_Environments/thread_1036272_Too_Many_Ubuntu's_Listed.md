---
title: "Too Many Ubuntu's Listed"
date: 2009-01-10
forum: Desktop Environments
---

### Post by RamFel on 2009-01-10
I have a dual boot PC, for WinXP as the main OS, and Ubuntu as the second. I'll admit that I don't use Ubuntu as much as Windows, and when I do launch Ubuntu, it does this big upgrade (like over a hundred updates) and consequently my menu defaults automatically to Ubuntu 7.10 Memtest86+

My first complaint is that I don't want or need for Memtest to run. I have it on bootable CD and can run it manually if I need to.

I then need to fix it to default to my preferred OS. 

My second complaint is that my dual boot OS screen looks like this:

-----------------------------------------------------
Ubuntu 7.10, Kernel 2.6.22-16-generic
Ubuntu 7.10, Kernel 2.6.22-16-generic (Recovery mode)
Ubuntu 7.10, Kernel 2.6.22-16-generic
Ubuntu 7.10, Kernel 2.6.22-16-generic (Recovery mode)
Ubuntu 7.10, Kernel 2.6.22-16-generic
Ubuntu 7.10, Kernel 2.6.22-16-generic (Recovery mode)
Ubuntu 7.10, memtest86+
Other Operating Systems
Microsoft Windows XP Professional
------------------------------------------------------

As you can see, Ubunto shows up three times now (the last time, it was two).

I want to fix this dual-boot OS screen to show Ubuntu only once.

Thanks
RamFel

---

### Post by lykwydchykyn on 2009-01-10
Boot to Ubuntu and edit /boot/grub/menu.lst.  You can delete the redundant entries from the file.

Make a backup of the file first, though; if you make a major mistake your system might not be bootable.

---

### Post by Shazaam on 2009-01-10
Run this in terminal (opens menu.lst for editing)...
```
gksudo gedit /boot/grub/menu.lst
```
(menu.el ess tee)
Once open, count your kernel entries (starting at zero). Example...
```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		7f2d5801-46dd-4a87-a30a-c7a55afb67ab
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=7f2d5801-46dd-4a87-a30a-c7a55afb67ab ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		7f2d5801-46dd-4a87-a30a-c7a55afb67ab
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=7f2d5801-46dd-4a87-a30a-c7a55afb67ab ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

#title		Ubuntu 8.10, kernel 2.6.27-7-generic
#uuid		7f2d5801-46dd-4a87-a30a-c7a55afb67ab
#kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7f2d5801-46dd-4a87-a30a-c7a55afb67ab ro quiet splash 
#initrd		/boot/initrd.img-2.6.27-7-generic
#quiet

#title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
#uuid		7f2d5801-46dd-4a87-a30a-c7a55afb67ab
#kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7f2d5801-46dd-4a87-a30a-c7a55afb67ab ro  single
#initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		7f2d5801-46dd-4a87-a30a-c7a55afb67ab
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```
In this example Windows would be 5. Go here...
```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		X

```
and put whatever number distro/operating system you want to load first where the X is. As you can see there are #'s in front of a few lines. This tells grub to ignore that entry. You can manually add #'s (comment out) to clean up your boot list. It is advisable to keep at least one older kernel on the list in case the new one fails.
When you are done editing go to "File>Save". Nautilus will usually make a copy of your old file that you can restore with the Ubuntu livecd.

---

### Post by Martin Marshalek on 2009-01-10
These multiple Ubuntu's are really the different kernels that you have installed (with the highest number being the newest). Each one takes about 96mb and, I assume, you don't even use all of them. As long as the kernel you're using works, you can delete the others in Synaptic. 

First, you must start Synaptic and type in the search box (without quotes) "linux-image-2." Somewhere on the list will be multiple entries that look like "linux-image-2.26.27-6-generic" (yours will be somewhat different being that you use Gutsy. Mark the kernels that you want to remove for un-installation. MAKE SURE YOU DON'T DELETE THE KERNEL YOU ARE USING (just note the option you select at boot and leave the kernel that is the same version). Click apply and then reboot. There you go, as long as you deleted the right kernels, your boot menu will be much less cluttered (and you will free up about 200-300mb in the process).

---

### Post by Kokopelli on 2009-01-10
or open synaptic sort by status and remove the kernels under the "installed (local or obsolete)" status section.  That will remove the unwanted kernels as well as their entries in grub.

---

### Post by Shazaam on 2009-01-11
You can also install StartupManager through Synaptic. Once installed look at the Advanced tab, the first checkbox should do the trick.

---

