---
title: "Slow Bootup/Help Needed"
date: 2005-01-04
forum: Desktop Environments
---

### Post by ankitmalik on 2005-01-04
I hava a kinda slow bootup.

And there are new hotplug errors though I have checked out the blacklist :D

But before anyone can help me on that, I need to show up my booting messages.

But I dont know where the messages which are displayed @ bootup are stored.

I think somewhere in /var but can someone please point me out to the correct file???

---

### Post by feneks on 2005-01-04
The messages of bootup are stored in /var/log/dmesg

messages during linux is running are stored likely in /var/log/messages

XFree86 for example has ist's own message-file down somewhere in /var/

edit
hey, wellcome to the "Ubuntu Inspiring Guru" members    :D

---

### Post by feneks on 2005-01-04
nice Blog

---

### Post by ankitmalik on 2005-01-05
Thanks!

Ok here is the file 

```
Linux version 2.6.8.1-3-386 (buildd@terranova) (gcc version 3.3.4 (Debian 1:3.3.4-9ubuntu5)) #1 Thu Nov 18 11:47:33 UTC 2004
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
 BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 0000000007ef0000 (usable)
 BIOS-e820: 0000000007ef0000 - 0000000007ef3000 (ACPI NVS)
 BIOS-e820: 0000000007ef3000 - 0000000007f00000 (ACPI data)
 BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
126MB LOWMEM available.
On node 0 totalpages: 32496
  DMA zone: 4096 pages, LIFO batch:1
  Normal zone: 28400 pages, LIFO batch:6
  HighMem zone: 0 pages, LIFO batch:1
DMI not present.
ACPI: RSDP (v000 IntelR                                ) @ 0x000f5e70
ACPI: RSDT (v001 IntelR AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x07ef3000
ACPI: FADT (v001 IntelR AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x07ef3040
ACPI: DSDT (v001 INTELR AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
ACPI: PM-Timer IO Port: 0x4008
Built 1 zonelists
Kernel command line: root=/dev/hda2 ro apm=on quiet splash
Local APIC disabled by BIOS -- reenabling.
Found and enabled local APIC!
Initializing CPU#0
PID hash table entries: 512 (order 9: 4096 bytes)
Detected 852.097 MHz processor.
Using pmtmr for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 16384 (order: 4, 65536 bytes)
Inode-cache hash table entries: 8192 (order: 3, 32768 bytes)
Memory: 121696k/129984k available (1335k kernel code, 7752k reserved, 730k data, 204k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 1687.55 BogoMIPS
Security Scaffold v1.0.0 initialized
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: 0383fbff 00000000 00000000 00000000
CPU: After vendor identify, caps:  0383fbff 00000000 00000000 00000000
CPU: L1 I cache: 16K, L1 D cache: 16K
CPU: L2 cache: 128K
CPU: After all inits, caps:        0383fbff 00000000 00000000 00000040
CPU: Intel Celeron (Coppermine) stepping 0a
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Checking 'hlt' instruction... OK.
Checking for popad bug... OK.
ACPI: IRQ9 SCI: Level Trigger.
enabled ExtINT on CPU#0
ESR value before enabling vector: 00000000
ESR value after enabling vector: 00000000
Using local APIC timer interrupts.
calibrating APIC timer ...
..... CPU clock speed is 851.0847 MHz.
..... host bus clock speed is 100.0217 MHz.
checking if image is initramfs...it isn't (ungzip failed); looks like an initrd
Freeing initrd memory: 4136k freed
NET: Registered protocol family 16
EISA bus registered
PCI: PCI BIOS revision 2.10 entry at 0xfb260, last bus=1
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20040816
ACPI: Interpreter enabled
ACPI: Using PIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
PCI: Transparent bridge - 0000:00:1e.0
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 *12 14 15)
ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
Linux Plug and Play Support v0.97 (c) Adam Belay
PnPBIOS: Scanning system for PnP BIOS support...
PnPBIOS: Found PnP BIOS installation structure at 0xc00fbbf0
PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xbc20, dseg 0xf0000
pnp: 00:0c: ioport range 0x800-0x87f has been reserved
PnPBIOS: 18 nodes reported by PnP BIOS; 18 recorded by driver
PCI: Using ACPI for IRQ routing
ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
ACPI: PCI interrupt 0000:00:01.0[A] -> GSI 11 (level, low) -> IRQ 11
ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
ACPI: PCI interrupt 0000:00:1f.2[D] -> GSI 10 (level, low) -> IRQ 10
ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
ACPI: PCI interrupt 0000:00:1f.3[B] -> GSI 5 (level, low) -> IRQ 5
ACPI: PCI interrupt 0000:00:1f.5[B] -> GSI 5 (level, low) -> IRQ 5
ACPI: PCI interrupt 0000:01:08.0[A] -> GSI 11 (level, low) -> IRQ 11
ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 12
ACPI: PCI interrupt 0000:01:09.0[B] -> GSI 12 (level, low) -> IRQ 12
ACPI: PCI interrupt 0000:01:09.1[C] -> GSI 10 (level, low) -> IRQ 10
ACPI: PCI interrupt 0000:01:09.2[D] -> GSI 11 (level, low) -> IRQ 11
ACPI: PCI interrupt 0000:01:09.3[A] -> GSI 5 (level, low) -> IRQ 5
ACPI: PCI interrupt 0000:01:0a.0[A] -> GSI 12 (level, low) -> IRQ 12
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
input: AT Translated Set 2 keyboard on isa0060/serio0
EISA: Probing bus 0 at eisa0
Cannot allocate resource for EISA slot 4
Cannot allocate resource for EISA slot 5
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 512 buckets, 4Kbytes
TCP: Hash tables configured (established 8192 bind 16384)
NET: Registered protocol family 8
NET: Registered protocol family 20
ACPI: (supports S0 S1 S4 S5)
ACPI wakeup devices: 
SLPB PCI0 HUB0 USB0 UAR1 UAR2 LPT1 
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4136 blocks [1 disk] into ram disk... |/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 204k freed
vesafb: probe of vesafb0 failed with error -6
ACPI: Processor [CPU0] (supports C1 C2, 2 throttling states)
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
ICH: IDE controller at PCI slot 0000:00:1f.1
ICH: chipset revision 2
ICH: not 100% native mode: will probe irqs later
    ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:pio
    ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
hda: SAMSUNG SV2002H, ATA DISK drive
Using anticipatory io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 39180960 sectors (20060 MB) w/468KiB Cache, CHS=38870/16/63, UDMA(66)
 /dev/ide/host0/bus0/target0/lun0: p1 p2 p4 < p5 >
hdc: SAMSUNG CD-ROM SC-152C, ATAPI CD/DVD-ROM drive
hdd: HL-DT-ST GCE-8525B, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
Adding 1035676k swap on /dev/hda5.  Priority:-1 extents:1
EXT3 FS on hda2, internal journal
mice: PS/2 mouse device common for all mice
hdc: ATAPI 52X CD-ROM drive, 128kB Cache, DMA
Uniform CD-ROM driver Revision: 3.20
hdd: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
lp0: using parport0 (interrupt-driven).
apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
apm: overridden by ACPI.
Capability LSM initialized
device-mapper: 4.1.0-ioctl (2003-12-10) initialised: dm@uk.sistina.com
md: md driver 0.90.0 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
Real Time Clock Driver v1.12
input: PC Speaker
inserting floppy driver for 2.6.8.1-3-386
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected an Intel i810 Chipset.
agpgart: Maximum main memory to use for agp memory: 93M
agpgart: detected 4MB dedicated video ram.
agpgart: AGP aperture is 64M @ 0xd0000000
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI interrupt 0000:00:1f.2[D] -> GSI 10 (level, low) -> IRQ 10
uhci_hcd 0000:00:1f.2: Intel Corp. 82801AA USB
PCI: Setting latency timer of device 0000:00:1f.2 to 64
uhci_hcd 0000:00:1f.2: irq 10, io base 0000d000
uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1f.5[B] -> GSI 5 (level, low) -> IRQ 5
PCI: Setting latency timer of device 0000:00:1f.5 to 64
intel8x0_measure_ac97_clock: measured 49533 usecs
intel8x0: clocking to 48000
8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
8139cp: pci dev 0000:01:08.0 (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
8139cp: Try the "8139too" driver instead.
8139too Fast Ethernet driver 0.9.27
ACPI: PCI interrupt 0000:01:08.0[A] -> GSI 11 (level, low) -> IRQ 11
eth0: RealTek RTL8139 at 0xc000, 00:0b:2b:0f:da:ea, IRQ 11
eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
ohci_hcd: 2004 Feb 02 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
ohci_hcd: block sizes: ed 64 td 64
ACPI: PCI interrupt 0000:01:09.0[B] -> GSI 12 (level, low) -> IRQ 12
ohci_hcd 0000:01:09.0: ALi Corporation USB 1.1 Controller
ohci_hcd 0000:01:09.0: irq 12, pci mem c8a47000
ohci_hcd 0000:01:09.0: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:01:09.1[C] -> GSI 10 (level, low) -> IRQ 10
ohci_hcd 0000:01:09.1: ALi Corporation USB 1.1 Controller (#2)
ohci_hcd 0000:01:09.1: irq 10, pci mem c8a49000
ohci_hcd 0000:01:09.1: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:01:09.2[D] -> GSI 11 (level, low) -> IRQ 11
ohci_hcd 0000:01:09.2: ALi Corporation USB 1.1 Controller (#3)
ohci_hcd 0000:01:09.2: irq 11, pci mem c8a88000
ohci_hcd 0000:01:09.2: new USB bus registered, assigned bus number 4
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:01:09.3[A] -> GSI 5 (level, low) -> IRQ 5
ehci_hcd 0000:01:09.3: ALi Corporation USB 2.0 Controller
ehci_hcd 0000:01:09.3: irq 5, pci mem c8a91000
ehci_hcd 0000:01:09.3: new USB bus registered, assigned bus number 5
ehci_hcd 0000:01:09.3: USB 2.0 enabled, EHCI 1.00, driver 2004-May-10
hub 5-0:1.0: USB hub found
hub 5-0:1.0: 6 ports detected
eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
``` 


Now can anyone help me reduce the flab!

By the way, this stuff is not exactly shown on the screen! What is the file which stores the exact stuff as it is shown on the screen.

---

### Post by ankitmalik on 2005-01-05
i dont have the time to install bootsplash and stuff but is there any other way I can have the ability to not display all the booting messages during bootup???

The messages are quite unsettling for other not so computer enthusiasts in my family :D

---

### Post by feneks on 2005-01-09
I had only a brief look at your dmesg: 

[QUOTE=ankitmalik]
Kernel command line: root=/dev/hda2 ro apm=on quiet splash
apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
apm: overridden by ACPI.
[/Quote] 
Why are you telling the kernel to use apm?

[QUOTE=ankitmalik]
md: md driver 0.90.0 MAX_MD_DEVS=256, MD_SB_DISKS=27
[/QUOTE]
Do you have any Multipledisks like RAID running? If no you could do:
**sudo apt-get --purge remove mdadm**

---

### Post by feneks on 2005-01-10
I couldn't find any error messages in dmesg. 

I don't know if the messages  like
*ACPI: PCI interrupt 0000:01:09.3[A] -> GSI 5 (level, low) -> IRQ 5*
are ok. If they aren't, ACPI for PCI can be turned off with the option **acpi=nopci** at grub's menu.lst. But as I said I've no idea if this is an error or not. 

To boost your bootsequence you could try to start GDM earlier. Then GDM will already prompt whereas CUPS and so on are booted in background. The bootsequence is handled by init and it's scripts. I advise you to have a very close look at how this works. If you do anything wrong Ubuntu possibly doesn't boot anymore. I have already set GDM at the beginning of runlevel 2. It seems to work properly.

---

