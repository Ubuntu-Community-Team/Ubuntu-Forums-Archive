---
title: "Duel booting problems"
date: 2006-09-14
forum: Desktop Environments
---

### Post by Frankelastic on 2006-09-14
[FONT="Comic Sans MS"]First off i would like to say hey to everyone, im am slowly building up my knowlede of linux, and only just last week managed to screw up my first ubuntu install (Everything is ok now after a clean install.)

My problem however is that i can not seem to boot xp off grub, when i click on the windows xp loader, i get all the way up to the windows loading screen, but then my computer restarts. (Im not sure if this is a windows xp prob or an ubuntu one). However, when booting off the windows drive, windows boots normally. 

I am not sure what other information to give and any help would be greatly appreciated.

Thanks in advance.[/FONT]

---

### Post by nikhilk on 2006-09-14
Post the contents of your /boot/grub/menu.lst file and /etc/fstab file.

Welcome to Ubuntu Forums.

---

### Post by Frankelastic on 2006-09-14
Here they are
      menu.lst-->
title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdc1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdc1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdc1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdc1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdd1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1
<--

and fstab-->
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd1    /media/windows ntfs  nls=utf8,umask=0222 0    0
/dev/sda1    /media/windows ntfs  nls=utf8,umask=0222 0    0
<--

---

### Post by turbojugend_gr on 2006-09-14
Try deleting the "makeactive" part below: 
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows NT/2000/XP (loader)
root (hd2,0)
savedefault
```

That's should do the trick, the thing is makeactive command is used for primary partions on a harddisk and since you have XP on your 3rd partition it should go. If this doesn't work put makeactive back in ot's position, and w8 for another solution. POSt how it went.-

---

### Post by turbojugend_gr on 2006-09-14
Don't delete the makeactive command, I found your issues answer... Sorry for any inconvinience!

You should change the windows part in menu.lst like this:
```
This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdd1
title Microsoft Windows XP Professional
rootnoverify (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows NT/2000/XP (loader)
rootnoverify (hd2,0)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1

```

I don't which XP isn't running for you, just change the faulty one though, hit back with your progress. ;)

---

### Post by Frankelastic on 2006-09-15
i tried what you suggested but i ended up with the same results. I forgot to mention before that i have previously tried to install a pre-release of vista. Is it possible that this could have done something to the mbr of xp. Also upon trying your suggestion i was reminded that when booting straight off the windows hard drive,(after a failed attempt to boot from grub) norton GoBack reports an error with the drive, fixex it and then tells me to reboot, upon this second reboot windows boots fine. Sorry for the trouble coused by my lack of memory.

Thanks.

---

### Post by turbojugend_gr on 2006-09-15
Oh come on... It is definately messed up by vista shit... Not mbr though, just the boot sectors of xp, which norton fixes to it's previous state (as before doing vista shit to your machine...). You should have told me that earlier, it's ok though. Since that's the case I can't help you you have to fix mbr for your xp drive or sth, but I can't be sure 'bout that. Best of luck m8.

---

### Post by Frankelastic on 2006-09-15
ok thanks for that, i couldnt beleive i forgot about the vista thing, well thanks for you help anyway. cya

---

