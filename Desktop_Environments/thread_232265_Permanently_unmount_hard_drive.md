---
title: "Permanently unmount hard drive"
date: 2006-08-08
forum: Desktop Environments
---

### Post by Bragador on 2006-08-08
Hi guys. It's probably an easy one.

Each time I unmount my windows partition and my hidden laptop partition so I have a cleaner desktop, when I reboot the icons are back.

Is there a way to save the changes ?

Thanks

---

### Post by x64Jimbo on 2006-08-08
You can remove them from your /etc/fstab
sudo gedit /etc/fstab
and remove the lines that refer to the drives that you want permanently unmounted. You could also just add the "noauto" option so that they don't mount on boot.

---

### Post by FenrisAbraxas on 2006-08-08
> **x64Jimbo said:**
> You can remove them from your /etc/fstab
sudo gedit /etc/fstab
and remove the lines that refer to the drives that you want permanently unmounted. You could also just add the "noauto" option so that they don't mount on boot.

The noauto option is better because if you remove the entries for those partitions you will have to mount them as root and using the sintaxis mount /mnt/something /dev/something .

---

### Post by bulldog on 2006-08-08
When you just don't want to see them on the desktop use gconf-editor and go to apps->nautilus->desktop and unclick what you don't want on your desktop.

They are still mounted so you can access them under your places menu and in media in your filesystem.

---

### Post by Teilanus on 2006-11-09
> **bulldog said:**
> When you just don't want to see them on the desktop use gconf-editor and go to apps->nautilus->desktop and unclick what you don't want on your desktop.

They are still mounted so you can access them under your places menu and in media in your filesystem.

Very helpful. Thanks!:D

---

