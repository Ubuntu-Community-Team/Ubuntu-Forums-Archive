---
title: "Kernel Downgrade PLEASE HELP !!!!"
date: 2006-08-26
forum: Desktop Environments
---

### Post by JKoder on 2006-08-26
Hello 
I am using Xubuntu 6.06.1 and i need to downgrade my linux kernel to 2.6.15.23 . Currently i have 2.6.15.26 and sound and network are not working right.
From Synaptic->Force version is not working because that option is disabled .
Please help !!!!!!

Thank you

---

### Post by neko18 on 2006-08-26
From GRUB, boot to the older kernel, then go to Synaptic and try to remove the new one.

---

### Post by JKoder on 2006-08-26
I will try that but i dont think i have the old kernel because after installing Ubuntu 6.06.1 i only have the new one ... and from synaptik like i sayd does not work !

Any other hint PLEASE !!!!!

---

### Post by neko18 on 2006-08-26
By "remove the new one" I mean make sure linux-image-2.6.15-23-(architecture) is installed then remove linux-image-2.6.15-26-(architecture)

---

### Post by JKoder on 2006-08-26
Ok but how to install 2.6.15.23(arhitecture) this is my problem :(

---

### Post by neko18 on 2006-08-26
With Synaptic.

---

### Post by JKoder on 2006-08-26
Synaptic ->Force version is disabled and i cannot see the kernel i want :(

---

### Post by neko18 on 2006-08-26
Are you on an i386 architecture?

---

### Post by JKoder on 2006-08-29
Hy.. sorry for delay
Yes i am on 386 arhitecture i thing Fujitsu Siemens Amilo L7300 Laptop

---

### Post by az on 2006-08-29
I really doubt that the kernel version is causing your problems.

Do a search in synaptic for "linux-image".  What versions do you have installed on your system?

Each kernel (linux-image-xxxx) version is a different package, which is why you can have more than one installed at the same time and also why you cannot force any version - they are not the same package.

If you do not see the grub menu (to pick which kernel you boot) when you start your computer, look to see for the promtpt to hit escape to reveal the grub menu.  There is a three second delay by default for you to do this.  Scroll down and boot the older kernel.

---

### Post by JKoder on 2006-08-29
Well i think my problems are with linux kernel because:
By default Ubuntu 6.06 uses kernel 2.6.15.23. After on update, it installs linux kernel 2.6.15.26. Here is the problem
I tryed to update everithing but linux kernel and my system was OK
After updateting the Linux kernel .... bad thing happen :(

And nou i whant to use Xubuntu 6.06.1 BUT it has that new kernle and those problems are there to

---

### Post by KingArthur10 on 2006-08-29
You should have the option in the grub boot menu to boot from the older kernal.  Might have to press delete or something like that (it says what to press) when grub stays up for a few seconds on boot.  Then you should have the list of kernals to choose from.  Boot into your older kernal and see if your problems are corrected.  If they are, you can just remove the new kernal from your grub boot path by typing in the terminal "sudo gedit /boot/grub/menu.lst".  Then just comment out the new kernal with # signs and you'll always boot into the older kernal.

---

