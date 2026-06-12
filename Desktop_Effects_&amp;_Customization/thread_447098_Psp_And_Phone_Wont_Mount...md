---
title: "Psp And Phone Wont Mount.."
date: 2007-05-17
forum: Desktop Effects &amp; Customization
---

### Post by zorro26 on 2007-05-17
HI GUYS, I AM NEW TO LINUX, WELL HAVE BEEN USING IT FOR FEW MONTHS, INSTALLED IT QUITE A FEW TIMES, PLAYED AROUND ALOT AND LEARNT ALOT. PROBLEM I AM HAVING IS I TRIED TO MOUNT MY PSP BUT IT WONT WORK, I USE TO MOUNT MY SAMSUNG I300 WHICH USES MASS STORAGE FORMULA USED TO MOUND FOR FEW MINS UNDER TFAT FOLDERS OR SOMETHING BUT THAT NOT HAPPENING NOW.

I SEARCHED UBUNTU, LINUX, PSP FORUMS AND GOOGLED ALOT. I FOLLWED AND DID LOADS QUITE  A FEW STUFF (I JUST COPY AND PASTE COMANDS IN TERMINAL WITH OUT KNOWING WHAT THEY MEAN).

like these

mount -t vfat /dev/sda /mnt/psp/
but i get this
mount: special device /dev/sda does not exist

CHANGED MY FSTAB FILES LOADS .. NOW IT LOOKS LIKE THIS

>  # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hda1
UUID=57a37a62-927c-4715-9cfb-ec1e5639812d / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5
UUID=f8f64f27-3e09-4dd8-8fdc-4968f1ddc584 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0


dmesg | tail

> [   47.423785] Bluetooth: Core ver 2.11
[   47.424090] NET: Registered protocol family 31
[   47.424092] Bluetooth: HCI device and connection manager initialized
[   47.424095] Bluetooth: HCI socket layer initialized
[   47.454319] Bluetooth: L2CAP ver 2.8
[   47.454322] Bluetooth: L2CAP socket layer initialized
[   47.518656] Bluetooth: RFCOMM socket layer initialized
[   47.518665] Bluetooth: RFCOMM TTY layer initialized
[   47.518667] Bluetooth: RFCOMM ver 1.8
[   50.524471] eth0: no IPv6 routers presen

CAN SOME ONE HELP ME TO GET UBUNTU RECOGNISE MY PSP. PLEASE/

---

### Post by christhemonkey on 2007-05-17
First off, please less of the caps!
(its like shouting over the internet)


Secondly, run this command:
```
dmesg | tail 
```
Then plug your PSP in, with it on (if it needs to be) and any sort of transfer mode enabled on it  (sorry i dont own a psp so am sort helping blind a little), 
plug in USB cable into both pc and psp, then run this command again:
```
dmesg | tail 
```

The "dmesg" part of the command shows the output of the kernel, the "|" pipes the output from that to "tail", which just displays the last few lines of it.

If the output of that command is exactly the same as it was before you plugged your psp in, then your psp is not playing along nicely...

Otherwise tell us the additional output from that command.

---

### Post by zorro26 on 2007-05-17
this is before i plugged psp in

> [   47.424090] NET: Registered protocol family 31
[   47.424092] Bluetooth: HCI device and connection manager initialized
[   47.424095] Bluetooth: HCI socket layer initialized
[   47.454319] Bluetooth: L2CAP ver 2.8
[   47.454322] Bluetooth: L2CAP socket layer initialized
[   47.518656] Bluetooth: RFCOMM socket layer initialized
[   47.518665] Bluetooth: RFCOMM TTY layer initialized
[   47.518667] Bluetooth: RFCOMM ver 1.8
[   50.524471] eth0: no IPv6 routers present
[ 1345.898016] Losing some ticks... checking if CPU frequency changed.


and this is after

> [   47.424090] NET: Registered protocol family 31
[   47.424092] Bluetooth: HCI device and connection manager initialized
[   47.424095] Bluetooth: HCI socket layer initialized
[   47.454319] Bluetooth: L2CAP ver 2.8
[   47.454322] Bluetooth: L2CAP socket layer initialized
[   47.518656] Bluetooth: RFCOMM socket layer initialized
[   47.518665] Bluetooth: RFCOMM TTY layer initialized
[   47.518667] Bluetooth: RFCOMM ver 1.8
[   50.524471] eth0: no IPv6 routers present
[ 1345.898016] Losing some ticks... checking if CPU frequency changed.


---

### Post by zorro26 on 2007-05-17
addtional output is as following

> [    0.000000] Linux version 2.6.20-15-generic (root@yellow) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 06:17:24 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] Command line: root=UUID=57a37a62-927c-4715-9cfb-ec1e5639812d ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ff10000 (usable)
[    0.000000]  BIOS-e820: 000000003ff10000 - 000000003ff20000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ff20000 - 0000000040000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 261904) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x00000000000fad60
[    0.000000] ACPI: RSDT (v001 A M I  OEMRSDT  0x10000507 MSFT 0x00000097) @ 0x000000003ff10000
[    0.000000] ACPI: FADT (v002 A M I  OEMFACP  0x10000507 MSFT 0x00000097) @ 0x000000003ff10200
[    0.000000] ACPI: MADT (v001 A M I  OEMAPIC  0x10000507 MSFT 0x00000097) @ 0x000000003ff10390
[    0.000000] ACPI: OEMB (v001 A M I  AMI_OEM  0x10000507 MSFT 0x00000097) @ 0x000000003ff20040
[    0.000000] ACPI: DSDT (v001  A0217 A0217001 0x00000001 INTL 0x02002026) @ 0x0000000000000000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] Number of nodes 1
[    0.000000] Node 0 MemBase 0000000000000000 Limit 000000003ff10000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 261904) 1 entries of 3200 used
[    0.000000] NUMA: Using 63 for the hash shift.
[    0.000000] Using node hash shift of 63
[    0.000000] Bootmem setup node 0 0000000000000000-000000003ff10000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   261904
[    0.000000] On node 0 totalpages: 261807
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1085 pages reserved
[    0.000000]   DMA zone: 2858 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3524 pages used for memmap
[    0.000000]   DMA32 zone: 254284 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Nosave address range: 000000000009f000 - 00000000000a0000
[    0.000000] Nosave address range: 00000000000a0000 - 00000000000e0000
[    0.000000] Nosave address range: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bf780000)
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] PERCPU: Allocating 34048 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 257142
[    0.000000] Kernel command line: root=UUID=57a37a62-927c-4715-9cfb-ec1e5639812d ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   12.649802] Console: colour VGA+ 80x25
[   12.650737] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   12.651370] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   12.651464] Checking aperture...
[   12.651468] CPU 0: aperture @ 8052000000 size 32 MB
[   12.651469] Aperture too small (32 MB)
[   12.657026] No AGP bridge found
[   12.670213] Memory: 1019564k/1047616k available (2217k kernel code, 27664k reserved, 1162k data, 304k init)
[   12.746668] Calibrating delay using timer specific routine.. 4402.49 BogoMIPS (lpj=8804987)
[   12.746727] Security Framework v1.0.0 initialized
[   12.746733] SELinux:  Disabled at boot.
[   12.746759] Mount-cache hash table entries: 256
[   12.746923] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   12.746926] CPU: L2 Cache: 1024K (64 bytes/line)
[   12.746928] CPU 0/0 -> Node 0
[   12.746951] SMP alternatives: switching to UP code
[   12.747341] Early unpacking initramfs... done
[   13.051397] ACPI: Core revision 20060707
[   13.051871] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   13.094116] Using local APIC timer interrupts.
[   13.139529] result 12500998
[   13.139531] Detected 12.500 MHz APIC timer.
[   13.142379] Brought up 1 CPUs
[   13.142405] time.c: Using 3.579545 MHz WALL PM GTOD PIT/TSC timer.
[   13.142407] time.c: Detected 2200.175 MHz processor.
[   13.142702] Time: 21:24:19  Date: 04/17/107
[   13.142740] NET: Registered protocol family 16
[   13.142824] ACPI: bus type pci registered
[   13.142831] PCI: Using configuration type 1
[   13.149242] ACPI: Interpreter enabled
[   13.149244] ACPI: Using IOAPIC for interrupt routing
[   13.150142] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   13.150146] PCI: Probing PCI hardware (bus 00)
[   13.150791] Boot video device is 0000:03:00.0
[   13.150969] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   13.169900] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[   13.170152] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[   13.171051] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 12 14 15)
[   13.171265] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 10 11 12 14 15)
[   13.171475] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 *11 12 14 15)
[   13.171684] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *10 11 12 14 15)
[   13.171947] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 7 10 11 12 14 15)
[   13.172156] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 *11 12 14 15)
[   13.172371] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 7 10 11 12 14 15)
[   13.172582] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 7 10 11 12 14 15)
[   13.172653] Linux Plug and Play Support v0.97 (c) Adam Belay
[   13.172660] pnp: PnP ACPI init
[   13.178535] pnp: PnP ACPI: found 14 devices
[   13.178581] PCI: Using ACPI for IRQ routing
[   13.178584] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   13.178650] NET: Registered protocol family 8
[   13.178651] NET: Registered protocol family 20
[   13.179450] pnp: 00:09: ioport range 0xc00-0xc0f has been reserved
[   13.179452] pnp: 00:09: ioport range 0xd00-0xd0f has been reserved
[   13.179455] pnp: 00:09: ioport range 0xa20-0xa2f has been reserved
[   13.179457] pnp: 00:09: ioport range 0xa30-0xa3f has been reserved
[   13.179695] PCI: Bridge: 0000:00:01.0
[   13.179698]   IO window: e000-efff
[   13.179702]   MEM window: dff00000-dfffffff
[   13.179705]   PREFETCH window: dc000000-deffffff
[   13.179708] PCI: Bridge: 0000:00:06.0
[   13.179710]   IO window: d000-dfff
[   13.179713]   MEM window: disabled.
[   13.179715]   PREFETCH window: disabled.
[   13.179718] PCI: Bridge: 0000:00:07.0
[   13.179720]   IO window: c000-cfff
[   13.179723]   MEM window: disabled.
[   13.179725]   PREFETCH window: disabled.
[   13.179740] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   13.179748] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   13.179756] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   13.179817] NET: Registered protocol family 2
[   13.206356] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   13.206670] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   13.208446] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   13.209328] TCP: Hash tables configured (established 131072 bind 65536)
[   13.209332] TCP reno registered
[   13.218410] checking if image is initramfs... it is
[   13.782324] Freeing initrd memory: 7303k freed
[   13.789470] audit: initializing netlink socket (disabled)
[   13.789483] audit(1179437059.096:1): initialized
[   13.789622] VFS: Disk quotas dquot_6.5.1
[   13.789640] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   13.789688] io scheduler noop registered
[   13.789690] io scheduler anticipatory registered
[   13.789692] io scheduler deadline registered
[   13.789702] io scheduler cfq registered (default)
[   13.861848] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   13.861873] assign_interrupt_mode Found MSI capability
[   13.861876] Allocate Port Service[0000:00:01.0:pcie00]
[   13.881916] Real Time Clock Driver v1.12ac
[   13.881957] Linux agpgart interface v0.102 (c) Dave Jones
[   13.881959] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   13.882069] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   13.882523] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   13.882681] mice: PS/2 mouse device common for all mice
[   13.883123] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   13.883343] input: Macintosh mouse button emulation as /class/input/input0
[   13.883370] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   13.883374] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   13.883571] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   13.883573] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   13.883730] serio: i8042 KBD port at 0x60,0x64 irq 1
[   13.883733] serio: i8042 AUX port at 0x60,0x64 irq 12
[   13.883897] TCP cubic registered
[   13.883905] NET: Registered protocol family 1
[   13.884017] ACPI: (supports S0 S1 S3 S4 S5)
[   13.884053]   Magic number: 7:872:449
[   13.884170] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   13.884277] Freeing unused kernel memory: 304k freed
[   13.902905] input: AT Translated Set 2 keyboard as /class/input/input1
[   15.049687] Capability LSM initialized
[   15.078227] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   15.580330] usbcore: registered new interface driver usbfs
[   15.580354] usbcore: registered new interface driver hub
[   15.580380] usbcore: registered new device driver usb
[   15.581102] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   15.581133] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 20
[   15.581145] ohci_hcd 0000:00:03.0: OHCI Host Controller
[   15.581300] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[   15.581315] ohci_hcd 0000:00:03.0: irq 20, io mem 0xdfeb8000
[   15.626845] Intel(R) PRO/1000 Network Driver - version 7.3.15-k2-NAPI
[   15.626849] Copyright (c) 1999-2006 Intel Corporation.
[   15.644585] usb usb1: configuration #1 chosen from 1 choice
[   15.644609] hub 1-0:1.0: USB hub found
[   15.644619] hub 1-0:1.0: 3 ports detected
[   15.697231] Floppy drive(s): fd0 is 1.44M
[   15.743609] FDC 0 is a post-1991 82077
[   15.752526] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 21
[   15.752543] ohci_hcd 0000:00:03.1: OHCI Host Controller
[   15.752658] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[   15.752674] ohci_hcd 0000:00:03.1: irq 21, io mem 0xdfeb9000
[   15.814000] usb usb2: configuration #1 chosen from 1 choice
[   15.814025] hub 2-0:1.0: USB hub found
[   15.814033] hub 2-0:1.0: 3 ports detected
[   15.919879] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 22 (level, low) -> IRQ 22
[   15.919894] ohci_hcd 0000:00:03.2: OHCI Host Controller
[   15.919916] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[   15.919929] ohci_hcd 0000:00:03.2: irq 22, io mem 0xdfeba000
[   15.977825] usb usb3: configuration #1 chosen from 1 choice
[   15.977847] hub 3-0:1.0: USB hub found
[   15.977854] hub 3-0:1.0: 2 ports detected
[   16.059670] usb 1-2: new low speed USB device using ohci_hcd and address 2
[   16.083968] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 23
[   16.083981] ehci_hcd 0000:00:03.3: EHCI Host Controller
[   16.084005] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4
[   16.084038] PCI: cache line size of 64 is not supported by device 0000:00:03.3
[   16.084047] ehci_hcd 0000:00:03.3: irq 23, io mem 0xdfebb000
[   16.084054] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   16.084109] usb usb4: configuration #1 chosen from 1 choice
[   16.084129] hub 4-0:1.0: USB hub found
[   16.084134] hub 4-0:1.0: 8 ports detected
[   16.197023] SCSI subsystem initialized
[   16.201917] SIS5513: IDE controller at PCI slot 0000:00:02.5
[   16.201939] SIS5513: chipset revision 1
[   16.201940] SIS5513: not 100% native mode: will probe irqs later
[   16.201946] SIS5513: SiS965 ATA 133 (2nd gen) controller
[   16.201956]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:DMA
[   16.201966]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:DMA
[   16.201973] Probing IDE interface ide0...
[   16.211196] libata version 2.20 loaded.
[   16.491435] hda: Maxtor 6L160P0, ATA DISK drive
[   16.767021] usb 1-2: new low speed USB device using ohci_hcd and address 3
[   16.971325] usb 1-2: configuration #1 chosen from 1 choice
[   16.987141] usbcore: registered new interface driver hiddev
[   16.992471] input: Wireless Mouse Wireless Mouse as /class/input/input2
[   16.992585] input: USB HID v1.10 Mouse [Wireless Mouse Wireless Mouse] on usb-0000:00:03.0-2
[   16.992597] usbcore: registered new interface driver usbhid
[   16.992599] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   17.164205] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   17.185529] Probing IDE interface ide1...
[   17.922126] hdc: SONY DVD RW DW-G120A, ATAPI CD/DVD-ROM drive
[   18.593638] ide1 at 0x170-0x177,0x376 on irq 15
[   18.610112] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 19
[   18.862521] e1000: 0000:00:0b.0: e1000_probe: (PCI:33MHz:32-bit) 00:15:f2:4f:e2:10
[   18.901910] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   18.903996] sata_sis 0000:00:05.0: version 0.7
[   18.904016] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 17 (level, low) -> IRQ 17
[   18.904029] sata_sis 0000:00:05.0: Detected SiS 182/965L chipset
[   18.904086] ata1: SATA max UDMA/133 cmd 0x000000000001b400 ctl 0x000000000001b002 bmdma 0x000000000001a000 irq 17
[   18.904112] ata2: SATA max UDMA/133 cmd 0x000000000001a800 ctl 0x000000000001a402 bmdma 0x000000000001a008 irq 17
[   18.904125] scsi0 : sata_sis
[   18.910597] hda: max request size: 512KiB
[   18.918493] hda: 320173056 sectors (163928 MB) w/8192KiB Cache, CHS=19929/255/63, UDMA(133)
[   18.920060] hda: cache flushes supported
[   18.920101]  hda: hda1 hda2 < hda5 >
[   18.969905] hdc: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   18.969912] Uniform CD-ROM driver Revision: 3.20
[   19.117914] Attempting manual resume
[   19.117917] swsusp: Resume From Partition 3:5
[   19.117919] PM: Checking swsusp image.
[   19.118022] PM: Resume from disk failed.
[   19.145544] kjournald starting.  Commit interval 5 seconds
[   19.145554] EXT3-fs: mounted filesystem with ordered data mode.
[   21.111056] ata1: SATA link down (SStatus 1 SControl 300)
[   21.121634] ATA: abnormal status 0x7F on port 0x000000000001b407
[   21.121657] scsi1 : sata_sis
[   23.329027] ata2: SATA link down (SStatus 1 SControl 300)
[   23.339605] ATA: abnormal status 0x7F on port 0x000000000001a807
[   26.286676] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex
[   27.880595] NET: Registered protocol family 17
[   28.050411] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   28.054908] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   28.448903] input: PC Speaker as /class/input/input3
[   28.718031] parport: PnPBIOS parport detected.
[   28.718074] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   28.841631] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 18
[   29.163673] intel8x0_measure_ac97_clock: measured 55807 usecs
[   29.163677] intel8x0: clocking to 48000
[   29.306463] fuse init (API version 7.8)
[   29.369355] lp0: using parport0 (interrupt-driven).
[   29.412440] Adding 3004112k swap on /dev/disk/by-uuid/f8f64f27-3e09-4dd8-8fdc-4968f1ddc584.  Priority:-1 extents:1 across:3004112k
[   29.534913] EXT3 FS on hda1, internal journal
[   29.898668] NET: Registered protocol family 10
[   29.898752] lo: Disabled Privacy Extensions
[   37.133933] Using specific hotkey driver
[   37.149452] No dock devices found.
[   37.179764] input: Power Button (FF) as /class/input/input4
[   37.183322] ACPI: Power Button (FF) [PWRF]
[   37.206304] input: Power Button (CM) as /class/input/input5
[   37.209842] ACPI: Power Button (CM) [PWRB]
[   37.308496] ibm_acpi: ec object not found
[   37.348897] pcc_acpi: loading...
[   37.570867] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3700+ processors (version 2.00.00)
[   37.570920] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x6
[   37.570923] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0x8
[   37.570925] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xa
[   37.570927] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[   40.877099] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   40.882827] [fglrx] Maximum main memory to use for locked dma buffers: 921 MBytes.
[   40.883118] [fglrx] module loaded - fglrx 8.34.8 [Feb 20 2007] on minor 0
[   41.167680] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   41.801519] ppdev: user-space parallel port driver
[   44.524593] [fglrx] total      GART = 130023424
[   44.524599] [fglrx] free       GART = 114032640
[   44.524602] [fglrx] max single GART = 114032640
[   44.524604] [fglrx] total      LFB  = 33423360
[   44.524605] [fglrx] free       LFB  = 21884928
[   44.524607] [fglrx] max single LFB  = 21884928
[   44.524609] [fglrx] total      Inv  = 0
[   44.524610] [fglrx] free       Inv  = 0
[   44.524611] [fglrx] max single Inv  = 0
[   44.524613] [fglrx] total      TIM  = 0
[   47.423785] Bluetooth: Core ver 2.11
[   47.424090] NET: Registered protocol family 31
[   47.424092] Bluetooth: HCI device and connection manager initialized
[   47.424095] Bluetooth: HCI socket layer initialized
[   47.454319] Bluetooth: L2CAP ver 2.8
[   47.454322] Bluetooth: L2CAP socket layer initialized
[   47.518656] Bluetooth: RFCOMM socket layer initialized
[   47.518665] Bluetooth: RFCOMM TTY layer initialized
[   47.518667] Bluetooth: RFCOMM ver 1.8
[   50.524471] eth0: no IPv6 routers present
[ 1345.898016] Losing some ticks... checking if CPU frequency changed.

---

### Post by zorro26 on 2007-05-18
can anyone help me pls?

---

### Post by christhemonkey on 2007-05-19
Are you sure your psp is plugged in properly?

Some extra lines should appear on the end if it is...

---

### Post by HeyBudItsSteve on 2007-07-08
After you plug your PSP in did you go to Settings -> USB Connections? I have run a couple different versions of Ubuntu and it always recognizes my PSP. And sorry, i have no idea about your phone.

---

### Post by alex_anthony on 2007-07-08
output of sudo fdisk -l please
l is a lower case L

---

