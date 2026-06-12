---
title: "Edit Grub"
date: 2009-07-05
forum: Desktop Environments
---

### Post by JimmieC on 2009-07-05
I was trying to install Xubuntu 9.04 from a Live CD to a USB drive but I think I installed Ubuntu 9.04 from my hard drive to my flash drive. I have two hard drives, Xp on the first and Ubuntu on the second with Grub installed to the MBR. I installed to the USB using the USB-Creater method and I think I mistakenly chose to install from the hard drive rather than the Live CD. Ubuntu was installed to the USB and two new lines were added to the GRUB boot screen. A a new "generic kernal" line and a "recover" line were added to the screen where I normally choose which OS to boot.  In GRUB, I can highlight a line and choose to E to "edit" the line. If I edit or remove the new lines from the GRUB  boot process will that affect my MBR or is it safe to remove these lines. 

Is there a safe way to edit the grub config file or do I need to be looking at another file. The new generic kernal line boots to Ubuntu on my my hard drive and everything works mormally, I just have these extra lines that I would like to get rid of. 

Ubuntu was installed to the USB and I have changed all my boot priority, etc., and still cannot boot from the Usb drive. But that's not my problem now, it's these extra lines, they're making me nuts.

Any help please.

Jim

---

### Post by Bucky Ball on 2009-07-05
I know this is a bit late and off-topic, but you could have installed xubuntu-desktop from Synaptics and just chosen 'xfce' or 'gnome' from the 'Sessions' options at login. They are based on exactly the same Ubuntu  kernel, just different desktop environments (Xfce and Gnome)

---

### Post by oldos2er on 2009-07-05
Run **gksu gedit /boot/grub/menu.lst** to edit your grub menu.

---

### Post by JimmieC on 2009-07-05
Thanks Ann, you've saved my sanity.

Jim

---

