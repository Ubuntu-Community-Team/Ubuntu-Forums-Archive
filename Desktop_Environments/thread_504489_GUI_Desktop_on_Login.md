---
title: "GUI Desktop on Login"
date: 2007-07-19
forum: Desktop Environments
---

### Post by Tanth9 on 2007-07-19
I have recently installed the Gnome desktop to my Ubuntu Server 7.04 install, and now every time I boot the server it goes to the GUI. Can I have it go to the shell by default and then use startx to run the GUI? And if so how do I set this up?

---

### Post by gertvdr on 2007-07-19
I think you can edit the /boot/grub/menu.lst file. Just add 'quiet splash' to the kernel line

---

### Post by mcduck on 2007-07-19
> **gertvdr said:**
> I think you can edit the /boot/grub/menu.lst file. Just add 'quiet splash' to the kernel line

That has nothing to do with the GUI. It only affects boot splash and how much information is printed on screen during the boot process..

Anyway, disabling autostarting GI should be possible simply by removing the script that starts it from some directory under /etc, but I'm not a even close to any Linux machine now so I can't tell you where exactly.

---

### Post by pbcartwright on 2007-07-19
you might want to read the README in /etc/init.d
this is where all the init scripts are. You will probably see gdm in that folder, which is what starts the GUI for gnome..

---

