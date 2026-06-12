---
title: "[SOLVED] When I update, old version of ubuntu still stays as well?"
date: 2008-12-22
forum: General Help
---

### Post by WillBMX on 2008-12-22
Well yeah as the title says, every time I update the old version of ubuntu stays available for me to boot into when grub loads up, and I'm starting to compile quite a list because I can boot each version in normal mode or recovery mode. Anyway the only real worry is that I am taking up precious HDD space with multiple versions of ubuntu installed on my meager 22gig ubuntu partition (my HDD is only 40gig, and space is running out fast :/ new one is on the way though). So anyway this is not a huge problem but it's kind of annoying. If there's anything easy I can do to remove the old versions of ubuntu then speak up! Thanks will be rewarded :)

---

### Post by uidb4056 on 2008-12-22
In the /boot folder you will found several files with the kernel number in the filename, you can safely delete the oldest (you can keep the 2 or 3 newest just in case you need to boot on a older kernel to fix something), may be you can first move this files first to another folder before delete them. You need to do this in a terminal using sudo. Then you need to edit /boot/grub/menu.lst to delete the removed kernel references.

---

### Post by Kevbert on 2008-12-22
The old versions can be deleted via Synaptic. You need to make sure you know which version you're using with
```
uname -a
```
in terrminal. It would also be worth keeping a previous version (in case of problems, it gives you something to fall back on).
Now using terminal enter
```
cd /boot
ls -l
```
This will list all kernels available. You now want to open Synaptic and search for linux-image.  From here you want to remove the unwanted linux-image...generic files (be careful not to remove the one you are using).  this will modify grub and remove the kernel files from the boot sector.

---

### Post by ajcham on 2008-12-22
It's worth noting that you don't actually have multiple Ubuntu installations - each option in Grub is the same installation, just booting a different Kernel version. The kernels don't take up a great deal of space, so removing them will not free up as much space as you may be hoping.

---

### Post by Kevbert on 2008-12-22
> **ajcham said:**
> It's worth noting that you don't actually have multiple Ubuntu installations - each option in Grub is the same installation, just booting a different Kernel version. The kernels don't take up a great deal of space, so removing them will not free up as much space as you may be hoping.

It can cause problems if the boot sector is nearly full/filled up especially if the boot sector is small, so I recommend removing any unwanted kernels.

It would be worth running
```
sudo apt-get clean
sudo apt-get autoclean
```

---

### Post by ajcham on 2008-12-22
> **Kevbert said:**
> It can cause problems if the boot sector is nearly full/filled up especially if the boot sector is small, so I recommend removing any unwanted kernels.


It was my understanding that the boot sector only contains Grub - the kernels and also the Grub configuration are stored within the filesystem (in the /boot directory). Therefore the boot sector doesn't become full when old kernels are retained. Am I mistaken?

In any case, in raising the point it wasn't my intention to imply that one shouldn't delete the old kernels - that's up to the individual - but that doing so would not free as much space as the OP expected.

---

### Post by drs305 on 2008-12-22
It is the /boot directory that can get full and cause problems. There was a time when users were incorrectly advised to make the /boot partition only 50B. As kernel size grew and old kernels were not deleted the partitions became full and problems ensued until space was restored by deleting older kernels.

Here is a tutorial on the grub menu's display of kernels and various options of how to deal with them:
[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by Kevbert on 2008-12-22
> **ajcham said:**
> It was my understanding that the boot sector only contains Grub - the kernels and also the Grub configuration are stored within the filesystem (in the /boot directory). Therefore the boot sector doesn't become full when old kernels are retained. Am I mistaken?
No, I believe you are correct.

> **ajcham said:**
> In any case, in raising the point it wasn't my intention to imply that one shouldn't delete the old kernels - that's up to the individual - but that doing so would not free as much space as the OP expected.
Agreed.
No offence intended.

---

### Post by WillBMX on 2008-12-23
What's Synaptic? haha I'm a noob to ubuntu as you probably guessed.

---

### Post by Elfy on 2008-12-23
It's in the admin system menu - it's a front end to the systems which do the installing and removing of the majority of your software.

Search for linux-image and you'll find all the kernels installed - right click and you get a choice - complete removal will work.

---

