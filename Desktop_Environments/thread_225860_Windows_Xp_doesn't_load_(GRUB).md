---
title: "Windows Xp doesn't load (GRUB)"
date: 2006-07-30
forum: Desktop Environments
---

### Post by Parsagora on 2006-07-30
My WinXP was with a spyware that did to open a lot of IE windows with advertisement. I found their names in the following register key:
> HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Internet Settings\ZoneMap\Domains

After to erase some ones, the WinXP starts to delay to load, sometimes the security mode was loaded, and finally the WinXP didn't open. The initializing stopped at the following GRUB'S message:

> 
root(hd0,0)
   Filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1

However, my ubuntu 6.06 still can read all the files that are in the WinXp's partition (like it always did).

When I type df -lh, this is showed:
> Sist. Arq.            Tam   Usad Disp  Uso% Montado em
/dev/hda2             5,6G  3,6G  1,8G  68% /
varrun                110M   88K  110M   1% /var/run
varlock               110M  4,0K  110M   1% /var/lock
udev                  110M  100K  110M   1% /dev
devshm                110M     0  110M   0% /dev/shm
lrm                   110M   19M   91M  17% /lib/modules/2.6.15-26-386/volatile
/dev/hda1              31G   16G   15G  52% /media/hda1
/dev/hda4             713M  2,5M  710M   1% /windows

And this is my menu.lst from GRUB:

> ## ## End Default Options ##

title      Ubuntu, kernel 2.6.15-26-386
root      (hd0,1)
kernel      /boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
initrd      /boot/initrd.img-2.6.15-26-386
savedefault
boot

title      Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root      (hd0,1)
kernel      /boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro single
initrd      /boot/initrd.img-2.6.15-26-386
boot

title      Ubuntu, kernel 2.6.15-25-386
root      (hd0,1)
kernel      /boot/vmlinuz-2.6.15-25-386 root=/dev/hda2 ro quiet splash
initrd      /boot/initrd.img-2.6.15-25-386
savedefault
boot

title      Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root      (hd0,1)
kernel      /boot/vmlinuz-2.6.15-25-386 root=/dev/hda2 ro single
initrd      /boot/initrd.img-2.6.15-25-386
boot

title      Ubuntu, kernel 2.6.15-23-386
root      (hd0,1)
kernel      /boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash
initrd      /boot/initrd.img-2.6.15-23-386
savedefault
boot

title      Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root      (hd0,1)
kernel      /boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro single
initrd      /boot/initrd.img-2.6.15-23-386
boot

title      Ubuntu, memtest86+
root      (hd0,1)
kernel      /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title      Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title      Microsoft Windows XP Professional
root      (hd0,0)
savedefault
makeactive
chainloader   +1

Can someone help me?

---

### Post by catlett on 2006-07-30
Post the output of ```
sudo fdisk -l
```this will list the partitions as the system sees them. Right now grub doesn't recognise the filesystem type for windows.
Onw orkaround is to use rootnoverify. This way grub doesn't try to mount the filesystem and hopefully that is all the error is about.
So if fdisk lists the partition as ntfs amd everything looks fine, change grub to rootnoverify.
```
sudo gedit /boot/grub/menu.lst
```
Then change this 
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1
```
To this, the only thing changing is the root line. It is going from [COLOR="Red"]root[/COLOR] (hd0,0) to [COLOR="Red"]rootnoverify[/COLOR] (hd0,0)
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Professional
rootnoverify  (hd0,0)
savedefault
makeactive
chainloader +1
```

---

