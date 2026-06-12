---
title: "Looking for quick GRUB help"
date: 2009-04-25
forum: General Help
---

### Post by evann on 2009-04-25
i had my 300gb for ntfs storage and then 80 gb had 40gb xp/40gb kubuntu. wanted to check out a fresh 9.04 ubuntu install so i just deleted old extended partition and replaced it with a fresh install.

Setup overview from partition editor:
/dev/sda/ hard drive 1 300gb sata
/dev/sda2/  = fat32 for file storage

/dev/sdb/ hard drive 2 80gb ide
/dev/sdb1/ = ntfs xp; boot flag
/dev/sdb2/ = [extended]
~/dev/sdb5 = ext3; "/" mnt
~/dev/sdb6 = swap

ubuntu boots fine but windows xp now gives me "Error 22: no such partition"
searched the net for grub editing tips but i need some help please guys. Here's the grub menu and I think it has to do with all that rootnoverify and map jibba-jabba but have had no luck fixing my xp boot.

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        aac4ac0b-60d9-4a66-bcea-dcf327dac1cc
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=aac4ac0b-60d9-4a66-bcea-dcf327dac1cc ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        aac4ac0b-60d9-4a66-bcea-dcf327dac1cc
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=aac4ac0b-60d9-4a66-bcea-dcf327dac1cc ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        aac4ac0b-60d9-4a66-bcea-dcf327dac1cc
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Professional
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

---

### Post by logos34 on 2009-04-25
try xp entry without 'map' lines:

gksudo gedit /etc/fstab

> title Microsoft Windows XP Professional
rootnoverify (hd**[COLOR="Red"]0[/COLOR]**,0)
savedefault
makeactive
chainloader +1

---

