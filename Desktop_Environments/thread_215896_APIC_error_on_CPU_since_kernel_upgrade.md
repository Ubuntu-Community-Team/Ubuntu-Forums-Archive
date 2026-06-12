---
title: "APIC error on CPU since kernel upgrade"
date: 2006-07-14
forum: Desktop Environments
---

### Post by samba on 2006-07-14
Hi,

I've had Dapper running very nicely for a few months with AIGLX/Compiz on my laptop, but now since the recent upgrades (I think since the upgrade to the kernel 2.6.15-25 -- but it's still there with 2.6.15-26) my computer hangs for some time at the "mounting root file systems" bit when I boot, and if I run "dmseg" I see that I continuously have these two lines repeating:

```

[17179692.956000] APIC error on CPU0: 40(40)
[17179692.956000] APIC error on CPU1: 40(40)

```

(there are two CPUs because my laptop as a Dual Core intel processor). My specs are

- Intel Core Duo Processor T2400 (1.83 GHz)
- 1024 MB DDR2 SDRAM
- 100 GB Hard drive
- 12.1" XGA display
- DVD SuperMulti drive
- Intel Pro Wireless 3945ABG

Anyone knows how to solve this problem? If it can help, my boot line in /boot/grub/menu.lst is
```

# kopt=root=/dev/sda2 ro resume=/dev/sda5 noapic

```
I had to remove the "nolapic" option as my laptop didn't boot anymore with this option.

cheers,
vincent

---

### Post by samba on 2006-07-17
Anyone? :-)

---

### Post by samba on 2006-07-28
Sorry to bounce it again, but I don't really know what to try, and it's quite annoying; boot time is pretty long (it hangs for a while at "mounting root file systems"), and everything seems to be slow... i assume this is because of the "APIC error". 

Anyone knows what i can do? I tried adding the noapic option at boot time, but it doesn't change anything. However if I add the nolapic option then it just doesn't boot anymore.

Thanks a lot...

Vincent :-)

---

### Post by samba on 2006-07-30
If it helps, here's my full dmesg output (in 2 messages sorry for length purposes):

```


[17179569.184000] Linux version 2.6.15-26-686 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Mon Jul 17 20:14:14 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
[17179569.184000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e0000 - 00000000000eee00 (reserved)
[17179569.184000]  BIOS-e820: 00000000000eee00 - 00000000000ef000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000000ef000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003f770000 (usable)
[17179569.184000]  BIOS-e820: 000000003f770000 - 000000003f780000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000003f780000 - 0000000040000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec18000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec20000 - 00000000fec28000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[17179569.184000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[17179569.184000]  BIOS-e820: 00000000feda0000 - 00000000fedc0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffb00000 - 00000000ffc00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[17179569.184000] 119MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 259952
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 30576 pages, LIFO batch:7
[17179569.184000] DMI 2.4 present.
[17179569.184000] ACPI: RSDP (v000 TOSHIB                                ) @ 0x000f01e0
[17179569.184000] ACPI: RSDT (v001 TOSHIB 750      0x00970814 TASM 0x04010000) @ 0x3f770000
[17179569.184000] ACPI: FADT (v002 TOSHIB 750      0x20030101 TASM 0x04010000) @ 0x3f770074
[17179569.184000] ACPI: SSDT (v001 TOSHIB A003C    0x20050926 MSFT 0x0100000e) @ 0x3f774673
[17179569.184000] ACPI: DBGP (v001 TOSHIB 750      0x00970814 TASM 0x04010000) @ 0x3f7751f5
[17179569.184000] ACPI: BOOT (v001 TOSHIB 750      0x00970814 TASM 0x04010000) @ 0x3f77004c
[17179569.184000] ACPI: MADT (v001 TOSHIB 750      0x00970814 TASM 0x04010000) @ 0x3f775151
[17179569.184000] ACPI: MCFG (v001 TOSHIB 750      0x00970814 TASM 0x04010000) @ 0x3f7751b9
[17179569.184000] ACPI: HPET (v001 TOSHIB 750      0x00970814 TASM 0x04010000) @ 0x3f775229
[17179569.184000] ACPI: SSDT (v001 TOSHIB A003C    0x20051013 MSFT 0x0100000e) @ 0x3f775261
[17179569.184000] ACPI: SSDT (v001 TOSHIB A003C    0x20060120 MSFT 0x0100000e) @ 0x3f7768d2
[17179569.184000] ACPI: SSDT (v001 TOSHIB A003C    0x20051021 MSFT 0x0100000e) @ 0x3f7785cd
[17179569.184000] ACPI: DSDT (v001 TOSHIB A003C    0x20060120 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0xd808
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:14 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[17179569.184000] Processor #1 6:14 APIC version 20
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1 already used, trying 2
[17179569.184000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda2 ro resume=/dev/sda5 ht=on quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[17179569.184000] Console: colour VGA+ 80x25
[17179569.184000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179569.184000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.184000] Memory: 1018520k/1039808k available (2110k kernel code, 20544k reserved, 595k data, 332k init, 122304k highmem)
[17179569.184000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.184000] hpet0: at MMIO 0xfed00000 (virtual 0xf8800000), IRQs 2, 8, 0
[17179569.184000] hpet0: 3 64-bit timers, 14318180 Hz
[17179569.184000] Using HPET for base-timer
[17179569.184000] Using HPET for gettimeofday
[17179569.184000] Detected 1828.758 MHz processor.
[17179569.184000] Using hpet for high-res timesource
[17179569.268000] Calibrating delay using timer specific routine.. 3661.93 BogoMIPS (lpj=7323876)
[17179569.268000] Security Framework v1.0.0 initialized
[17179569.268000] SELinux:  Disabled at boot.
[17179569.268000] Mount-cache hash table entries: 512
[17179569.268000] CPU: After generic identify, caps: bfe9fbff 00000000 00000000 00000000 0000c1a9 00000000 00000000
[17179569.268000] CPU: After vendor identify, caps: bfe9fbff 00000000 00000000 00000000 0000c1a9 00000000 00000000
[17179569.268000] monitor/mwait feature present.
[17179569.268000] using mwait in idle threads.
[17179569.268000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179569.268000] CPU: L2 cache: 2048K
[17179569.268000] CPU: Physical Processor ID: 0
[17179569.268000] CPU: Processor Core ID: 0
[17179569.268000] CPU: After all inits, caps: bfe9fbff 00000000 00000000 00000040 0000c1a9 00000000 00000000
[17179569.268000] mtrr: v2.0 (20020519)
[17179569.268000] Enabling fast FPU save and restore... done.
[17179569.268000] Enabling unmasked SIMD FPU exception support... done.
[17179569.268000] Checking 'hlt' instruction... OK.
[17179569.284000] SMP alternatives: switching to UP code
[17179569.284000] checking if image is initramfs... it is
[17179569.832000] Freeing initrd memory: 6809k freed
[17179569.836000] ACPI: Looking for DSDT ... not found!
[17179569.840000] CPU0: Intel Genuine Intel(R) CPU           T2400  @ 1.83GHz stepping 08
[17179569.840000] SMP alternatives: switching to SMP code
[17179569.840000] Booting processor 1/1 eip 3000
[17179569.848000] Initializing CPU#1
[17179569.876000] APIC error on CPU0: 00(40)
[17179569.932000] Calibrating delay using timer specific routine.. 3657.46 BogoMIPS (lpj=7314928)
[17179569.932000] CPU: After generic identify, caps: bfe9fbff 00000000 00000000 00000000 0000c1a9 00000000 00000000
[17179569.932000] CPU: After vendor identify, caps: bfe9fbff 00000000 00000000 00000000 0000c1a9 00000000 00000000
[17179569.932000] monitor/mwait feature present.
[17179569.932000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179569.932000] CPU: L2 cache: 2048K
[17179569.932000] CPU: Physical Processor ID: 0
[17179569.932000] CPU: Processor Core ID: 1
[17179569.932000] CPU: After all inits, caps: bfe9fbff 00000000 00000000 00000040 0000c1a9 00000000 00000000
[17179569.932000] CPU1: Intel Genuine Intel(R) CPU           T2400  @ 1.83GHz stepping 08
[17179569.932000] Total of 2 processors activated (7319.40 BogoMIPS).
[17179569.932000] ENABLING IO-APIC IRQs
[17179569.932000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179570.084000] checking TSC synchronization across 2 CPUs: passed.
[17179570.084000] APIC error on CPU1: 00(40)
[17179570.088000] Brought up 2 CPUs
[17179570.088000] NET: Registered protocol family 16
[17179570.088000] EISA bus registered
[17179570.088000] ACPI: bus type pci registered
[17179570.088000] PCI: PCI BIOS revision 2.10 entry at 0xfd48c, last bus=4
[17179570.088000] PCI: Using MMCONFIG
[17179570.088000] ACPI: Subsystem revision 20051216
[17179570.088000] ACPI: Interpreter enabled
[17179570.088000] ACPI: Using IOAPIC for interrupt routing
[17179570.092000] ACPI: PCI Interrupt Link [LNKA] (IRQs *10)
[17179570.092000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *11)
[17179570.092000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *11)
[17179570.092000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *11)
[17179570.092000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *11)
[17179570.092000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *11)
[17179570.092000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *11)
[17179570.092000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *11)
[17179570.092000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.092000] PCI: Probing PCI hardware (bus 00)
[17179570.092000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179570.096000] Boot video device is 0000:00:02.0
[17179570.096000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179570.096000] PCI: Transparent bridge - 0000:00:1e.0
[17179570.096000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.100000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[17179570.100000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[17179570.104000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.MPEX._PRT]
[17179570.104000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.104000] pnp: PnP ACPI init
[17179570.108000] pnp: PnP ACPI: found 14 devices
[17179570.108000] PnPBIOS: Disabled by ACPI PNP
[17179570.108000] PCI: Using ACPI for IRQ routing
[17179570.108000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.124000] pnp: 00:08: ioport range 0x1e0-0x1ef has been reserved
[17179570.124000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[17179570.124000] PCI: Bridge: 0000:00:1c.0
[17179570.124000]   IO window: b000-bfff
[17179570.124000]   MEM window: ffc00000-ffcfffff
[17179570.124000]   PREFETCH window: disabled.
[17179570.124000] PCI: Bridge: 0000:00:1c.2
[17179570.124000]   IO window: disabled.
[17179570.124000]   MEM window: ffa00000-ffafffff
[17179570.124000]   PREFETCH window: disabled.
[17179570.124000] PCI: Bus 4, cardbus bridge: 0000:03:0b.0
[17179570.124000]   IO window: 00001000-000010ff
[17179570.124000]   IO window: 00001400-000014ff
[17179570.124000]   PREFETCH window: 50000000-51ffffff
[17179570.124000]   MEM window: 52000000-53ffffff
[17179570.124000] PCI: Bridge: 0000:00:1e.0
[17179570.124000]   IO window: 1000-1fff
[17179570.124000]   MEM window: 52000000-54ffffff
[17179570.124000]   PREFETCH window: 50000000-51ffffff
[17179570.124000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 169
[17179570.124000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179570.124000] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 177
[17179570.124000] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[17179570.124000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179570.124000] PCI: Enabling device 0000:03:0b.0 (0000 -> 0003)
[17179570.124000] ACPI: PCI Interrupt 0000:03:0b.0[A] -> GSI 21 (level, low) -> IRQ 185
[17179570.124000] Simple Boot Flag at 0x7c set to 0x1
[17179570.124000] audit: initializing netlink socket (disabled)
[17179570.124000] audit(1154282442.120:1): initialized
[17179570.124000] highmem bounce pool size: 64 pages
[17179570.124000] VFS: Disk quotas dquot_6.5.1
[17179570.124000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.124000] Initializing Cryptographic API
[17179570.124000] io scheduler noop registered
[17179570.124000] io scheduler anticipatory registered
[17179570.124000] io scheduler deadline registered
[17179570.124000] io scheduler cfq registered
[17179570.124000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 169
[17179570.124000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179570.124000] assign_interrupt_mode Found MSI capability
[17179570.124000] Allocate Port Service[pcie00]
[17179570.124000] Allocate Port Service[pcie03]
[17179570.124000] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 177
[17179570.124000] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[17179570.124000] assign_interrupt_mode Found MSI capability
[17179570.124000] Allocate Port Service[pcie00]
[17179570.124000] Allocate Port Service[pcie03]
[17179570.124000] isapnp: Scanning for PnP cards...
[17179570.484000] isapnp: No Plug & Play device found
[17179570.496000] Real Time Clock Driver v1.12
[17179570.496000] hpet_resources: 0xfed00000 is busy
[17179570.496000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179570.500000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179570.500000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179570.500000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179570.504000] 00:0b: ttyS4 at I/O 0x338 (irq = 4) is a 16550A
[17179570.504000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179570.504000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179570.504000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179570.504000] mice: PS/2 mouse device common for all mice
[17179570.504000] EISA: Probing bus 0 at eisa.0
[17179570.504000] Cannot allocate resource for EISA slot 1
[17179570.504000] EISA: Detected 0 cards.
[17179570.504000] NET: Registered protocol family 2
[17179570.528000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179570.556000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179570.556000] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[17179570.556000] TCP bind hash table entries: 65536 (order: 7, 786432 bytes)
[17179570.556000] TCP: Hash tables configured (established 131072 bind 65536)
[17179570.556000] TCP reno registered
[17179570.556000] TCP bic registered
[17179570.556000] NET: Registered protocol family 1
[17179570.556000] NET: Registered protocol family 8
[17179570.556000] NET: Registered protocol family 20
[17179570.556000] Starting balanced_irq
[17179570.556000] Using IPI No-Shortcut mode
[17179570.556000] ACPI wakeup devices: 
[17179570.556000] USB1 USB3 USB4 EHCI AZAL GLAN WLAN  LID PWRB 
[17179570.556000] ACPI: (supports S0 S3 S4 S5)
[17179570.556000] Freeing unused kernel memory: 332k freed
[17179570.600000] vga16fb: initializing
[17179570.600000] vga16fb: mapped to 0xc00a0000
[17179570.708000] Console: switching to colour frame buffer device 80x25
[17179570.708000] fb0: VGA16 VGA frame buffer device
[17179571.732000] Capability LSM initialized
[17179571.792000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179571.792000] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[17179571.792000] ACPI: Thermal Zone [THRM] (33 C)
[17179572.212000] ICH7: IDE controller at PCI slot 0000:00:1f.1
[17179572.212000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 177
[17179572.212000] ICH7: chipset revision 2
[17179572.212000] ICH7: not 100% native mode: will probe irqs later
[17179572.212000]     ide0: BM-DMA at 0xaf10-0xaf17, BIOS settings: hda:DMA, hdb:pio

```

---

### Post by samba on 2006-07-30
(suite)

```

[17179572.212000] Probing IDE interface ide0...
[17179574.432000] hda: MATSHITADVD-RAM UJ-842S, ATAPI CD/DVD-ROM drive
[17179575.492000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179575.500000] hda: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179575.500000] Uniform CD-ROM driver Revision: 3.20
[17179575.532000] SCSI subsystem initialized
[17179575.532000] ACPI: bus type scsi registered
[17179575.532000] libata version 1.20 loaded.
[17179575.532000] ahci 0000:00:1f.2: version 1.2
[17179575.532000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 217
[17179624.716000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179624.716000] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x5 impl SATA mode
[17179624.716000] ahci 0000:00:1f.2: flags: 64bit ncq ilck pm led clo pio slum part 
[17179624.716000] ata1: SATA max UDMA/133 cmd 0xF8884900 ctl 0x0 bmdma 0x0 irq 225
[17179624.716000] ata2: SATA max UDMA/133 cmd 0xF8884980 ctl 0x0 bmdma 0x0 irq 225
[17179624.716000] ata3: SATA max UDMA/133 cmd 0xF8884A00 ctl 0x0 bmdma 0x0 irq 225
[17179624.716000] ata4: SATA max UDMA/133 cmd 0xF8884A80 ctl 0x0 bmdma 0x0 irq 225
[17179624.928000] ata1: dev 0 cfg 00:045a 49:0f00 82:746b 83:7f69 84:6063 85:f469 86:3c49 87:6063 88:203f 93:0000
[17179624.928000] ata1: dev 0 ATA-7, max UDMA/100, 195371568 sectors: LBA48
[17179624.928000] sata_get_dev_handle: SATA dev addr=0x1f0002, handle=0xdffe4300
[17179624.932000] ata1: dev 0 configured for UDMA/100
[17179624.932000] sata_get_dev_handle: SATA dev addr=0x1f0002, handle=0xdffe4300
[17179624.932000] scsi0 : ahci
[17179625.136000] ata2: no device found (phy stat 00000000)
[17179625.136000] scsi1 : ahci
[17179625.396000] ata3: no device found (phy stat 00000000)
[17179625.396000] scsi2 : ahci
[17179625.628000] ata4: no device found (phy stat 00000000)
[17179625.628000] scsi3 : ahci
[17179625.628000]   Vendor: ATA       Model: HTS541010G9SA00   Rev: MBZO
[17179625.632000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179625.636000] Driver 'sd' needs updating - please use bus_type methods
[17179625.636000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[17179625.636000] SCSI device sda: drive cache: write back
[17179625.636000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[17179625.636000] SCSI device sda: drive cache: write back
[17179625.636000]  sda: sda1 sda2 sda3 < sda5 >
[17179626.028000] sd 0:0:0:0: Attached scsi disk sda
[17179626.368000] usbcore: registered new driver usbfs
[17179626.368000] usbcore: registered new driver hub
[17179626.372000] USB Universal Host Controller Interface driver v2.3
[17179626.372000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 233
[17179626.372000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179626.372000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179626.372000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179626.372000] uhci_hcd 0000:00:1d.0: irq 233, io base 0x0000afe0
[17179626.372000] hub 1-0:1.0: USB hub found
[17179626.372000] hub 1-0:1.0: 2 ports detected
[17179626.396000] ieee1394: Initialized config rom entry `ip1394'
[17179626.528000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 217
[17179626.528000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179626.528000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179626.528000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179626.528000] uhci_hcd 0000:00:1d.1: irq 217, io base 0x0000af80
[17179626.528000] hub 2-0:1.0: USB hub found
[17179626.528000] hub 2-0:1.0: 2 ports detected
[17179626.676000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 177
[17179626.676000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179626.676000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179626.676000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179626.676000] uhci_hcd 0000:00:1d.2: irq 177, io base 0x0000af60
[17179626.676000] hub 3-0:1.0: USB hub found
[17179626.676000] hub 3-0:1.0: 2 ports detected
[17179626.800000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 50
[17179626.800000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179626.800000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179626.800000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17179626.800000] uhci_hcd 0000:00:1d.3: irq 50, io base 0x0000af40
[17179626.800000] hub 4-0:1.0: USB hub found
[17179626.800000] hub 4-0:1.0: 2 ports detected
[17179626.928000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 233
[17179626.928000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179626.928000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179626.928000] ehci_hcd 0000:00:1d.7: debug port 1
[17179626.928000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17179626.928000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17179626.928000] ehci_hcd 0000:00:1d.7: irq 233, io mem 0xffd3fc00
[17179626.932000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179626.932000] hub 5-0:1.0: USB hub found
[17179626.932000] hub 5-0:1.0: 8 ports detected
[17179627.128000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[17179627.128000] PCI: Enabling device 0000:03:0b.1 (0000 -> 0002)
[17179627.128000] ACPI: PCI Interrupt 0000:03:0b.1[B] -> GSI 20 (level, low) -> IRQ 58
[17179627.180000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[58]  MMIO=[54006000-540067ff]  Max Packet=[2048]
[17179627.196000] Probing IDE interface ide1...
[17179629.384000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[17179629.384000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0000390000a4a255]
[17179629.416000] Attempting manual resume
[17179629.444000] EXT3-fs: mounted filesystem with ordered data mode.
[17179629.444000] kjournald starting.  Commit interval 5 seconds
[17179640.360000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179641.176000] APIC error on CPU0: 40(40)
[17179641.176000] APIC error on CPU1: 40(40)
[17179641.192000] APIC error on CPU0: 40(40)
[17179641.192000] APIC error on CPU1: 40(40)
[17179641.300000] Linux agpgart interface v0.101 (c) Dave Jones
[17179641.304000] agpgart: Detected an Intel 945GM Chipset.
[17179641.304000] agpgart: Detected 7932K stolen memory.
[17179641.320000] agpgart: AGP aperture is 256M @ 0xe0000000
[17179641.348000] hw_random hardware driver 1.0.0 loaded
[17179641.444000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179641.524000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179641.568000] ACPI: PCI Interrupt 0000:03:0b.0[A] -> GSI 21 (level, low) -> IRQ 185
[17179641.568000] Yenta: CardBus bridge found at 0000:03:0b.0 [1179:0001]
[17179641.568000] Yenta: Enabling burst memory read transactions
[17179641.568000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179641.568000] Yenta: Routing CardBus interrupts to PCI
[17179641.568000] Yenta TI: socket 0000:03:0b.0, mfunc 0x01aa1022, devctl 0x64
[17179641.712000] Intel(R) PRO/1000 Network Driver - version 7.0.33-k2
[17179641.712000] Copyright (c) 1999-2005 Intel Corporation.
[17179641.712000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 50
[17179641.712000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[17179641.712000] sdhci: Secure Digital Host Controller Interface driver, 0.10
[17179641.712000] sdhci: Copyright(c) Pierre Ossman
[17179641.760000] ieee80211_1_1_13_crypt: registered algorithm 'NULL'
[17179641.760000] ieee80211_1_1_13: 802.11 data/management/control stack, 1.1.13
[17179641.760000] ieee80211_1_1_13: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179641.772000] e1000: 0000:01:00.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:0e:7b:9f:37:dd
[17179641.780000] input: PC Speaker as /class/input/input1
[17179641.804000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 185
[17179641.804000] Socket status: 30000006
[17179641.804000] Yenta: Raising subordinate bus# of parent bus (#03) from #04 to #07
[17179641.804000] pcmcia: parent PCI bridge I/O window: 0x1000 - 0x1fff
[17179641.804000] cs: IO port probe 0x1000-0x1fff: clean.
[17179641.804000] pcmcia: parent PCI bridge Memory window: 0x52000000 - 0x54ffffff
[17179641.804000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x51ffffff
[17179641.832000] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[17179641.832000] PCI: Enabling device 0000:03:0b.3 (0000 -> 0002)
[17179641.832000] ACPI: PCI Interrupt 0000:03:0b.3[D] -> GSI 23 (level, low) -> IRQ 233
[17179641.880000] sdhci: ============== REGISTER DUMP ==============
[17179641.880000] sdhci: Sys addr: 0x00000000 | Version:  0x00008900
[17179641.880000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[17179641.884000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[17179641.884000] sdhci: Present:  0x000a0000 | Host ctl: 0x00000000
[17179641.884000] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[17179641.884000] sdhci: Walk up:  0x00000000 | Clock:    0x00000000
[17179641.884000] sdhci: Timeout:  0x0000000e | Int stat: 0x00000000
[17179641.884000] sdhci: Int enab: 0x11ff00cf | Sig enab: 0x11ff00cf
[17179641.884000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[17179641.884000] sdhci: Caps:     0x01c030b0 | Max curr: 0x00000000
[17179641.884000] sdhci: ===========================================
[17179641.884000] APIC error on CPU1: 40(40)
[17179641.884000] APIC error on CPU0: 40(40)
[17179641.932000] mmc0: SDHCI at 0x54006800 irq 233 DMA
[17179641.932000] PCI: Enabling device 0000:00:1b.0 (0000 -> 0002)
[17179641.932000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 66
[17179641.932000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[17179641.936000] ieee80211_crypt: registered algorithm 'NULL'
[17179641.940000] ieee80211: 802.11 data/management/control stack, git-1.1.7
[17179641.940000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179641.948000] input: PS/2 Mouse as /class/input/input2
[17179641.952000] APIC error on CPU1: 40(40)
[17179641.952000] APIC error on CPU0: 40(40)
[17179642.008000] APIC error on CPU0: 40(40)
[17179642.028000] APIC error on CPU1: 40(40)
[17179642.028000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input3
[17179642.028000] tpm_inf_pnp 00:09: Found TPM with ID IFX0102
[17179642.028000] tpm_inf_pnp 00:09: TPM found: config base 0x4e, io base 0x680, chip version 000b, vendor id 15d1 (Infineon), product id 000b (SLB 9635 TT 1.2)
[17179642.060000] ts: Compaq touchscreen protocol output
[17179642.108000] APIC error on CPU1: 40(40)
[17179642.108000] APIC error on CPU0: 40(40)
[17179642.128000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.0.5m
[17179642.128000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[17179642.224000] APIC error on CPU0: 40(40)
[17179642.224000] APIC error on CPU1: 40(40)
[17179642.236000] APIC error on CPU0: 40(40)
[17179642.236000] APIC error on CPU1: 40(40)
[17179642.280000] APIC error on CPU0: 40(40)
[17179642.280000] APIC error on CPU1: 40(40)
[17179642.300000] APIC error on CPU0: 40(40)
[17179642.300000] APIC error on CPU1: 40(40)
[17179642.656000] cs: IO port probe 0x100-0x3af: clean.
[17179642.656000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179642.656000] cs: IO port probe 0x820-0x8ff: clean.
[17179642.656000] cs: IO port probe 0xc00-0xcf7: clean.
[17179642.660000] cs: IO port probe 0xa00-0xaff: clean.
[17179643.384000] NET: Registered protocol family 17
[17179645.060000] e1000: eth0: e1000_watchdog_task: NIC Link is Up 1000 Mbps Full Duplex
[17179648.244000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 177
[17179648.244000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[17179648.244000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[17179649.360000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
[17179649.496000] Adding 3012148k swap on /dev/sda5.  Priority:-1 extents:1 across:3012148k
[17179649.564000] EXT3 FS on sda2, internal journal
[17179649.752000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179649.752000] md: bitmap version 4.39
[17179650.412000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179650.840000] cdrom: open failed.
[17179652.464000] ACPI: AC Adapter [ADP1] (on-line)
[17179652.464000] ACPI: Battery Slot [BAT1] (battery present)
[17179652.464000] ACPI: Battery Slot [BAT2] (battery absent)
[17179652.552000] ACPI: Power Button (FF) [PWRF]
[17179652.552000] ACPI: Lid Switch [LID]
[17179652.552000] ACPI: Power Button (CM) [PWRB]
[17179652.632000] ibm_acpi: ec object not found
[17179652.672000] pcc_acpi: loading...
[17179652.724000] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19a-dev
[17179652.724000] toshiba_acpi:     HCI method: \_SB_.VALZ.GHCI
[17179652.724000] toshiba_acpi: Toshiba hotkeys are sent as ACPI events
[17179652.724000] toshiba_acpi: ktoshkeyd will check 2 times per second
[17179652.724000] toshiba_acpi: Dropped 0 keys from the queue on startup
[17179652.740000] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
[17179653.648000] APIC error on CPU0: 40(40)
[17179653.648000] APIC error on CPU1: 40(40)
[17179653.672000] APIC error on CPU0: 40(40)
[17179653.672000] APIC error on CPU1: 40(40)
[17179653.992000] NET: Registered protocol family 10
[17179653.992000] lo: Disabled Privacy Extensions
[17179653.992000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17179653.992000] IPv6 over IPv4 tunneling driver
[17179654.772000] APIC error on CPU0: 40(40)
[17179654.772000] APIC error on CPU1: 40(40)
[17179655.448000] APIC error on CPU0: 40(40)
[17179655.448000] APIC error on CPU1: 40(40)
[17179655.532000] APIC error on CPU1: 40(40)
[17179655.532000] APIC error on CPU0: 40(40)
[17179655.588000] APIC error on CPU1: 40(40)
[17179655.588000] APIC error on CPU0: 40(40)
[17179657.476000] APIC error on CPU0: 40(40)
[17179657.476000] APIC error on CPU1: 40(40)
[17179657.604000] APIC error on CPU1: 40(40)
[17179657.604000] APIC error on CPU0: 40(40)
[17179657.624000] APIC error on CPU1: 40(40)
[17179657.624000] APIC error on CPU0: 40(40)
[17179657.680000] APIC error on CPU0: 40(40)
[17179657.680000] APIC error on CPU1: 40(40)
[17179658.732000] APIC error on CPU0: 40(40)
[17179658.732000] APIC error on CPU1: 40(40)
[17179658.756000] APIC error on CPU0: 40(40)
[17179658.756000] APIC error on CPU1: 40(40)
[17179659.304000] APIC error on CPU0: 40(40)
[17179659.304000] APIC error on CPU1: 40(40)
[17179659.728000] APIC error on CPU0: 40(40)
[17179659.728000] APIC error on CPU1: 40(40)
[17179659.900000] APIC error on CPU0: 40(40)
[17179659.900000] APIC error on CPU1: 40(40)
[17179659.952000] lp: driver loaded but no devices found
[17179659.972000] ppdev: user-space parallel port driver
[17179659.976000] APIC error on CPU1: 40(40)
[17179659.976000] APIC error on CPU0: 40(40)
[17179660.000000] APIC error on CPU1: 40(40)
[17179660.000000] APIC error on CPU0: 40(40)
[17179660.020000] APIC error on CPU0: 40(40)
[17179660.020000] APIC error on CPU1: 40(40)
[17179660.132000] [drm] Initialized drm 1.0.1 20051102
[17179660.132000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 50
[17179660.132000] [drm] Initialized i915 1.4.0 20060119 on minor 0
[17179661.316000] apm: BIOS not found.
[17179662.156000] Bluetooth: Core ver 2.8
[17179662.156000] NET: Registered protocol family 31
[17179662.156000] Bluetooth: HCI device and connection manager initialized
[17179662.156000] Bluetooth: HCI socket layer initialized
[17179662.168000] Bluetooth: L2CAP ver 2.8
[17179662.168000] Bluetooth: L2CAP socket layer initialized
[17179662.184000] Bluetooth: RFCOMM socket layer initialized
[17179662.184000] Bluetooth: RFCOMM TTY layer initialized
[17179662.184000] Bluetooth: RFCOMM ver 1.7
[17179664.824000] eth0: no IPv6 routers present
[17179678.948000] eth0: no IPv6 routers present
[17179684.108000] usb 3-1: new full speed USB device using uhci_hcd and address 2
[17179685.396000] usbcore: registered new driver hiddev
[17179685.400000] input: Logitech Logitech USB Headset as /class/input/input4
[17179685.400000] input: USB HID v1.00 Device [Logitech Logitech USB Headset] on usb-0000:00:1d.2-1
[17179685.400000] usbcore: registered new driver usbhid
[17179685.400000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179685.884000] usb 3-1: USB disconnect, address 2
[17179686.264000] usbcore: registered new driver snd-usb-audio
[17179724.784000] usb 3-1: new full speed USB device using uhci_hcd and address 3
[17179725.092000] input: Logitech Logitech USB Headset as /class/input/input5
[17179725.092000] input: USB HID v1.00 Device [Logitech Logitech USB Headset] on usb-0000:00:1d.2-1
[17179733.872000] APIC error on CPU0: 40(40)
[17179733.872000] APIC error on CPU1: 40(40)
[17179734.312000] APIC error on CPU0: 40(40)
[17179734.312000] APIC error on CPU1: 40(40)
[17179734.412000] APIC error on CPU0: 40(40)
[17179734.412000] APIC error on CPU1: 40(40)
[17179734.476000] APIC error on CPU0: 40(40)
[17179734.476000] APIC error on CPU1: 40(40)


```

---

### Post by fishyf on 2007-07-14
Hi,
did you get anywhere with this, it's just started happening on my Satelite pro with feisty.

Actually, it's not hanging, but there are lots of similar messages in dmesg.

---

### Post by fhco on 2007-07-16
Just chiming in to say the same thing is happening with my Toshiba Satellite U205 (Core 2) in Feisty, where it did not happen in Edgy. I'm still searching for a fix, but haven't found anything. Adding the "noapic" option at boot seems to have stopped or slowed the locking up issue I was having, but that might just be placebo effect since it wasn't happening THAT often. I still get the stream of error messages, though.

---

