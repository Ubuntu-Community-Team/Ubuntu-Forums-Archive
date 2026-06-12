---
title: "Problem with USB Wifi based on ZD1211"
date: 2005-10-18
forum: Desktop Environments
---

### Post by Eleka on 2005-10-18
Hello people!

I'm tring to install the drivers for a USB Wifi dongle based on chip Zd1211. I read this [https://wiki.ubuntu.com/zd1211wifi]("https://wiki.ubuntu.com/zd1211wifi") and I installed the module on the kernel with modprobe, I included the module zd1211 on the /etc/modules, but when I inset the USB, it doesn't work.

I tested it booting up with the USB, inserting it in the middle of the boot up, inserting it when Ubuntu finished of booting up, and all I have is this post ...

Somebody help me with it?

---

### Post by dom on 2005-10-31
i just got this working on my machine,

[http://ubuntuforums.org/showthread.php?p=458488](http://ubuntuforums.org/showthread.php?p=458488)

it finds the device on boot up, no problem.

the problem i am having is trying to have it configured with the security and dhcp on boot.

i have to run a script i wrote to do this, after i boot, which isn't nice.

---

