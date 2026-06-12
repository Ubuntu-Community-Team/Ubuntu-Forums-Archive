---
title: "Bootloaders and Patitions"
date: 2006-04-13
forum: Desktop Environments
---

### Post by Mr Egg on 2006-04-13
Hey, I'm about to install Ubuntu onto my PC and I first need help with a few problems. First, I have 3 partitions on my PC, I have a C, D and E partition. C has my original copy of Windows XP installed and recently I installed another copy of XP on D (don't ask why :-P) and E is a SYSTEM_SAV. My computer is a dual-boot between C and D, what I want to know is how do I remove the dual-boot and remove the D partition and replace it with Ubuntu (without damaging my other drives). :-k 

Thanks in advance,
David. :KS

---

### Post by dcstar on 2006-04-13
[QUOTE=Mr Egg]Hey, I'm about to install Ubuntu onto my PC and I first need help with a few problems. First, I have 3 partitions on my PC, I have a C, D and E partition. C has my original copy of Windows XP installed and recently I installed another copy of XP on D (don't ask why :-P) and E is a SYSTEM_SAV. My computer is a dual-boot between C and D, what I want to know is how do I remove the dual-boot and remove the D partition and replace it with Ubuntu (without damaging my other drives). :-k 

Thanks in advance,
David. :KS[/QUOTE]
Probably best to use the Windows install disk to remove the one you don't want, and then install Ubuntu.

Ubuntu will install the Grub bootloader, which should let you select either of them.

---

### Post by Mr Egg on 2006-04-13
Well, rather than removing the partition of drive D could I just reformat it with the Ubuntu partition table to ext3 and install Ubuntu on that?

---

### Post by Sef on 2006-04-13
> Well, rather than removing the partition of drive D could I just reformat it with the Ubuntu partition table to ext3 and install Ubuntu on that?

Yes, that is what I would recommend doing.

---

### Post by Mr Egg on 2006-04-13
And when I want to uninstall Ubuntu and I put the Windows XP disc in and fixmbr in the recovery console will it return my pc to a Dual-Boot XP or just the single boot?

---

### Post by syg00 on 2006-04-13
Fixmbr does just that - re-installs the (stage0) loader code to the MBR. In M$ofts case this means it requires a partition marked as bootable (active), and contains ntldr (and boot.ini amongst others).
boot.ini decides on whether you multiboot or not - your original/current one will be unaffected.

---

### Post by Mr Egg on 2006-04-13
Ahhh, thanks alot :D  I may install Ubuntu on my PC tomorrow after I am done backing up stuff. Thanks so much for your help, this forum is very helpful and I've only been here a few days. Now I know how to dual-boot and uninstall Ubuntu, thanks alot.

---

