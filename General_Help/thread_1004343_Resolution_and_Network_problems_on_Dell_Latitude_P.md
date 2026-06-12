---
title: "Resolution and Network problems on Dell Latitude PP01L"
date: 2008-12-07
forum: General Help
---

### Post by the8thstar on 2008-12-07
Hello there,

I have installed #! CrunchBang Linux (Ubuntu 8.10 + OpenBox basically) on an old Dell Latitude PP01L. 

Everything is running well considering the age of the hardware for the most part. However, I still need to solve two problems:

1. The network (ethernet port) doesn't respond. The "Auto eth0" option is greyed out, which leads to two clues: either the network card is fried or the hardware isn't detected. Any ideas on how to diagnose this?

2. The graphics card used to display a 1024x768 resolution in Windows XP, but it is now limited to 800x600. Again, do you guys have any idea on how to solve this problem?

Thanks in advance for your help!

---

### Post by SPr on 2008-12-07
What's the result of lspci? Does it show the hardware? Does the router show an ethernet connection? Have you tried altering the screen resolution?

---

### Post by the8thstar on 2008-12-07
\\

> the8thstar@the8thstar-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:03.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
00:03.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
00:10.0 Ethernet controller: 3Com Corporation 3c556 Hurricane CardBus [Cyclone] (rev 10) 
00:10.1 Communication controller: 3Com Corporation Mini PCI 56k Winmodem (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02)

---

### Post by SPr on 2008-12-07
The hardware shows up. Does sudo lshw -C network give any clues? Can you ping the router? Have you checked that the router works?

Have you searched for information about problems with this computer and Ubuntu? Do you know which kernel module 3Com Corporation 3c556 Hurricane CardBus [Cyclone] (rev 10) needs? Does lsmod|more show that it's loaded?

[http://manpages.ubuntu.com/manpages/hardy/man4/xl.html](http://manpages.ubuntu.com/manpages/hardy/man4/xl.html) I've done some searching for you.

---

