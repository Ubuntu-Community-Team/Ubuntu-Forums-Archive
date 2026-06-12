---
title: "Ubuntu hangs after GRUB"
date: 2009-05-31
forum: Desktop Environments
---

### Post by AlexKpow on 2009-05-31
I hope this is the right section.

After selecting Ubuntu 9.04 from the GRUB menu, it hangs for about 20 seconds at "Starting up...". However, when I select Windows 7, it doesn't hang at all, effectively making Windows start up faster than Ubuntu :(. Here is my menu.lst file, I currently have 2 SATA drives, the first one with Windows 7 and Ubuntu, and the second with Vista.

```


title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        112eee18-ce9b-4cbf-b779-fd42aaf6d91d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=112eee18-ce9b-4cbf-b779-fd42aaf6d91d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        112eee18-ce9b-4cbf-b779-fd42aaf6d91d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=112eee18-ce9b-4cbf-b779-fd42aaf6d91d ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        112eee18-ce9b-4cbf-b779-fd42aaf6d91d
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows 7 64-bit (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows Vista (loader)
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


```

FYI, my specs are:
mobo: EVGA 750i
GPU: EVGA GTX260c216
CPU: Intel Q6600 2.4ghz
RAM: 4gb

---

### Post by AlexKpow on 2009-06-01
No one?

---

### Post by AlexKpow on 2009-06-02
:(

---

### Post by Mike Buksas on 2009-06-03
You may want to take a look at [this thread.]("http://ubuntuforums.org/showthread.php?t=1174118") I'm having the same problem, but haven't tried it's solution yet.

Mike

---

