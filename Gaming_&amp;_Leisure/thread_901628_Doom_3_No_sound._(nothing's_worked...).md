---
title: "Doom 3 No sound. (nothing's worked...)"
date: 2008-08-26
forum: Gaming &amp; Leisure
---

### Post by KnightXsjado on 2008-08-26
I know there are a ton of people having sound issues with native linux doom 3, but I have yet to come across someone with the same problem as me...
I installed Doom 3 via the binary and copied the needed pak files in order to play, now like everyone else my game starts up and runs perfectly fine, minus there is no sound at all. no distorted sound nothing. I have tried running doom3 + pluss oss and what not and all the other "solutions" and still no sound. I'm not getting any errors at game start up regarding sound... or anything for that matter. I've tried alsa everything... nothing gives... I'm running an asus motherboard p5k-e wifi edition and I am using the onboard ADI AD1988B audio chipset.
can anyone help me out?

---

### Post by Ferrat on 2008-08-26
Have you changed sound device in the game to OSS? should change that in options if I remember correctly

Should be under Options >> System (inside the game)

---

### Post by KnightXsjado on 2008-08-26
yes I have tried all three options in that menu even after starting 
doom3 +set s_driver oss

:confused:

I'm totally at a dead end :(
im running 64bit ubuntu hardy heron 8.04

---

### Post by Crafty Kisses on 2008-08-26
Post the results of > lspci

---

### Post by KnightXsjado on 2008-08-26
ac1dburn@Ac1dBurn-Cr4shOver1d3:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
04:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)

there's the results you asked for.


I installed urban terror and seem to be having the same problem with it too... no sound

---

### Post by linuxguymarshall on 2008-08-26
Were you sure to copy all the files. Check my guide here : [http://ubuntuforums.org/showthread.php?t=894519](http://ubuntuforums.org/showthread.php?t=894519)

This will tell you all the files you need. If you missed one of them it could be causing this problem.

---

### Post by KnightXsjado on 2008-08-26
Well I went through everything one more time and right before I restarted I disabled some system sounds that I had ticked on prior installing doom 3, I have no idea if that had Anything to do with it but I highly doubt it, but for some reason when I restarted this time around the sounds started working. :]
I hear creepy noises now cool.

---

