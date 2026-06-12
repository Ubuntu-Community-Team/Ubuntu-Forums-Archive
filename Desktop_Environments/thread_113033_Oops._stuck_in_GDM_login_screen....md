---
title: "Oops. stuck in GDM login screen..."
date: 2006-01-05
forum: Desktop Environments
---

### Post by macsimski on 2006-01-05
<edit: i mean KDM of course.. my mistake...)

hello all.

I did a kernel upgrade to 2.6.14 mentioned in 

[http://ubuntuforums.org/showthread.php?t=84174](http://ubuntuforums.org/showthread.php?t=84174)

but it went wrong. kernel panic. so in grub i selected my old kernel 2.6.12-10 and booted the machine.
I got to the KDM login screen and when i typed in my password and hit enter, the screen turns black briefly, shows the standard x boot raster witch a watch cursor, stays so for about a second or 5 and returns me to the KDM login screen.

What goes wrong?

When i do a sudo -s and  i kill this process in a terminal (ctrl-alt-F1) and type startx, my windowmanager (xfce) comes up fine. as a regular user i can't. 

i've edited the /boot/grub/menu.lst file to erase the new kernel so it now automatically boots my previous kernel. but i'm still stuck at the KDM login screen.

suggestions?

---

### Post by Sokraates on 2006-01-05
You deleted the entry, but the kernel's still there.

```
sudo apt-get remove --purge linux-image-2.6.14 
```

will remove the new kernel. Though maybe there were more numbers after 14 (like "-1" or something similar).

**Edit:** As far as I can tell your problem lies with the new kernel having changed the some rights. If removing 2.6.14 doesn't help, reinstall your old one.

Eventually, you could try changing permissions with the help of a live-cd.

Good luck.

---

