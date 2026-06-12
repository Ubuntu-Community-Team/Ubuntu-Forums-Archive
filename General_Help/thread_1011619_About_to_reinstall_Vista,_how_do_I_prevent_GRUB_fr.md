---
title: "About to reinstall Vista, how do I prevent GRUB from dying?"
date: 2008-12-14
forum: General Help
---

### Post by Aleksei Vasiliev on 2008-12-14
I'm going to reinstall Vista on my system since it is performing very badly. I have a triple-boot system on one hard drive:
* Windows XP
* Windows Vista
* Ubuntu 8.10

My system goes to the GRUB bootloader, which can then be used to launch the Microsoft bootloader.

I know that when I reinstall Vista, it will kill GRUB. How do I save GRUB?

My Ubuntu install (or maybe my home partition only?) is encrypted.

---

### Post by TeXtonyx on 2008-12-15
I don't think you can prevent Vista from overwriting grub in the MBR.
Vista isn't flexible like grub which can be installed to the /boot
partition. I would back up my menu.lst and fstab first and then
reinstall grub after Vista to replace Vista in the MBR. I'm not
so sure that the fstab UUID settings will remain the same as the
old identifier when Vista is reinstalled and then grub is rerun.
sudo blkid is the command which lets you see and then compare UUIDs
although this may not even be an issue.

---

### Post by RomanIvanov on 2008-12-15
You will defenitely find useful this approach, may be nnot the best but works: [http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

---

### Post by caljohnsmith on 2008-12-15
After you successfully install Vista, you can restore Grub to the MBR (Master Boot Record) by booting your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd0,2), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Then reboot, and you should have Grub back. Let me know if your run into problems though.

---

