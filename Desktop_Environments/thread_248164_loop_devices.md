---
title: "loop devices"
date: 2006-08-31
forum: Desktop Environments
---

### Post by netstv on 2006-08-31
Hi.

I am relatively new to ubuntu.  I develop on my linux box.  Previously I used Fedora core.  I do embedded software so I have to create a ramdisk etc..

The problem is that when I do a build I need to create the ramdisk and in order to do that I need to use a loopback device.

My scripts basically cycle through loop0-loop8 to see if I can get one.  I do it by losetup /dev/loop_xx_

The problem occurs when I reboot the system, there are no loop devices created by default.  

The way I see it I have three options:

1.  Find out what "button" to flip to get loop devices to be created and stay persistant.
2.  Create a startup script that runs "losetup -f"
3.  Change my build script to use losetup -f to find a free loopback device.

Option 3 is my best bet, but I am just wondering if this distro of Linux has always been like this...

Thanks.
-stv

---

### Post by caliskan on 2006-11-01
What about this option?:

module loop has to be loaded for the loopback devices to be created.  To have  module "loop" loaded automatically at boot, add the word "loop" to its own separate line in file /etc/modules

---

