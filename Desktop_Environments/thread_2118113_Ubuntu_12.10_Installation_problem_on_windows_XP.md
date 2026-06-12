---
title: "Ubuntu 12.10 Installation problem on windows XP"
date: 2013-02-20
forum: Desktop Environments
---

### Post by manojanand on 2013-02-20
i am trying to install Ubuntu 12.10 on Windows XP using wubi.exe. On startup i am getting two options
1. windows xp
2. ubuntu

when i choose windows , it starts in normal way. But when i choose ubuntu , it asks for user name and password. After entering password , system accepts it. But only ubuntu coloured screen comes but no icons. i also get some message like "application compaz" failed. Not sure about this message.

Here i am giving my system configuration :
Model: PI845GLM
Pentium 4 2267MHz (L1 cache: 8.00 Kb, L2 cache: 512.0 Kb) Ext.clock: 133 MHz
AMIBIOS 070010 04/02/01 (07-Sep-2004)
768 Mb (784 880 Kb) DIMM1: 512 Mb(DIMM,SDRAM) DIMM2: 256 Mb(DIMM,SDRAM)

Hard disks:
76.3 Gb (36.6 Gb free = 47.9%) (22.2 Gb free on C: drive)
primary disk: SAMSUNG SP0802N size: 76.3 Gb sernum: S00JJ30XB94910
C:(Ntfs) 41.0 Gb (22.2 Gb free = 54.1%)
D:(Ntfs) 35.4 Gb (14.4 Gb free = 40.8%)

Video card: Intel(R) 82845G/GL/GE/PE/GV Graphics Controller (64.0 Mb): 1024 x 768 - True Color (32 bit)
Sound card: C-Media AC97 Audio Device
Network cards: (1) SiS 900 PCI Fast Ethernet Adapter
(2) WAN (PPP/SLIP) Interface
(3) WAN (PPP/SLIP) Interface
(4) SiS 900 PCI Fast Ethernet Adapter
(5) WAN Miniport (IP)

Adapter: (1) Ethernet
(2) PPP
(3) PPP
(4)
(5)

---

### Post by bcbc on 2013-02-20
Maybe your system is a bit light for the default Unity in 12.10?

You could try lubuntu or xubuntu (but xubuntu isn't available with Wubi since release 12.10)

---

### Post by SMOKE14 on 2013-02-20
Unity is a bit resource heavy. You might try to uninstall it from the control panel in Wubi and try using Wubi to install Lubuntu under Desktop Environment. Better yet, try using Puppy Linux.

---

### Post by manojanand on 2013-02-21
Some one suggested me 
> Try the boot option:

nomodeset

May help

what does that mean and how can i implement it. Will it be of any help?

---

### Post by bcbc on 2013-02-21
Yes it might help, but nomodeset won't give you the best graphics display. And normally people that use it will install a closed source graphics driver to fix the problem, but I don't think that applies in your case.

So you'll have an inferior display permanently. 

Of course, you might be able to install a Gnome fallback or some other less intensive display manager. Check out the options here: [http://askubuntu.com/questions/65083/what-different-desktop-environments-and-shells-are-available]("http://askubuntu.com/q/65083/14916")

---

