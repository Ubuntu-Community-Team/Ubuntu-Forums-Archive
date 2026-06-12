---
title: "CD/DVD volue label on desktop"
date: 2005-07-10
forum: Desktop Environments
---

### Post by harry on 2005-07-10
I use AMD64 version of Ubuntu Hoary. Few days ago, I installed Ubuntu Hoary x86 to my friend's computer.

Ubuntu and KDE are running like hell on my machine, but one thing that is driving me crazy is non-existent volume label of (un)mounted CD/DVD volumes. When media is inserted, there's umounted CD/DVD icon on desktop with device name (hda or hdc). Friend's KDE is showing, even by default, volume name of (un)mounted CD/DVD. I can check volume name by using volname command from shell, thus it should work for KDE too.

Here's copy paste of my fstab.
proc            /proc           proc            defaults                0       0
/dev/sda6       /               reiserfs        defaults                0       1
/dev/sda1       /boot           ext3            defaults                0       2
/dev/sda8       /home           reiserfs        defaults                0       2
/dev/sda7       /usr            reiserfs        defaults                0       2
/dev/sda9       /var            reiserfs        defaults                0       2
/dev/sda5       none            swap            sw                      0       0
/dev/hdc        /media/cdrom    iso9660,udf     ro,noauto,user     0       0
/dev/hda        /media/cdrom1   iso9660,udf     ro,noauto,user     0       0
/dev/sdb1       /mnt/sdb        reiserfs        defaults                0       1
/dev/sdc1       /mnt/usb        auto            rw,user,noauto,umask=0  0       0
/home /i386/home none bind 0 0
/mnt/sdb /i386/mnt/sdb none bind 0 0
/tmp /i386/tmp none bind 0 0
/dev /i386/dev none bind 0 0
/proc /i386/proc proc defaults 0 0
/usr/share/fonts /i386/usr/share/fonts none bind 0 0

Anyone knows any solution to my 'problem'?

---

