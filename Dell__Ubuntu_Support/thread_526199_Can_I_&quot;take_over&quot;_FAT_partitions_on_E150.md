---
title: "Can I &quot;take over&quot; FAT partitions on E1505N?"
date: 2007-08-15
forum: Dell  Ubuntu Support
---

### Post by AJL on 2007-08-15
I'd like to take back the 2 gb of FAT (16|32) space on my E1505N and format it for swap use.

Is there any known issues with doing this on my Dell Ubuntu laptop?  Especially since the MediaDirect boot option doesn't do s#@ anyways.

Thanks!
Aaron

---

### Post by aldenhg on 2007-08-15
Yeah, you can do whatever you want to those extra partitions, but keep in mind that your bootloader (grub) will have a whole bunch of links that are incorrect if you go messing around with your partition table. It's not tough to fiix (just edit the bottom of /boot/grub/menu.list to reflect the new partition layout - googleing "edit grub menu" will get you all the help you need.), but it's also not for the faint of heart because if you restart before making the edits you'll have a really tough time fixing everything if you don't already know how.

---

### Post by sciurus on 2007-08-16
> **aldenhg said:**
> Yeah, you can do whatever you want to those extra partitions, but keep in mind that your bootloader (grub) will have a whole bunch of links that are incorrect if you go messing around with your partition table. It's not tough to fiix (just edit the bottom of /boot/grub/menu.list to reflect the new partition layout - googleing "edit grub menu" will get you all the help you need.), but it's also not for the faint of heart because if you restart before making the edits you'll have a really tough time fixing everything if you don't already know how.

Running mkswap on a non-boot partition won't affect grub at all. The only file that should need editing is /etc/fstab

---

