---
title: "cannot boot after installation"
date: 2008-12-31
forum: General Help
---

### Post by fajarhp on 2008-12-31
please help me!
on live cd I have problem with booting, but I can solve this. I try to type command

boot: live generic.all_generic_ide=1

it can boot on live cd succesful.
but when after i have tried to install on hardisk. ubuntu failed to boot.on monitor only showed freezing splash screen.


note: my ubuntu is ubuntu 7.10 gutsy gibbon.
mb asus p5q3 deluxe wifi
sata western digital wd5000 series.
2x2 gb ddr3 1066hz corsair
cpu intel q9400
vga ati radeon hd 4670

---

### Post by SPr on 2008-12-31
Hit Alt+Ctrl+f1 through to f12 when the computer is booting/freezes and you should be able able to see where the boot up process is sticking.

If that doesn't work turn off the splash screen by hitting "e" in the grub menu. Highlight the option you want to boot and edit it to add the option "nosplash" at the end of the line. (Instructions for editing lines are printed on screen.) Press "b" to boot. (I think those instructions are correct - read [http://www.gnu.org/software/grub/manual/html_node/Interface.html#Interface](http://www.gnu.org/software/grub/manual/html_node/Interface.html#Interface) to be sure.)

Edit (just rebooted and checked this :) ) :
When computer first starts hit "e" in the Grub menu. Use the arrow keys to highlight the kernel you want to boot and hit "e" again. Add the word "nosplash" to the end of the line and hit "enter". Then hit "b" to boot that kernel with the "nosplash" entry.

---

### Post by caljohnsmith on 2008-12-31
How about on start up when you get the Grub menu, select the Ubuntu entry you want to boot, press "e" to edit it, select the "kernel" line, press "e" to edit it, and at the end of the line add:
```
all_generic_ide
```
Press enter to save the change, and finally "b" to boot. Let me know if that works or what exactly happens.

---

### Post by Randomperson_1000 on 2009-05-12
Are you using 7.10 live cd? From memory im pretty sure that you wont get a gui with the ati 4670 if u use 7.10 use 8.10 or 9.04 if u want a gui

---

