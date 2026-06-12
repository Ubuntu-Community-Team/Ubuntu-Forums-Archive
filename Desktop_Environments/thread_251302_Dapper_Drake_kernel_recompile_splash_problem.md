---
title: "Dapper Drake: kernel recompile splash problem"
date: 2006-09-05
forum: Desktop Environments
---

### Post by fat_penguin on 2006-09-05
Hi,
I've recompiled the official kernel (only for test) following this procedure:

```
sudo apt-get install linux-source-2.6.15
cd /usr/src
sudo tar -xjvf linux-2.6.15.tar.bz2
sudo ln -s /usr/src/linux-2.6.15 /usr/src/linux
cd /usr/src/linux
sudo cp /boot/config-2.6.15-26-386 .
sudo make-kpkg clean 
sudo make-kpkg --initrd --append-to-version custom-version kernel_image modules_image
sudo dpkg -i kernel-image-2.6.15-custom-version_10.00.Custom_i386.deb
```

Note: I dont change anything on the .config file !!

The problem is that now, when the new kernel boot, I can not see anything until the GDM graphical login interface. No splash image...

If I change the /boot/grub/menu.lst file deleting the "splash" parameter I can show the boot message ... simple text mode.

Maybe problem with frambuffer or initrd image?

Thx.
byebye
fat_penguin


PS: sorry for my bad english

---

