---
title: "default os option...."
date: 2008-12-31
forum: Desktop Environments
---

### Post by visitnag on 2008-12-31
Hi,
Happy new year to all.
I have installed ubuntu8.1 on windows xp. When i start the system it is booting with ubuntu, i want to have WinXp as my default os. The following is my /boot/grub/menu.lst, let me know how to edit this to get winxp as default os. Thank you all.. 

## ## End Default Options ##

title           Ubuntu 8.10, kernel 2.6.27-7-generic
uuid            93bb35df-be3f-4273-adf8-3132abd9c8dc
kernel          /vmlinuz-2.6.27-7-generic root=UUID=ed42024f-f1c3-4bb0-88df-c7ec41463434 ro quiet splash
initrd          /initrd.img-2.6.27-7-generic
quiet

title           Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid            93bb35df-be3f-4273-adf8-3132abd9c8dc
kernel          /vmlinuz-2.6.27-7-generic root=UUID=ed42024f-f1c3-4bb0-88df-c7ec41463434 ro  single
initrd          /initrd.img-2.6.27-7-generic

title           Ubuntu 8.10, memtest86+
uuid            93bb35df-be3f-4273-adf8-3132abd9c8dc
kernel          /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by TestDummy! on 2008-12-31
Change

**default 0**

to

**default 4**

in **/boot/grub/menu.lst**

It's the first option in the file following the lines of comments.

---

