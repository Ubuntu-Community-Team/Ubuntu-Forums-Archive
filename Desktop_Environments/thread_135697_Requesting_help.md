---
title: "Requesting help"
date: 2006-02-24
forum: Desktop Environments
---

### Post by naveents on 2006-02-24
I need 2 make windows Xp as the default Operating system while booting..my current boot screen shows ubuntu as default..i am a software engineer and as my dad also wants to use the PC,i would need to make XP as the first option...plz help me in this matter!!!!

---

### Post by Ramses de Norre on 2006-02-24
You need to edit the menu.lst file in /boot/grub.
Somewhere in the beginning between all commented lines there is a line that now probably says 'default 0', you need to change the 0 to the number of windows. So just count in the kernel list lower in the file to know which number windows is. 
Only thing I don't know is what happens when a kernel is added then.
Maybe you can also move the windows section and place it before the ubuntu sections, it will load as default to then (if default is still set at 0).

---

### Post by ajgreeny on 2006-02-24
You can certainly move the windows entry up the list in menu.lst, but it can cause some problems later if you upgrade kernels of your linux distro(s).  It is easy enough to change the number of the default, remembering to start at 0 rather than 1.

---

### Post by Ramses de Norre on 2006-02-24
But I was wondering, if you install a newer kernel through apt-get upgrade, it is automaticaly added to your menu.lst. Will the default number change automaticaly too then?

---

### Post by ajgreeny on 2006-02-24
If I remember correctly the new updated version is added to the top of the list.  Its a log time since I did this so can't remember properly.

If you've got a floppy drive which you can boot from its worth putting a copy of grub on that and then if all goes wrong you will still have a working grub to use.  Do "sudo grub-install fd0".

If you get an error message about BIOS (can't remember the exact words) make sure your floppy is listed in /boot/grub/device.map with the line 
(fd0)	/dev/fd0
at the bottom.  Good luck.

PS  Hold on to the old kernel until you know the new one is working OK.

---

