---
title: "Grub boot failure"
date: 2004-11-17
forum: Desktop Environments
---

### Post by timjones on 2004-11-17
I have installed Ubuntu dual boot with Windows XP SP2.

Install went fine and reboot to Ubuntu was OK.  However, if I reboot to XP and then boot back to Ubuntu, I see the Grub prompt for the merest of seconds and the system re-boots over and over.

This is the second time this has occured.  I have another system with Ubuntu and XP SP1, which works fine.

Does anyone have a suggestion or have experienced the same problem.

TIA

Tim

---

### Post by marky on 2005-01-20
Hi!

I have EXACTLY the same problem with my Toshiba Satellite Pro 6100, but I did not find any solution for this yet. I'll keep on searching for a solution. Anything I find, I'll post here.

---

### Post by shmonkey on 2005-01-21
take a look at your /boot/grub/menu.lst file

change 'timeout' to a larger value to give your more time in the grub menu.

Check the set up for your XP partitions or post it here to get someone to take a look at it.  

regards

Shmonkey

---

