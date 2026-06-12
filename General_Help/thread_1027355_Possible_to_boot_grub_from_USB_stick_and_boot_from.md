---
title: "Possible to boot grub from USB stick and boot from harddrive using the grub"
date: 2009-01-01
forum: General Help
---

### Post by Basicalyptic on 2009-01-01
As the title says, would it be possible to install grub on a usb thumb drive and then use it to boot ubuntu installed in a hard drive?

---

### Post by djbushido on 2009-01-01
Technically yes, but not recommended by any means. What are you trying to do? because if it's dual-booting, then grub should handle windows. Also, keep in mind that if you lose the flash drive, you're screwed. If you would still like to go through with this, reply.

---

### Post by Basicalyptic on 2009-01-01
I'd use the Windows XP bootloader and if I'd need ubuntu, I would just stick the thumb drive to the pc and reboot. It doesn't matter if I lose the stick, because I don't store anything important on this computer. I could start this computer faster, because I use ubuntu mainly on my other computer.

---

### Post by djbushido on 2009-01-01
Why don't you set up the ubuntu grub as the system bootloader, then just default to booting windows? you wouldn't need to worry about a usb drive, and windows would remain intact.

---

### Post by caljohnsmith on 2009-01-01
Yes, it is possible to do exactly what you want to do; you can install Grub to the MBR of your USB stick and yet have Grub point to the Ubuntu on the HDD for its boot files. Then if you set your BIOS to boot the USB stick before your HDD, you will get the Grub menu and should be able to boot into Ubuntu. If the USB stick is disconnected, your computer should boot your internal HDD and go straight into Windows. If you want help doing that, how about posting the following with your USB stick connected:
```
sudo fdisk -lu
```
And we can work from there if you want.

---

