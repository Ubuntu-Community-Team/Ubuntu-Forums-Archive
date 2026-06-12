---
title: "How do I reconfigure GRUB?"
date: 2006-07-24
forum: Desktop Environments
---

### Post by saroth on 2006-07-24
I moved my Ubuntu Dapper Drake partition to a new hard drive. The new partition has a new path, /dev/hda1 instead of /dev/hdc1. So, currently I must edit the boot command every time I want to boot into Ubuntu. I have uninstalled and reinstalled the kernel to see if that would cause GRUB to reconfigure automatically, but it doesn't work ](*,). How do I change the boot command in GRUB?

---

### Post by llamakc on 2006-07-24
sudo gedit /boot/grub/menu.lst

and make sure grub points to the same parameters you're manually setting at boot.

---

### Post by Jagot on 2006-07-24
Is this what you're looking for?

[https://help.ubuntu.com/community/GrubHowto#head-44a5805eeda20ec1b6bd6c274cbf3a74230675d1](https://help.ubuntu.com/community/GrubHowto#head-44a5805eeda20ec1b6bd6c274cbf3a74230675d1)

---

### Post by saroth on 2006-07-24
Thanks for all the help! This seems to have fixed the problem.

---

### Post by LeeM on 2006-07-24
> **saroth said:**
> Thanks for all the help! This seems to have fixed the problem.

One cautionary note - in general, it's a realllllllly good idea to copy the existing menu.lst to a backup, e.g.,

cp menu.lst menu.lst_backup

before editing the file! 

(The voice of experience)
:(

---

