---
title: "Splash screen during Linux kernel boot"
date: 2014-05-30
forum: Desktop Environments
---

### Post by kiran8 on 2014-05-30
Hi,  I have noticed that during ubuntu kernel boot,  the kernel messages are not visible on screen and instead a color screen is shown. i want to implement the same thing for an embedded  device.  I am using ubuntu 12.04. The bootloader is u-boot. In the embedded board the bootloader displays a splash screen and then when the kernel starts the screen goes blank. And after that I see the init messages.   I think I can use something like psplash to hide the init messages. But How to hide the kernel messages. Or atleast if I can disable the kernel from updating the screen, it will retain  the splash screen from the bootloader. For this I tried kernel parameters "quiet vga=normal nofb nomodeset video=vesafb:off i915.modeset=0". But this did not work.   Can  someone please help me.

---

### Post by Portaro on 2014-05-30
First of all see what is the option you have in 
/etc/default/grubsudo gedit /etc/default/grub

look here -> [http://ubuntuhandbook.org/index.php/2014/01/boot-into-text-console-ubuntu-linux-14-04/](http://ubuntuhandbook.org/index.php/2014/01/boot-into-text-console-ubuntu-linux-14-04/)

ON some cases to see the plymouth you need use - vga=791 when you install a proprietary drivers of some ati graphics, also maybe you need the v86d daemon to cesafb
[http://packages.ubuntu.com/lucid/v86d](http://packages.ubuntu.com/lucid/v86d)

sudo apt-get install v86d

There is a nice fixing method to see plymouth and make this work in some pcs (with proprietary drivers already installed, if not you dont need this)
[http://forumubuntusoftware.info/viewtopic.php?f=7&t=5230&start=0](http://forumubuntusoftware.info/viewtopic.php?f=7&t=5230&start=0)

I think you install your proprietary drivers for graphic card and you cant addapt plymouth to the defaulte RX of your new mode graphics, if not or if you use the default drivers for graphic card probably you only need take attention on /etc/default/grub

---

