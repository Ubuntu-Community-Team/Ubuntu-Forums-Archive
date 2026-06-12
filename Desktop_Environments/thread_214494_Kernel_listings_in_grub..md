---
title: "Kernel listings in grub."
date: 2006-07-12
forum: Desktop Environments
---

### Post by Ted D. on 2006-07-12
I now have several kernels listed in grub at boot up.

Ubuntu, kernel 2.6.15-26-386
               2.6.15-26-386 recovery mode
               2.6.15-25-386
               2.6.15-25-386 recovery mode
               2.6.15-23-386
               2.6.15-23-386 recovery mode
               2.6.12-10-386
               2.6.12-10-386 recovery mode
               2.6.12-9-386
               2.6.12-9-386 recovery mode
Ubuntu, memtest86+

Do I need all that are listed?
If not, can I just erase the line in grub? Is this correct or do I need to remove them in another way?
Your assistance please and Thanks in advance.
Ted D.

---

### Post by Najand on 2006-07-12
If you just want to hide them in grub menu, just edit /boot/grub/menu.list by vim or any other editors you like.
Go to the bottom of the file and add "#" signs before the "title" line with the name of the kernel you don't wanna use and the other lines below it. Don't forget to edit menu.list using "sudo" command.

---

### Post by Ted D. on 2006-07-13
Perfect. Thanks Najand

---

### Post by mcduck on 2006-07-13
You can hide them in Grub if you want, but if the current kernel version is working with no problems then you have absolutely no reason to keep older versions on your disk. Find them with Synaptic and remove them, and the entries in Grub will disappear too..

---

