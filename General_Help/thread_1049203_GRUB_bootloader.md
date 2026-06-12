---
title: "GRUB bootloader"
date: 2009-01-24
forum: General Help
---

### Post by chris.tkd on 2009-01-24
Hi,

I currently have ubuntu 8.04 installed.

If i put in a hard drive from another computer (keeping my current harddrive with ubuntu installed also) with vista x64 installed will grub pick it up the vista boot as an option automatically or will i need to reinstall grub?

Thanks,
Chris.

---

### Post by Axelpalm on 2009-01-24
Add windows to you /boot/grub/menu.lst manually.

---

### Post by bumanie on 2009-01-24
You will need to reinstall grub and it will be best if you have vista as the first bootable drive in bios. You will also have to manually add vista to the /boot/grub/menu.lst via chainloading, so that grub knows to hand over to vista's bootloader if you wish to boot into vista.

---

### Post by Axelpalm on 2009-01-24
> **bumanie said:**
> You will need to reinstall grub and it will be best if you have vista as the first bootable drive in bios. You will also have to manually add vista to the /boot/grub/menu.lst via chainloading, so that grub knows to hand over to vista's bootloader if you wish to boot into vista.
what's the point of re-installing grub ? and then anyway manually add windows chainloading ?
Yes, it is better to have windows on first disk (I think).

---

### Post by chris.tkd on 2009-01-24
Will the effect of reinstalling grub be the same as adding vista to my menu.lst? 

Does a vista entry in the menu.lst look the same as an xp install (except for a difference in the root)? how do you work out the root of an install?

---

### Post by jocko on 2009-01-24
You do NOT need to reinstall grub (reinstalling grub will not magically add vista to the boot menu anyway), and you do NOT need to set the vista drive as first bootable drive. Just make the end of your menu.lst look something like this:```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

title Windows Vista
[COLOR=Blue]root (hd1,0)[/COLOR]
savedefault
makeactive
[COLOR=Blue]map  (hd0) (hd1)
map  (hd1) (hd0)[/COLOR]
chainloader +1
```Notice that in this case vista is on the second hard drive (i.e not the first drive in the bios boot order), but the "map" commands will make sure grub re-maps the drives before the vista bootloader is loaded.
The "root" is the partition you have vista on. The first hard drive (=first in bios boot order) is (hd0) and the second hard drive is (hd1). So the first partition of the second hard drive is (hd1,0). It may be more complicated if you have more than two hard drives, as you have to figure out which physical drive is (hd1) and which is (hd2)...

---

