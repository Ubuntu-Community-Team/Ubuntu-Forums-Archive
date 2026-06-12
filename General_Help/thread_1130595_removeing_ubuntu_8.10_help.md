---
title: "removeing ubuntu 8.10 help"
date: 2009-04-19
forum: General Help
---

### Post by macabuntu on 2009-04-19
hello i have ubuntu 8.10 on a dual boot sys and im needing the space so my question is can i just go to computer management and delete the partition and reformat right in windows ?

---

### Post by sailthesea on 2009-04-19
Do you have any Windows or Ubuntu CDs? That would probably help You could shrink or delete the partitions to make space Careful though!

---

### Post by paradigm2 on 2009-04-19
> **macabuntu said:**
> hello i have ubuntu 8.10 on a dual boot sys and im needing the space so my question is can i just go to computer management and delete the partition and reformat right in windows ?

What is your boot loader right now?  When you power on the computer does it go to linux's loader (Grub) oor is it window's boot loader?

Where is windows installed, where is ubuntu installed?

If you boot from the windows loader mainly and windows is primary on the main active drive/partition, you ought to be able to just reformat the ubuntu partition.

As said, careful. Make sure you are sure and understand what you are doing before actually doing it.  All your data may be lost if you make a mistake.

---

### Post by macabuntu on 2009-04-20
win and ubutu is on the same HD and im useing a grub bott loader and on my disk management i have to partitions one thats 24G and the other is 1g witch is what i set for ubuntu

---

### Post by cariboo on 2009-04-20
Yes you can use the Windows disk management tools to delete the Ubuntu partitions. You will have to use your install disk to remove grub from the mbr. If don't have a windows install cd, use [SuperGrub disk]("http:///www.supergrubdisk.org/") to repair the mbr.

Jim

---

### Post by cyclobs on 2009-04-20
if you delete the linux partition you will have to insert your windows cd in and go into the recoveray console, login with the administator password and type 'fixmbr' (without quotes)

otherwise you wont be able to boot windows due to the lack of a boot loader

---

### Post by daniel014 on 2009-04-20
The way I remove Ubuntu is by booting into Windows, using a program called MbrFix:

After putting the MbrFix.exe file in C:\

```
C:>MbrFix /drive 0 fixmbr
```

Swap 0 with the number of your hard drive.

Then boot into GPartEd ([http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/")) and remove the Ubuntu partitions.

That always worked for me, I hope it helps.

---

