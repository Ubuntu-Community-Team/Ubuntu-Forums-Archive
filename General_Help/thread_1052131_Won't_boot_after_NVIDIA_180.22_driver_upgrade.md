---
title: "Won't boot after NVIDIA 180.22 driver upgrade"
date: 2009-01-27
forum: General Help
---

### Post by dorkdork777 on 2009-01-27
Using Ubuntu 8.10 64-bit.

After installing version 180.22 of the "binary blob" NVIDIA driver, my system will no longer boot. The bar fills up just fine, but then it falls back to the Bulletproof-X menu (with options to troubleshoot, etc).

Here's the xorg log from the unsuccessful boot:

[http://pastebin.com/fc79ed24](http://pastebin.com/fc79ed24)

To install, I downloaded the 64-bit drivers, restarted into Recovery mode, and chose the root shell from the "recovery" options. Then I ran the installer, which went by without a hitch... or so I thought, until I tried restarting.

Any help? :)

EDIT: Fixed it! [Solution here.]("http://ubuntuforums.org/showpost.php?p=6573714&postcount=22") However, when I got back to a "working" desktop, it informed me HAL had been broken and died or something, so I had no sound or Wi-Fi. A simple restart fixed this. :D

---

### Post by dabl on 2009-01-27
Probably you need a boot code to adapt the splash resolution to your monitor.

To get it to boot in 1600x1200 mode on my Samsung SyncMaster 1100, I use vga=837.

xforcevesa shows the boot splash nicely, but the greeter crashes about half the time.

vga=788 shows the greeter nicely, but the splash is split and half off the screen.

BTW, you won't find "vga=837" anywhere in the *buntu documentation.  ;)

Bottom line -- do some experiments and see what you can find that works.

---

