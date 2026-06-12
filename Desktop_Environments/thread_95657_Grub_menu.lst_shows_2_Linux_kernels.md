---
title: "Grub menu.lst shows 2 Linux kernels"
date: 2005-11-27
forum: Desktop Environments
---

### Post by Terrycymru on 2005-11-27
I am running a dual boot system and I have recently auto upgraded to the latest Linux kernel. Now my grub menu.lst shows the old and the new Linux kernels making the list unneccessarily long. Is this a bug? Is it safe to remove the old Linux kernel entries or comment them out?

---

### Post by towsonu2003 on 2005-11-27
hi,
that's not a bug... when doing a kernel upgrade, the system uploads a new kernel without really touching to the old one. 

The list has 2 kernels so that if the new oone doesnt work, u can switch to the other one. 

I have about 10 items in my menu.list due to changes I made... that's fine, dont worry.

---

### Post by Terrycymru on 2005-11-27
Thanks towsonu2003 for your quick reply and explanation. I'll leave the old kernel in place. However, I wouldn't want the menu.lst to grow too long because it makes it more tedious toggling to the required OS on a dual boot system.

---

### Post by angkor on 2005-11-27
[QUOTE=Terrycymru]Thanks towsonu2003 for your quick reply and explanation. I'll leave the old kernel in place. However, I wouldn't want the menu.lst to grow too long because it makes it more tedious toggling to the required OS on a dual boot system.[/QUOTE]

If the new kernel works without any problems, you can always uninstall the old kernel using apt.

```
sudo apt-get remove linux-image-blah-blah
```

---

### Post by towsonu2003 on 2005-11-27
[QUOTE=Terrycymru]Thanks towsonu2003 for your quick reply and explanation. I'll leave the old kernel in place. However, I wouldn't want the menu.lst to grow too long because it makes it more tedious toggling to the required OS on a dual boot system.[/QUOTE]
you're most welcome :) 

if you have no problems with new kernel (wait for a couple of months...), you can comment the lines for old kernel... that's if you dont have serious hard disk free space problems. 

to comment them: 
```
 
sudo cp /boot/grub/menu.list /boot/grub/menu.list.backup
sudo gedit /boot/grub/menu.list 
```

be very carefull as any error may screw the boot process...

there you will see many lines, scroll to the end where you will see the list of the kernels and the windows entry (assumption). here is mine as example (DO **NOT** copy paste it as yours): 
```

## ## End Default Options ##

title           Ubuntu, kernel 2.6.12-10-686
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-10-686 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-686
savedefault
boot

title           Ubuntu, kernel 2.6.12-10-686 (no splash)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-10-686 root=/dev/hda3 ro quiet
initrd          /boot/initrd.img-2.6.12-10-686
savedefault
boot

title           Ubuntu, kernel 2.6.12-10-686 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-10-686 root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.12-10-686
boot

title           Ubuntu, kernel 2.6.12-10-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-10-386 (no splash)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro quiet
initrd          /boot/initrd.img-2.6.12-10-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.12-10-386
boot

title           Ubuntu, kernel 2.6.12-9-686
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-9-686 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-686
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot

# title         Ubuntu, memtest86+
# root          (hd0,2)
# kernel                /boot/memtest86+.bin
# boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```
one of my old kernel entries is this (towards the very end in my file):
```
 
title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot

```
to comment it, make it look like this:
```

# title           Ubuntu, kernel 2.6.12-9-386
# root            (hd0,2)
# kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro quiet splash
# initrd          /boot/initrd.img-2.6.12-9-386
# savedefault
# boot

```
and it will dissapear from your grub list on boot. 

Again, do this if the new kernel is okay and if you feel you are **very** comfortable doing it...

and, have fun :)

---

### Post by gw90se on 2005-11-27
If I have edited the grub menu to boot number 6 (for example) so that Windows boots up (Ihave to do this at my work location), will I also need to edit the boot number to 4 (if I were to comment out 2 entries)?

---

### Post by Vlammetje on 2005-11-27
ah, good tip... I have about 10 items in my bot up list now which is a bit much... will have a careful play with remving a few then (pray for me!!!:p )

---

