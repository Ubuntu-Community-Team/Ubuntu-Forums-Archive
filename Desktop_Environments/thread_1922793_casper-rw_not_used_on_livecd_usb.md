---
title: "casper-rw not used on livecd usb"
date: 2012-02-09
forum: Desktop Environments
---

### Post by sirber on 2012-02-09
Hi

I made a bootable USB from "lubuntu-11.10-desktop-amd64.iso" using "Universal-USB-Installer-1.8.7.6.exe" and created a casper-rw file. When I boot the drive, the casper-rw file is not mounted and is locked (read only) in "/cdrom". The same procedure with ubuntu 11.10 works fine.

I tryed to add "persistent" to the kernel boot option whitout success.

---

### Post by WasMeHere on 2012-02-09
Welcome to the Ubuntu Forums sirber,

I have made a Lubuntu persistent boot USB drive but using unetbootin and the 32-bit version of 11.10 similar to the following link.

[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showthread.php?t=1885392_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1885392")

In the last post of this thread you can see how the casper-rw file should be mounted when it works. As you can see the size of the root file system /cow mounted on / has increased from 1.8GB to 4GB (when the casper-rw file system is overlayed the rofs instead of using RAM).

Maybe you have better luck with the 32-bit version :-)

Have fun finding out about Ubuntu
Olle

---

### Post by sirber on 2012-02-09
I'll try, thank you!

---

### Post by sirber on 2012-02-09
/ is 3.9GB, same size as my usb/casper-rw. I used unetbootin as suggested. I think it worked, I'll come back later today to mark this thread solved if so. Thanks!

---

