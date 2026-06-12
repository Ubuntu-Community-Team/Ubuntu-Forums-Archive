---
title: "Is it possible to triple boot XP Home, Xubuntu, and Ubuntu?"
date: 2007-11-23
forum: Dell  Ubuntu Support
---

### Post by lil_azn_boi_101 on 2007-11-23
Is it possible to use one drive to triple boot XP Home, Xubuntu, and Ubuntu? I notice that GRUB only lets me pick XP Home and Ubuntu, while I have XP home and Xubuntu, so is that an indicator that only one Ubuntu can exist at a time?

---

### Post by glosman15 on 2007-11-23
> **lil_azn_boi_101 said:**
> Is it possible to use one drive to triple boot XP Home, Xubuntu, and Ubuntu? I notice that GRUB only lets me pick XP Home and Ubuntu, while I have XP home and Xubuntu, so is that an indicator that only one Ubuntu can exist at a time?

Umm, why would you bother doing this?  Why not just install Xfce, and then when you boot, choose which DE you want in the GDM?  The way you want to do it seems a little odd to me.  Despite that, it should be possible to tri-boot, just install Ubuntu first then Xubuntu then XP.

---

### Post by derby007 on 2007-11-23
I think its easier to have XP installed first. Then install Ubuntu (Gnome), then get the XFCE desktop, "apt get install xfce-desktop", or "KDE-desktop", as Ubuntu's grub manager will let u choose between Windows & Ubuntu.

---

### Post by quinreis on 2007-11-23
Sure it is possible.
Usualy we are starting with windows already installed. If that is the case, get a live linux like knoppix to split the hard disk into as many partitions as you want OSes. Plus a small partition for swap, about as big as your ram. On a knoppix cd there is a cool ap called gparted which does a good job of managing partitions.
Then go ahead and install the extra oses one by one. debian/ubuntu installers are quite good at keeping exsisting OSes bootable. 

If you dont have windows installed, you MUST start with it, because it will overwrite the master boot record and your other OSes will not be easily bootable. However, you can use the ubuntu installer safely to partition the disk before installing windows.

---

### Post by padams10001 on 2007-11-23
It is possible, but pointless.

---

### Post by gbrainin on 2007-11-23
> **quinreis said:**
> Sure it is possible.
Usualy we are starting with windows already installed. If that is the case, get a live linux like knoppix to split the hard disk into as many partitions as you want OSes. Plus a small partition for swap, about as big as your ram. On a knoppix cd there is a cool ap called gparted which does a good job of managing partitions.

   You don't need a separate CD; gparted is on the Ubuntu live CD.  IIRC, it is not on the menu when you boot from the 7.04 (Feisty) CD, but you can install it from the CD.  If you're using the 7.10 (Gutsy) CD, I think it's in the System menu somewhere.

---

### Post by banewman on 2007-11-23
I've had Xp,ubuntu, mepis and fedora on the one hd - so yes, you can. :)

---

### Post by raxso on 2007-11-26
Yes it is possible. XP first then Ubuntu and then just install the desktop manager that you want.

---

