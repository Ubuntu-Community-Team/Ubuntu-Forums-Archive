---
title: "Can't install Ubuntu 11.10 on HP Pavilion HPE h8xt"
date: 2011-10-30
forum: Desktop Environments
---

### Post by JPRZ on 2011-10-30
[LEFT]- Trying to install Ubuntu11.10 Desktop 32 bit on a HP Pavilion HPE h8xt desktop PC. I boot from the CD, the install looks like it it starting, but then basically nothing. I first see a purple screen with 3 icons along the bottom. A PC or drive icon maybe then a little rectangle, then a man inside a circle.
[COLOR=#000000]- Then the screen changes and shows "Ubuntu" with 5 dots underneath it. The dots are changing color from white to red, going back and forth, like a progress bar. [/COLOR]
[COLOR=#000000]- It does that for about a minute, then the screen changes to some text in the upper left, for about 3 seconds with info about mounting a network..., then changes to an all black screen with just a mouse pointer.[/COLOR]
[COLOR=#000000]- And it stays like that. No messages, no errors, nothing. I let it sit there, maybe 10 minutes, and nothing. No change. Just the mouse pointer. I eventually power cycle the PC and have tried the install 3 times, and each time it does the same thing.[/COLOR][/LEFT]
 
[LEFT][COLOR=#000000]**Anyone get Ubuntu to install on these PCs?**[/COLOR][/LEFT]
 
[LEFT][COLOR=#000000]Model: h8-1160t[/COLOR]
UEFI (BIOS)
[COLOR=#000000]Intel Core i7 2600[/COLOR]
[COLOR=#000000]8.00 GB Dual-Channel DDR3[/COLOR]
[COLOR=#000000]PEGATRON CORPORATION - Motherboard - Chipset - H67[/COLOR]
[COLOR=#000000]AMD Radeon HD 6570 graphics card[/COLOR]
[COLOR=#000000]977GB Seagate 7200RPM HDD[/COLOR]
[COLOR=#000000]hp DVD A DH16ABSH[/COLOR]
[COLOR=#000000]Onboard Audio (AMD High Definition Audio Device)[/COLOR]
[COLOR=#000000]Onboard Realtek PCIe GBE Family Controller (NIC)[/COLOR]
[COLOR=#000000]802.11n Wireless LAN Card[/COLOR][/LEFT]

---

### Post by spookyhat on 2011-11-06
I have a similar HP desktop and that same problem. I managed to boot into a non accelerated desktop after many, many, attempts at passing the nomodeset parameter with 11.04, and then install the proprietary ATI/AMD video driver. Sadly, I can't seem to get that to work with 11.10. 

I'm going to try using the alternate install disk and installing fglrx from the command line, I tried it yesterday, but due to my noobishness I had trouble connecting to my network sans gui.

---

### Post by shakabra on 2011-11-06
Your problem may be the UEFI BIOS. If you can disable this ( I can on my laptop) you should and then try to install again. Also an alternate install image wouldn't hurt.

---

### Post by typhoon_tip on 2011-11-06
I don't know very well that Desktop, and probably my suggestion will not work, but I had a similar problem on Desktops in our offices (install screen indefinitely hangs). I entered the BIOS and disabled floppy drive detect (it was enabled, but of course the system did not have any floppy drive).

If you can see the "dots" screen, usually means that the video driver is already working properly.

---

