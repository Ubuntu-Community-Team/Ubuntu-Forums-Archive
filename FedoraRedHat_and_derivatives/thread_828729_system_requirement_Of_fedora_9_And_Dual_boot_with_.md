---
title: "system requirement Of fedora 9 And Dual boot with Ubuntu"
date: 2008-06-14
forum: Fedora/RedHat and derivatives
---

### Post by reyhan on 2008-06-14
Hey, What is the system 
requirement of Fedora 9?
And How do i Dual boot it With Ubuntu 8.04?

---

### Post by Fingel on 2008-06-14
After one of them is installed, just insert the disc for the other. The installer should run normally. It will be easier than dual botting with windows because linux works well with itself :)
The good thing about dual booting 2 linux distros is that you can share your home dir, and your swap, so you end up saving a lot of disk space.
Cheers.

---

### Post by reyhan on 2008-06-14
So... , After i install fedora Do i need Install the GRUB again?

---

### Post by Fingel on 2008-06-14
No grup should automatically detect and add ubuntu to its list.

---

### Post by reyhan on 2008-06-14
Okey Thanks

---

### Post by djhyland on 2008-06-16
Even if Fedora's GRUB doesn't automatically make an entry for Ubuntu, you can mount your Ubuntu partition from Fedora, go to its /boot/grub/menu.lst, and copy over the entries for Ubuntu into Fedora's /boot/grub/menu.lst.  Of course, DON'T delete the entries for Fedora.

The above method worked for me, piece of cake.

---

### Post by reyhan on 2008-06-16
Yeah i Already Done it its piece of cake

---

