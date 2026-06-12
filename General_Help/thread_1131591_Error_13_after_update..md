---
title: "Error 13 after update."
date: 2009-04-21
forum: General Help
---

### Post by sadicote on 2009-04-21
:oI just killed my system (i think), after doing an update with Update Manager, I am getting an error message during boot for all the kernels and their recovery modes that i have, "Error 13: Invalid or unsupported executable format, press any key to continue", and when i do that i am returned to the tty terminal,also, in recovery mode, "Target filesystem doesn't have /sbin/init. No init found. Try passing init= bootarg" I have to manually reboot/shutdown after that as 'exit' doesn't get me anywhere and i get a "system panic: Attempted kill init" or something like that. I don't know about the system but i am panicked out of my mind! Now i swear, all i did was update Jaunty and, reboot as was required for the updates to take effect; i did wonder why linux kernel 2.6.28.11 was included in the updates list when i already had it, but didn't pay much attention to it, after all "regular updates are good for the system/security". This is one time where i presume to demand your urgent assistance, so "pretty please with cream and a cherry on top". I am using a live Ibex at the moment and after having tasted of the latest Jaunty, i don't think i can live with it.:(

---

### Post by sadicote on 2009-04-21
Guys, you should also know that i am not dual-booting or anything of that sort, so i have nothing to fall back on. And i regret to say this--and apologize--but i did sense a tendency here, of giving more priority to dual-booters, people who expressed a tentative desire to switch to Ubuntu, or those who out-rightly threatened to have nothing to do with it in future.:(:(

---

### Post by sadicote on 2009-04-21
I have already tried booting from a Live CD, using sudo grub-install, which returned "device not specified"; after that i tried sudo grub-install /dev/sda1, which also returned with a "device not found". Would appreciate some advice on how to proceed from here, or i am going to be stuck with using a Live CD. I have decided not to reinstall and wouldn't even think of "switching back to Windows".

---

### Post by sadicote on 2009-04-21
It is a fact, Jaunty update effs up the grub menu if it's on ext4. Somebody report this as a bug before the final release..oh, what do i care, i will take care of my problems by googling, henceforth, and manage with what i have. Good luck to all of you.

---

