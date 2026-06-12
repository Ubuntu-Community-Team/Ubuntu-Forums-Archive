---
title: "Dual Booting, two boot loaders"
date: 2009-07-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by josephe on 2009-07-13
Hi all
Love Ubunutu but since I need to pop into Windows (Vista) from time to time I have dual-booted my Dell Inspiron 1520 it works fine except that I get GRUB and the Windows boot loader starting one after the other.
 
Can someone please give me a step by step for switching of GRUB and let Windows Boot Loader give me the choice of Vista or Ubuntu
 
Many thanks
 
Joseph

---

### Post by mikewhatever on 2009-07-14
Why do you think you have two boot loaders? Can you describe in details what happens when you boot.

---

### Post by josephe on 2009-07-15
Well when I boot the machine I get a GRUB screen, with Ubuntu and Vista as options, so far fine. If I choose Vista it then presents me with the Windows Boot Loader Vista as option 1 Ubuntu 8.04 (my previous install) second
 
I'm going to try EasyBCD to sort this out, but appreciate any suggestions
 
Thanks

---

### Post by mikewhatever on 2009-07-15
Did you install the previous 8.04 inside Windows? If so, you may simply need to edit the boot.ini file and remove an Ubuntu related entry.
Grub doesn't actually load Windows, but rather hands the process to the Windows boot loader. What you describe is normal, except the 8.04 entry.

---

### Post by /\/\@/\/ |_| on 2009-07-15
IMO simply edit the boot configuration of vista.
The boot.ini is not available in the vista , however the 'msconfig' provides a safe way to edit the boot configuration.
Run 'cmd' and then enter 'msconfig' , a window will open, then go to the 'boot' tab and delete the previous ubuntu entry form there.:popcorn:

---

