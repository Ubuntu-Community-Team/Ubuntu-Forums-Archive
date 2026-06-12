---
title: "Random MBR question"
date: 2009-05-14
forum: General Help
---

### Post by Svensk023 on 2009-05-14
Ok, this may be a dumb question, but I have three HDD's
/dev/sda = Windows Vista (for valve games and photoshop)
/dev/sdb = Ubuntu 9.04 
/dev/sdc = Experiments with other linux OS's

So right now my /dev/sdc is blank and I want to try out KDE 4.2 on it with kubuntu 9.04 (yes I have ran [sudo apt-get install kubuntu-desktop] and it dosen't coexist with my custom GNOME settings very well, and visa-versa) so by defualt do you know where my MBR was installed when I installed Ubuntu? because I need to know whether to put it on my /dev/sda or /dev/sdb just in case I get rid of the Kubuntu installation on my /dev/sdc and not run into a grub error.

---

### Post by KhurramM on 2009-05-14
By default it should be in the primary hard disk.

U know which one.

On the other way around, plug out sdc and see if your system boots, after making changes to the boot manager.

The boot manager of ubuntu should be running. I am sure currently kubuntus bootmanager is running:

use:

grub-install

inside ubuntu

This should work.

Precautions for ever, backup all data before experimenting the partitions.

---

### Post by Svensk023 on 2009-05-14
alright, thank you
-Svensk

---

