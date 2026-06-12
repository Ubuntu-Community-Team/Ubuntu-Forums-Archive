---
title: "Ubuntu Hang / Freeze no reason"
date: 2005-12-05
forum: Desktop Environments
---

### Post by sancho21 on 2005-12-05
Hi All. 

I think one of you have experienced with this problem. It seems that my computer doesn't match with Ubuntu (I guess) :( Why I said so, because my Ubuntu often hangs without specific reason. These are the behaviour of my computer when it hangs (freez):

1. The hardisk sometimes busy (busy red light indicator on) but sometimes not
2. It hangs right after I played an mp3 song on windows partition with JuK or XMMS. -> this is the most often happens.
3. It hangs after I open aplications at the same time. Atau membuka aplikasi secara bersamaan. 
4. After it hangs, it becomes responsiveless (freeze as I said). I even can't move to terminal (Ctrl+Alt+F1-4) nor gnome terminal can't respond to Ctrl+C 

Sometimes I feel as if my screen just like wallpaper (to describe the freeze without any indication like busy light). Is there any relation with noapic and nolapic (even I've done that to my boot param)? Or kernel?

It happens in XFce4, Gnome and, if I'm not mistaken, KDE. I happens in Ubuntu Hoary permanent (write to disk) and Ubuntu Breezy Live (sent package). This freeze behaviour not happen in Knoppix 3.3 (about more than 1 year ago) 

Is there anyone know how to solve this problem. I'm really desperated and afraid while I'm writing my box suddenly hangs or when updating critical package.

Thanks 

This the description of my computer. Sorry if it is too long.

Motherboard:
CPU Type		Intel Pentium IIIE, 667 MHz (5 x 133)
Motherboard Name	PCChips M756LMR
Motherboard Chipset	SiS 630
System Memory		240 MB  (SDRAM)
BIOS Type		AMI (05/10/01)

Multimedia:
Audio Adapter		C-Media CMI8738/C3DX Audio Device

Storage:
IDE Controller		SiS PCI IDE Controller
Floppy Drive		Floppy disk drive
Disk Drive              ST380011A  (80 GB, 7200 RPM, Ultra-ATA/100)
Disk Drive		USB Mass Sorage USB Device  (54 MB, USB)
Optical Drive		LITE-ON CD-RW SOHR-5238S
Optical Drive		SAMSUNG CD-ROM SC-152C  (52x CD-ROM)
SMART Hard Disks Status	OK

Network:
Network Adapter		D-Link DFE-530TX PCI Fast Ethernet Adapter (rev.C)
Modem			HSP56 MicroModem

[ BIOS ]

BIOS Properties:
Vendor			American Megatrends Inc.
Version			062710
Release Date		07/15/97
Size			256 KB
Boot Devices		Floppy Disk, Hard Disk, CD-ROM, ATAPI ZIP, LS-120
Capabilities		Flash BIOS, Shadow BIOS, Selectable Boot, EDD
Supported Standards	DMI, APM, ACPI, ESCD, PnP
Expansion Capabilities	ISA, PCI, AGP, USB

[ System ]

System Properties:
Manufacturer		PCCHIPS
Product			M756LMRT
Version			123456890
Wake-Up Type		Modem Ring

[ Motherboard ]

Motherboard Properties:
Manufacturer		PCCHIPS
Product			M756LMRT
Version			1.0

[ Chassis ]

Chassis Properties:
Manufacturer		PCCHIPS
Version			Version 1.00
Serial Number		123456890
Asset Tag		0123ABC
Chassis Type		Desktop Case

[ Memory Controller ]
Memory Controller Properties:
Error Detection Method			32-bit ECC
Error Correction			Single-bit
Supported Memory Interleave		1-Way
Current Memory Interleave		1-Way
Supported Memory Speeds			70ns, 60ns
Supported Memory Types			SPM, FPM, EDO, Parity, ECC, SIMM
Supported Memory Voltages		3.3V
Maximum Memory Module Size		128 MB
Memory Slots				4

[ Processors / Pentium III ]

Processor Properties:
Manufacturer		i
Version			Pentium III
External Clock		133 MHz
Current Clock		667 MHz
Type			Central Processor
Voltage			3.3 V, 2.9 V
Status			Enabled
Upgrade			Slot 1
Socket Designation	Slot-1

---

### Post by davesouth on 2007-07-05
I realize this is an old post, but I'd like to dig it up.

I also am experiencing similar problems. I believe it is related to my motherboard, also a PCChips brand ( M848ALU ) Could it be the SiS chipset?

Athlon XP 3200+ @ 200MHz
PcChips M848ALU v2.1
SiS 748/964 Chipset
1024 Kingston premium DDR

---

### Post by bluhound on 2007-08-05
The same problem is also happening to me.  The only difference is that my motherboard is an Asus P4S333-VM with a SiS 650 chipset.  Three mobos with SiS chipsets having similar problems.  Sounds like a SiS bug.

---

### Post by mangocrazy on 2007-09-15
I don't believe it's a bug with SiS, I believe it's a bug within Feisty (7.04). My wife's PC has a SiS 748/964 chipset and hangs apparently randomly under Feisty. When she boots into Dapper (6.06) the problem simply doesn't happen. Neither does it happen when she boots into Windows XP or 98. Her machine, like mine is set up to multi-boot using Grub.

As far as I am aware this is a known problem that Ubuntu seem entirely unwilling to fix. I don't know whether SiS chipset support got broken when Edgy got introduced (I don't use Edgy) or whether it happened with Feisty.

But SiS chipset support is most certainly broken in Feisty. Is anyone listening?

---

### Post by backcracker on 2007-10-07
Same thing...
mobo: MSI MS-7181 - VIA K8M800 chipset

---

### Post by dlane on 2007-11-02
Happens for me, too, with a new Asus A62E notebook (Santa Rosa chipset) running Gutsy.  Only seems to happen when the machine is running on battery, and the lid closed, e.g. in transit.  Probably happens every other time that I travel more than 5-10 minutes...  very strange and very frustrating.  The caps and scroll lock lights flash, and I need to hold the power switch to shut down - no key responses whatsoever... 

For what it's worth, the machine suspends and hibernates successfully, but the wireless doesn't usually come back successfully and requires a dbus restart and sometimes a reinsertion of the wireless device module (iwl4965) top be usable again......

Anyone have any thoughts?

Dave

---

### Post by kaos_frack on 2008-02-28
Same problem, the only thing i can do is move the cursor...
gutsy (fresh install)
compaq presario v2000 laptop
anybody know the reason?

---

### Post by kaos_frack on 2008-02-28
*bump*

---

### Post by kaos_frack on 2008-03-04
alright, i havent had any hangs after i disabled the option "password prompt as normal dialog" in accessibility settings
can anybody confirm?

---

### Post by tropcky on 2008-03-04
deeeeeeeem  i have the same problem with my  pc 
matherbord : gigabyte GE-8GE800 
RAM :1 G
PROCESER ( REALLY POOR ) : 2.5   256
any way that didnt happened with 7.04  

is ther a way to fix it

---

### Post by cetheriel on 2008-03-04
maybe it's the windows partition. windows xp/vista likes ntfs-3, and it sucks.
i'd say you try partitioning a little hd for windows (ntfs-3) some more for linux (ext3 or reiserfs) and everything else in FAT so both systems can handle it easily.

---

### Post by tropcky on 2008-03-04
will sorry but its not a good way i have 2 hard disks each one is 80 g  and its full its gonna be so dem hard to back all thes up and reformatting  is ther anther way

---

### Post by kaos_frack on 2008-03-04
guys, can you please confirm the following:

I haven't exprienced any hangs after disabling "password dialogs as normal windows" in "system->preferences->universal access->assistive technology preferences"

seems like it's a bug

---

### Post by tropcky on 2008-03-04
oky bro but befor i disable any thing in the system i have 2 know its jop 

befor disabling "password dialogs as normal windows" i have to know what it jop and after i disable it if ther any danger on the system?
 i just have 2 know

---

### Post by kaos_frack on 2008-03-04
nope there is no danger, its just an accessibility issue...
this option is by disable default, i enable it and experienced system hangs
actually if you don't know then probably it is disbabled now

---

### Post by tropcky on 2008-03-04
then we still in the problem and we still dont know how 2 fix that

---

