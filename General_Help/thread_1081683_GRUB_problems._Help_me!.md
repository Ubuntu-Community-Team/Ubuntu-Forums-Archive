---
title: "GRUB problems. Help me!"
date: 2009-02-26
forum: General Help
---

### Post by t3chnique on 2009-02-26
Hi! I recently upgraded from Ubuntu 8.04 to Ubuntu 8.10. Here's the problems that I have with the GRUB menu

GRUB menu would not show up when booting up any more. I know that Ubuntu hides GRUB menu by default so I edited the GRUB menu file by putting a '#' in front of the 'hiddenmenu'. It still would not show up at start up :mad:

Oh, another thing, i also tried to hit 'escape' at start up but that didn't work either. It just boot up to UBUNTU automatically. Please  help!!! I need to access Windows XP.

Thank you in advance

---

### Post by fooman on 2009-02-26
you could give startup-manager a try.

it has options to show/hide the bootloader screen and the time that it will show (you may just need to increase that a few seconds)....in a terminal:

```
sudo apt-get install startupmanager
```after it installs,  find it in system > adminustration > startup-manager

the options you want are under the boot options tab.  there are many other useful items in there as well.

hope that helps.

---

### Post by mb_webguy on 2009-02-26
What's your timeout value?

---

### Post by t3chnique on 2009-02-26
@mb_webguy

My time out value is 10 seconds

---

### Post by t3chnique on 2009-02-26
the startup manager let me boot back into Windows XP. But the problem isn't solved because GRUB menu doesn't show up at start up so i have no way to choose UBUNTU as my start up OS.

---

### Post by fooman on 2009-02-26
you can use the live cd to edit the menu.lst file.

boot the live cd,  open a terminal and run this command:

```
sudo fdisk -l
```find which partition your ubuntu is installed to.  it will look like "sdaX" ...the "X" representing whichever number corresponds to the ubuntu partition (like sda1 or sda2, etc..)

then mount that partition with:

```
sudo mount /dev/sdaX /mnt
``` ...change the "X" to the correct number per above.



next edit the file with this command:

```
gksudo gedit /mnt/boot/grub/menu.lst
```look for the "default num" section in the file and change it to "default  0" (no quotes of course).  zero will represent the first entry in the list,  which should be your ubuntu partition.

while your in there,  double check that the timeout line *does not* have a # in front of it and that the hiddenmenu *does* have one.

hope that helps.

---

### Post by t3chnique on 2009-02-27
Thank you fooman! I will try it

---

### Post by sahabcse on 2009-02-27
Hi

For fixing the grub follow below url


==================================
[http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html](http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html)
[http://sahabm.blogspot.com/2009/01/grub-fix-windows.html](http://sahabm.blogspot.com/2009/01/grub-fix-windows.html)
=================================

Regards,
Sahab

---

