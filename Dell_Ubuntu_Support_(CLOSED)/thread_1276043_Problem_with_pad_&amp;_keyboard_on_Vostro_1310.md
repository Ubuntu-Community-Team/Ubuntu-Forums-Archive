---
title: "Problem with pad &amp; keyboard on Vostro 1310"
date: 2009-09-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by diotima on 2009-09-26
I have Ubuntu 9.04 on my laptop (Dell Vostro 1310), I keep it updated, but for some time I have the same problem: my keyboard and pad do not work when I start the system. The mouse works. I have to restart the whole system and after restarting it pad and keyboard are back with their normal functions.

---

### Post by urugTON on 2009-09-26
I have a Vostro 1510 running 9.04.  I used to have problems similar to yours.  I do not remember where I found the work around, but I needed to pass a parameter to the kernel at boot time.

My menu.lst entry now reads:

kernel /boot/vmlinuz-2.6.28-15-generic root=UUID=d36a5a02-1f19-4252-a8cd-6d03ea7b70da ro quiet splash i8042.reset

In this discussion, the important part is the "i8042.reset".  You can search the Dell forums for the string to find out more.  I had forgotten that I'd added that parameter until I installed a new kernel recently and the keyboard problem showed up again.

You can try the string out by rebooting, highlighting the entry at the grub menu and pressing "e".  You'll be presented with a couple of lines, one of which will start with "kernel".  Press "e" again and add the string at the end of the line.  Then enter "b" to boot.  All of the options are shown at the bottom of the screen.  These changes are not permanent.  You'll have to edit /boot/grub/menu.lst for a lasting solution.

---

### Post by diotima on 2009-09-28
I've made the changes and it works :) Thank you very much!

---

### Post by sunwatt on 2009-10-03
I am having this problem, mouse works but not keyboard. Dell Mini 9 Linux  Mint 7 OS.

With external USB hub and external mouse/keyboard I didnt know there was a problem till I took this mobile.

Boots up, but cant type in name/password. 

Same thing at home if usb hub is unplugged.

So I put a Ubuntu 9.04 live DVD in my external Dell drive and with no usb hub connected the onboard keyboard and mouse are working fine.

BTW, I tried booting up with my Mint 7 CD and my Mint 7 memory stick, and had keyboard problems.

I can bootup to BIOS. 

I really like Mint 7 on my Mini 9. I would love to be able to fix the problem, and stay with Mint.

But I have the Ubuntu 9.04 DVD in my hands and getting itchy.

Will the fix in this thread work on a Mini 9?

If so, can someone walk me thru how and where to enter this fix? I'm a tabpole, only been with Linux 4 months.

thanks

Jim

---

