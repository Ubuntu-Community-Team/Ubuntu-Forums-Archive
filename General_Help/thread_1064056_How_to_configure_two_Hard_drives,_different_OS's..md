---
title: "How to configure two Hard drives, different OS's."
date: 2009-02-08
forum: General Help
---

### Post by mwade on 2009-02-08
Hello,

I have a question about the use of multiple hard drives.  I currently have one hard drive with Ubuntu installed.  I want to buy another hard drive to install windows.  I am familiar with dual booting, but only dual booting two OS's on the same hard drive.  How or where do I configure to choose b/t the two hard drive's (and operating systems).  Does it have to do with the hard drive jumpers?  I would think that if using the OS bootloader the drive has already been selected.  Is it in the BIOS?

Thanks for your help.

---

### Post by logos34 on 2009-02-08
> **mwade said:**
> How or where do I configure to choose b/t the two hard drive's (and operating systems).  Does it have to do with the hard drive jumpers?  I would think that if using the OS bootloader the drive has already been selected.  Is it in the BIOS?



Simply add an entry for windows (with 'mapping') to your ubuntu /boot/grub/menu.lst [like this]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk")

---

### Post by lha on 2009-02-08
Safest bet is to unplug your Ubuntu drive before installing Windows. When Windows is installed, put the drive with Ubuntu back and set bios to boot from it. Edit menu.lst as logos34 suggested.

---

