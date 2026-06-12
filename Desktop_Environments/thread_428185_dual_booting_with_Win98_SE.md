---
title: "dual booting with Win98 SE"
date: 2007-04-30
forum: Desktop Environments
---

### Post by SnowLinux on 2007-04-30
Howdy Folks,

I'm new to the Ubuntu world and keen to try Kunbuntu and Edubuntu of 7.04 release

So far I've installed Edubuntu, but having first installed Win98 SE on to a primary DOS partition formatted to FAT32 then installing Edubuntu with partitions of /, /home and swap, there is no boot menu being created by Grub and when booting the PC its jumping straight to Edbuntu  -  any suggestions on offer please ?

Also - is anyone aware if the KDE desk can be used on Edubuntu?

thanks in advance for any response

---

### Post by dcstar on 2007-04-30
> **SnowLinux said:**
> Howdy Folks,

I'm new to the Ubuntu world and keen to try Kunbuntu and Edubuntu of 7.04 release

So far I've installed Edubuntu, but having first installed Win98 SE on to a primary DOS partition formatted to FAT32 then installing Edubuntu with partitions of /, /home and swap, there is no boot menu being created by Grub and when booting the PC its jumping straight to Edbuntu  -  any suggestions on offer please ?

Also - is anyone aware if the KDE desk can be used on Edubuntu?

thanks in advance for any response

Here is the relevant part of my /boot/grub/menu.lst file (at the end) - edit yours in a terminal with:

```
sudo gedit /boot/grub/menu.lst
```

This boots the first partition of my first hard disk, you may have to edit things for your setup.

```

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows 95/98/Me
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by SnowLinux on 2007-04-30
thanks for the above, tried edit the menu file with lines similar to that but did not solve the problem

I do have a PC with Win 98 SE and  PCLinux installed (excellent distro by the way) and I've compared the 
Grub menu.lst file in PCLinux with that for Edubuntu, added the Win98SE lines to the Edubuntu version using sudo but did not work - further exploration is needed, I will experiment till I get the dual boot. 

By the way any idea why the MBR utility is not default on the Edubuntu install?
I had to install it using Symaptec!

I have the notion that I should install Edubuntu then install Win98 SE

---

