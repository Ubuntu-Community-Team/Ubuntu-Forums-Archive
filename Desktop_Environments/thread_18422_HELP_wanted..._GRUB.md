---
title: "HELP wanted... GRUB"
date: 2005-03-06
forum: Desktop Environments
---

### Post by mirtux on 2005-03-06
Hi,
  i'm in big trouble... :-(  i've tried to add a splashscreen to GRUB editing the file menu.lst. The problem is that when i boot the machine i get a blanck screen! If i press enter the default kernel starts with screen problems but it stops at some point.

How is possible to gain access to a simple linux prompt to change again the menu.lst, for example using win XP?

Thanks,
MC

---

### Post by rosslaird on 2005-03-06
You could boot from cd (if you have one), mount your hard disk, and edit grub that way. I don't think you can do it from Windows (but I'm not sure).

Almost any Linux bootable cd will work: knoppix, debian, ubuntu, etc.

Ross

---

### Post by doitashimashite on 2005-03-06
During boot, in the Grub menu, you can also press the "e" key to edit the line, and after editing press "b" to continue booting.

---

### Post by mirtux on 2005-03-06
Hi,
  first of all thanks for help. I've used the Ubuntu live CD (...i'm using Debian unstable...) and modified the menu.lst after opening the root console.

Thanks for help,
MC

---

