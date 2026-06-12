---
title: "Dual boot...."
date: 2005-12-18
forum: General Help
---

### Post by Donnut on 2005-12-18
Hi, I just re-installed Ubuntu on a friends comp, then installed windows xp on a seperate 40gb partition.  My question is, what happened to grub?  When I boot up now, I just see windows, not grub...  What did I do wrong?

---

### Post by Ocxic on 2005-12-18
common mistake, windows by defualt will OVERWRITE the MBR during the install, just reinstall ubuntu to the same partion and if it askes, say yes to install GRUB to the MBR, then you'll get a nice list to choose from at boot time. 

You could also try doing and expert install of ubuntu by typing "expert" at the CD boot prompt, and ONLY selecting "install Grub" from the menu presented. then when grub is done installing, abort the install, and reboot your comp. this way you don't have to do a full re-install.
there is no garantee it will work, if not just do the re-install like i said b4.

---

### Post by LoclynGrey on 2005-12-18
Sounds like windows installed it self as the boot loader, which means you will have to go and play with boot.ini (sorry not sure how to help with boot.ini) normally you install windows first and then linux which gives you grub as the default boot loader.

---

### Post by Donnut on 2005-12-18
OK, apparently I just had it mixed up which to install 1st.  Thanks all.

---

### Post by rcerreto on 2005-12-18
Yes, windows installation overwrites MBR.
If you have a LiveCD you can boot from it and then:

[B]sudo mount /dev/hdax /mnt
sudo grub-install --root-directory=/mnt[/B] /dev/hda

changing <x> with the partition where you installed Ubuntu.

Then you'll be able to boot Ubuntu but no more windows.
Boot Ubuntu and 

**sudo gedit /boot/grub/menu.lst**

add these lines:

title           Windows
root            (hd0,z)                    # Again, you'll have to set the correct partition
                                                  # change z with 0 for hda1, 1 for hda2 etc.
makeactive
chainloader     +1

Now you can boot both.

That's faster than performing a complete reinstall.

---

