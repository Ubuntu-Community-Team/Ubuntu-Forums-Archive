---
title: "Ubuntu 10.10 and disable/changing splash screen"
date: 2010-11-05
forum: Desktop Environments
---

### Post by metallica1973 on 2010-11-05
I would like to modify the splash screen that you see when booting up Xubuntu 10.10. I want something light. What dimesions should I have it at like 800X600 1280X768 and etc. I will be using this on many different resolutions. Also where does the splash reside on this build?

---

### Post by pavankumarl73 on 2010-12-16
put # in front of quiet splash line in /etc/default/grub to disable splash screen

---

### Post by pavankumarl73 on 2010-12-16
> **pavankumarl73 said:**
> put # in front of quiet splash line in /etc/default/grub to disable splash screen

Don't forget run "sudo update-grub" and sudo update-initramfs -u" after that

---

### Post by Krytarik on 2010-12-16
[http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html) (it should work for 10.10 also)

EDIT: Do you also want to change the resolution of the boot menu, splash screen and consoles?:
[http://ubuntuforums.org/showthread.php?t=1642570](http://ubuntuforums.org/showthread.php?t=1642570)

---

