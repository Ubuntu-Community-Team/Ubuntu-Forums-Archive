---
title: "Debian stole the grub"
date: 2006-08-23
forum: Desktop Environments
---

### Post by craig552 on 2006-08-23
I recentlty installed Debian on to a second partition (hda3). During the install Debian detected Ubuntu and asked if I wanted them both listed in grub, which I do, so I clicked OK. 
However, Debian installed a second grub on to hda3 which it configured to dual boot with ubuntu. The original grub is still on hda1 with Ubuntu root.

My problem is that the second copy of grub (on hda3) is being used as the boot loader, but I want to use the grub on hda1.

How can I get the original version of grub to start at boot, and not the new version?

---

### Post by PathSpace on 2006-08-23
What is wrong with the new GRUB?  Does it not detect your Ubuntu partition?

---

### Post by harisund on 2006-08-23
You could boot into Ubuntu (if you can, that is) and execute something like 'sudo grub-install /dev/hda1' but then be prepared if you are not able to access your Debian installation immediately since I doubt Ubuntu knows about Debian's presence.

---

### Post by craig552 on 2006-08-24
@pathspace
It does see Ubuntu, but I want to use grub on hda1 cos I'm planning on scrubbing hda3 soon. hda3 is just a test partition, it gets used for several different things.

@harisund
Cheers I'll give that a go later. I've already backed up menu.lst from the hda3 grub (with ubuntu and debian), so after the install I'll just stick it in /boot/grub/ on hda1.

What is it in the bootup sequence which points to a specific bootloader/partition?

---

### Post by Tomosaur on 2006-08-24
Alter the menu.lst file on the hda3 partition so that the line which says 'groot' points to the partition you actually wish to use.

---

### Post by Ramses de Norre on 2006-08-24
Boot into ubuntu and do ```
sudo grub
root (hd0,0)
setup (hd0)
quit
sudo update-grub
```
This will install grub in the mbr of hda1 (the hd0 part) and will use the menu.lst from /boot/grub/ on hda1 (the hd0,0 part).
Change partition numbers to your needs..
The update-grub part will setup all installed kernels in your menu.lst and if you're lucky it will find debian too.

---

### Post by craig552 on 2006-08-26
Cheers Ramses, that worked great.

---

