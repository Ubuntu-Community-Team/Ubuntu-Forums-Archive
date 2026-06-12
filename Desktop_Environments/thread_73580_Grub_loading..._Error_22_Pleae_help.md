---
title: "Grub loading... Error 22 Pleae help"
date: 2005-10-09
forum: Desktop Environments
---

### Post by iriedodge on 2005-10-09
i've got a grub error 22, any tips on how to get my machine to boot, anything... it also has winxp on there, I think I deleted the ubuntu partition accidentally. I can't seem to boot the Ubuntu install CD or thw win XP CD (USB-dvd, which normally will boot fine) :confused:

---

### Post by annex on 2005-10-10
From the grub manual: [http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting]("http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting")

> 22 : No such partition
This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk.  
This makes it sound to me like you're grub config is wrong somehow. I'd bet the next step would be to boot to an Ubuntu CD. You say you can't though.

I really don't see how Grub would prevent you from booting from a CD. I'd suggest checking in your BIOS you have CD booting enabled and that it the computer attempts to boot to it before booting to the HDD.

I hope this helps, I'm new to grub.  I used to use Lilo.

---

