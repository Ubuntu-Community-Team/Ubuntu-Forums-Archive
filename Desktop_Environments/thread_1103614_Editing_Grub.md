---
title: "Editing Grub"
date: 2009-03-22
forum: Desktop Environments
---

### Post by grimm08 on 2009-03-22
I am currently running an Ubuntu/XP configuration, and I just had to reinstall Ubuntu on a different paratition now Grub is remembering the old locations.  I want to clean up my Grub menu, so how do I remove the old locations from Grub?

---

### Post by men28 on 2009-03-22
You have to edit file named /boot/grub/menu.lst.
But be very careful! Copy it to something like menu.lst.original and only after the copying edit it.

---

### Post by jslick on 2009-03-23
First backup your current grub menu.lst file.  Copy /boot/grub/menu.lst to your home directory or something.

I'm assuming you're using gnome?  Edit your grub menu.lst file:  Alt+F2, type in```
gksu gedit /boot/grub/menu.lst
```
In KDE 4.2, this would be:```
kdesu kate /boot/grub/menu.lst
```

Comment out the lines of code you don't want by using the pound sign:  #
For example:```
#title		Kubuntu 8.10 Intrepid Ibex, kernel 2.6.27-7-generic (recovery mode)
#root		82ac2aed-6db8-455b-9943-31288cf395c1
#kernel		/boot/vmlinuz-2.6.27-7-generic #root=UUID=82ac2aed-6db8-455b-9943-31288cf395c1 ro single
#initrd		/boot/initrd.img-2.6.27-7-generic
#boot

```

Also, you can change the grub wait time by editing the "timeout" line (default is 10 seconds, which is too long for me).  The third line of my grub file says:```
timeout 5
```.  This means that the grub menu will only wait 5 seconds before automatically booting the selected entry.

---

### Post by grimm08 on 2009-03-23
Thanks that does help.

---

