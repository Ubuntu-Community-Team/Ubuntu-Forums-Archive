---
title: "Ubunto live wont work"
date: 2006-01-13
forum: Desktop Environments
---

### Post by mixxoys on 2006-01-13
i just got ubuntu shipped and when i put in the cd and rebooted it showed the logo and when i press enter it will go and show my compaq logo and go right back to the logo and when ever i press enter it will do the same again, and again, and again.

---

### Post by L Campbell on 2006-01-13
[QUOTE=mixxoys]i just got ubuntu shipped and when i put in the cd and rebooted it showed the logo and when i press enter it will go and show my compaq logo and go right back to the logo and when ever i press enter it will do the same again, and again, and again.[/QUOTE]

Did you try it with your BIOS set to boot from the CD?

---

### Post by mixxoys on 2006-01-13
yes, yes i did.. it isnt doing a loop when it trys to boot the disk it reboots. i noticed that the last thing it said befor rebooting is "Uncompressing, Ok , booting kernel", or something along the line of that

---

### Post by bbmw on 2006-01-14
I am having the same problem after spending 24+ hours downloading 5.10 live over dial-up !!!
I am a Linux/unix noob

My computer is :
Compaq Presario S6020WM
 main board is MS-6577 (Neon)
 Celeron 2.6 Mhz
 256Mb Ram
 Intel 845GV chipset
 NVIDA GeForce FX 5500 OC PCI

Any help you can give me would be great

---

### Post by bbmw on 2006-01-14
I have had some sucess geting 5.10 to boot from the live CD.

I used:
live acpi=off nolapic noapm    That I found somewhere on this forum

It started to boot, Then I had to answer some hardware questions etc. Some more stuff scrolled by then it stopped at "Starting hotplug subsystem".
I will research this some more.

---

### Post by mixxoys on 2006-01-14
[QUOTE=bbmw]I have had some sucess geting 5.10 to boot from the live CD.

I used:
live acpi=off nolapic noapm    That I found somewhere on this forum

It started to boot, Then I had to answer some hardware questions etc. Some more stuff scrolled by then it stopped at "Starting hotplug subsystem".
I will research this some more.[/QUOTE]

Hey, thanks it running right now on that live acpi=off nolapic noapm , thank you alot :D

---

### Post by bbmw on 2006-01-14
[QUOTE=mixxoys]Hey, thanks it running right now on that live acpi=off nolapic noapm , thank you alot :D[/QUOTE]
Im glad to hear that its working for you
Its still stopping at "Starting hotplug subsystem" (I think this is the usb port)
I have tried a lot of options and combinations of options with no sucess

---

### Post by mixxoys on 2006-01-14
Are you using a wireless network card?

---

### Post by bbmw on 2006-01-17
No im not using a wirless card but I have found that by disabling my pci Nvida
graphics card in bios that it works with just the acpi=off option but then I have to change the bios back to use windows.
I have seen some forums about this but I need to reread them.
I have also read somewhere that you should try the options singly then in diffrent combinations to find the smallest number that will work, like I said before I am now only using acpi=off but I think I will need another to use my graphics card

---

