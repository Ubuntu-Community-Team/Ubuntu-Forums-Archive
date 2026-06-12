---
title: "grub bootparamters don't stick"
date: 2008-05-16
forum: Desktop Environments
---

### Post by DFreeze on 2008-05-16
I want to add a bootparameter to grub (i8042.noloop=1 to get my touchpad working) but adding it in /boot/grub/menu.lst doesn't work. Sure, it shows op in my menu.lst, but after boot still no touchpad. Rebooting and editing the bootparameters in grub shows that the added bootparameter isn't there. 

How do I get it to stick?

---

### Post by hermes0710 on 2008-05-16
Can you post your menu.lst (with the parameters)?

---

### Post by DFreeze on 2008-05-16
> **hermes0710 said:**
> Can you post your menu.lst (with the parameters)?

Without all the jibba-jabba in the beginning, here's the listing. I've put the boot parameter in front of all the ubuntus I have installed (the touchpad hasn't worked since Edgy), but tested it only on the first one, my main OS.

```
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda5.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (on /dev/hda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a5f26bb9-e6df-4bcc-9492-38ac2daa123b ro quiet splash i8042.noloop=1
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda5.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode) (on /dev/hda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a5f26bb9-e6df-4bcc-9492-38ac2daa123b ro single i8042.noloop=1
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda5.
title		Ubuntu 8.04, memtest86+ (on /dev/hda5)
root		(hd0,4)
kernel		/boot/memtest86+.bin  
savedefault
boot

title		Ubuntu Testing 8.04, kernel 2.6.24-16-generic
root		(hd0,10)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=da2383c2-389a-457e-bd25-2c35cf1be8c2 ro quiet splash i8042.noloop=1
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,10)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=da2383c2-389a-457e-bd25-2c35cf1be8c2 ro single i8042.noloop=1
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.24-15-generic
root		(hd0,10)
kernel		/boot/vmlinuz-2.6.24-15-generic root=UUID=da2383c2-389a-457e-bd25-2c35cf1be8c2 ro quiet splash i8042.noloop=1
initrd		/boot/initrd.img-2.6.24-15-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-15-generic (recovery mode)
root		(hd0,10)
kernel		/boot/vmlinuz-2.6.24-15-generic root=UUID=da2383c2-389a-457e-bd25-2c35cf1be8c2 ro single i8042.noloop=1
initrd		/boot/initrd.img-2.6.24-15-generic


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda10.
title		PCLinuxOS release 2007 (PCLinuxOS) for i586 (on /dev/hda10)
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.18.8.tex5 root=/dev/hda10 
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda8.
title		KUbuntu 7.10, kernel 2.6.22-14-generic (on /dev/hda8)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2e3f50c2-6043-4a96-9a2d-7781746afaea ro quiet splash i8042.noloop=1
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda9.
title		UbuntuStudio 7.10, memtest86+ (on /dev/hda9) i8042.noloop=1
root		(hd0,8)
kernel		/boot/memtest86+.bin  
savedefault
boot

```

---

### Post by hermes0710 on 2008-05-16
The only thing i see from your menu.lst different to others' using the same parameter is that they have the parameter before the "root=???" option. Try doing the same.

I mean have something like
```
kernel		/boot/vmlinuz-2.6.24-15-generic i8042.noloop=1 root=UUID=da2383c2-389a-457e-bd25-2c35cf1be8c2 ro single
```
instead of
```
kernel		/boot/vmlinuz-2.6.24-15-generic root=UUID=da2383c2-389a-457e-bd25-2c35cf1be8c2 ro single i8042.noloop=1
```

---

### Post by DFreeze on 2008-05-16
Hey, thanks for your help so far. I've tried to place the boot parameters before the 'root=...' part, but it didn't help. When in grub, and pressing 'e' to edit the default boot options show. The i8042... is nowhere to be seen. Either with the option on the end, or before the 'root=...' statement. 

Any ideas?

::UPDATE::

<shame mode> OMG how stupid can I be! I just couldn't believe that something as straightforward as a textfile is not read right - and that's when it hit me. Normally I was working on Ubuntu-Testing (my Hardy disk). That one is the last OS installed on this machine. Later I upgraded my Gutsy to Hardy, and started working from that disk again, but the grub menu is off course on the last disk installed... So I edited the menu.lst on my Hardy testing disk and off I went...</shame mode> 

Sorry to have wasted your time, but thanks anyway for trying to help. People like you make this forum such a cool place to come to!

---

### Post by hermes0710 on 2008-05-16
Try changing the timeout seconds in menu.lst to see if this will take effect on the next reboot. Strange ...

---

### Post by DFreeze on 2008-05-16
Oh, I see you replied during my typing my reply. I explained in the post above what happened - and why I'm ashamed. ;)

---

### Post by hermes0710 on 2008-05-16
Don't be... Happens to all of us... Once i was editing a post's fstab, posted it and rebooted to see the differences :)

---

### Post by DFreeze on 2008-05-16
> **hermes0710 said:**
> Don't be... Happens to all of us... Once i was editing a post's fstab, posted it and rebooted to see the differences :)

Haha, difference was night and day, for sure ;) Yeah, I guess you're right. It's just that after the light goes on and I see what's going on, it looks so downright simple, I must have been an idiot not to see... 

They say you learn from your mistakes - well then I must surely learn a lot :)

---

