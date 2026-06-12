---
title: "Bootloader fails to install"
date: 2008-11-28
forum: Debian
---

### Post by rolnics on 2008-11-28
I've got a Lenny DVD install disk everything goes fine until I get to installing the bootloader. Grub won't install and neither will LILO.

Just for info, I've only got Heron installed and have grub on a separate partition, but all I want is to install grub on the debian partition so it boots

Any suggestions would be great

---

### Post by prshah on 2008-11-28
> **rolnics said:**
> 
everything goes fine until I get to installing the bootloader. Grub won't install and neither will LILO.


You need to turn off "Virus Protection" related options (if you have any) in the BIOS to allow writes to the MBR.

---

### Post by rolnics on 2008-11-28
Thanks for that, I'm not aware of that option in my BIOS, but I will check when I get home.

Could I use an Ubuntu live-cd to install grub for Debian?

---

### Post by LinuxGuy1234 on 2008-11-28
> **rolnics said:**
> Thanks for that, I'm not aware of that option in my BIOS, but I will check when I get home.

Could I use an Ubuntu live-cd to install grub for Debian?

You can use the Ubuntu Live CD to install GRUB for Debian.

---

### Post by basenvironment on 2008-11-28
You could simply add the new debian install to your active menu.lst file

---

