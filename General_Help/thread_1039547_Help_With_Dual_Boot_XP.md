---
title: "Help With Dual Boot XP"
date: 2009-01-14
forum: General Help
---

### Post by kokonobs on 2009-01-14
I have XP and Ubuntu Hardy Heron on my pc.
Recently at start up i noticed i have several ubuntu options that look like this:

Ubuntu 8.... 2.6.24-23 generic

Ubuntu 8.... 2.6.24-23 generic (recovery mode)

Ubuntu 8.... 2.6.24-22 generic 

Ubuntu 8.... 2.6.24-22 generic (recovery mode)

Ubuntu 8.... 2.6.24-21 generic

Ubuntu 8.... 2.6.24-21 generic (recovery mode)

Ubuntu 8.... 2.6.24-19 generic

Ubuntu 8.... 2.6.24-19 generic (recovery mode)

Ubuntu 8.... memtest 86+

Whats all this about. At the start i had just a couple. Any help would be welcome.

NB: Bit of a newbie.
Thanks

---

### Post by hyperdude111 on 2009-01-14
You have recently done system update which have updated the kernel (hence the number) The other options are there in case the new kernel does not work for you. They also have the failsafe so if smething goes wrong you can try to fix it from there.

You can remove some entries if the newer kernel version works for you delete the lower equivalent. by:

sudo gedit /boot/grub/menu.lst

You should see a large text file with your boot menu in the middle, edit away, delete what you dont want to see, but make a backup in case you make a mistake.

~hyper~

---

### Post by logos34 on 2009-01-14
There was a kernel update yesterday.

You can hide the older entries or even delete them altogether.  (it is recommended to keep the second most recent working kernel for backup, though).

gksudo gedit /boot/grub/menu.lst

Either comment out ('#') the older entries like this:

> #title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
#root		(hd0,5)
#kernel		/boot/vmlinuz-2.6.24-19-generic #root=UUID=d77656b5-aa1c-4375-8bfa-b517cebff023 ro splash quiet
#initrd		/boot/initrd.img-2.6.24-19-generic


or adjust this:
> 
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=[COLOR="Red"]**1**[/COLOR]

then run

sudo update-grub

Or uninstall them through Synaptic

---

### Post by Maheriano on 2009-01-14
Ya basically when you buy a new version of Windows (95, 98, 2000, XP, Vista), you are buying the updated kernel....the brain behind the operating system. The Linux kernel is constantly being upgraded so it updates your machine whenever a new kernel is released. The reason it keeps the old ones is in case there's some issue with the new kernel, you can just boot into the older one.

---

### Post by ajgreeny on 2009-01-14
Open synaptic, search for **2.6.24-21** and remove all the installed packages with that in the name and also the **2.6.24-21** entries.  That willremove the kernela and ancillary items no longer needed, free up a lot of space, if you need it, and also edit out the entries for those kernels from your menu.lst file.  It will still leave you with the last two kernels, though if the 2.6.24-23 works OK, there is really no need to keep anything but that.

---

### Post by kokonobs on 2009-01-20
Thanks to you all... I was worried there. I did not understand why i had so many. All makes sense now.
My thanks would go to you all. Cheers

---

### Post by mayorpacmanjones on 2009-01-20
wow, i have no idea about what that code means

---

