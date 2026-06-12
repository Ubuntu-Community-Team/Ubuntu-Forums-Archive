---
title: "Multiple listings of o/s on Grub boot screen during startup"
date: 2009-03-22
forum: General Help
---

### Post by ozguitarplayer on 2009-03-22
Hi,
I have just installed Ubuntu 8.10 on a new hdd

During startup on the grub screen where I can select which o/s to boot into I notice there are two listings for Ubuntu 8.10

Ubuntu 8.10, kerenl 2.6.27-11-generic
Ubuntu 8.10, kerenl 2.6.27-11-generic (recovery mode)
Ubuntu 8.10, kerenl 2.6.27-7-generic
Ubuntu 8.10, kerenl 2.6.27-7-generic (revovery mode)
Ubuntu 8.10, memtest 86+

The last time I used 8.10 I had a third entry, 
I think it was 2.6.27-5?-generic

What causes this multiple listing and is it something that should be corrected or can it be left there?

---

### Post by bumanie on 2009-03-22
They can be safely kept there, they are listings of your current kernel and older ones. It is useful to have at least one old kernel that works with your system just in case a future kernel does not, you can then choose to boot from the older kernel. If you want a shorter list, you can comment out the older kernels in the /boot/grub/menu.lst by placing a # before the entries. This does not get rid of the kernels, only stops them being shown in the list. Unless pushed for hard drive space there is no real reason to get rid of the older kernels.

#title		Ubuntu 8.10, kernel 2.6.27-7-generic
#uuid		5632a4d8-d571-4750-b433-d3ef788785ae
#kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=5632a4d8-d571-4750-b433-d3ef788785ae ro quiet splash 
#initrd		/boot/initrd.img-2.6.27-7-generic
#quiet

#title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
#uuid		5632a4d8-d571-4750-b433-d3ef788785ae
#kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=5632a4d8-d571-4750-b433-d3ef788785ae ro  single
#initrd		/boot/initrd.img-2.6.27-7-generic

This is how I have commented out the 2.6.27-7 kernel. I have left the 2.6.27-9 untouched (not shown) For some reason my system won't install the 2.6.27-11 kernel, so my latest is 2.6.27-9. To get the list for editing
> gksudo gedit /boot/grub/menu.lstPut a # in front of the kernels you don't want to appear, save and next time you boot the entries without a # will appear.

---

