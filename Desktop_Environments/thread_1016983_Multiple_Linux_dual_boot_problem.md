---
title: "Multiple Linux dual boot problem"
date: 2008-12-20
forum: Desktop Environments
---

### Post by mhinder on 2008-12-20
Hello,
I recently installed Ubuntu 8.10 and am trying to dual boot it with Windows being the default choice. Currently Ubuntu is the default choice but here is what's listed:

Ubuntu 8.10, kernel 2.6.27-9 generic
Ubuntu 8.10, kernel 2.6.27-9 generic (recovery mode)
Ubuntu 8.10, kernel 2.6.27-7 generic
Ubuntu 8.10, kernel 2.6.27-7 generic (recovery mode)
Ubuntu 8.10, memtest86+

Other opperating systems:
Microsoft Windows XP Professional

I don't understand why Ubuntu is listed so many times and how do I allow it to take a backseat to Windows for startup because I went into Windows startup and it doesn't recognize that Ubuntu is a choice.

---

### Post by Kirky_D on 2008-12-20
There are so many ubuntu choices because you have updated the kernel. (you can see the different version numbers in the grub entry). This is done because sometimes updating the kernel can cause problems so you simply boot into an older kernel that worked. 

To change the order you have to edit /boot/grub/menu.lst this is the file that takes care of the bootup options. 

```
sudo gedit /boot/grub/menu.lst
```

in this file simply find the entry for windows (it is on multiple lines) and put it above the entries for ubuntu.

```
default 1

timeout 10

title Microsoft Windows XP Professional
root (hd0,1)
savedefault
makeactive
chainloader +1

title Ubuntu, kernel 2.6.17-10-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro single
initrd /boot/initrd.img-2.6.17-10-generic
boot

title Ubuntu, memtest86+
root (hd0,4)
kernel /boot/memtest86+.bin
quiet
boot
```

NOTE THAT THE ABOVE IS JUST AN EXAMPLE YOURS WILL BE DIFFERENT

---

### Post by mhinder on 2008-12-20
Is there anything that will go bad if I remove the older kernal entry? Also, is there a way to enter Ubuntu recovery mode if I remove the option from the boot menu?

---

### Post by Shazaam on 2008-12-20
It is good practice (as stated before) to keep at least one older kernel (with it's coresponding "Recovery mode" version) handy. No need to uninstall it, just comment (#) the older ones out in menu.lst like so...
```
title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		7f2d5801-46dd-4a87-a30a-c7a55afb67ab
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=7f2d5801-46dd-4a87-a30a-c7a55afb67ab ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

#title		Ubuntu 8.10, kernel 2.6.27-7-generic
#uuid		7f2d5801-46dd-4a87-a30a-c7a55afb67ab
#kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7f2d5801-46dd-4a87-a30a-c7a55afb67ab ro quiet splash 
#initrd		/boot/initrd.img-2.6.27-7-generic
#quiet
```

To make Windows the default choice edit this line...
```
default		0
```
Count the kernel entries (starting from zero) till you get to the Windows entry. Here is a snippet to help...
```

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		7f2d5801-46dd-4a87-a30a-c7a55afb67ab
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=7f2d5801-46dd-4a87-a30a-c7a55afb67ab ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		7f2d5801-46dd-4a87-a30a-c7a55afb67ab
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=7f2d5801-46dd-4a87-a30a-c7a55afb67ab ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		7f2d5801-46dd-4a87-a30a-c7a55afb67ab
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7f2d5801-46dd-4a87-a30a-c7a55afb67ab ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		7f2d5801-46dd-4a87-a30a-c7a55afb67ab
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7f2d5801-46dd-4a87-a30a-c7a55afb67ab ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		7f2d5801-46dd-4a87-a30a-c7a55afb67ab
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Puppy
root		(hd0,5)
kernel		/boot/vmlinuz root=/dev/sda6 
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		MEPIS at sda7, kernel 2.6.22-1-mepis-smp (on /dev/sda7)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-1-mepis-smp root=/dev/sda7 nomce quiet splash vga=791 
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sda8)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-19-generic root=/dev/sda8 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```
So I would change it to...
```
default		8
```
which will boot Windows first.

---

