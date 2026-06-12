---
title: "[SOLVED] How do I change the Standard OS in GRUB Bootloader?"
date: 2009-01-05
forum: General Help
---

### Post by Hunsrus on 2009-01-05
Gentlemen,

I've been using Ubuntu for quite some time now, using a dual boot with Windows XP x64. However, I still use windows more than Ubuntu, and I'm slowly making the step to Ubuntu.

Now ofcourse, every time I boot up, the OS in the GRUB bootloader that is standardly selected, is Ubuntu. Is there any way to change this standard selection to Windows, so I can just boot up, walk away from my PC and get myself a cup of coffee?

Thanks.

Hunsrus

---

### Post by iaculallad on 2009-01-05
To edit your menu.lst file:

Open /boot/grub/menu.lst for editing:

```
gksudo gedit /boot/grub/menu.lst
```

Find this line and change the default value to point to the value of your desired kernel.

```
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
**[COLOR="DarkRed"]default         0[/COLOR]**
```

Sample values using my current menu.lst file will be:

```
## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-15-generic		**[COLOR="Blue"]<----- 0[/COLOR]**
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=16d722ac-565b-4d2d-9c6e-317b1ac253ff ro quiet splash
initrd          /boot/initrd.img-2.6.22-15-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)		**[COLOR="Blue"]<----- 1[/COLOR]**
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=16d722ac-565b-4d2d-9c6e-317b1ac253ff ro single
initrd          /boot/initrd.img-2.6.22-15-generic

title           Ubuntu 7.10, kernel 2.6.22-14-generic		[COLOR="Blue"]**<----- 2**[/COLOR]
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=16d722ac-565b-4d2d-9c6e-317b1ac253ff ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)		**[COLOR="Blue"]<----- 3[/COLOR]**
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=16d722ac-565b-4d2d-9c6e-317b1ac253ff ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+		**[COLOR="Blue"]<----- 4[/COLOR]**
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

If I want to boot on "Ubuntu 7.10, kernel 2.6.22-14-generic" as default, I would change the value of default to 2 instead of 0.

> # You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
**[COLOR="DarkRed"]default         2[/COLOR]**

After you had changed it, Save and close. And while on your terminal, reboot.

```
sudo shutdown -r now
```

HTH

---

### Post by blazemore on 2009-01-05
He speaketh the truth.
There are probably a few graphical editors, but I find this the easiest way.
Perhaps this should be a part of the installation process, much as it is with Suse.

---

### Post by Hunsrus on 2009-01-05
Thank you, this sure helps.

Hunsrus

---

### Post by mcduck on 2009-01-05
> **iaculallad said:**
> To edit your menu.lst file:

Open /boot/grub/menu.lst for editing:

```
gksudo gedit /boot/grub/menu.lst
```

Find this line and change the default value to point to the value of your desired kernel.

```
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
**[COLOR="DarkRed"]default         0[/COLOR]**
```

Sample values using my current menu.lst file will be:

```
## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-15-generic		**[COLOR="Blue"]<----- 0[/COLOR]**
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=16d722ac-565b-4d2d-9c6e-317b1ac253ff ro quiet splash
initrd          /boot/initrd.img-2.6.22-15-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)		**[COLOR="Blue"]<----- 1[/COLOR]**
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=16d722ac-565b-4d2d-9c6e-317b1ac253ff ro single
initrd          /boot/initrd.img-2.6.22-15-generic

title           Ubuntu 7.10, kernel 2.6.22-14-generic		[COLOR="Blue"]**<----- 2**[/COLOR]
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=16d722ac-565b-4d2d-9c6e-317b1ac253ff ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)		**[COLOR="Blue"]<----- 3[/COLOR]**
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=16d722ac-565b-4d2d-9c6e-317b1ac253ff ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+		**[COLOR="Blue"]<----- 4[/COLOR]**
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

If I want to boot on "Ubuntu 7.10, kernel 2.6.22-14-generic" as default, I would change the value of default to 2 instead of 0.



After you had changed it, Save and close. And while on your terminal, reboot.

```
sudo shutdown -r now
```

HTH

after that you should also find this line in the default options section of the menu.lst:
```

# updatedefaultentry=false
```
..and change it into this:
```

# updatedefaultentry=true
```
What this means is that when a kernel update adds new kernel to Grub menu the value for default OS will be updated.

For example if you now have 3 Ubuntu entries (normal boot, recovery mode and memtest) and then one Windows entry the default boot option for Windows would be "3". Then kernel update adds a new kernel (2 new entries) and Windows becomes sixth entry on the list instead of fourth. If the default boot option isn't updated it will now point to your old Linux kernel instead of Windows.

---

