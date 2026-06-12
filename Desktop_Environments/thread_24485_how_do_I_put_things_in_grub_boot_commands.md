---
title: "how do I put things in grub boot commands?"
date: 2005-04-07
forum: Desktop Environments
---

### Post by jasplund on 2005-04-07
I'm trying to get my ltmodem to work and apparently I'm supposed to put the line pci=routeirq in the grub boot commands. How do i do this? 

Johan
See further [http://www.ubuntuforums.org/showthread.php?t=21312](http://www.ubuntuforums.org/showthread.php?t=21312)

---

### Post by soul_rebel on 2005-04-07
it is in the /boot/grb/menu.lst
be careful

---

### Post by jasplund on 2005-04-07
Am I supposed to write it like this 

"title		Ubuntu, kernel 2.6.10-5-686 
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.10-5-686 root=/dev/hda6 ro quiet splash vga=0x317 **pci=routeirq** 
initrd		/boot/initrd.img-2.6.10-5-686
savedefault
boot"


thanks Johan

---

### Post by duff on 2005-04-07
[QUOTE=jasplund]Am I supposed to write it like this 

"title		Ubuntu, kernel 2.6.10-5-686 
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.10-5-686 root=/dev/hda6 ro quiet splash vga=0x317 **pci=routeirq** 
initrd		/boot/initrd.img-2.6.10-5-686
savedefault
boot"


thanks Johan[/QUOTE]

that'll work for that one kernel entry, but only until you update your kernel.  To make sure it's there all the time, look for the line that starts with "# kopt" and add the additional kernel options there.

---

### Post by bored2k on 2005-04-07
Why dont you guys download grubconf and do that through a pretty harmless GUI .. safer [sort of].

---

### Post by skoal on 2005-04-07
If you just want to test it out first, without making any file changes:

Hit ESC when grub first boots up, hit 'e' (for edit), select the kernel line you wish to add the option to, and append those options to it (like for yours):

kernel /boot/vmlinuz-2.6.10-5-686 root=/dev/hda6 ro quiet splash vga=0x317 pci=routeirq

That will not make any changes to your 'menu.lst' and you can 'try before you buy' that way...

---

