---
title: "Grub Help"
date: 2006-01-29
forum: Desktop Environments
---

### Post by LPJR on 2006-01-29
I just installed Ubuntu and I have a problem.  It seems I lost access to windows as it is not listed in the Grub menu at boot-up.  I read elsewhere in this forum to go into my grub folder and look at menu.lst.  I found the grub folder under lib\grub but unfortunetly there is no menu.lst.  

My configuration is
C: drive contains Ubuntu
D: Data drive
E: CD-Rom
F: DVD-Rom CD/RW
G: SiI 3112 Raid 0 contains Windows

(please note those drive designations are windows)
As a further bit of information - I had to tell my bios to boot from HDD-1 (asus a7n8x-e), where as before it used to be HDD-0.

Please help me, anything would be better then where I stand right now.  

Lee

---

### Post by RAOF on 2006-01-29
You want to add something like this:
```

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows NT/2000/XP (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```To the end of your /boot/grub/menu.lst
You might have to play around with the hd numbers - your windows drive may not be (hd0,0).  The numbers are (hd<drivenumber>,<partitionnumber>), so (hd0,0) may work for you, if the bios thinks the windows drive is HDD-0.
The only other problem may be the SiI 3112 Raid 0 - that's probably a software raid device (where the OS driver actually does the raid work), and I'm not sure how grub will handle it.

---

### Post by darth_vector on 2006-01-29
the full path for menu.lst is /boot/grub/menu.lst

---

