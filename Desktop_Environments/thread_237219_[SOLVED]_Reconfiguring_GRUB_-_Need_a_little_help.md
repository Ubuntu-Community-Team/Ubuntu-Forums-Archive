---
title: "[SOLVED] Reconfiguring GRUB - Need a little help"
date: 2006-08-15
forum: Desktop Environments
---

### Post by wieman01 on 2006-08-15
I have just wiped out my Windows partition and have moved my "home" partition & "root" partition from **hda5/hda6** to **hda1/hda3**.

Subsequently I had to change the "/etc/fstab" file in the new partition's file system (hda3), no problem. I can also boot the copy of my current Linux system, however, GRUB still points to the old partition's (hda3) configuration file ("menu.lst").

Does anybody know how I can tell GRUB to look for "menu.lst" on the primary/new rather than the secondary partition? How do I reconfigure GRUB? Apparently it's on the wrong MBR.

Thanks in advance.

---

### Post by aggyb on 2006-08-15
Generally, once you've got booted into your system if you run:
```
sudo grub-install /dev/hda
```
you should find the problem will be resolved.

Hope that helps

AggyB

---

### Post by wieman01 on 2006-08-16
> **aggyb said:**
> Generally, once you've got booted into your system if you run:
```
sudo grub-install /dev/hda
```
you should find the problem will be resolved.

Hope that helps

AggyB

Great, mate. I will give it a shot tonight if I mess it up. I am not too familiar with GRUB...

---

### Post by wieman01 on 2006-08-16
Just to close this thread. I finally resolved my problem using this guide:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

You can configure GRUB after booting Linux OR by pressing 'c' when the GRUB screen appears.

---

