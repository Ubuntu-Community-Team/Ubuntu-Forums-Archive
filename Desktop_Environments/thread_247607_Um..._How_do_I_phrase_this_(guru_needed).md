---
title: "Um... How do I phrase this? (guru needed)"
date: 2006-08-30
forum: Desktop Environments
---

### Post by CyberCod on 2006-08-30
I'm having a problem so strange that i do not know what to put in google.

I would normally research these things myself before asking for help, but I'm stumped as to how to even look.](*,) 

The PC in question is:

Celeron-D 2.13Ghz
512Mb RAM
ATI Radeon 7000VE PCI
onboard sound and ethernet

Fresh install of Ubuntu, using 686 kernel.


Description of querk:
Took almost an hour to install (I checked cd for errors).  Boots VERY slowly.  Runs one single application fine, but slows to a crawl when multitasking.  For instance, installing a package with synaptic and browsing a web page at the same time.  A veritable crawl, I say.  And while it is doing this, the processor usage is not high.  Actually quite low, in fact.

So far, I've checked the hard drive dma mode.  Its using DMA6, so that isn't it.  And its far from full.  Plenty of free space.

I tried to check into whether the processor is configured right, and found that it says "unknown processor" in the Device Manager.  But I don't know what i can do about this.  I upraded to 686 kernel in the hopes of fixing this, but no luck there.

Hardware accelleration is working fine.

Sound is fine.

RAM should be plenty, though the system monitor panel applet shows that its in use 66% as cache, and 33% for programs.  Being the great big whopping troll that I am, I don't know whether that is good or not.

I appreciate your time reading this.  Any and all help is appreciated.  

Thanx

---

### Post by mlind on 2006-08-30
I see you have tried with 386 kernel before which would have been my first suggestion. Problem like this sounds like hardware / kernel related.
Do you have any exotic hardware attached? Does **dmesg** (command) or /var/log/messages contain anything odd? What gfx driver you use for ati?
Does slowness occur if you shutdown Xserver and multitask applications from tty ?

You can try viewing existing bug reports against Dapper kernel, and see if you find anything similar to your issue
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bugs](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bugs)

---

### Post by Shay Stephens on 2006-08-30
What happens when you check the speed of the drive?

```
sudo hdparm -Tt /dev/hda4
```
substitute hda4 for your actual drive

Just for comparison, this is the result I got with my drive a while back
 Timing cached reads:   564 MB in  2.01 seconds = 280.64 MB/sec
 Timing buffered disk reads:   68 MB in  3.07 seconds =  22.17 MB/sec

And this is what I am getting now
 Timing cached reads:   2040 MB in  2.00 seconds = 1019.94 MB/sec
 Timing buffered disk reads:  104 MB in  3.01 seconds =  34.57 MB/sec

I don't know what I did to get the cached read value so high.  It might be a result of the 686 kernel, I did change that a while ago, perhaps after my first results were obtained.  Maybe I am using a different drive too, hmm I will have to look into that.

---

### Post by CyberCod on 2006-08-31
> **mlind said:**
> 
Do you have any exotic hardware attached? 

Does **dmesg** (command) or /var/log/messages contain anything odd? 

What gfx driver you use for ati?


Does slowness occur if you shutdown Xserver and multitask applications from tty ?



No exotic hardware.

Using default drivers installed by ubuntu for ati.  
```

Driver		"ati"

```



dmesg output:  (keep in mind I don't know what I'm looking for in there)
```

[17179569.184000] Linux version 2.6.15-26-686 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Thu Aug 3 03:13:28 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001fef0000 (usable)
[17179569.184000]  BIOS-e820: 000000001fef0000 - 000000001fef3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001fef3000 - 000000001ff00000 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 510MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f5aa0
[17179569.184000] On node 0 totalpages: 130800
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 126704 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.2 present.
[17179569.184000] ACPI: RSDP (v000 AWARD                                 ) @ 0x000f7410
[17179569.184000] ACPI: RSDT (v001 AWARD  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fef3000
[17179569.184000] ACPI: FADT (v001 AWARD  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fef3040
[17179569.184000] ACPI: MADT (v001 AWARD  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fef6b40
[17179569.184000] ACPI: DSDT (v001 AWARD  AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:4 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 1ff00000:ded00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda2 ro quiet splash vga=792
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[17179569.184000] Detected 2138.677 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour dummy device 80x25
[17179571.556000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.556000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)[17179571.568000] Memory: 506984k/523200k available (2110k kernel code, 15556k reserved, 595k data, 332k init, 0k highmem)
[17179571.568000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179571.648000] Calibrating delay using timer specific routine.. 4280.87 BogoMIPS (lpj=8561759)
[17179571.648000] Security Framework v1.0.0 initialized
[17179571.648000] SELinux:  Disabled at boot.
[17179571.648000] Mount-cache hash table entries: 512
[17179571.648000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[17179571.648000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[17179571.648000] monitor/mwait feature present.
[17179571.648000] using mwait in idle threads.
[17179571.648000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[17179571.648000] CPU: L2 cache: 256K
[17179571.648000] CPU: Hyper-Threading is disabled
[17179571.648000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 0000441d 00000000 00000000
[17179571.648000] mtrr: v2.0 (20020519)
[17179571.648000] Enabling fast FPU save and restore... done.
[17179571.648000] Enabling unmasked SIMD FPU exception support... done.
[17179571.648000] Checking 'hlt' instruction... OK.
[17179571.664000] SMP alternatives: switching to UP code
[17179571.664000] checking if image is initramfs... it is
[17179572.344000] Freeing initrd memory: 6788k freed
[17179572.356000] ACPI: Looking for DSDT ... not found!
[17179572.360000] CPU0: Intel(R) Celeron(R) CPU 2.13GHz stepping 09
[17179572.360000] Total of 1 processors activated (4280.87 BogoMIPS).
[17179572.360000] ENABLING IO-APIC IRQs
[17179572.360000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179572.504000] Brought up 1 CPUs
[17179572.504000] NET: Registered protocol family 16
[17179572.504000] EISA bus registered
[17179572.504000] ACPI: bus type pci registered
[17179572.516000] PCI: PCI BIOS revision 2.10 entry at 0xfb510, last bus=1
[17179572.516000] PCI: Using configuration type 1
[17179572.516000] ACPI: Subsystem revision 20051216
[17179572.524000] ACPI: Interpreter enabled
[17179572.524000] ACPI: Using IOAPIC for interrupt routing
[17179572.528000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179572.528000] PCI: Probing PCI hardware (bus 00)
[17179572.528000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179572.528000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:02.5
[17179572.528000] Boot video device is 0000:00:09.0
[17179572.528000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179572.560000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
[17179572.560000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 14 15)
[17179572.560000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 14 15)
[17179572.560000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 14 15)
[17179572.560000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 14 15)
[17179572.560000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 14 15)
[17179572.560000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 14 15)
[17179572.560000] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 9 10 11 14 15)
[17179572.564000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179572.564000] pnp: PnP ACPI init
[17179572.568000] pnp: PnP ACPI: found 11 devices
[17179572.568000] PnPBIOS: Disabled by ACPI PNP
[17179572.568000] PCI: Using ACPI for IRQ routing
[17179572.568000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179572.604000] PCI: Bridge: 0000:00:01.0
[17179572.604000]   IO window: disabled.
[17179572.604000]   MEM window: disabled.
[17179572.604000]   PREFETCH window: disabled.
[17179572.604000] audit: initializing netlink socket (disabled)
[17179572.604000] audit(1156973923.600:1): initialized
[17179572.604000] VFS: Disk quotas dquot_6.5.1
[17179572.604000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179572.604000] Initializing Cryptographic API
[17179572.604000] io scheduler noop registered
[17179572.604000] io scheduler anticipatory registered
[17179572.604000] io scheduler deadline registered
[17179572.604000] io scheduler cfq registered
[17179572.604000] isapnp: Scanning for PnP cards...
[17179572.956000] isapnp: No Plug & Play device found
[17179572.988000] Real Time Clock Driver v1.12
[17179572.988000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179574.004000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179574.004000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179574.004000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179574.004000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.008000] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.008000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179574.012000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179574.012000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179574.012000] mice: PS/2 mouse device common for all mice
[17179574.020000] EISA: Probing bus 0 at eisa.0
[17179574.020000] Cannot allocate resource for EISA slot 1
[17179574.020000] Cannot allocate resource for EISA slot 4
[17179574.020000] EISA: Detected 0 cards.
[17179574.020000] NET: Registered protocol family 2
[17179574.044000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179574.068000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179574.068000] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[17179574.068000] TCP bind hash table entries: 16384 (order: 5, 196608 bytes)
[17179574.068000] TCP: Hash tables configured (established 16384 bind 16384)
[17179574.068000] TCP reno registered
[17179574.068000] TCP bic registered
[17179574.068000] NET: Registered protocol family 1
[17179574.068000] NET: Registered protocol family 8
[17179574.068000] NET: Registered protocol family 20
[17179574.068000] Using IPI No-Shortcut mode
[17179574.068000] ACPI wakeup devices:
[17179574.068000] FUTS PCI0 USB0 USB1 USB2 USB3 MAC0 AMR0 UAR1 PS2M PS2K
[17179574.068000] ACPI: (supports S0 S1 S4 S5)
[17179574.068000] Freeing unused kernel memory: 332k freed
[17179574.124000] vesafb: framebuffer at 0xe0000000, mapped to 0xe0880000, using 4608k, total 32768k
[17179574.124000] vesafb: mode is 1024x768x24, linelength=3072, pages=13
[17179574.124000] vesafb: protected mode interface info at c000:5488
[17179574.124000] vesafb: scrolling: redraw
[17179574.124000] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[17179574.124000] vesafb: Mode is VGA compatible
[17179574.220000] Console: switching to colour frame buffer device 128x48
[17179574.220000] fb0: VESA VGA frame buffer device
[17179574.232000] Capability LSM initialized
[17179574.276000] ACPI: Fan [FAN] (on)
[17179574.284000] ACPI: Thermal Zone [THRM] (40 C)
[17179575.060000] SIS5513: IDE controller at PCI slot 0000:00:02.5
[17179575.060000] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 169
[17179575.060000] SIS5513: chipset revision 1
[17179575.060000] SIS5513: not 100% native mode: will probe irqs later
[17179575.060000] SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
[17179575.060000]     ide0: BM-DMA at 0x4000-0x4007, BIOS settings: hda:DMA, hdb:pio
[17179575.060000]     ide1: BM-DMA at 0x4008-0x400f, BIOS settings: hdc:DMA, hdd:pio
[17179575.060000] Probing IDE interface ide0...
[17179575.348000] hda: MAXTOR 6L060J3, ATA DISK drive
[17179576.020000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179576.032000] Probing IDE interface ide1...
[17179576.768000] hdc: _NEC DVD_RW ND-3550A, ATAPI CD/DVD-ROM drive
[17179577.440000] ide1 at 0x170-0x177,0x376 on irq 15
[17179577.448000] hda: max request size: 128KiB
[17179577.460000] hda: 117266688 sectors (60040 MB) w/1819KiB Cache, CHS=65535/16/63, UDMA(133)
[17179577.460000] hda: cache flushes supported
[17179577.460000]  hda: hda1 hda2 hda3
[17179577.520000] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179577.520000] Uniform CD-ROM driver Revision: 3.20
[17179578.048000] usbcore: registered new driver usbfs
[17179578.048000] usbcore: registered new driver hub
[17179578.048000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179578.052000] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 177
[17179578.052000] ohci_hcd 0000:00:03.0: OHCI Host Controller
[17179578.084000] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[17179578.084000] ohci_hcd 0000:00:03.0: irq 177, io mem 0xed012000
[17179578.140000] hub 1-0:1.0: USB hub found
[17179578.140000] hub 1-0:1.0: 3 ports detected
[17179578.244000] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 185
[17179578.244000] ohci_hcd 0000:00:03.1: OHCI Host Controller
[17179578.272000] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[17179578.272000] ohci_hcd 0000:00:03.1: irq 185, io mem 0xed013000
[17179578.328000] hub 2-0:1.0: USB hub found
[17179578.328000] hub 2-0:1.0: 3 ports detected
[17179578.432000] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 22 (level, low) -> IRQ 193
[17179578.432000] ohci_hcd 0000:00:03.2: OHCI Host Controller
[17179578.460000] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[17179578.460000] ohci_hcd 0000:00:03.2: irq 193, io mem 0xed014000
[17179578.516000] hub 3-0:1.0: USB hub found
[17179578.516000] hub 3-0:1.0: 2 ports detected
[17179578.620000] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 201
[17179578.620000] ehci_hcd 0000:00:03.3: EHCI Host Controller
[17179578.620000] PCI: cache line size of 128 is not supported by device 0000:00:03.3
[17179578.620000] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4
[17179578.620000] ehci_hcd 0000:00:03.3: irq 201, io mem 0xed010000
[17179578.620000] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179578.624000] hub 4-0:1.0: USB hub found
[17179578.624000] hub 4-0:1.0: 8 ports detected
[17179578.828000] Attempting manual resume
[17179578.876000] EXT3-fs: mounted filesystem with ordered data mode.
[17179578.900000] kjournald starting.  Commit interval 5 seconds
[17179634.756000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179634.956000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179636.072000] input: PC Speaker as /class/input/input1
[17179636.104000] Linux agpgart interface v0.101 (c) Dave Jones
[17179636.192000] agpgart: Detected SiS 648 chipset
[17179636.200000] agpgart: AGP aperture is 64M @ 0xe8000000
[17179636.608000] parport: PnPBIOS parport detected.
[17179636.608000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179636.712000] Floppy drive(s): fd0 is 1.44M
[17179636.728000] FDC 0 is a post-1991 82077
[17179636.912000] sis900.c: v1.08.09 Sep. 19 2005
[17179636.912000] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 209
[17179636.916000] 0000:00:04.0: Unknown PHY transceiver found at address 0.
[17179636.916000] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
[17179636.916000] 0000:00:04.0: Unknown PHY transceiver found at address 2.
[17179636.916000] 0000:00:04.0: Unknown PHY transceiver found at address 3.
[17179636.916000] 0000:00:04.0: Unknown PHY transceiver found at address 4.
[17179636.920000] 0000:00:04.0: Unknown PHY transceiver found at address 5.
[17179636.920000] 0000:00:04.0: Unknown PHY transceiver found at address 6.
[17179636.920000] 0000:00:04.0: Unknown PHY transceiver found at address 7.
[17179636.920000] 0000:00:04.0: Unknown PHY transceiver found at address 8.
[17179636.920000] 0000:00:04.0: Unknown PHY transceiver found at address 9.
[17179636.924000] 0000:00:04.0: Unknown PHY transceiver found at address 10.
[17179636.924000] 0000:00:04.0: Unknown PHY transceiver found at address 11.
[17179636.924000] 0000:00:04.0: Unknown PHY transceiver found at address 12.
[17179636.924000] 0000:00:04.0: Unknown PHY transceiver found at address 13.
[17179636.924000] 0000:00:04.0: Unknown PHY transceiver found at address 14.
[17179636.928000] 0000:00:04.0: Unknown PHY transceiver found at address 15.
[17179636.928000] 0000:00:04.0: Unknown PHY transceiver found at address 16.
[17179636.928000] 0000:00:04.0: Unknown PHY transceiver found at address 17.
[17179636.928000] 0000:00:04.0: Unknown PHY transceiver found at address 18.
[17179636.928000] 0000:00:04.0: Unknown PHY transceiver found at address 19.
[17179636.932000] 0000:00:04.0: Unknown PHY transceiver found at address 20.
[17179636.932000] 0000:00:04.0: Unknown PHY transceiver found at address 21.
[17179636.932000] 0000:00:04.0: Unknown PHY transceiver found at address 22.
[17179636.932000] 0000:00:04.0: Unknown PHY transceiver found at address 23.
[17179636.932000] 0000:00:04.0: Unknown PHY transceiver found at address 24.
[17179636.936000] 0000:00:04.0: Unknown PHY transceiver found at address 25.
[17179636.936000] 0000:00:04.0: Unknown PHY transceiver found at address 26.
[17179636.936000] 0000:00:04.0: Unknown PHY transceiver found at address 27.
[17179636.936000] 0000:00:04.0: Unknown PHY transceiver found at address 28.
[17179636.936000] 0000:00:04.0: Unknown PHY transceiver found at address 29.
[17179636.936000] 0000:00:04.0: Unknown PHY transceiver found at address 30.
[17179636.940000] 0000:00:04.0: Unknown PHY transceiver found at address 31.
[17179636.964000] 0000:00:04.0: Using transceiver found at address 1 as default
[17179636.964000] eth0: SiS 900 PCI Fast Ethernet at 0xe000, IRQ 209, 00:11:5b:82:98:d4.
[17179637.004000] input: ImPS/2 Logitech Wheel Mouse as /class/input/input2
[17179637.016000] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 217
[17179637.072000] ts: Compaq touchscreen protocol output
[17179637.332000] intel8x0_measure_ac97_clock: measured 54839 usecs
[17179637.332000] intel8x0: clocking to 48000
[17179637.628000] lp0: using parport0 (interrupt-driven).
[17179637.704000] Adding 1028148k swap on /dev/hda3.  Priority:-1 extents:1 across:1028148k
[17179637.780000] EXT3 FS on hda2, internal journal
[17179638.100000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179638.100000] md: bitmap version 4.39
[17179639.172000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179639.392000] NET: Registered protocol family 17
[17179639.736000] eth0: Media Link On 100mbps full-duplex
[17179641.188000] cdrom: open failed.
[17179641.928000] NET: Registered protocol family 10
[17179641.928000] lo: Disabled Privacy Extensions
[17179641.928000] IPv6 over IPv4 tunneling driver
[17179642.084000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[17179642.196000] NTFS volume version 3.1.
[17179652.880000] eth0: no IPv6 routers present
[17179653.484000] ACPI: Power Button (FF) [PWRF]
[17179653.484000] ACPI: Power Button (CM) [PWRB]
[17179653.484000] ACPI: Sleep Button (CM) [FUTS]
[17179653.688000] ibm_acpi: ec object not found
[17179653.740000] pcc_acpi: loading...
[17179671.392000] [drm] Initialized drm 1.0.1 20051102
[17179671.424000] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 225
[17179671.424000] [drm] Initialized radeon 1.24.0 20060225 on minor 0
[17179674.748000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179674.748000] apm: overridden by ACPI.
[17179675.752000] [drm] Setting GART location based on new memory map
[17179675.752000] [drm] writeback test succeeded in 1 usecs
[17179682.520000] Bluetooth: Core ver 2.8
[17179682.520000] NET: Registered protocol family 31
[17179682.520000] Bluetooth: HCI device and connection manager initialized
[17179682.520000] Bluetooth: HCI socket layer initialized
[17179682.556000] Bluetooth: L2CAP ver 2.8
[17179682.556000] Bluetooth: L2CAP socket layer initialized
[17179682.812000] Bluetooth: RFCOMM socket layer initialized
[17179682.812000] Bluetooth: RFCOMM TTY layer initialized
[17179682.812000] Bluetooth: RFCOMM ver 1.7
[17183826.740000] Warning: /proc/ide/hd?/settings interface is obsolete, and will be removed soon!

```


also, I don't know how to execute stuff in tty... what is tty?  terminal?
can graphical applications run without xserver?



sudo hdparm -Tt /dev/hda2 gives

```

 Timing cached reads:   2576 MB in  2.00 seconds = 1287.92 MB/sec
 Timing buffered disk reads:    6 MB in  3.33 seconds =   1.80 MB/sec


```


I've got to sleep (work at 4:30am), i'm looking forward to reading your helpful suggestions tomorrow.

---

### Post by cptnapalm on 2006-08-31
Timing cached reads:   2576 MB in  2.00 seconds = 1287.92 MB/sec
 Timing buffered disk reads:    6 MB in  3.33 seconds =   1.80 MB/sec


wow.  That is seriously goofy.  In my experience, the two readouts scale together.  But your cached reads are a good 20% faster than mine, but your buffered disk reads are like 30x slower than mine.

My best guess off the top of my head (I'm a non-guru, I'm afraid) is that there is something off with your hdparm settings, in some form or fashion.

Could you give us the output, please, of sudo /dev/hda?

(My laptop has SATA, so I can't help out too much, but perhaps we can get enough info out there so someone else may be able to work with it).

---

### Post by mlind on 2006-08-31
Yeah, there's something stange about those values.. My old Maxtor 120GB gives
```

/dev/hda:
 Timing cached reads:   1292 MB in  2.00 seconds = 646.11 MB/sec
 Timing buffered disk reads:  158 MB in  3.02 seconds =  52.26 MB/sec

```

---

### Post by CyberCod on 2006-08-31
> **mlind said:**
> Yeah, there's something stange about those values.. My old Maxtor 120GB gives
```

/dev/hda:
 Timing cached reads:   1292 MB in  2.00 seconds = 646.11 MB/sec
 Timing buffered disk reads:  158 MB in  3.02 seconds =  52.26 MB/sec

```


```

/dev/hda:
 Timing cached reads:   2348 MB in  2.00 seconds = 1173.93 MB/sec
 Timing buffered disk reads:   16 MB in  3.34 seconds =   4.78 MB/sec

```


I"m off to work

---

### Post by hajk on 2006-08-31
Reboot with the liveCD... same problem? If not, then you could research the configuration differences in the liveCD and HD-installed versions.

---

### Post by CyberCod on 2006-08-31
I'm installing on a different hard-drive.  That way I can tell if it is the drive or the install disk at fault.

I'm thinking the drive is dying.  XP has started acting very sluggish too.

So far it is installing a lot faster on the new drive.  (10min vs 45)

Is it possible to migrate my installation to new drive with different partition layout?  I just don't want to have to download all of those apps again.

---

### Post by fragos on 2006-08-31
I just did the same speed test three times and very varied results.

fragos@Geo:~$ sudo hdparm -Tt /dev/hda2
Password:
/dev/hda2:
 Timing cached reads:   1796 MB in  2.00 seconds = 897.94 MB/sec
 Timing buffered disk reads:   58 MB in  3.29 seconds =  17.64 MB/sec

fragos@Geo:~$ sudo hdparm -Tt /dev/hda2
/dev/hda2:
 Timing cached reads:   1820 MB in  2.00 seconds = 909.94 MB/sec
 Timing buffered disk reads:  102 MB in  3.01 seconds =  33.91 MB/sec

fragos@Geo:~$ sudo hdparm -Tt /dev/hda2
/dev/hda2:
 Timing cached reads:   2348 MB in  2.00 seconds = 1173.93 MB/sec
 Timing buffered disk reads:  162 MB in  3.03 seconds =  53.50 MB/sec

---

### Post by CyberCod on 2006-09-02
Well, I installed on another hard drive.  A nice fast perpendicular recording drive.

Now Ubuntu is running like a dream.  I guess I'll just put that other drive in a USB enclosure and use it for moving files between friends.

I'm getting another drive to use in its place.  

Only problem I see is migrating the ubuntu install over to it.

Can i just copy all the files over and install GRUB from Ultimate Boot Disk?

Would that work? or is there a program that would simplify this?


I'd have to modify /boot/grub/menu.lst because the new drive will have a windows installation on partition 1.... whereas this install I'm using now has Ubuntu on partition 1.


Any tips here would be appreciated.  The drive will be here middle of next week probably.

Thank you all for your time and help.

---

