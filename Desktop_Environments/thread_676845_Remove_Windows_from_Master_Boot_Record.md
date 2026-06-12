---
title: "Remove Windows from Master Boot Record"
date: 2008-01-24
forum: Desktop Environments
---

### Post by neal.s on 2008-01-24
I uninstalled Windows XP from my laptop yesterday, in favour of a Virtual Box for my few Windows needs. When my grub loader boots up it still has the Windows entry in it. I'm going to be skipping the bootloader anyway, but it just bugs me that it's still there. Does anyone know how I can edit that list?

---

### Post by wieman01 on 2008-01-24
> sudo gedit /boot/grub/menu.lst
Then remove the relevant Windows section. Post the contents here if you feel uncertain. And make a backup of that file first:
> sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup

---

### Post by neal.s on 2008-01-24
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

Should I delete all that, or just the first two lines?

---

### Post by neal.s on 2008-01-24
There's also this above:

> # This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

I imagine I won't need that anymore, either.

---

### Post by wieman01 on 2008-01-24
Yes, please remove both sections and restart the PC. Time to open a bottle of champagne. :-)

---

### Post by neal.s on 2008-01-24
Done and done!

:)

---

### Post by wieman01 on 2008-01-24
Cool. Please mark this thread as 'Solved'.

---

