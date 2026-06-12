---
title: "This is driving me nuts, everythings going nuts"
date: 2007-04-26
forum: Desktop Environments
---

### Post by BU5T4 on 2007-04-26
Hi Folks,

I'm having some major problems with ubuntu. Since upgrading using synaptic package manager.

When i try to login to gnome the screen goes blank and then a small white box opens on the top right hand side of my screen. After that nothing happens except i can move the mouse.

If I press ALT F2 it goes back to the login screen. If I reboot a couple of times it will let me login to gnome but once its running if I try and open up a terminal window or any other window like network settings or something it will just freeze that app and will only close if I open a root terminal (Which works) and kill the proccess.

I managed to login to kde but the problem with terminal and other programs is still the same but I can manage to get firefox to open and run fine in kde without crashing.

i'm quite new to linux but do know the basics. 

What kind of info would you guys need to know?

kde control center says release 2.6.20-15 generic, is this my ubuntu version?

I'm running a Compaq Presario v5000 laptop.

Dmesg

```

[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e0000 size: 0000000000020000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003f580000 end: 000000003f680000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003f680000 size: 0000000000080000 end: 000000003f700000 type: 4
[    0.000000] copy_e820_map() start: 000000003f700000 size: 0000000000900000 end: 0000000040000000 type: 2
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010000000 end: 00000000f0000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
[    0.000000] copy_e820_map() start: 00000000fed00000 size: 0000000000000400 end: 00000000fed00400 type: 2
[    0.000000] copy_e820_map() start: 00000000fed14000 size: 0000000000006000 end: 00000000fed1a000 type: 2
[    0.000000] copy_e820_map() start: 00000000fed1c000 size: 0000000000074000 end: 00000000fed90000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000ff000000 size: 0000000001000000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f680000 (usable)
[    0.000000]  BIOS-e820: 000000003f680000 - 000000003f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f700000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 118MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f65b0
[    0.000000] Entering add_active_range(0, 0, 259712) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   259712
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   259712
[    0.000000] On node 0 totalpages: 259712
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 237 pages used for memmap
[    0.000000]   HighMem zone: 30099 pages, LIFO batch:7
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6580
[    0.000000] ACPI: RSDT (v001 PTLTD  Capell00 0x06040000  LTP 0x00000000) @ 0x3f68d18a
[    0.000000] ACPI: FADT (v001 HP     NISSAN   0x06040000 LOHR 0x0000005a) @ 0x3f693dfc
[    0.000000] ACPI: MADT (v001 HP     NISSAN   0x06040000 LOHR 0x0000005a) @ 0x3f693e70
[    0.000000] ACPI: HPET (v001 HP     NISSAN   0x06040000 LOHR 0x0000005a) @ 0x3f693ed8
[    0.000000] ACPI: MCFG (v001 HP     NISSAN   0x06040000 LOHR 0x0000005a) @ 0x3f693f10
[    0.000000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x3f693fd8
[    0.000000] ACPI: MADT (v001 PTLTD  	 APIC   0x06040000  LTP 0x00000000) @ 0x3f693f7e
[    0.000000] ACPI: SSDT (v001 SataRe SataAhci 0x00001000 INTL 0x20060217) @ 0x3f68d8a4
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20060217) @ 0x3f68d6c8
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20060217) @ 0x3f68d1d2
[    0.000000] ACPI: DSDT (v001 HP     NISSAN   0x06040000 INTL 0x20060217) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: 2 duplicate APIC table ignored.
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:14 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] Detected 1463.052 MHz processor.
[   14.974741] Built 1 zonelists.  Total pages: 257683
[   14.974745] Kernel command line: root=UUID=7187fcfb-bca0-4d6b-97de-a9c458575ee1 ro quiet splash vga=792
[   14.974939] mapped APIC to ffffd000 (fee00000)
[   14.974942] mapped IOAPIC to ffffc000 (fec00000)
[   14.974945] Enabling fast FPU save and restore... done.
[   14.974948] Enabling unmasked SIMD FPU exception support... done.
[   14.974957] Initializing CPU#0
[   14.975034] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   14.975084] Console: colour dummy device 80x25
[   14.975377] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   14.975798] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   15.009654] Memory: 1016608k/1038848k available (1992k kernel code, 21504k reserved, 893k data, 328k init, 121344k highmem)
[   15.009665] virtual kernel memory layout:
[   15.009667]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   15.009668]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   15.009670]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   15.009671]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   15.009672]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   15.009674]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   15.009675]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   15.009679] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   15.009861] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   15.009868] hpet0: 3 64-bit timers, 14318180 Hz
[   15.010874] Using HPET for base-timer
[   15.089759] Calibrating delay using timer specific routine.. 2929.42 BogoMIPS (lpj=5858858)
[   15.089807] Security Framework v1.0.0 initialized
[   15.089818] SELinux:  Disabled at boot.
[   15.089835] Mount-cache hash table entries: 512
[   15.089993] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 0000c109 00000000 00000000
[   15.090003] monitor/mwait feature present.
[   15.090005] using mwait in idle threads.
[   15.090010] CPU: L1 I cache: 32K, L1 D cache: 32K
[   15.090013] CPU: L2 cache: 1024K
[   15.090017] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002940 0000c109 00000000 00000000
[   15.090028] Compat vDSO mapped to ffffe000.
[   15.090033] Remapping vsyscall page to ffffe000
[   15.090049] Checking 'hlt' instruction... OK.
[   15.105868] SMP alternatives: switching to UP code
[   15.106097] Freeing SMP alternatives: 11k freed
[   15.106311] Early unpacking initramfs... done
[   15.558316] ACPI: Core revision 20060707
[   15.558554] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   15.592644] CPU0: Intel(R) Celeron(R) M CPU        410  @ 1.46GHz stepping 08
[   15.592672] Total of 1 processors activated (2929.42 BogoMIPS).
[   15.592868] ENABLING IO-APIC IRQs
[   15.593080] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   15.736932] Brought up 1 CPUs
[   15.737185] Booting paravirtualized kernel on bare hardware
[   15.737284] Time: 11:28:33  Date: 03/26/107
[   15.737311] NET: Registered protocol family 16
[   15.737397] EISA bus registered
[   15.737402] ACPI: bus type pci registered
[   15.737489] PCI: PCI BIOS revision 2.10 entry at 0xfd873, last bus=8
[   15.737492] PCI: Using configuration type 1
[   15.737494] Setting up standard PCI resources
[   15.741119] ACPI: Interpreter enabled
[   15.741122] ACPI: Using IOAPIC for interrupt routing
[   15.741805] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   15.741812] PCI: Probing PCI hardware (bus 00)
[   15.742653] Boot video device is 0000:00:02.0
[   15.743326] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   15.743331] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   15.744186] PCI: Firmware left 0000:08:08.0 e100 interrupts enabled, disabling
[   15.744281] PCI: Transparent bridge - 0000:00:1e.0
[   15.744360] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   15.748328] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   15.748641] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   15.748971] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[   15.749532] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   15.750074] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   15.750334] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 *4 5 6 7 11 12 14 15)
[   15.750593] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[   15.750856] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   15.751116] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 *6 7 10 12 14 15)
[   15.751377] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[   15.751638] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[   15.751897] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[   15.793897] Linux Plug and Play Support v0.97 (c) Adam Belay
[   15.793907] pnp: PnP ACPI init
[   15.821352] pnp: PnP ACPI: found 10 devices
[   15.821358] PnPBIOS: Disabled by ACPI PNP
[   15.821404] PCI: Using ACPI for IRQ routing
[   15.821407] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   15.821412] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[   15.821415] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[   15.821418] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[   15.821421] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[   15.821423] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
[   15.821426] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
[   15.821469] PCI: Cannot allocate resource region 0 of device 0000:06:00.0
[   15.842131] NET: Registered protocol family 8
[   15.842134] NET: Registered protocol family 20
[   15.842695] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[   15.842702] PCI: Bridge: 0000:00:1c.0
[   15.842703]   IO window: disabled.
[   15.842709]   MEM window: disabled.
[   15.842714]   PREFETCH window: disabled.
[   15.842720] PCI: Bridge: 0000:00:1c.1
[   15.842722]   IO window: disabled.
[   15.842728]   MEM window: disabled.
[   15.842733]   PREFETCH window: disabled.
[   15.842749] PCI: Bridge: 0000:00:1c.2
[   15.842751]   IO window: disabled.
[   15.842757]   MEM window: 50000000-500fffff
[   15.842762]   PREFETCH window: disabled.
[   15.842768] PCI: Bridge: 0000:00:1e.0
[   15.842772]   IO window: 2000-2fff
[   15.842779]   MEM window: d0100000-d01fffff
[   15.842783]   PREFETCH window: disabled.
[   15.842817] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[   15.842826] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   15.842851] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
[   15.842859] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   15.842883] PCI: Enabling device 0000:00:1c.2 (0100 -> 0102)
[   15.842889] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   15.842897] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   15.842911] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   15.842937] NET: Registered protocol family 2
[   15.880767] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   15.880881] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   15.881739] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   15.882189] TCP: Hash tables configured (established 131072 bind 65536)
[   15.882193] TCP reno registered
[   15.892843] checking if image is initramfs... it is
[   16.783695] Freeing initrd memory: 8886k freed
[   16.783918] Simple Boot Flag at 0x36 set to 0x1
[   16.784261] audit: initializing netlink socket (disabled)
[   16.784274] audit(1177586914.832:1): initialized
[   16.784348] highmem bounce pool size: 64 pages
[   16.784408] VFS: Disk quotas dquot_6.5.1
[   16.784428] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   16.784478] io scheduler noop registered
[   16.784482] io scheduler anticipatory registered
[   16.784484] io scheduler deadline registered
[   16.784493] io scheduler cfq registered (default)
[   24.780842] 0000:00:1d.7 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[   24.781115] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   24.781175] assign_interrupt_mode Found MSI capability
[   24.781178] Allocate Port Service[0000:00:1c.0:pcie00]
[   24.781218] Allocate Port Service[0000:00:1c.0:pcie02]
[   24.781342] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   24.781401] assign_interrupt_mode Found MSI capability
[   24.781404] Allocate Port Service[0000:00:1c.1:pcie00]
[   24.781438] Allocate Port Service[0000:00:1c.1:pcie02]
[   24.781559] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   24.781618] assign_interrupt_mode Found MSI capability
[   24.781621] Allocate Port Service[0000:00:1c.2:pcie00]
[   24.781652] Allocate Port Service[0000:00:1c.2:pcie02]
[   24.781827] isapnp: Scanning for PnP cards...
[   25.135850] isapnp: No Plug & Play device found
[   25.161979] Real Time Clock Driver v1.12ac
[   25.162038] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   25.162788] mice: PS/2 mouse device common for all mice
[   25.163368] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   25.163611] input: Macintosh mouse button emulation as /class/input/input0
[   25.163647] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   25.163651] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   25.163950] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   25.184172] i8042.c: Detected active multiplexing controller, rev 1.1.
[   25.201472] serio: i8042 KBD port at 0x60,0x64 irq 1
[   25.201478] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   25.201481] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   25.201483] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   25.201486] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   25.202974] EISA: Probing bus 0 at eisa.0
[   25.202984] Cannot allocate resource for EISA slot 1
[   25.202987] Cannot allocate resource for EISA slot 2
[   25.203014] EISA: Detected 0 cards.
[   25.233085] TCP cubic registered
[   25.233094] NET: Registered protocol family 1
[   25.233116] Using IPI No-Shortcut mode
[   25.233186] ACPI: (supports S0 S3 S4 S5)
[   25.233238]   Magic number: 3:34:480
[   25.233547] Freeing unused kernel memory: 328k freed
[   25.236283] Time: tsc clocksource has been installed.
[   25.320208] input: AT Translated Set 2 keyboard as /class/input/input1
[   25.336117] vesafb: framebuffer at 0xc0000000, mapped to 0xf8880000, using 6144k, total 7872k
[   25.336122] vesafb: mode is 1024x768x32, linelength=4096, pages=1
[   25.336125] vesafb: protected mode interface info at 00ff:44f0
[   25.336127] vesafb: scrolling: redraw
[   25.336130] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   25.372474] Console: switching to colour frame buffer device 128x48
[   25.408673] fb0: VESA VGA frame buffer device
[   26.634617] Capability LSM initialized
[   26.677303] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   26.677310] ACPI: Processor [CPU0] (supports 8 throttling states)
[   26.677319] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   11.564000] ACPI: Thermal Zone [TZ01] (37 C)
[   11.564000] ACPI: Thermal Zone [TZ02] (27 C)
[   11.572000] Time: hpet clocksource has been installed.
[   12.064000] usbcore: registered new interface driver usbfs
[   12.064000] usbcore: registered new interface driver hub
[   12.064000] usbcore: registered new device driver usb
[   12.064000] USB Universal Host Controller Interface driver v3.0
[   12.064000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[   12.064000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   12.064000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   12.064000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   12.064000] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00001820
[   12.064000] usb usb1: configuration #1 chosen from 1 choice
[   12.064000] hub 1-0:1.0: USB hub found
[   12.064000] hub 1-0:1.0: 2 ports detected
[   12.152000] SCSI subsystem initialized
[   12.160000] libata version 2.20 loaded.
[   12.168000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[   12.168000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   12.168000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   12.168000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   12.168000] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00001840
[   12.168000] usb usb2: configuration #1 chosen from 1 choice
[   12.168000] hub 2-0:1.0: USB hub found
[   12.168000] hub 2-0:1.0: 2 ports detected
[   12.176000] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k2-NAPI
[   12.176000] e100: Copyright(c) 1999-2006 Intel Corporation
[   12.272000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   12.272000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   12.272000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   12.272000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   12.272000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[   12.272000] usb usb3: configuration #1 chosen from 1 choice
[   12.272000] hub 3-0:1.0: USB hub found
[   12.272000] hub 3-0:1.0: 2 ports detected
[   12.376000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
[   12.376000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   12.376000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   12.376000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   12.376000] uhci_hcd 0000:00:1d.3: irq 17, io base 0x00001880
[   12.376000] usb usb4: configuration #1 chosen from 1 choice
[   12.376000] hub 4-0:1.0: USB hub found
[   12.376000] hub 4-0:1.0: 2 ports detected
[   12.480000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[   12.480000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   12.480000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   12.480000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   12.480000] ehci_hcd 0000:00:1d.7: debug port 1
[   12.480000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   12.480000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xd0544000
[   12.484000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   12.484000] usb usb5: configuration #1 chosen from 1 choice
[   12.484000] hub 5-0:1.0: USB hub found
[   12.484000] hub 5-0:1.0: 8 ports detected
[   12.592000] ata_piix 0000:00:1f.1: version 2.10ac1
[   12.592000] ACPI: PCI Interrupt 0000:00:1f.1[B] -> GSI 19 (level, low) -> IRQ 20
[   12.592000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   12.592000] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011810 irq 14
[   12.592000] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011818 irq 15
[   12.592000] scsi0 : ata_piix
[   12.928000] ata1.00: ATAPI, max MWDMA2
[   13.108000] ata1.00: configured for MWDMA2
[   13.108000] scsi1 : ata_piix
[   13.108000] ata2: port disabled. ignoring.
[   13.116000] scsi 0:0:0:0: CD-ROM            PIONEER  DVDRW   DVR-K16  1.15 PQ: 0 ANSI: 5
[   13.116000] ahci 0000:00:1f.2: version 2.1
[   13.116000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[   13.168000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   13.168000] Uniform CD-ROM driver Revision: 3.20
[   13.168000] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   13.172000] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   14.120000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   14.120000] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x5 impl SATA mode
[   14.120000] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[   14.120000] ata3: SATA max UDMA/133 cmd 0xf8834500 ctl 0x00000000 bmdma 0x00000000 irq 20
[   14.120000] ata4: SATA max UDMA/133 cmd 0xf8834580 ctl 0x00000000 bmdma 0x00000000 irq 20
[   14.120000] ata5: SATA max UDMA/133 cmd 0xf8834600 ctl 0x00000000 bmdma 0x00000000 irq 20
[   14.120000] ata6: SATA max UDMA/133 cmd 0xf8834680 ctl 0x00000000 bmdma 0x00000000 irq 20
[   14.120000] scsi2 : ahci
[   14.604000] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   14.604000] ata3.00: ATA-7: ST98823AS, 3.05, max UDMA/100
[   14.604000] ata3.00: 156301488 sectors, multi 16: LBA48 
[   14.604000] ata3.00: configured for UDMA/100
[   14.604000] scsi3 : ahci
[   14.916000] ata4: SATA link down (SStatus 0 SControl 0)
[   14.916000] scsi4 : ahci
[   15.228000] ata5: SATA link down (SStatus 0 SControl 300)
[   15.228000] scsi5 : ahci
[   15.540000] ata6: SATA link down (SStatus 0 SControl 0)
[   15.540000] scsi 2:0:0:0: Direct-Access     ATA      ST98823AS        3.05 PQ: 0 ANSI: 5
[   15.540000] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[   15.540000] ACPI: PCI Interrupt 0000:08:08.0[A] -> GSI 20 (level, low) -> IRQ 21
[   15.568000] e100: eth0: e100_probe: addr 0xd0100000, irq 21, MAC addr 00:16:D4:0D:3D:7A
[   15.576000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[   15.576000] sda: Write Protect is off
[   15.576000] sda: Mode Sense: 00 3a 00 00
[   15.576000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   15.576000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[   15.576000] sda: Write Protect is off
[   15.576000] sda: Mode Sense: 00 3a 00 00
[   15.576000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   15.576000]  sda: sda1 sda2 < sda5 >
[   15.616000] sd 2:0:0:0: Attached scsi disk sda
[   15.840000] Attempting manual resume
[   15.840000] swsusp: Resume From Partition 8:5
[   15.840000] PM: Checking swsusp image.
[   15.840000] PM: Resume from disk failed.
[   15.856000] EXT3-fs: INFO: recovery required on readonly filesystem.
[   15.856000] EXT3-fs: write access will be enabled during recovery.
[   21.084000] kjournald starting.  Commit interval 5 seconds
[   21.084000] EXT3-fs: sda1: orphan cleanup on readonly fs
[   21.084000] ext3_orphan_cleanup: deleting unreferenced inode 5341415
[   21.084000] ext3_orphan_cleanup: deleting unreferenced inode 5341402
[   21.084000] ext3_orphan_cleanup: deleting unreferenced inode 5341399
[   21.084000] ext3_orphan_cleanup: deleting unreferenced inode 5341398
[   21.084000] ext3_orphan_cleanup: deleting unreferenced inode 5341397
[   21.084000] EXT3-fs: sda1: 5 orphan inodes deleted
[   21.084000] EXT3-fs: recovery complete.
[   21.108000] EXT3-fs: mounted filesystem with ordered data mode.
[   34.124000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   35.872000] Linux agpgart interface v0.102 (c) Dave Jones
[   35.928000] agpgart: Detected an Intel 945GM Chipset.
[   35.928000] agpgart: Detected 7932K stolen memory.
[   35.948000] agpgart: AGP aperture is 256M @ 0xc0000000
[   35.984000] NET: Registered protocol family 17
[   36.048000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   36.048000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   36.080000] iTCO_vendor_support: vendor-support=0
[   36.104000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   36.104000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   36.104000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   36.188000] intel_rng: FWH not detected
[   37.144000] ieee80211_crypt: registered algorithm 'NULL'
[   37.152000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   37.152000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   37.348000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   37.348000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   37.384000] bcm43xx driver
[   37.444000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[   37.512000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[   37.552000] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   37.552000] PCI: Setting latency timer of device 0000:06:00.0 to 64
[   37.840000] lp: driver loaded but no devices found
[   37.904000] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[   37.960000] usbcore: registered new interface driver ndiswrapper
[   37.992000] Adding 3004112k swap on /dev/disk/by-uuid/81f3b43b-9dc3-42c1-a5ce-88daf6ba7818.  Priority:-1 extents:1 across:3004112k
[   38.056000] EXT3 FS on sda1, internal journal
[   38.800000] hda_intel: azx_get_response timeout, switching to polling mode...
[   42.632000] ACPI: AC Adapter [ACAD] (on-line)
[   42.752000] ACPI: Battery Slot [BAT1] (battery present)
[   42.820000] input: Power Button (FF) as /class/input/input3
[   42.824000] ACPI: Power Button (FF) [PWRF]
[   42.824000] ACPI Error (evxfevnt-0189): Could not enable SleepButton event [20060707]
[   42.824000] ACPI Warning (evxface-0146): Could not enable fixed event 3 [20060707]
[   42.872000] input: Lid Switch as /class/input/input4
[   42.876000] ACPI: Lid Switch [LID]
[   42.924000] input: Power Button (CM) as /class/input/input5
[   42.928000] ACPI: Power Button (CM) [PWRB]
[   42.952000] Using specific hotkey driver
[   42.992000] No dock devices found.
[   43.104000] ibm_acpi: ec object not found
[   43.208000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   43.208000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   43.260000] pcc_acpi: loading...
[   49.124000] [drm] Initialized drm 1.1.0 20060810
[   49.144000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   49.148000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   49.816000] ppdev: user-space parallel port driver
[   54.772000] apm: BIOS not found.
[  261.792000] ip_tables: (C) 2000-2006 Netfilter Core Team

```

Cant figure this out atall, I don't really know where to start to be honest. 

Any help would be greatly appreciated

---

### Post by macabro22 on 2007-04-26
this happens to me everytime I try to set up my wifi bus card using network-manager. Network manager crashes (its screen goes blank) then I hold on the power button and expericence the same thing as you do when I log on.

---

### Post by macabro22 on 2007-04-26
Ah!! Its happening again. Help!

---

### Post by BU5T4 on 2007-04-27
OK well now I cant get logged into gnome atall.

I can still login to kde but gnome isnt having it.

I even tried logging into my ubuntu instalation from a friends house using vnc viewer from a windows box, but I get the same screen with the small white box on the top left and black accross the rest of the window.

I rebooted my machine from a ssh sesssion and it still hasnt came back up so I will try and get a screen shot of the problem.

Any help would be very much appreciated.

---

### Post by h00RU on 2007-04-27
How about a little more info.
Print out /var/log/Xorg.0.log, ~/.profile and ~/.xsession-errors
I appears to be something in your desktop setup for Gnome as KDE at least starts up.
TL
h

---

### Post by BU5T4 on 2007-04-27
Thanks for the reply h00RU

I tried to paste in my log files as you requested but they were too large for the forum so you can view them here. [http://www.bu5t4.homelinux.com/help/]("http://www.bu5t4.homelinux.com/help/")

Hope this helps.

if you need any more info just ask.

Thanks alot for your help, this has me stumped.

D-A

---

### Post by h00RU on 2007-04-27
After looking at the logs, it appears that libcairo does not support the video driver you are using for the Intel 965GM. 

This is probably a reportable bug.

I suggest uninstalling compiz and see if you can boot into Gnome. If so, report the bug (the info you need is in the Xsession-errors) and wait for a response. In the mean time you might try beryl/emerald instead of compiz/metacity. No guarantee that this will work either as beryl require libcairo also. You could do more experimentation by trying other window managers and Desktops (ie.. Icewm, xfce ...). 

The other option would be to go back to Edgy where the libs are more stable and mature.

I'm no expert, just a user who has worked a lot on Linux running on laptops (mostly IBM).

Hope this helps. 
h

---

### Post by BU5T4 on 2007-04-28
Hi H00RU,

Thanks for the advice buddy. I appreciate it.

It's weird as I was using beryl for ages before upgrading ubuntu and it worked a treat.

What would be the best way of downgrading? is it possible to do this using synaptic package manager?

How do I go about reporting a bug?

D-A

---

### Post by seshomaru samma on 2007-04-29
To report a bug look [here]("https://launchpad.net/ubuntu")
search through all the bugs to make sure this bug was not reported before.

To downgrade - make a /home partition (like[ this]("http://www.psychocats.net/ubuntu/separatehome"))
Reinstall Linux

---

