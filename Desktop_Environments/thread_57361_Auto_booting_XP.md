---
title: "Auto booting XP"
date: 2005-08-16
forum: Desktop Environments
---

### Post by Kareth1987 on 2005-08-16
Hi,

I was wondering if it's possible to auto boot XP and skip the selection process of GRUB when i boot?

And maybe when its booting i press a key or something to load the boot screen so that i can choose linux when i would like to use it.

Thankyou,

-Drew

P.S. This isnt really important, but is it possible to change the colour of the text/background in the terminal? I dunno, just a bit of personalisation :D

---

### Post by izmaelis on 2005-08-16
You can configure GRUB to boot your M$ Windows by default just like Ubuntu is set to boot by default now. You can change amount of time when GRUB window is displayed too.

---

### Post by Buffalo Soldier on 2005-08-16
There is a way to change the default boot from Ubuntu to WinXP. Refer to: [http://ubuntuguide.org/#changedefaultosgrub](http://ubuntuguide.org/#changedefaultosgrub)

note: X_sequence = the order of the *title* entry on the menu. For example if WinXP is the fifth entry on the menu then your X_sequence should be 4. (start counting from 0).

```
title		Ubuntu, kernel 2.6.10-5-686 [color=red]<- first entry[/color]
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.10-5-686 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-686
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-686 (recovery mode) [color=red]<- second entry[/color]
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.10-5-686 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.10-5-686
savedefault
boot

title		Ubuntu, kernel memtest86+ [color=red]<- third entry[/color]
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems: [color=red]<-  fourth entry[/color]
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition [color=red]<- fifth entry[/color]
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```
For changing the color at terminal, go to the terminal toolbar and go to Edit -> Current Profile -> Colors.

---

### Post by ekravche on 2005-08-26
[QUOTE=Buffalo Soldier]There is a way to change the default boot from Ubuntu to WinXP. Refer to: [http://ubuntuguide.org/#changedefaultosgrub](http://ubuntuguide.org/#changedefaultosgrub)

note: X_sequence = the order of the *title* entry on the menu. For example if WinXP is the fifth entry on the menu then your X_sequence should be 4. (start counting from 0).

```
title		Ubuntu, kernel 2.6.10-5-686 [color=red]<- first entry[/color]
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.10-5-686 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-686
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-686 (recovery mode) [color=red]<- second entry[/color]
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.10-5-686 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.10-5-686
savedefault
boot

title		Ubuntu, kernel memtest86+ [color=red]<- third entry[/color]
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems: [color=red]<-  fourth entry[/color]
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition [color=red]<- fifth entry[/color]
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```
For changing the color at terminal, go to the terminal toolbar and go to Edit -> Current Profile -> Colors.[/QUOTE]


nice, thanx for the reply

---

