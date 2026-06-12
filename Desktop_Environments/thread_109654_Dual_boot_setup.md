---
title: "Dual boot setup"
date: 2005-12-29
forum: Desktop Environments
---

### Post by pioni on 2005-12-29
Is it possible to install Windows in dual boot configuration after Ubuntu? I'm installing Ubuntu on my last remaining Windows PC and decided that I'd rather not install Windows 2000 until it's absolutely necessary. The PC has three hard disks and I was thinking of formatting all of these as single partition (per disk). Later, if I need it, I could install Windows 2000 on one of those disks by removing all other disks but one, installing W2k on that, connecting the other disks back and adding the disk with W2k to grub.conf. Is this possible? Having a quite slow computer this will take a day at least, so I'd like to do it only once. :) If you know better ways to do this, please let me know. First I thought I'd install W2k and Ubuntu on the same disk (W2k first, then Ubuntu), but since I'm not sure when I need Windows, if at all, it'd be better to install W2k later.

---

### Post by mcmillan on 2005-12-29
Dual booting should be no problem, there's plenty of guides around, so just do a search if you're unsure what to do. It tends to be easier installing windows first, since it will overwrite the MBR. If do decide to install ubuntu first you'll need to reinstall grub after windows has been installed. I'm pretty sure that's an option when you boot with the install cd, but I'm not exactly certain how to do it.

---

### Post by Zalbor on 2005-12-29
Not 100% sure it will work, but you can do try this:
```
sudo dd if=/dev/hda of=/home/user/mbrfile bs=512 count=1
```
Supposing that /dev/hda is your hard drive, this will copy the entire mbr to a file named mbrfile in the directory /home/user.

After installing windows, you can boot with a live cd (Knoppix will do, if you don't have live ubuntu) and try this (after mounting your partition in /ubuntu):
```
sudo dd if=/ubuntu/home/user/mbrfile of=/dev/hda bs=512 count=1
```
Of course, this will bring back the original mbr, and you'll have to add the lines for booting windows into the /boot/grub/menu.lst file yourself. But if you know what these lines are, this way might be easier.

---

