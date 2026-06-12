---
title: "Inconsistent Bootup Freezing"
date: 2009-04-05
forum: General Help
---

### Post by Checkka on 2009-04-05
I'm having a strange issue in Ubuntu 8.10 where the laptop freezes during the bootup process.  Doing an CRTL+ALT+F1 reveals that this occurs just after "kinit: No resume image, doing normal boot...".

This doesn't always occur, but its been occuring more and more often now.  And its reached the point where it always occurs.

---

### Post by spiderbatdad on 2009-04-05
that message means you are not resuming a suspended session...in other words a normal boot. Try to read through dmesg
```
dmesg > ~/Desktop/dmesg.txt
```look for suggestions like "try using acpi=off," or other boot options to apply to the way ubuntu boots on your system: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Checkka on 2009-04-05
Doesn't that only show my successful bootup?  I can't get into terminal on an unsuccessful bootup.

---

### Post by spiderbatdad on 2009-04-05
You can try to apply the boot option on a one-time basis from the grub options screen by pressing e when your ubuntu os is offered. When you see the line starting with the word kernel, move to that line with the arrow key and press e again. Then go to the end of that line and delete quiet splash, type in acpi=off 
Hit enter and press b to boot. If that doesnt work, try again with acpi=force

---

### Post by Zwack on 2009-04-11
First thing to try is edit the line in grub to read nosplash instead of splash.  That will give you the text mode start up.  Does your laptop boot when plugged into a power supply and not when running on battery (I found this with mine, on battery I had to hold down a key to get it to boot)... If this is the case try acpi=noirq on that grub kernel line.

Z.

---

