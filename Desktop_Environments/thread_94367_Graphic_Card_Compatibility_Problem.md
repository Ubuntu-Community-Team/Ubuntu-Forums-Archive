---
title: "Graphic Card Compatibility Problem"
date: 2005-11-23
forum: Desktop Environments
---

### Post by gappy on 2005-11-23
After a bit of tweaking, my homemade desktop works well under Kubuntu 5.10, with one glaring exception. When I use Konqueror, after a while the KDE gets "out of sync": the windows are painted as a texture of random points, mostly black. Interestingly, MEPIS does not exhibit this problem, and has better out-of-the-box hardware compatibility (with the exeption of the sound subsystem). 

My desktop runs on an Athlon 3500+, and an ASUS 6600 TD. The card is not defective: it performs flawlessly under Windoze.

Any advice is greatly appreciated.

-gappy:confused:

---

### Post by 23meg on 2005-11-23
Does this happen only and only when you start Konqueror? Check your system logs for any possible errors before it happens.

---

### Post by gappy on 2005-11-23
[QUOTE=23meg]Does this happen only and only when you start Konqueror? Check your system logs for any possible errors before it happens.[/QUOTE]

Actually, it does happen with Firefox as well, but less often. Which logs should I check?

---

### Post by 23meg on 2005-11-23
/var/log/syslog
/var/log/auth.log
/var/log/kern.log
/var/log/messages
/var/log/Xorg.0.log

---

### Post by gappy on 2005-11-24
[QUOTE=23meg]/var/log/syslog
/var/log/auth.log
/var/log/kern.log
/var/log/messages
/var/log/Xorg.0.log[/QUOTE]

Thanks. Should I look for any special message? searching by "card" or nvidia" di not yiels special results; e.g., on /var/log/Xorg.0.log  I read:

[COLOR="YellowGreen"][FONT="Courier New"](II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,005e card 105b,0ca4 rev a3 class 05,80,00 hdr 00
(II) PCI: 00:01:0: chip 10de,0050 card 105b,0ca4 rev a3 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0052 card 105b,0ca4 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,005a card 105b,0ca4 rev a2 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,005b card 105b,0ca4 rev a3 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,0059 card 105b,0ca4 rev a2 class 04,01,00 hdr 00
(II) PCI: 00:06:0: chip 10de,0053 card 105b,0ca4 rev a2 class 01,01,8a hdr 00
(II) PCI: 00:07:0: chip 10de,0054 card 105b,0ca4 rev a3 class 01,01,85 hdr 00
(II) PCI: 00:08:0: chip 10de,0055 card 105b,0ca4 rev a3 class 01,01,85 hdr 00
(II) PCI: 00:09:0: chip 10de,005c card 0000,0000 rev a2 class 06,04,01 hdr 01
(II) PCI: 00:0a:0: chip 10de,0057 card 105b,0ca4 rev a3 class 06,80,00 hdr 00
(II) PCI: 00:0d:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10de,0141 card 1043,8199 rev a2 class 03,00,00 hdr 00
(II) PCI: 03:06:0: chip 104c,8023 card 0ca4,105b rev 00 class 0c,00,10 hdr 00
[/FONT][/COLOR]

on /var/log/kern.log I have the following interesting message

[COLOR="YellowGreen"][FONT="Courier New"]Nov 23 09:56:44 localhost kernel: [ 1082.353830] nvidia: module license 'NVIDIA' taints kernel.
[/FONT][/COLOR]

The card is mounted on a PCI Express port, and I had installed the nvidia drivers, as explained in the Ubuntu wiki. Should I then look for any message related to the CPI Express port? or ACPI? PIC-DMA?

---

### Post by gappy on 2005-11-30
I found a fix to the problem below. It is described at [ubuntuguide]("http://ubuntuguide.org/#installnvidiadriver"). Installing the nvidia package alone is not sufficient.

-gappy

---

