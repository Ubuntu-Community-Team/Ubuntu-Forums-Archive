---
title: "Kernel problem on AMD-Ati Mother Board (HP Pavilion dv4-1108ax)"
date: 2009-06-05
forum: General Help
---

### Post by XAZero on 2009-06-05
Hi all

First, don’t hate me because I already posted this before, but nobody was reading my post and I realized that the thread’s name wasn’t correct and also the prefix was wrong (English is not my first language), and I didn’t see a way to change both


This is what’s happening with my brand new HP Pavilion dv5-1108ax (Specifications provided at the end of the document), I'm not gonna list all the problems that I'm having with _9.04_ in this laptop (because are so many), but at least I'm gonna write a bit about what I tink is a bug in the kernel (i'm not sure), If someone knows something about how to get it working please post. well here it is:

Distro used: Kubuntu 9.04, Using livecd to install.
(I also tryed ubuntu having the same result)

At the boot time the following message is displayed, but it continues loading.

*[    X.XXXXXX] atax: softreset failed (device not redy)*

Immediately after that the following FATAL !!?? is displayed, but it continues booting anyway 

*modprobe: FATAL: Could not load /lib/modules/2.6.28-11-generic/modules.dep: No such file or directory*

Then the live cd starts and the system installs without problems (Install in the full HD was selected), but when the pc is restarting the following error is displayed few times, but the system continue restarting.

*[xxxx.xxxxxx]end_request: IO error,  dev sr0, sector xxxxxxx*

And to finish, when the computer restarts Ubuntu can’t load because of the following GRUB error:

[I]GRUB Loading stage1.5.


GRUB loading, please wait…
Error 21[/I]


Comments
-The HD has no problems (I reinstalled MS Windows without problems)
-I burned few times the iso file having the same result so, that’s not the problem
-If I install to an external hard disk, there is no such GRUB error, but softresest failed and modprobe fatal. And as an extra: if I unplug and re-plug the external HD when loading, the system boots.
-Googling, I fund that the softreset problem is too common and the common factor is that the computers affected  are AMD & Ati based. 
-Excuse my english please.


Computer specs (by cpuz 1.51)

Pavilion dv5-1108ax (AMD-ATI)

**Processor(s)**   
Number of cores 2 per processor 
Number of threads 2 per processor 
Name AMD Turion X2 RM-70 
Specification AMD Turion(tm) X2 Dual-Core Mobile RM-70 
Package Socket S1 (638 ) 
Family/Model/Stepping F.3.1 
Extended Family/Model 11.3 
Brand ID 6 
Core Stepping LG-B1 
Technology 65 nm 
Core Speed 503.2 MHz 
Multiplier x Bus speed 2.5 x 201.3 MHz 
HT Link speed 1811.6 MHz 
Stock frequency 2000 MHz 
Instruction sets MMX (+), 3DNow! (+), SSE, SSE2, SSE3, x86-64 
L1 Data cache (per processor) 2 x 64 KBytes, 2-way set associative, 64-byte line size 
L1 Instruction cache (per processor) 2 x 64 KBytes, 2-way set associative, 64-byte line size 
L2 cache (per processor) 2 x 512 KBytes, 16-way set associative, 64-byte line size 
 
**Chipset & Memory **  
Northbridge AMD 780G rev. 00 
Southbridge ATI SB700 rev. 00 
Graphic Interface PCI-Express 
PCI-E Link Width x16 
PCI-E Max Link Width x16 
Memory Type DDR2 
Memory Size 2048 MBytes 
Memory Frequency 402.6 MHz (1:2) 
[B]
System [/B]  
System Manufacturer Hewlett-Packard 
System Name HP Pavilion dv5 Notebook PC 
System S/N CNF84823YW 
Mainboard Vendor Quanta 
Mainboard Model 3600 
BIOS Vendor Hewlett-Packard 
BIOS Version F.33 
BIOS Date 04/21/2009

---

