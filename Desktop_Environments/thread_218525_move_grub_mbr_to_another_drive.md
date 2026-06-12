---
title: "move grub mbr to another drive"
date: 2006-07-18
forum: Desktop Environments
---

### Post by VirtuAlex on 2006-07-18
I have three drives. Due to neglegence my boot record happened to be installed on wrong one which I planned to use for other purposes. Is there any easy way to just copy mbr from one drive to another without reinstalling all the grub?

---

### Post by VirtuAlex on 2006-07-18
anybody?

---

### Post by yabbadabbadont on 2006-07-18
Please post the following:

The contents of /boot/grub/menu.lst (or grub.conf, whichever it is called).
The output of "sudo fdisk -l".
The contents of /etc/fstab.
Finally, tell us on which drive it is currently installed and which one you want it moved to.

---

### Post by VirtuAlex on 2006-07-18
> **yabbadabbadont said:**
> Please post the following:

The contents of /boot/grub/menu.lst (or grub.conf, whichever it is called).
The output of "sudo fdisk -l".
The contents of /etc/fstab.
Finally, tell us on which drive it is currently installed and which one you want it moved to.
I'm not on my comp right now. But is it really so techy?

---

### Post by yabbadabbadont on 2006-07-18
Not really.  I just wanted to make sure that I gave you correct instructions.

I'm not on an Ubuntu computer right now either...  if the Ubuntu grub package includes the "grub-install" command, then it should be as simple as:

sudo grub-install /dev/hda

(or /dev/hdb, /dev/hdc, ..., whichever is the drive you want it installed upon)

---

### Post by VirtuAlex on 2006-07-18
Should I back up /boot/grub/ before I do that, or it won't make changes there?

---

### Post by yabbadabbadont on 2006-07-18
I don't think it will change anything there but better safe than sorry.

---

### Post by VirtuAlex on 2006-07-19
Okay, I did it. In my case it was```
sudo grub-install /dev/sda
```
It was not all though. When I've changed boot sequence the drives numbering changed too, so I had to figure out new numbers, and edit menu.lst accordingly. I also removed ```
map		(hd0) (hd1)
map		(hd1) (hd0)
``` from windows menu entry since windows is now naturally on the first drive as it likes to be. Then I also changed /boot/grub/device.map. I tried to do it with grub-install --recheck option, but it doesn't seem to do it correctly.

I'm still wondering how it assingns drive numbers. It stuck my ide drive in between of two sata in number sequence despite I put it last in the boot sequence. Now I have
hd0 sda
hd1 hdb
hd2 sdb

Why it is so?

---

### Post by yabbadabbadont on 2006-07-19
I'm not positive, but I think that grub creates the device.map file based on the order of the drives as reported by the BIOS.

---

