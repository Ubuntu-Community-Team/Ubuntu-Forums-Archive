---
title: "Xubuntu 8.10 boot hangs"
date: 2009-02-12
forum: General Help
---

### Post by diamondjim08 on 2009-02-12
After installing and using Xubuntu 8.10 for about a month, I noticed the boot process hangs and freezes in the very beginning of the operation.  The Xubuntu progress bar swings back and forth then hangs about 10% into the progress when the bar advances from left to right.  No key strokes change anything in the boot process.  I am forced to turn off the machine by holding down the power button for about 3 secs until the machine powers off.

In recovery menu, "resume normal boot" will boot he machine perfectly every time and it then runs normally.  Returning the machine to automatically boot itself results in a freezing of the boot process described above.

How do I fix this?  Or can it be fixed?

Thanks,
<> Jim

---

### Post by plucky on 2009-02-12
> How do I fix this? Or can it be fixed?



You need to find out what it is doing when it hangs.
To do so you need to make the boot screen print out what it is doing,so open a terminal and ```
sudo nano /boot/grub/menu.lst
``` and edit the kernel line to remove the word **quiet** so it looks like ```
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=125bc66f-c84c-41b8-9d91-3ca866cb4800 ro splash
``` or similar.


Then when you reboot the splash screen will tell you what it is doing.If that still doesn't show you what is happening,then edit the same file and remove the word **splash** as well.The system will then boot without the splash screen and show the full text boot.

You should then see where it is hanging.


Good Luck

---

