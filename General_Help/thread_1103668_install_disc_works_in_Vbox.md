---
title: "install disc works in Vbox?"
date: 2009-03-22
forum: General Help
---

### Post by nick937 on 2009-03-22
I have a windows xp media center edition install disc(1&2) , and I can install it perfectly in virualbox.. but when I try to install it on my system it doesnt go to the setup screen..


it says "press any key to boot from cd"

so i press a key.

and then it says something like "checking system requirements"

and then a black screen .


My laptop came with windows vista (1 yr old laptop). so I assume my system requirements are fine...

I have let the screen sit there for like 15 minutes (black screen), so i assume I have let it wait long enough..


Whats the problem!?:(

---

### Post by nick937 on 2009-03-22
something just came to me... i burnt the iso via the "CD/DVD Creator" in ubuntu... is there some setting I must have missed to have it burnt correctly? because I just use the straight iso in Vbox.. Ill try the disc on vbox to see if it works..

---

### Post by nick937 on 2009-03-22
nope.. the disc works in vbox too..

---

### Post by DGortze380 on 2009-03-22
VirtualBox works on a hardware abstraction layer with virtual hardware. Just because the disc / OS works in VirtualBox doesn't mean it will work on your machine.

Sounds to me like you're having driver issues.

What are your system specs.

---

### Post by nick937 on 2009-03-22
```

SYSTEM INFORMATION
	Running Ubuntu Linux, the Ubuntu 8.10 (intrepid) release.
	GNOME: 2.24.1 (Ubuntu 2008-10-24)
	Kernel version: 2.6.27-11-generic (#1 SMP Thu Jan 29 19:24:39 UTC 2009)
	GCC: 4.3.2 (i486-linux-gnu)
	Xorg: unknown (24 October 2008  08:00:16AM) (24 October 2008  08:00:16AM)
	Hostname: Fish-Tank
	Uptime: 0 days 0 h 6 min

CPU INFORMATION
	GenuineIntel, Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz
	Number of CPUs: 2
	CPU clock currently at 800.000 MHz with 4096 KB cache
	Numbering: family(6) model(15) stepping(10)
	Bogomips: 3990.41
	Flags: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm ida

MEMORY INFORMATION
	Total memory: 2015 MB
	Total swap: 4095 MB

STORAGE INFORMATION
	SCSI device -  scsi0
		Vendor:  ATA      
		Model:  WDC WD1600BEVS-6 
	SCSI device -  scsi3
		Vendor:  MATSHITA 
		Model:  DVD-RAM UJ-851S  

HARDWARE INFORMATION
MOTHERBOARD
	Host bridge
		Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
		Subsystem: Hewlett-Packard Company Device 30cc
	PCI bridge(s)
		Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
		Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
		Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
		Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01)
		Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
		Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
		Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
		Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01)
	USB controller(s)
		Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
		Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
		Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
		Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
		Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
		Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
		Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
		Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
		Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
		Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
		Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
		Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
		Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
		Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
	ISA bridge
		Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
		Subsystem: Hewlett-Packard Company Device 30cc
	IDE interface
		Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
		Subsystem: Hewlett-Packard Company Device 30cc

GRAPHIC CARD
	VGA controller
		Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
		Subsystem: Hewlett-Packard Company Device 30cc

SOUND CARD
	Multimedia controller
		Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
		Subsystem: Hewlett-Packard Company Device 30cc

NETWORK
	Network controller
		Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
		Subsystem: Hewlett-Packard Company Device 135b
	Ethernet controller
		Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
		Subsystem: Hewlett-Packard Company Device 30cc
```

---

### Post by nick937 on 2009-03-22
So i can install vista, but not xp? because something I have is not supported by the xp disc?

---

### Post by overdrank on 2009-03-22
> **nick937 said:**
> I have a windows xp media center edition install disc(1&2) , 

> **nick937 said:**
> something just came to me... i burnt the iso via the "CD/DVD Creator" in ubuntu... 

I am confused. If you have the disc why did you need to burn them?

---

### Post by nick937 on 2009-03-22
> **overdrank said:**
> I am confused. If you have the disc why did you need to burn them?

its not an official disc;)

i go the .iso 's and burnt them to discs.

all because my tvtuner isnt supported by linux yet (analog anway)


and I really don't want to install vista.. takes up way too much room

---

### Post by overdrank on 2009-03-22
> **nick937 said:**
> its not an official disc;)

i go the .iso 's and burnt them to discs.



The forums do not support this. Thread closed.

---

