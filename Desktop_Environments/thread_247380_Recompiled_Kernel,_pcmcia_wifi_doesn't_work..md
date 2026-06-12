---
title: "Recompiled Kernel, pcmcia wifi doesn't work."
date: 2006-08-30
forum: Desktop Environments
---

### Post by wylde342 on 2006-08-30
I just followed the "HOW TO" here, [http://ubuntuforums.org/showthread.php?t=157560](http://ubuntuforums.org/showthread.php?t=157560)

My PCMCIA wireles card is a D-Link w/ the Atheros chipset.  In other words, I just plugged it in and didn't have to do anything.  I used the exact same config for the new kernel as the one which comes with the install cd.  When I reboot into the new kernel, I can't get the wireless card to work.

Any ideas?  It's not using the ndiswrapper I dont think as Ubuntu recognized it w/o me loading anything.

---

### Post by tedrogers on 2006-09-01
Hi,

I have exactly the same issue with my WPC54G version 3 on my IBM T22. I did a fresh install (6.06), updated fully, followed all the instructions and all I get it the 'connection attempt' feedback (swirling 2 blue dots thing) and no wireless connection.

I have no encryption or anything complicated just yet, such as MAC Address filtering. I am broadcasting my ESSID and that's it...nothing else.

Hopefully all of the following results/info can help someone isolate the problem(s). Some of it (like dmesg) means very little to me. Anyway, here we go.

Performing a wireless scan seems to work fine. Well at least the WPC54G v3 card is able to see my router wirelessly because it determined my ESSID correctly.

sudo iwlist wlan0 scan:

wlan0     Scan completed :
          Cell 01 - Address: **:**:**:**:**:**
                    ESSID:"**SECRET**"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:0/100  Signal level:-43 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

The weird thing here for me is that the MAC Address listed in the above results (although I have ghosted it out with *'s) - in reality this differs from the MAC Address printed on the back of the card?!?!

iwconfig (for wlan0):

IEEE 802.11g  ESSID:off/any
Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
Bit Rate:54 Mb/s   Tx-Power:25 dBm
RTS thr:2347 B   Fragment thr:2346 B
Power Management:off
Link Quality:0  Signal level:0  Noise level:0
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0   Missed beacon:0

dmesg (this is a long one, MAC address also ghosted over, which funnily enough was accurate using dmesg):

[17179569.184000] Linux version 2.6.15-26-686 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Thu Aug 3 03:13:28 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000000fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000000fff0000 - 000000000fffec00 (ACPI data)
[17179569.184000]  BIOS-e820: 000000000fffec00 - 0000000010000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 255MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 65520
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 61424 pages, LIFO batch:15
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f7160
[17179569.184000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x0fff4d07
[17179569.184000] ACPI: FADT (v001 IBM    TP-T21   0x06040000  0x00000000) @ 0x0fffeb65
[17179569.184000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x0fffebd9
[17179569.184000] ACPI: DSDT (v001 IBM    TP-T21   0x06040000 MSFT 0x0100000c) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 10000000:eff80000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (01282000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[17179569.184000] Detected 796.679 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.656000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.660000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179569.688000] Memory: 248168k/262080k available (2110k kernel code, 13268k reserved, 595k data, 332k init, 0k highmem)
[17179569.688000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.768000] Calibrating delay using timer specific routine.. 1594.67 BogoMIPS (lpj=3189356)
[17179569.768000] Security Framework v1.0.0 initialized
[17179569.768000] SELinux:  Disabled at boot.
[17179569.768000] Mount-cache hash table entries: 512
[17179569.768000] CPU: After generic identify, caps: 0387f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179569.768000] CPU: After vendor identify, caps: 0387f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179569.768000] CPU: L1 I cache: 16K, L1 D cache: 16K
[17179569.768000] CPU: L2 cache: 256K
[17179569.768000] CPU serial number disabled.
[17179569.768000] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[17179569.768000] mtrr: v2.0 (20020519)
[17179569.768000] Enabling fast FPU save and restore... done.
[17179569.768000] Enabling unmasked SIMD FPU exception support... done.
[17179569.768000] Checking 'hlt' instruction... OK.
[17179569.784000] SMP alternatives: switching to UP code
[17179569.784000] checking if image is initramfs... it is
[17179571.152000] Freeing initrd memory: 6809k freed
[17179571.192000] ACPI: Looking for DSDT ... not found!
[17179571.200000] ACPI: setting ELCR to 0200 (from 0800)
[17179571.240000] CPU0: Intel Pentium III (Coppermine) stepping 06
[17179571.240000] SMP motherboard not detected.
[17179571.240000] Local APIC not detected. Using dummy APIC emulation.
[17179571.240000] Brought up 1 CPUs
[17179571.244000] NET: Registered protocol family 16
[17179571.244000] EISA bus registered
[17179571.244000] ACPI: bus type pci registered
[17179571.244000] PCI: PCI BIOS revision 2.10 entry at 0xfd94f, last bus=7
[17179571.244000] PCI: Using configuration type 1
[17179571.244000] ACPI: Subsystem revision 20051216
[17179571.532000] ACPI: Interpreter enabled
[17179571.532000] ACPI: Using PIC for interrupt routing
[17179571.536000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[17179571.536000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[17179571.540000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[17179571.540000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[17179571.540000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179571.540000] PCI: Probing PCI hardware (bus 00)
[17179571.540000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179571.652000] PCI quirk: region 1000-103f claimed by PIIX4 ACPI
[17179571.652000] PCI quirk: region 1040-104f claimed by PIIX4 SMB
[17179571.652000] PIIX4 devres C PIO at 15e8-15ef
[17179571.652000] PIIX4 devres I PIO at 03f0-03f7
[17179571.652000] PIIX4 devres J PIO at 002e-002f
[17179571.652000] Boot video device is 0000:01:00.0
[17179571.652000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179571.876000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[17179571.876000] ACPI: Power Resource [PSER] (on)
[17179571.880000] ACPI: Power Resource [PSIO] (on)
[17179571.880000] ACPI: Embedded Controller [EC] (gpe 9) interrupt mode.
[17179571.884000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179571.884000] pnp: PnP ACPI init
[17179571.996000] pnp: PnP ACPI: found 15 devices
[17179571.996000] PnPBIOS: Disabled by ACPI PNP
[17179571.996000] PCI: Using ACPI for IRQ routing
[17179571.996000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179572.004000] pnp: 00:01: ioport range 0x1000-0x103f could not be reserved
[17179572.004000] pnp: 00:01: ioport range 0x1040-0x104f has been reserved
[17179572.004000] pnp: 00:01: ioport range 0xfe00-0xfe0f has been reserved
[17179572.004000] pnp: 00:08: ioport range 0x15e0-0x15ef has been reserved
[17179572.004000] PCI: Bridge: 0000:00:01.0
[17179572.004000]   IO window: disabled.
[17179572.004000]   MEM window: f0000000-f7ffffff
[17179572.004000]   PREFETCH window: 28000000-280fffff
[17179572.004000] PCI: Bus 2, cardbus bridge: 0000:00:02.0
[17179572.004000]   IO window: 00001400-000014ff
[17179572.004000]   IO window: 00001c00-00001cff
[17179572.004000]   PREFETCH window: 20000000-21ffffff
[17179572.004000]   MEM window: 22000000-23ffffff
[17179572.004000] PCI: Bus 6, cardbus bridge: 0000:00:02.1
[17179572.004000]   IO window: 00002000-000020ff
[17179572.004000]   IO window: 00002400-000024ff
[17179572.004000]   PREFETCH window: 24000000-25ffffff
[17179572.004000]   MEM window: 26000000-27ffffff
[17179572.004000] **** SET: Misaligned resource pointer: cfe2ce62 Type 07 Len 0
[17179572.004000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[17179572.004000] PCI: setting IRQ 11 as level-triggered
[17179572.004000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179572.008000] **** SET: Misaligned resource pointer: cfe2ce62 Type 07 Len 0
[17179572.008000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[17179572.008000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[17179572.008000] Simple Boot Flag at 0x35 set to 0x1
[17179572.008000] audit: initializing netlink socket (disabled)
[17179572.008000] audit(1157126691.004:1): initialized
[17179572.008000] VFS: Disk quotas dquot_6.5.1
[17179572.008000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179572.008000] Initializing Cryptographic API
[17179572.008000] io scheduler noop registered
[17179572.008000] io scheduler anticipatory registered
[17179572.008000] io scheduler deadline registered
[17179572.008000] io scheduler cfq registered
[17179572.008000] Limiting direct PCI/PCI transfers.
[17179572.008000] isapnp: Scanning for PnP cards...
[17179572.364000] isapnp: No Plug & Play device found
[17179572.408000] Real Time Clock Driver v1.12
[17179572.408000] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[17179572.420000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179572.420000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179572.420000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179572.420000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.420000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a NS16550A
[17179572.428000] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.428000] **** SET: Misaligned resource pointer: ceb16482 Type 07 Len 0
[17179572.428000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[17179572.428000] ACPI: PCI Interrupt 0000:00:03.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179572.432000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179572.432000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179572.432000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179572.432000] mice: PS/2 mouse device common for all mice
[17179572.436000] EISA: Probing bus 0 at eisa.0
[17179572.436000] Cannot allocate resource for EISA slot 1
[17179572.436000] Cannot allocate resource for EISA slot 2
[17179572.436000] EISA: Detected 0 cards.
[17179572.436000] NET: Registered protocol family 2
[17179572.456000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.476000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179572.476000] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[17179572.476000] TCP bind hash table entries: 16384 (order: 5, 196608 bytes)
[17179572.476000] TCP: Hash tables configured (established 16384 bind 16384)
[17179572.476000] TCP reno registered
[17179572.476000] TCP bic registered
[17179572.476000] NET: Registered protocol family 1
[17179572.476000] NET: Registered protocol family 8
[17179572.476000] NET: Registered protocol family 20
[17179572.476000] Using IPI No-Shortcut mode
[17179572.476000] ACPI wakeup devices:
[17179572.476000]  LID SLPB PCI0  USB UART
[17179572.476000] ACPI: (supports S0 S1 S3 S4 S5)
[17179572.476000] Freeing unused kernel memory: 332k freed
[17179572.612000] vga16fb: initializing
[17179572.612000] vga16fb: mapped to 0xc00a0000
[17179572.740000] Console: switching to colour frame buffer device 80x25
[17179572.740000] fb0: VGA16 VGA frame buffer device
[17179573.772000] Capability LSM initialized
[17179573.944000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179573.944000] ACPI: Processor [CPU] (supports 8 throttling states)
[17179573.948000] ACPI: Thermal Zone [THM0] (57 C)
[17179575.336000] PIIX4: IDE controller at PCI slot 0000:00:07.1
[17179575.336000] PIIX4: chipset revision 1
[17179575.336000] PIIX4: not 100% native mode: will probe irqs later
[17179575.336000]     ide0: BM-DMA at 0x1850-0x1857, BIOS settings: hda:DMA, hdb:pio
[17179575.336000]     ide1: BM-DMA at 0x1858-0x185f, BIOS settings: hdc:DMA, hdd:pio
[17179575.336000] Probing IDE interface ide0...
[17179575.628000] hda: IBM-DJSA-220, ATA DISK drive
[17179576.300000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179576.348000] Probing IDE interface ide1...
[17179577.084000] hdc: HITACHI DVD-ROM GD-S200, ATAPI CD/DVD-ROM drive
[17179577.756000] ide1 at 0x170-0x177,0x376 on irq 15
[17179577.776000] hda: max request size: 128KiB
[17179577.796000] hda: 39070080 sectors (20003 MB) w/1874KiB Cache, CHS=41344/15/63, UDMA(33)
[17179577.796000] hda: cache flushes not supported
[17179577.796000]  hda: hda1 hda2 < hda5 >
[17179577.860000] hdc: ATAPI 24X DVD-ROM drive, 512kB Cache, UDMA(33)
[17179577.860000] Uniform CD-ROM driver Revision: 3.20
[17179578.216000] usbcore: registered new driver usbfs
[17179578.220000] usbcore: registered new driver hub
[17179578.224000] USB Universal Host Controller Interface driver v2.3
[17179578.224000] **** SET: Misaligned resource pointer: ceb6e9e2 Type 07 Len 0
[17179578.228000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[17179578.228000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179578.228000] uhci_hcd 0000:00:07.2: UHCI Host Controller
[17179578.228000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[17179578.228000] uhci_hcd 0000:00:07.2: irq 11, io base 0x00001860
[17179578.228000] hub 1-0:1.0: USB hub found
[17179578.228000] hub 1-0:1.0: 2 ports detected
[17179578.452000] Attempting manual resume
[17179578.572000] usb 1-1: new low speed USB device using uhci_hcd and address 2
[17179578.584000] EXT3-fs: mounted filesystem with ordered data mode.
[17179578.604000] kjournald starting.  Commit interval 5 seconds
[17179597.520000] Linux agpgart interface v0.101 (c) Dave Jones
[17179597.548000] agpgart: Detected an Intel 440BX Chipset.
[17179597.552000] agpgart: AGP aperture is 64M @ 0xf8000000
[17179597.616000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179597.628000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179599.048000] input: PC Speaker as /class/input/input1
[17179599.140000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179599.140000] Yenta: CardBus bridge found at 0000:00:02.0 [1014:0130]
[17179599.140000] Yenta: Using INTVAL to route CSC interrupts to PCI
[17179599.140000] Yenta: Routing CardBus interrupts to PCI
[17179599.140000] Yenta TI: socket 0000:00:02.0, mfunc 0x00001000, devctl 0x66
[17179599.428000] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[17179599.428000] Socket status: 30000020
[17179599.432000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[17179599.432000] Yenta: CardBus bridge found at 0000:00:02.1 [1014:0130]
[17179599.432000] Yenta: Using INTVAL to route CSC interrupts to PCI
[17179599.432000] Yenta: Routing CardBus interrupts to PCI
[17179599.432000] Yenta TI: socket 0000:00:02.1, mfunc 0x00001000, devctl 0x66
[17179599.664000] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[17179599.664000] Socket status: 30000006
[17179599.664000] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179599.676000] e100: Intel(R) PRO/100 Network Driver, 3.4.14-k4-NAPI
[17179599.676000] e100: Copyright(c) 1999-2005 Intel Corporation
[17179599.676000] ACPI: PCI Interrupt 0000:00:03.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179599.804000] e100: eth0: e100_probe: addr 0xe8120000, irq 11, MAC addr 00:10:A4:8B:17:19
[17179600.080000] pccard: CardBus card inserted into slot 0
[17179600.100000] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[17179600.140000] parport: PnPBIOS parport detected.
[17179600.140000] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[17179600.144000] input: TPPS/2 IBM TrackPoint as /class/input/input2
[17179600.184000] Floppy drive(s): fd0 is 1.44M
[17179600.228000] gameport: CS46xx Gameport is pci0000:00:05.0/gameport0, speed 1807kHz
[17179600.232000] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[17179600.232000] piix4_smbus 0000:00:07.3: IBM Laptop detected; this module may corrupt your serial eeprom! Refusing to load module!
[17179600.232000] piix4_smbus: probe of 0000:00:07.3 failed with error -1
[17179600.256000] FDC 0 is a National Semiconductor PC87306
[17179600.680000] irda_init()
[17179600.680000] NET: Registered protocol family 23
[17179600.764000] usbcore: registered new driver hiddev
[17179600.780000] input: ARROW STRONG USB Mouse as /class/input/input3
[17179600.784000] input: USB HID v1.00 Mouse [ARROW STRONG USB Mouse] on usb-0000:00:07.2-1
[17179600.784000] usbcore: registered new driver usbhid
[17179600.784000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179600.804000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 3.
[17179600.804000] nsc-ircc, chip->init
[17179600.804000] nsc-ircc, Found chip at base=0x02e
[17179600.804000] nsc-ircc, driver loaded (Dag Brattli)
[17179600.804000] nsc_ircc_open(), can't get iobase of 0x2f8
[17179600.804000] nsc-ircc, Found chip at base=0x02e
[17179600.804000] nsc-ircc, driver loaded (Dag Brattli)
[17179600.804000] nsc_ircc_open(), can't get iobase of 0x2f8
[17179600.808000] pnp: Device 00:0d disabled.
[17179600.816000] cs: IO port probe 0x100-0x3af: clean.
[17179600.816000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179600.816000] cs: IO port probe 0x820-0x8ff: clean.
[17179600.816000] cs: IO port probe 0xc00-0xcf7: clean.
[17179600.820000] cs: IO port probe 0xa00-0xaff: clean.
[17179600.820000] cs: IO port probe 0x100-0x3af: clean.
[17179600.820000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179600.820000] cs: IO port probe 0x820-0x8ff: clean.
[17179600.820000] cs: IO port probe 0xc00-0xcf7: clean.
[17179600.820000] cs: IO port probe 0xa00-0xaff: clean.
[17179600.952000] ts: Compaq touchscreen protocol output
[17179602.168000] lp0: using parport0 (interrupt-driven).
[17179602.280000] ndiswrapper version 1.8 loaded (preempt=yes,smp=yes)
[17179602.400000] ndiswrapper: driver lsbcmnds (The Linksys Group, Inc.,02/14/2005, 3.90.36.0) loaded
[17179602.400000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
[17179602.400000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179602.400000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[17179602.412000] ndiswrapper: using irq 11
[17179602.784000] NET: Registered protocol family 17
[17179603.560000] wlan0: vendor: ''
[17179603.560000] wlan0: ndiswrapper ethernet device 00:14:bf:b0:3a:c5 using driver lsbcmnds, 14E4:4318.5.conf
[17179603.560000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[17179603.700000] Adding 746980k swap on /dev/hda5.  Priority:-1 extents:1 across:746980k
[17179603.876000] EXT3 FS on hda1, internal journal
[17179604.336000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179604.336000] md: bitmap version 4.39
[17179605.304000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179609.044000] ACPI: AC Adapter [AC] (on-line)
[17179609.056000] ACPI: Battery Slot [BAT0] (battery present)
[17179609.256000] ACPI: Power Button (FF) [PWRF]
[17179609.256000] ACPI: Lid Switch [LID]
[17179609.256000] ACPI: Sleep Button (CM) [SLPB]
[17179609.616000] ibm_acpi: IBM ThinkPad ACPI Extras v0.12a
[17179609.616000] ibm_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
[17179609.616000] ibm_acpi: dock device not present
[17179609.780000] pcc_acpi: loading...
[17179610.008000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[17179619.040000] [drm] Initialized drm 1.0.1 20051102
[17179619.096000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179619.096000] [drm] Initialized savage 2.4.1 20050313 on minor 0
[17179619.100000] mtrr: base(0xf2000000) is not aligned on a size(0x5000000) boundary
[17179621.476000] IBM machine detected. Enabling interrupts during APM calls.
[17179621.480000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179621.480000] apm: overridden by ACPI.
[17179624.828000] ttyS1: LSR safety check engaged!
[17179629.380000] Non-volatile memory driver v1.2
[17179629.528000] input: /usr/sbin/thinkpad-keys as /class/input/input4
[17179633.304000] Bluetooth: Core ver 2.8
[17179633.304000] NET: Registered protocol family 31
[17179633.304000] Bluetooth: HCI device and connection manager initialized
[17179633.304000] Bluetooth: HCI socket layer initialized
[17179633.332000] Bluetooth: L2CAP ver 2.8
[17179633.332000] Bluetooth: L2CAP socket layer initialized
[17179633.364000] Bluetooth: RFCOMM socket layer initialized
[17179633.364000] Bluetooth: RFCOMM TTY layer initialized
[17179633.364000] Bluetooth: RFCOMM ver 1.7
[17179641.656000] NET: Registered protocol family 10
[17179641.656000] lo: Disabled Privacy Extensions
[17179641.656000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179641.660000] IPv6 over IPv4 tunneling driver
[17179648.572000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17179649.368000] ISO 9660 Extensions: RRIP_1991A
[17179651.884000] wlan0: no IPv6 routers present
[17179800.084000] wlan0: no IPv6 routers present
[17180127.088000] wlan0: no IPv6 routers present
[17180171.204000] wlan0: no IPv6 routers present
[17180243.680000] wlan0: no IPv6 routers present
[17180295.312000] pccard: card ejected from slot 0
[17180295.348000] ndiswrapper: device wlan0 removed
[17180295.372000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[17180316.960000] pccard: CardBus card inserted into slot 0
[17180317.004000] ndiswrapper: driver lsbcmnds (The Linksys Group, Inc.,02/14/2005, 3.90.36.0) loaded
[17180317.004000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
[17180317.004000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17180317.004000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[17180317.016000] ndiswrapper: using irq 11
[17180318.280000] wlan0: vendor: ''
[17180318.280000] wlan0: ndiswrapper ethernet device **:**:**:**:**:** using driver lsbcmnds, 14E4:4318.5.conf
[17180318.280000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[17180329.304000] wlan0: no IPv6 routers present
[17180445.312000] wlan0: no IPv6 routers present
[17180493.788000] wlan0: no IPv6 routers present
[17180571.948000] wlan0: no IPv6 routers present
[17180644.236000] wlan0: no IPv6 routers present
[17180821.916000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[17180821.916000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[17180838.344000] eth0: no IPv6 routers present
[17181211.916000] e100: eth0: e100_watchdog: link down
[17181326.668000] wlan0: no IPv6 routers present
[17181389.376000] wlan0: no IPv6 routers present

ndiswrapper -l:

Installed ndis drivers:
lsbcmnds                driver present, hardware present

I hope someone out there can help me out. I've been trying to get this working for weeks now, but I have to admit that I never got this far before and got the Network Manager to display the Wireless Network options below Wired Network.

One final thing, I also went into Network Settings and configured  wlan0. By configured I mean that I Enabled the device in Properties and then Activated it on the main screen. This made no difference at all, but at least now it is staying active because before it used to Deativate itself.

Well, any help is appreciated.

Thanks.

---

