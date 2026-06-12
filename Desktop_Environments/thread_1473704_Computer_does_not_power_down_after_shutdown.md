---
title: "Computer does not power down after shutdown"
date: 2010-05-05
forum: Desktop Environments
---

### Post by benanderson on 2010-05-05
Ubuntu 9.10 running on an old Socket 478 system (circa 2004) w/ 256MB of RAM using a "Phoenix" branded BIOS.
I've shutdown from the menu and i've shutdown using the *sudo shutdown -h now* command. The system shutdown as normal but did not cut power to the fans or the DVDROM drive even though the hard disk had already spun down and the status message that it had halted successfully had appeared on the screen.

I tried creating a new file in /boot/grub called "menu.list" (since it does not exist even though previous forum posts says that it should) and added the following line.
```
reboot=no shutdown=no
```
But that was even worse because the power button didn't respond at all so I removed the file after rebooting, BUT, the power button now does NOT respond at all, it only powers on the machine and nothing more. Even after removing the file and forcing a hardware reboot! I have to pull the cable out the back of the machine now!

Ubuntu is the only Linux distro that has ever done this on this machine, windows XP also powered off correctly.

I know how to deal with the command line but I've never had to do anything with the power management before sooooooo, help? :B

Thanks.
~Ben

---

### Post by _0R10N on 2010-05-05
```
sudo init 0
``` doesn't shutdown the system?

---

### Post by benanderson on 2010-05-05
> **_0R10N said:**
> ```
sudo init 0
``` doesn't shutdown the system?

Halts the OS, but does not cut the power.

---

