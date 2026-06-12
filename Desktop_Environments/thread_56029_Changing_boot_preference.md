---
title: "Changing boot preference"
date: 2005-08-11
forum: Desktop Environments
---

### Post by artmoe on 2005-08-11
I hope this is the right forum. I'm running H H 5.04 and using the GRUB loader. When I start the comp, Ubuntu is the default OS. I want Windows XP to be the default so I don't have to pick it everytime. I use Windows more than Ubuntu. At least for now.
How do I change GRUB to boot to Windows by default. Thanks.

---

### Post by yongyi on 2005-08-11
[http://www.ubuntuguide.org/#changedefaultosgrub](http://www.ubuntuguide.org/#changedefaultosgrub)

---

### Post by myha on 2005-08-11
Hi!

You need to change default os in grub...

Open grub config with your editor, location is   /boot/grub/menu.lst

Set your default os under Default nume section:
```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
default          *number* 
``` 
On the bottom you have list of all the boot options, and just select the number of winXP and write it down instead of *number* in above code.

---

### Post by artmoe on 2005-08-14
Thanks. I went to the mentioned link and that didn't do anything, so then opened up "gedit" and put in "4'' for the boot sequence and that did work. Thanks. 
By the way, this brings up another question pertaining to "Gedit", I notice that when I change or alter a Gedit document, it retains a backup copy in the file system, unlike Windows. Can you refer me to documentation that describes in detail using Gedit.
Thanks.

---

