---
title: "[SOLVED] Remove kubuntu from dual boot"
date: 2008-09-21
forum: Desktop Environments
---

### Post by kli6891 on 2008-09-21
I have kubuntu dual boot with ubuntu, both 8.04.1. 

Now I want to delete kubuntu to make more room for ubuntu.

How do I do that, and configure Grub afterwards?


thanks in advance!

---

### Post by Pro-reason on 2008-09-22
So you're really dual booting two installations of Ubuntu, one with GNOME and one with KDE?  That's a bit wasteful.  You should simply install Ubuntu once, and add to it whatever desktop environments you like.

Open up GParted and delete the partition that you don't want.  Edit /boot/grub/menu.lst and /etc/fstab to reflect the changes.  You might need to reinstall the bootloader.

---

### Post by kli6891 on 2008-09-22
Could you tell me the command to reinstall the bootloader?

Thanks.

---

### Post by Pro-reason on 2008-09-22
[Restoring the GRUB bootloader]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

If the system fails to boot after manipulating partitions, reinstall the bootloader as described.

---

### Post by kli6891 on 2008-09-22
Okay, it worked.

Thanks a lot!

---

