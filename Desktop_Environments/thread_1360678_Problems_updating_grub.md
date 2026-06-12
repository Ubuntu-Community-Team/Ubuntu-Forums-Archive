---
title: "Problems updating grub"
date: 2009-12-21
forum: Desktop Environments
---

### Post by sjoseph on 2009-12-21
I've updated grub using the 'update grub' command a few times, but the last time I tried I got an error message as follows:

sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) 

Any thoughts. Thanks in advanced.

---

### Post by AVH on 2010-01-16
I get the same response to "sudo update-grub" . i.e. "Could not find /boot/grub/menu.lst file". 

However, when I try "sudo update-grub2" I get "update-grub2: command not found".

I thought I chose to stay with grub rather than grub2 when I installed Karmic, but changing '/etc/default/grub' doesn't affect the boot process ( which works), and' /boot/grub/menu.lst' doesn't exist. So... I'm a little confused as to what is going on.

---

### Post by AVH on 2010-01-16
Apparently, I do, in fact, have the new grub2. At least, my boot screen says " GNU Grub Version 1.97 beta4" across the top.  

Also, neither the 'esc' key or the 'shift' key get any response in the boot screen.

---

