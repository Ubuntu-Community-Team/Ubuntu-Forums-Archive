---
title: "No CD ROM Drives"
date: 2005-12-01
forum: Desktop Environments
---

### Post by politicaldog on 2005-12-01
In the device manager I can see that they look like hard drives. I can't play anything on either CD Drive.

Unable to mount the selected volumes Mount: special device /dev/hdc does not exist

or

Unable to mount the selected volumes Mount: special device /dev/hdd does not exist

Rick

---

### Post by politicaldog on 2005-12-02
Helloooo Helloooo  [SIZE="1"]echo echo[/SIZE].............lol


Help

Rick

---

### Post by Pablo_Escobar on 2005-12-02
Post Your /etc/fstab contents here.

---

### Post by politicaldog on 2005-12-02
[QUOTE /etc/fstab [/QUOTE]


Is that the commands to type into the terminal?

Rick

---

### Post by Pablo_Escobar on 2005-12-02
Nope
> cat /etc/fstab

---

### Post by politicaldog on 2005-12-02
Ok, I'm new to this shell thing.

When I type that it says    bash: cat/etc/fstab: No such file or directory

richard@ubuntu:~$  this is the prompt I'm at

Rick

---

### Post by Pablo_Escobar on 2005-12-02
> cat /etc/fstab

There is a space after the cat :)

---

### Post by politicaldog on 2005-12-02
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
richard@ubuntu:~$


Guess I didn't type it right the first time

---

### Post by linbetwin on 2005-12-02
There is a space after "cat"

EDIT: sorry, too late!

---

### Post by Pablo_Escobar on 2005-12-02
1. Do You have 2 CD-ROMs ??
2. Input into terminal:
> ls /dev/cd*

---

### Post by politicaldog on 2005-12-02
Yes, One is a TDK RW and the other is just a cd reader.

richard@ubuntu:~$ ls /dev/cd*
ls: /dev/cd*: No such file or directory

---

### Post by Pablo_Escobar on 2005-12-02
Type in :
> dmesg |more
and look for the part which says about CD-ROMs (the interesting bit is hd*)

---

### Post by politicaldog on 2005-12-02
[4294667.296000] Linux version 2.6.12-10-386 (buildd@terranova) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Fri Nov 18 11:51:02 UTC 2005
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[4294667.296000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000e7400 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 0000000007ff0000 (usable)
[4294667.296000]  BIOS-e820: 0000000007ff0000 - 0000000007fffc00 (ACPI data)
[4294667.296000]  BIOS-e820: 0000000007fffc00 - 0000000008000000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 00000000ffc80000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 127MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 32752
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:1
[4294667.296000]   Normal zone: 28656 pages, LIFO batch:15
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:1
[4294667.296000] DMI 2.2 present.
[4294667.296000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6d70
[4294667.296000] ACPI: RSDT (v001 PTLTD    RSDT   0x0604000d  LTP 0x00000000) @
0x07ffc9c7
[4294667.296000] ACPI: FADT (v001 HP     Obiou    0x0604000d PTL  0x000f4240) @
0x07ffc9f3
[4294667.296000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x0604000d  LTP 0x00000001) @
0x07fffbd9
[4294667.296000] ACPI: DSDT (v001     HP       K2 0x0604000d MSFT 0x01000004) @
0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x408
[4294667.296000] Allocating PCI resources starting at 08000000 (gap: 08000000:f7c80000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash
[4294667.296000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[4294667.296000] mapped APIC to ffffd000 (01101000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 512 (order: 9, 8192 bytes)
[4294667.296000] Detected 666.700 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294668.240000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)[4294668.241000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[4294668.255000] Memory: 121348k/131008k available (1416k kernel code, 9068k reserved, 762k data, 224k init, 0k highmem)
[4294668.255000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294668.255000] Calibrating delay loop... 1318.91 BogoMIPS (lpj=659456)
[4294668.278000] Security Framework v1.0.0 initialized
[4294668.278000] SELinux:  Disabled at boot.
[4294668.278000] Mount-cache hash table entries: 512
[4294668.278000] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[4294668.278000] CPU: After vendor identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[4294668.278000] CPU: L1 I cache: 16K, L1 D cache: 16K
[4294668.278000] CPU: L2 cache: 256K
[4294668.278000] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[4294668.278000] CPU: Intel Pentium III (Coppermine) stepping 03
[4294668.278000] Enabling fast FPU save and restore... done.
[4294668.278000] Enabling unmasked SIMD FPU exception support... done.
[4294668.278000] Checking 'hlt' instruction... OK.
[4294668.282000] Checking for popad bug... OK.
[4294668.282000] checking if image is initramfs... it is
[4294669.476000] Freeing initrd memory: 5171k freed
[4294669.478000] ACPI: Looking for DSDT in initrd... not found!
[4294669.679000]  not found!
[4294669.693000] ACPI: setting ELCR to 0200 (from 0e00)
[4294669.696000] NET: Registered protocol family 16
[4294669.696000] EISA bus registered
[4294669.696000] ACPI: bus type pci registered
[4294669.696000] PCI: PCI BIOS revision 2.10 entry at 0xfd99d, last bus=2
[4294669.696000] PCI: Using configuration type 1
[4294669.696000] mtrr: v2.0 (20020519)
[4294669.696000] ACPI: Subsystem revision 20050729
[4294669.744000] ACPI: Interpreter enabled
[4294669.744000] ACPI: Using PIC for interrupt routing
[4294669.745000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294669.745000] PCI: Probing PCI hardware (bus 00)
[4294669.745000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294669.790000] Boot video device is 0000:01:00.0
[4294669.791000] PCI: Transparent bridge - 0000:00:1e.0
[4294669.792000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294669.792000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[4294669.794000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 14 15)[4294669.794000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 14 15)
*0, disabled.
[4294669.795000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 14 15)[4294669.795000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 *9 10 11 14 15)
[4294669.861000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.SLOT._PRT]
[4294669.863000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294669.863000] pnp: PnP ACPI init
[4294669.863000] PCI: setting IRQ 13 as level-triggered
[4294669.964000] pnp: PnP ACPI: found 14 devices
[4294669.965000] PnPBIOS: Disabled by ACPI PNP
[4294669.965000] PCI: Using ACPI for IRQ routing
[4294669.965000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294669.967000] pnp: 00:05: ioport range 0x400-0x44f could not be reserved
[4294669.967000] pnp: 00:05: ioport range 0x460-0x47f has been reserved
[4294669.967000] pnp: 00:05: ioport range 0x4d0-0x4d1 has been reserved
[4294669.967000] pnp: 00:05: ioport range 0x500-0x50f has been reserved
[4294669.967000] pnp: 00:05: ioport range 0x580-0x5af has been reserved
[4294669.968000] Simple Boot Flag value 0x79 read from CMOS RAM was invalid
[4294669.968000] Simple Boot Flag at 0x3b set to 0x1
[4294669.969000] audit: initializing netlink socket (disabled)
[4294669.969000] audit: initialized
[4294669.969000] VFS: Disk quotas dquot_6.5.1
[4294669.969000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294669.969000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294669.969000] devfs: boot_options: 0x0
[4294669.969000] Initializing Cryptographic API
[4294669.969000] isapnp: Scanning for PnP cards...
[4294670.068000] isapnp: Card 'U.S. Robotics 56K FAX INT'
[4294670.068000] isapnp: 1 Plug & Play card detected total
[4294670.127000] pnp: Device 00:08 activated.
[4294670.128000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PSM] at 0x60,0x64 irq 1,12
[4294670.140000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294670.141000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294670.141000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294670.142000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294670.143000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294670.149000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294670.149000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294670.151000] pnp: Device 01:01.00 activated.
[4294670.152000] ttyS2 at I/O 0x3e8 (irq = 5) is a 16550A
[4294670.152000] io scheduler noop registered
[4294670.152000] io scheduler anticipatory registered
[4294670.152000] io scheduler deadline registered
[4294670.152000] io scheduler cfq registered
[4294670.153000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294670.155000] EISA: Probing bus 0 at eisa.0
[4294670.155000] Cannot allocate resource for EISA slot 1
[4294670.155000] Cannot allocate resource for EISA slot 2
[4294670.155000] Cannot allocate resource for EISA slot 3
[4294670.155000] EISA: Detected 0 cards.
[4294670.155000] NET: Registered protocol family 2
[4294670.167000] IP: routing cache hash table of 512 buckets, 4Kbytes
[4294670.168000] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[4294670.168000] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
[4294670.169000] TCP: Hash tables configured (established 8192 bind 8192)
[4294670.169000] NET: Registered protocol family 8
[4294670.169000] NET: Registered protocol family 20
[4294670.169000] ACPI wakeup devices:
[4294670.169000]  KBC COMA COMB SLOT  USB
[4294670.169000] ACPI: (supports S0 S1 S4 S5)
[4294670.170000] Freeing unused kernel memory: 224k freed
[4294670.188000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294670.219000] vga16fb: initializing
[4294670.219000] vga16fb: mapped to 0xc00a0000
[4294670.282000] Console: switching to colour frame buffer device 80x30
[4294670.282000] fb0: VGA16 VGA frame buffer device
[4294671.452000] Capability LSM initialized
[4294671.487000] NET: Registered protocol family 1
[4294671.522000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294671.522000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294671.522000] ACPI: bus type ide registered
[4294671.535000] ICH: IDE controller at PCI slot 0000:00:1f.1
[4294671.535000] ICH: chipset revision 2
[4294671.535000] ICH: not 100% native mode: will probe irqs later
[4294671.535000]     ide0: BM-DMA at 0x1020-0x1027, BIOS settings: hda:pio, hdb:DMA
[4294671.536000] Probing IDE interface ide0...
[4294671.799000] hda: IBM-DTLA-307015, ATA DISK drive
[4294672.054000] hdb: Maxtor 91024U4, ATA DISK drive
[4294672.105000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294672.105000] Probing IDE interface ide1...
[4294672.618000] ide2: I/O resource 0x3EE-0x3EE not free.
[4294672.618000] ide2: ports already in use, skipping probe
[4294672.618000] Probing IDE interface ide3...
[4294673.131000] Probing IDE interface ide4...
[4294673.643000] Probing IDE interface ide5...
[4294674.165000] hda: max request size: 128KiB
[4294674.222000] hda: 29886400 sectors (15301 MB) w/1916KiB Cache, CHS=29649/16/63, UDMA(66)
[4294674.222000] hda: cache flushes not supported
[4294674.222000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
[4294674.298000] hdb: max request size: 128KiB
[4294674.299000] hdb: 19999728 sectors (10239 MB) w/2048KiB Cache, CHS=19841/16/63, UDMA(66)
[4294674.299000] hdb: cache flushes not supported
[4294674.299000]  /dev/ide/host0/bus0/target1/lun0:
[4294674.826000] Attempting manual resume
[4294674.826000] swsusp: Suspend partition has wrong signature?
[4294674.967000] usbcore: registered new driver usbfs
[4294674.967000] usbcore: registered new driver hub
[4294674.971000] USB Universal Host Controller Interface driver v2.2
[4294674.971000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
[4294674.971000] PCI: setting IRQ 9 as level-triggered
[4294674.971000] ACPI: PCI Interrupt 0000:00:1f.2[D] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[4294674.971000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[4294674.971000] uhci_hcd 0000:00:1f.2: Intel Corporation 82801AA USB
[4294675.033000] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[4294675.033000] uhci_hcd 0000:00:1f.2: irq 9, io base 0x00001000
[4294675.033000] hub 1-0:1.0: USB hub found
[4294675.033000] hub 1-0:1.0: 2 ports detected
[4294675.105000] ACPI: PCI Interrupt 0000:02:09.0[A] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[4294675.105000] 3c59x: Donald Becker and others. [www.scyld.com/network/vortex.html](www.scyld.com/network/vortex.html)
[4294675.105000] 0000:02:09.0: 3Com PCI 3c905C Tornado at 0x2000. Vers LK1.1.19
[4294677.779000] ACPI: CPU0 (power states: C1[C1])
[4294677.980000] Attempting manual resume
[4294677.980000] swsusp: Suspend partition has wrong signature?
[4294678.007000] kjournald starting.  Commit interval 5 seconds
[4294678.007000] EXT3-fs: mounted filesystem with ordered data mode.
[4294679.734000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294685.077000] Adding 369452k swap on /dev/hda5.  Priority:-1 extents:1
[4294685.434000] EXT3 FS on hda1, internal journal
[4294692.632000] parport: PnPBIOS parport detected.
[4294692.632000] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[4294692.727000] lp0: using parport0 (interrupt-driven).
[4294692.793000] mice: PS/2 mouse device common for all mice
[4294693.099000] logips2pp: Detected unknown logitech mouse model 0
[4294693.222000] input: ImPS/2 Logitech Wheel Mouse on isa0060/serio1
[4294694.285000] ts: Compaq touchscreen protocol output
[4294697.519000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294701.980000] Linux agpgart interface v0.101 (c) Dave Jones
[4294702.004000] agpgart: Detected an Intel i820 Chipset.
[4294702.024000] agpgart: AGP aperture is 64M @ 0xf8000000
[4294702.281000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294702.353000] shpchp: shpc_init : shpc_cap_offset == 0
[4294702.353000] shpchp: shpc_init : shpc_cap_offset == 0
[4294702.353000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294702.686000] hw_random hardware driver 1.0.0 loaded
[4294703.663000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[4294703.663000] PCI: setting IRQ 10 as level-triggered
[4294703.663000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[4294703.884000] gameport: CS46xx Gameport is pci0000:02:01.0/gameport0, speed 1420kHz
[4294706.389000] Real Time Clock Driver v1.12
[4294706.574000] input: PC Speaker
[4294707.207000] Floppy drive(s): fd0 is 1.44M
[4294707.221000] FDC 0 is a National Semiconductor PC87306
[4294709.835000] ACPI: PCI Interrupt 0000:02:09.0[A] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[4294709.869000] NET: Registered protocol family 17
[4294712.770000] NET: Registered protocol family 10
[4294712.770000] Disabled Privacy Extensions on device c02eb280(lo)
[4294712.771000] IPv6 over IPv4 tunneling driver
[4294714.951000] ACPI: Power Button (FF) [PWRF]
[4294714.951000] ACPI: Power Button (CM) [PWRB]
[4294715.272000] ibm_acpi: ec object not found
[4294723.305000] eth0: no IPv6 routers present
[4294729.744000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294729.744000] apm: overridden by ACPI.
[4294734.102000] Bluetooth: Core ver 2.7
[4294734.102000] NET: Registered protocol family 31
[4294734.102000] Bluetooth: HCI device and connection manager initialized
[4294734.102000] Bluetooth: HCI socket layer initialized
[4294734.210000] Bluetooth: L2CAP ver 2.7
[4294734.210000] Bluetooth: L2CAP socket layer initialized
[4294734.252000] Bluetooth: RFCOMM ver 1.5
[4294734.252000] Bluetooth: RFCOMM socket layer initialized
[4294734.252000] Bluetooth: RFCOMM TTY layer initialized

---

### Post by Pablo_Escobar on 2005-12-02
> [4294672.618000] ide2: I/O resource 0x3EE-0x3EE not free.
[4294672.618000] ide2: ports already in use, skipping probe

Here is something wrong, maybe Your bios settings :(
Sorry can't help You :(

---

### Post by politicaldog on 2005-12-02
Ok, I'll look in my BIOS Settings

Thanks
Rick

Pablo...yes I had something in the BIOS wrong. It was only looking at Primary's. I set it to both and well......IT WORKS

Thanks
Rick

---

