---
title: "Problem after last update"
date: 2006-08-06
forum: Desktop Environments
---

### Post by rwlyonsjr on 2006-08-06
I just did the latest system update and when I did my re-boot, my system went into Kernel Panic. This is Kernel ending in .26 - I went back to Kernel ending in .23 and everything came up fine except for the fact that it took a while for my wireless USB card to get an IP address. Is there a known problem with the latest Kernel release and if so, how should I get my computer to default back to the older Kernel.

My System is an HP Pavillion a1410n with an AMD 64 Chip - I am running Ubuntu 32 bit at this time...Thanks in advance for your help!

Robert

---

### Post by fourchannel on 2006-08-06
I dunno about the kernel, but I can tell how to change the default kernel selected at boot.

if you open up /boot/grub/menu.lst, that is the file that controls the boot prompt ```
sudo gedit /boot/grub/menu.lst
``` look for a line, near the top, called ```
default 0
``` That 0 stands for the first entry in the file (the entries are at the end of the file), 1 is the second listing, 2 is the third and so on.

---

### Post by rwlyonsjr on 2006-08-06
Thanks, I will try that in order to boot my old Kernel by default, but I hope someone can tell me why I had that kernel Panic and If I should just remove the new Kernel from ym system. Things seem to be ok now with the Old Kernel...

---

