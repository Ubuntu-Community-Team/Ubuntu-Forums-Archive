---
title: "M1530 Suspend Button and Battery button (Fn+F1 and Fn+F3) issues..."
date: 2009-01-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by spacesearcher on 2009-01-14
I am running Ubuntu 8.10 on a Dell XPS 1530 BIOS A12

When I push Fn and F1 the suspend button the computer does not suspend then I am unable to do anything if i click Applications it will highlight the applications button but it will not bring up the menu same goes for the drop down to shutdown the computer. I can get the menus to respond again by flipping the cube or hitting ctrl+alt+F1 then ctrl+alt+F7. 

If I press Fn+F3 to see the charge on the battery it will keep bringing up new notification boxes on top of each other. ctrl+alt+right will make it stop bringing up new notification boxes but the keyboard is unresponsive unless I do ctrl+alt+f1 I then can go back and do ctrl+alt+f7 and type again.

In keyboard shortcuts under suspend it has "XF86Standby" next to suspend there is nothing in that menu that looks like it controls the battery  button.

Does anyone know what is wrong or how I can go about figuring it out? I would like to be able to suspend my computer with the keyboard shortcut.

---

### Post by bluewres on 2009-01-29
It's interesting, I had never tried using those keyboard commands in ubuntu on my xps m1530 before I saw your post, but apparently I have similar issues.  When I use fn + f1 it goes to a black screen with an error message (I will post the message later) and I have the same issue with f3.  My bios is version A08.  Anyone have a clue as to what's up?

---

### Post by bluewres on 2009-01-29
Turns out it varies each time what the error message is, but it seems that there is always a line that says something like "failed to resubmit (2)"

---

### Post by wolterh on 2009-02-11
bump

---

### Post by superm1 on 2009-02-12
please make sure you are on a fully updated system.  some of the items mentioned in the first post are resolved when you perform updates.

---

### Post by spacesearcher on 2009-02-12
I am fully updated as of an hour ago and the problem still is happening.

---

### Post by superm1 on 2009-02-12
If you're fully up to date and rebooted into the new kernel and these things are still happening, it's possible that you were one of the machines that needs a little different of a quirk.

what's your 

sudo dmidecode output look like?

---

### Post by spacesearcher on 2009-02-12
Here it is:

```
# dmidecode 2.9
SMBIOS 2.4 present.
45 structures occupying 2001 bytes.
Table at 0x000F71E0.

Handle 0xDA00, DMI type 218, 251 bytes
OEM-specific Type
	Header and Data:
		DA FB 00 DA B2 00 0D 5F 0F 37 40 7D 00 00 00 00
		00 7E 00 02 00 00 00 40 00 04 00 01 00 41 00 04
		00 00 00 65 00 05 00 00 00 66 00 05 00 01 00 5E
		00 06 00 01 00 5F 00 06 00 00 00 89 01 07 00 00
		00 8A 01 07 00 01 00 42 00 08 00 01 00 43 00 08
		00 00 00 55 00 09 00 00 00 6D 00 09 00 01 00 2D
		00 0A 00 02 00 6E 00 0A 00 01 00 2E 00 0A 00 00
		00 11 01 0B 00 00 00 10 01 0B 00 01 00 F0 00 0C
		00 01 00 ED 00 0C 00 00 00 41 01 0D 00 01 00 40
		01 0D 00 00 00 47 01 0E 00 01 00 46 01 0E 00 00
		00 4A 01 0F 00 00 00 4B 01 0F 00 01 00 52 01 10
		00 01 00 53 01 10 00 00 00 80 01 11 00 01 00 7F
		01 11 00 00 00 7C 01 12 00 01 00 7B 01 12 00 00
		00 7E 01 13 00 01 00 7D 01 13 00 00 00 92 01 14
		00 00 00 91 01 14 00 01 00 94 01 15 00 00 00 93
		01 15 00 01 00 FF FF 00 00 00 00

Handle 0xDA01, DMI type 218, 251 bytes
OEM-specific Type
	Header and Data:
		DA FB 01 DA B2 00 0D 5F 0F 37 40 86 01 16 00 01
		00 85 01 16 00 00 00 82 01 17 00 01 00 81 01 17
		00 00 00 84 01 18 00 01 00 83 01 18 00 00 00 9B
		01 19 00 00 00 9C 01 19 00 01 00 9D 01 19 00 02
		00 9E 01 19 00 03 00 8D 01 1A 00 00 00 8E 01 1A
		00 01 00 EA 00 1B 00 00 00 EB 00 1B 00 01 00 EC
		00 1B 00 02 00 28 00 1C 00 00 00 29 00 1C 00 01
		00 2A 00 1C 00 02 00 2B 00 1D 00 00 00 2C 00 1E
		00 00 00 E7 00 1F 00 01 00 E6 00 1F 00 00 00 0E
		01 20 00 01 00 0F 01 20 00 00 00 9B 00 21 00 01
		00 9C 00 21 00 00 00 4D 01 22 00 01 00 4C 01 22
		00 00 00 01 01 23 00 00 00 02 01 23 00 01 00 04
		01 23 00 02 00 37 01 24 00 00 00 38 01 24 00 01
		00 D9 01 25 00 01 00 D8 01 25 00 00 00 EA 01 26
		00 00 00 EB 01 26 00 01 00 EC 01 27 00 00 00 ED
		01 27 00 01 00 FF FF 00 00 00 00

Handle 0xDA02, DMI type 218, 65 bytes
OEM-specific Type
	Header and Data:
		DA 41 02 DA B2 00 0D 5F 0F 37 40 76 01 76 01 01
		00 75 01 75 01 01 00 DD 01 DD 01 03 00 DC 01 DC
		01 02 00 01 F0 01 F0 00 00 02 F0 02 F0 00 00 03
		F0 03 F0 00 00 04 F0 04 F0 00 00 FF FF 00 00 00
		00

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: Dell Inc.
	Version: A12
	Release Date: 11/19/2008
	Address: 0xF0000
	Runtime Size: 64 kB
	ROM Size: 2048 kB
	Characteristics:
		ISA is supported
		PCI is supported
		PC Card (PCMCIA) is supported
		PNP is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		Boot from CD is supported
		Selectable boot is supported
		3.5"/720 KB floppy services are supported (int 13h)
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		AGP is supported
		Smart battery is supported
		BIOS boot specification is supported
		Function key-initiated network boot is supported
		Targeted content distribution is supported
	BIOS Revision: 1.2
	Firmware Revision: 1.2

Handle 0x0100, DMI type 1, 27 bytes
System Information
	Manufacturer: Dell Inc.
	Product Name: XPS M1530                       
	Version: Not Specified
	Serial Number: CTN6VF1
	UUID: 44454C4C-5400-104E-8036-C3C04F564631
	Wake-up Type: Power Switch
	SKU Number: Not Specified
	Family:  

Handle 0x0200, DMI type 2, 9 bytes
Base Board Information
	Manufacturer: Dell Inc.
	Product Name: 0R387D
	Version:    
	Serial Number: .CTN6VF1.CN7016682D09JT.

Handle 0x0300, DMI type 3, 13 bytes
Chassis Information
	Manufacturer: Dell Inc.
	Type: Portable
	Lock: Not Present
	Version: Not Specified
	Serial Number: CTN6VF1
	Asset Tag: Not Specified
	Boot-up State: Safe
	Power Supply State: Safe
	Thermal State: Safe
	Security Status: None

Handle 0x0400, DMI type 4, 40 bytes
Processor Information
	Socket Designation: Microprocessor
	Type: Central Processor
	Family: <OUT OF SPEC>
	Manufacturer: Intel
	ID: 76 06 01 00 FF FB EB BF
	Version: Not Specified
	Voltage: 3.3 V
	External Clock: 200 MHz
	Max Speed: 2400 MHz
	Current Speed: 2400 MHz
	Status: Populated, Enabled
	Upgrade: None
	L1 Cache Handle: 0x0700
	L2 Cache Handle: 0x0701
	L3 Cache Handle: Not Provided
	Serial Number: Not Specified
	Asset Tag: Not Specified
	Part Number: Not Specified
	Core Count: 2
	Core Enabled: 2
	Thread Count: 2
	Characteristics:
		64-bit capable

Handle 0x0700, DMI type 7, 19 bytes
Cache Information
	Socket Designation: Not Specified
	Configuration: Enabled, Not Socketed, Level 1
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 32 KB
	Maximum Size: 32 KB
	Supported SRAM Types:
		Unknown
	Installed SRAM Type: Unknown
	Speed: Unknown
	Error Correction Type: None
	System Type: Data
	Associativity: 4-way Set-associative

Handle 0x0701, DMI type 7, 19 bytes
Cache Information
	Socket Designation: Not Specified
	Configuration: Enabled, Not Socketed, Level 2
	Operational Mode: Varies With Memory Address
	Location: Internal
	Installed Size: 3072 KB
	Maximum Size: 3072 KB
	Supported SRAM Types:
		Pipeline Burst
	Installed SRAM Type: Pipeline Burst
	Speed: 15 ns
	Error Correction Type: None
	System Type: Unified
	Associativity: Other

Handle 0x0804, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: USB
	Internal Connector Type: None
	External Reference Designator: Not Specified
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0806, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: MONITOR
	Internal Connector Type: None
	External Reference Designator: Not Specified
	External Connector Type: DB-15 female
	Port Type: Video Port

Handle 0x080B, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: FireWire
	Internal Connector Type: None
	External Reference Designator: Not Specified
	External Connector Type: IEEE 1394
	Port Type: Firewire (IEEE P1394)

Handle 0x080C, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: Modem
	Internal Connector Type: None
	External Reference Designator: Not Specified
	External Connector Type: RJ-11
	Port Type: Modem Port

Handle 0x080D, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: Ethernet
	Internal Connector Type: None
	External Reference Designator: Not Specified
	External Connector Type: RJ-45
	Port Type: Network Port

Handle 0x0900, DMI type 9, 13 bytes
System Slot Information
	Designation: PCMCIA 0
	Type: 32-bit PC Card (PCMCIA)
	Current Usage: Available
	Length: Other
	ID: Adapter 0, Socket 0
	Characteristics:
		5.0 V is provided
		3.3 V is provided
		PC Card-16 is supported
		Cardbus is supported
		Zoom Video is supported
		Modem ring resume is supported

Handle 0x0A00, DMI type 10, 6 bytes
On Board Device Information
	Type: Video
	Status: Enabled
	Description: NVIDIA NB8P-GS                

Handle 0x0A01, DMI type 10, 6 bytes
On Board Device Information
	Type: Sound
	Status: Enabled
	Description: Sigmatel 9205

Handle 0x0B00, DMI type 11, 5 bytes
OEM Strings
	String 1: Dell System
	String 2: 5[0003]
	String 3: 13[PP25L]

Handle 0x0D00, DMI type 13, 22 bytes
BIOS Language Information
	Installable Languages: 1
		en|US|iso8859-1
	Currently Installed Language: en|US|iso8859-1

Handle 0x1000, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 4 GB
	Error Information Handle: Not Provided
	Number Of Devices: 2

Handle 0x1100, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x1000
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM_A
	Bank Locator: Not Specified
	Type: DDR
	Type Detail: Synchronous
	Speed: 667 MHz (1.5 ns)
	Manufacturer: CE00000000000000
	Serial Number: 763214CB
	Asset Tag: 510809
	Part Number: M4 70T5663QZ3-CE6 

Handle 0x1101, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x1000
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 1024 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM_B
	Bank Locator: Not Specified
	Type: DDR
	Type Detail: Synchronous
	Speed: 667 MHz (1.5 ns)
	Manufacturer: AD00000000000000
	Serial Number: 00001028
	Asset Tag: 000747
	Part Number: HYMP112S64CP6-Y5  

Handle 0x1301, DMI type 19, 15 bytes
Memory Array Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x000BFFFFFFF
	Range Size: 3 GB
	Physical Array Handle: 0x1000
	Partition Width: 0

Handle 0x1401, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0007FFFFFFF
	Range Size: 2 GB
	Physical Device Handle: 0x1100
	Memory Array Mapped Address Handle: 0x1301
	Partition Row Position: 1
	Interleave Position: 1
	Interleaved Data Depth: 8

Handle 0x1411, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00080000000
	Ending Address: 0x000BFFFFFFF
	Range Size: 1 GB
	Physical Device Handle: 0x1100
	Memory Array Mapped Address Handle: 0x1301
	Partition Row Position: 1

Handle 0x1402, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0007FFFFFFF
	Range Size: 2 GB
	Physical Device Handle: 0x1101
	Memory Array Mapped Address Handle: 0x1301
	Partition Row Position: 1
	Interleave Position: 2
	Interleaved Data Depth: 8

Handle 0x1412, DMI type 126, 19 bytes
Inactive

Handle 0x1500, DMI type 21, 7 bytes
Built-in Pointing Device
	Type: Touch Pad
	Interface: Bus Mouse
	Buttons: 2

Handle 0x1600, DMI type 22, 26 bytes
Portable Battery
	Location: Sys. Battery Bay
	Manufacturer: SMP             
	Name: DELL RN89481    
	Design Capacity: 78000 mWh
	Design Voltage: 11100 mV
	SBDS Version: 1.0
	Maximum Error: 9%
	SBDS Serial Number: 05EB
	SBDS Manufacture Date: 2008-01-21
	SBDS Chemistry: LION            
	OEM-specific Information: 0x00000001

Handle 0x1B00, DMI type 27, 12 bytes
Cooling Device
	Type: Fan
	Status: OK
	OEM-specific Information: 0x0000DD00

Handle 0x1C00, DMI type 28, 20 bytes
Temperature Probe
	Description: CPU Internal Temperature
	Location: Processor
	Status: OK
	Maximum Value: 127.0 deg C
	Minimum Value 0.0 deg C
	Resolution: 1.000 deg C
	Tolerance: 0.5 deg C
	Accuracy: Unknown
	OEM-specific Information: 0x0000DC00

Handle 0x2000, DMI type 32, 11 bytes
System Boot Information
	Status: No errors detected

Handle 0xB000, DMI type 176, 5 bytes
OEM-specific Type
	Header and Data:
		B0 05 00 B0 00

Handle 0xB100, DMI type 177, 12 bytes
OEM-specific Type
	Header and Data:
		B1 0C 00 B1 02 00 00 00 00 00 00 00

Handle 0xD000, DMI type 208, 10 bytes
OEM-specific Type
	Header and Data:
		D0 0A 00 D0 01 04 FE 00 2E 02

Handle 0xD800, DMI type 216, 9 bytes
OEM-specific Type
	Header and Data:
		D8 09 00 D8 01 03 01 F0 03
	Strings:
		NVidia Corp.         
		 
		060.084.064.000.008.000  

Handle 0xD900, DMI type 217, 8 bytes
OEM-specific Type
	Header and Data:
		D9 08 00 D9 01 02 01 03
	Strings:
		US-101
		Proprietary

Handle 0xDB00, DMI type 219, 9 bytes
OEM-specific Type
	Header and Data:
		DB 09 00 DB 03 01 02 03 FF
	Strings:
		System Device Bay
		Floppy, Battery, CD-ROM, CD-RW, DVD, DVD+RW, DVD+/-RW, Hard Disk, BLU-RAY
		DVD+/-RW  

Handle 0xDC00, DMI type 220, 22 bytes
OEM-specific Type
	Header and Data:
		DC 16 00 DC 01 F0 00 00 02 F0 00 00 00 00 03 F0
		04 F0 00 00 00 00

Handle 0xDD00, DMI type 221, 19 bytes
OEM-specific Type
	Header and Data:
		DD 13 00 DD 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00

Handle 0xD400, DMI type 212, 37 bytes
OEM-specific Type
	Header and Data:
		D4 25 00 D4 74 00 75 00 00 10 2D 2E 5C 00 78 BF
		40 5D 00 78 BF 00 08 00 1D DF 00 03 00 1D DF 00
		FF FF 00 00 00

Handle 0xD401, DMI type 212, 17 bytes
OEM-specific Type
	Header and Data:
		D4 11 01 D4 74 00 75 00 03 40 49 4A FF FF 00 00
		00

Handle 0xDE00, DMI type 222, 16 bytes
OEM-specific Type
	Header and Data:
		DE 10 00 DE 01 02 FF FF 00 00 00 00 00 00 00 01

Handle 0x7F00, DMI type 127, 4 bytes
End Of Table

```

---

### Post by superm1 on 2009-02-12
Ok, the quirk is proper for your BIOS.  Can you try using FN-ESC for your suspend?  See if that's any better.

If not, then we'll need to figure out which layer is failing.

---

### Post by wolterh on 2009-02-12
Nice that I am not the only one having this problem. Well, besides making me jealous the fact that you, spacesearcher, have 2400 MHz and I have 2200 MHz, I saw the demidecode's virtually identical. 

After performing a difference check with the **diff** command, I saw this output, which I hope you, the ubuntu developer, will be able to understand, for I am not.
```
$ diff Desktop/dmidecode Desktop/dude\'s\ dmidecode 
93,94c93,94
< 	Serial Number: 330GXH1
< 	UUID: 44454C4C-3300-1030-8047-B3C04F584831
---
> 	Serial Number: CTN6VF1
> 	UUID: 44454C4C-5400-104E-8036-C3C04F564631
102c102
< 	Product Name: 0D501F
---
> 	Product Name: 0R387D
104c104
< 	Serial Number: .330GXH1.CN701668AR0HO4.
---
> 	Serial Number: .CTN6VF1.CN7016682D09JT.
112c112
< 	Serial Number: 330GXH1
---
> 	Serial Number: CTN6VF1
125c125
< 	ID: FD 06 00 00 FF FB EB BF
---
> 	ID: 76 06 01 00 FF FB EB BF
129,130c129,130
< 	Max Speed: 2200 MHz
< 	Current Speed: 2200 MHz
---
> 	Max Speed: 2400 MHz
> 	Current Speed: 2400 MHz
167,168c167,168
< 	Installed Size: 2048 KB
< 	Maximum Size: 2048 KB
---
> 	Installed Size: 3072 KB
> 	Maximum Size: 3072 KB
278,282c278,282
< 	Speed: 800 MHz (1.2 ns)
< 	Manufacturer: AD00000000000000
< 	Serial Number: 00001027
< 	Asset Tag: 000850
< 	Part Number: HYMP125S64CP8-S6  
---
> 	Speed: 667 MHz (1.5 ns)
> 	Manufacturer: CE00000000000000
> 	Serial Number: 763214CB
> 	Asset Tag: 510809
> 	Part Number: M4 70T5663QZ3-CE6 
290c290
< 	Size: 2048 MB
---
> 	Size: 1024 MB
297c297
< 	Speed: 800 MHz (1.2 ns)
---
> 	Speed: 667 MHz (1.5 ns)
299,301c299,301
< 	Serial Number: 00004018
< 	Asset Tag: 000850
< 	Part Number: HYMP125S64CP8-S6  
---
> 	Serial Number: 00001028
> 	Asset Tag: 000747
> 	Part Number: HYMP112S64CP6-Y5  
306,307c306,307
< 	Ending Address: 0x000FFFFFFFF
< 	Range Size: 4 GB
---
> 	Ending Address: 0x000BFFFFFFF
> 	Range Size: 3 GB
314,315c314,315
< 	Ending Address: 0x000FFFFFFFF
< 	Range Size: 4 GB
---
> 	Ending Address: 0x0007FFFFFFF
> 	Range Size: 2 GB
322,323c322,329
< Handle 0x1411, DMI type 126, 19 bytes
< Inactive
---
> Handle 0x1411, DMI type 20, 19 bytes
> Memory Device Mapped Address
> 	Starting Address: 0x00080000000
> 	Ending Address: 0x000BFFFFFFF
> 	Range Size: 1 GB
> 	Physical Device Handle: 0x1100
> 	Memory Array Mapped Address Handle: 0x1301
> 	Partition Row Position: 1
328,329c334,335
< 	Ending Address: 0x000FFFFFFFF
< 	Range Size: 4 GB
---
> 	Ending Address: 0x0007FFFFFFF
> 	Range Size: 2 GB
348,350c354,356
< 	Manufacturer: Sanyo           
< 	Name: DELL XT8168B    
< 	Design Capacity: 52000 mWh
---
> 	Manufacturer: SMP             
> 	Name: DELL RN89481    
> 	Design Capacity: 78000 mWh
353,355c359,361
< 	Maximum Error: 5%
< 	SBDS Serial Number: 05EE
< 	SBDS Manufacture Date: 2008-11-25
---
> 	Maximum Error: 9%
> 	SBDS Serial Number: 05EB
> 	SBDS Manufacture Date: 2008-01-21
454d459
< 

```

Thanks.

For now, I will not try the FN+ESC because I am installing Unreal 2004 at the moment, but I will gladly try it out as soon as the installation is completed.

----------------------------------------------------------

Well, now I've tested the FN+ESC key combination, but the result is the same one: I get a succesfull suspend, but I am unable to wake up the machine, having no more options than forcing turn-off.

Now, I would like to know how could I help you to determine "which layer" has the problem.

---

### Post by wolterh on 2009-02-13
bump

---

### Post by spacesearcher on 2009-02-14
Okies i tried the fn + esc and it did suspend the computer the first time i did it it wouldn't let me type or open things like the applications menu until i hit ctrl + alt + f1 now it seems to work fine.

---

### Post by wolterh on 2009-02-14
Oh, I tried that but I had no success!
My computer suspends fine. Then, I wait until there is no fan spinning and the power light dims gently on and off. Afterwards, I start pressing keys, mouse buttons--everything. She won't wake up. I press Control+Alt+F1: nothing happened.

So, what exactly did you do to make your's work? I would like a step by step guide haha. 

I had this doubts after reading your post. You say that you pressed Control+Alt+F1 to make it work, but, was the computer awake before, or did that keycombo woke it up?

--------------EDIT-----------------
Hi again, I kept reading and saw that the users of achlinux were having the same problem, so I dived in and posted on some thread, where they were talking about this same subject. After bumping, something I love to do, some guy told me to install the latest nvidia drivers, 180.29, and that would fix the problem.

So I did. I went into the Software Sources and added some jaunty sources (because jaunty has the 180.29 drivers in the restricted repo) and installed afterwards the newest drivers.

Now that all was set, I tried the FN-ESC suspend keypress, and bam! suspended. Nice. Then I went through my old problem: I couldn't wake the machine up. I thought something was wrong until--I don't know why--I closed the lid, and reopened it. My precious machine started clicking and spinning stuff it hides inside, and woke up!

So, I don't know what fixed it, either the drivers, or just the close-open lid technique. I guess they made the script specially for people who made their laptops suspend when the lid was closed.

---

