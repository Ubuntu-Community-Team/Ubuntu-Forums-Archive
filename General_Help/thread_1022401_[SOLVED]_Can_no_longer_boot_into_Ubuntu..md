---
title: "[SOLVED] Can no longer boot into Ubuntu."
date: 2008-12-26
forum: General Help
---

### Post by Soupcan on 2008-12-26
I recently installed Arch, and I can't select Ubuntu from the GRUB menu any more. Ubuntu is installed on /dev/sda1, and everything is still there. Arch is installed with / on sda3 and /home on sda4. How do i fix this so I can boot into either Arch or Ubuntu?

---

### Post by ispy on 2008-12-26
I'm no expert, but you probably need to edit your /boot/menu/grub.list file to show Ubuntu.

Also, check out SuperGrub.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by neu2buntu on 2008-12-26
copy and paste the output of ```
gedit /boot/grub/menu.lst
```

---

### Post by Soupcan on 2008-12-26
Output of gedit /boot/grub/menu.lst:
```
# Config file for GRUB - The GNU GRand Unified Bootloader
# /boot/grub/menu.lst

# DEVICE NAME CONVERSIONS 
#
#  Linux           Grub
# -------------------------
#  /dev/fd0        (fd0)
#  /dev/sda        (hd0)
#  /dev/sdb2       (hd1,1)
#  /dev/sda3       (hd0,2)
#

#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+
#  for more details and different resolutions see
#  http://wiki.archlinux.org/index.php/GRUB#Framebuffer_Resolution 

# general configuration:
timeout   5
default   0
color light-blue/black light-cyan/blue

# boot sections follow
# each is implicitly numbered from 0 in the order of appearance below
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

# (0) Arch Linux
title  Arch Linux
root   (hd0,2)
kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/614de1b8-1bfe-4a1c-9d36-81a5f9236bdb ro
initrd /boot/kernel26.img

# (1) Arch Linux
title  Arch Linux Fallback
root   (hd0,2)
kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/614de1b8-1bfe-4a1c-9d36-81a5f9236bdb ro
initrd /boot/kernel26-fallback.img

# (1) Windows
#title Windows
#rootnoverify (hd0,0)
#makeactive
#chainloader +1
```

---

### Post by logos34 on 2008-12-26
add this to bottom:

> title Ubuntu Linux 
configfile (hd0,0)/boot/grub/menu.lst

---

### Post by Soupcan on 2008-12-26
> **logos34 said:**
> add this to bottom:

Perfect. Thanks.

---

