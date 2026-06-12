---
title: "Kernel panic on bootup"
date: 2007-10-23
forum: Dell  Ubuntu Support
---

### Post by Go2doug on 2007-10-23
About one-third of the time when I boot to Ubuntu, a kernel panic occurs.

I am using Kubuntu 7.10 (problem also occurred with 7.04). I have a Dell XPS 410n, Nvidia 8600 GTS, Creative Sound Blaster Audigy, 2 GB RAM, 2.13 GHz dualcore Intel CPU. I have Windows XP and Vista in separate partitions.

When I power up the PC, the grub screen loads but sometimes when I choose Ubuntu, I get a kernel panic with a screen full of error codes and such that make no sense to me.

The panics always mention EIP. Below are the bottom two lines that have appeared in the last two panics:

[30.239888] EIP: [<c01201672] touche_cache + 0x57/0xb0 SS: ESP 0068:df863d38
[30.239994] Kernel panic - not syncing: Attempted to kill init!

[35.60945] EIP: [<c01023f2>] cpu_idle +0x32/0xe0 SS: ESP 0068:df839fa4
[35.609557] Kernel panic - not syncing: Attempted to kill init!

After a kernel panic, I booted to the Ubuntu Live CD, and I entered these commands:

```
mkdir /fixit
mount -t ext3 /dev/sda4 /fixit
chroot /fixit
dmesg
```

I also ran the command "dmesg > /tmp/kernel.panic.txt."

The results of "dmesg" and the command above are attached in .txt files.

I have also run the Memtest that is a choice in the grub screen. It came back with no errors.

If this panic cannot be solved on this board, what other option do I have? How can I submit a bug report directly to Canonical so the Ubuntu developers can analyze the panic?

Many thanks in advance.

**Edit:** Apparently I can't attach the text files because they are too big. I will reply with the output in separate posts in this thread.

---

### Post by Go2doug on 2007-10-23
**Results of "dmesg"**

 61)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x05] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x07] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high level lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] Built 1 zonelists.  Total pages: 519767
[    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2128.049 MHz processor.
[   29.103653] Console: colour VGA+ 80x25
[   29.103946] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   29.104220] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   29.168590] Memory: 2065716k/2095436k available (2015k kernel code, 28428k reserved, 916k data, 364k init, 1177932k highmem)
[   29.168597] virtual kernel memory layout:
[   29.168598]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   29.168598]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   29.168599]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   29.168600]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   29.168601]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   29.168602]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   29.168603]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   29.168605] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   29.168634] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   29.168748] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   29.168752] hpet0: 3 64-bit timers, 14318180 Hz
[   29.249731] Calibrating delay using timer specific routine.. 4259.06 BogoMIPS (lpj=8518137)
[   29.249748] Security Framework v1.0.0 initialized
[   29.249753] SELinux:  Disabled at boot.
[   29.249762] Mount-cache hash table entries: 512
[   29.249860] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[   29.249866] monitor/mwait feature present.
[   29.249867] using mwait in idle threads.
[   29.249871] CPU: L1 I cache: 32K, L1 D cache: 32K
[   29.249873] CPU: L2 cache: 4096K
[   29.249875] CPU: Physical Processor ID: 0
[   29.249876] CPU: Processor Core ID: 0
[   29.249878] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
[   29.249885] Compat vDSO mapped to ffffe000.
[   29.249896] Checking 'hlt' instruction... OK.
[   29.265820] SMP alternatives: switching to UP code
[   29.266176] Early unpacking initramfs... done
[   29.531026] ACPI: Core revision 20070126
[   29.585625] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   29.684758] CPU0: Intel(R) Core(TM)2 CPU          6420  @ 2.13GHz stepping 06
[   29.684770] SMP alternatives: switching to SMP code
[   29.684822] Booting processor 1/1 eip 3000
[   29.695174] Initializing CPU#1
[   29.773501] Calibrating delay using timer specific routine.. 4256.01 BogoMIPS (lpj=8512028)
[   29.773506] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[   29.773510] monitor/mwait feature present.
[   29.773513] CPU: L1 I cache: 32K, L1 D cache: 32K
[   29.773514] CPU: L2 cache: 4096K
[   29.773516] CPU: Physical Processor ID: 0
[   29.773517] CPU: Processor Core ID: 1
[   29.773518] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
[   29.774120] CPU1: Intel(R) Core(TM)2 CPU          6420  @ 2.13GHz stepping 06
[   29.774136] Total of 2 processors activated (8515.08 BogoMIPS).
[   29.774274] ENABLING IO-APIC IRQs
[   29.774436] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   29.921507] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   29.941512] Brought up 2 CPUs
[   30.094500] migration_cost=42
[   30.094602] Booting paravirtualized kernel on bare hardware
[   30.094651] Time: 21:04:46  Date: 09/23/107
[   30.094666] NET: Registered protocol family 16
[   30.094729] EISA bus registered
[   30.094733] ACPI: bus type pci registered
[   30.128813] PCI: PCI BIOS revision 2.10 entry at 0xfb78a, last bus=4
[   30.128815] PCI: Using configuration type 1
[   30.128816] Setting up standard PCI resources
[   30.140609] ACPI: EC: Look up EC in DSDT
[   30.182835] ACPI: System BIOS is requesting _OSI(Linux)
[   30.182837] ACPI: Please test with "acpi_osi=!Linux"
[   30.182838] Please send dmidecode to [email]linux-acpi@vger.kernel.org[/email]
[   30.199656] ACPI: Interpreter enabled
[   30.199659] ACPI: (supports S0 S3 S4 S5)
[   30.199672] ACPI: Using IOAPIC for interrupt routing
[   30.281750] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   30.281767] PCI: Probing PCI hardware (bus 00)
[   30.282301] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[   30.282305] PCI quirk: region 0880-08bf claimed by ICH6 GPIO
[   30.282778] PCI: Transparent bridge - 0000:00:1e.0
[   30.282823] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   30.283527] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI4._PRT]
[   30.284111] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
[   30.284596] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   30.285070] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI5._PRT]
[   31.219677] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[   31.220446] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[   31.221205] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 15)
[   31.221951] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[   31.222713] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[   31.223469] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[   31.224235] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[   31.224986] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 5 6 7 9 10 11 12 15)
[   31.225222] Linux Plug and Play Support v0.97 (c) Adam Belay
[   31.225231] pnp: PnP ACPI init
[   31.225237] ACPI: bus type pnp registered
[   31.268345] pnp: PnP ACPI: found 9 devices
[   31.268346] ACPI: ACPI bus type pnp unregistered
[   31.268350] PnPBIOS: Disabled by ACPI PNP
[   31.268383] PCI: Using ACPI for IRQ routing
[   31.268385] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   31.279020] NET: Registered protocol family 8
[   31.279022] NET: Registered protocol family 20
[   31.279058] pnp: 00:01: ioport range 0x800-0x85f has been reserved
[   31.279060] pnp: 00:01: ioport range 0xc00-0xc7f has been reserved
[   31.279063] pnp: 00:01: ioport range 0x860-0x8ff could not be reserved
[   31.279069] pnp: 00:06: iomem range 0x0-0x9ffff could not be reserved
[   31.279071] pnp: 00:06: iomem range 0x100000-0xffffff could not be reserved
[   31.279074] pnp: 00:06: iomem range 0x1000000-0x7fe53bff could not be reserved
[   31.279076] pnp: 00:06: iomem range 0xf0000-0xfffff could not be reserved
[   31.279080] pnp: 00:07: ioport range 0x100-0x1fe has been reserved
[   31.279082] pnp: 00:07: ioport range 0x200-0x277 has been reserved
[   31.279084] pnp: 00:07: ioport range 0x280-0x2e7 has been reserved
[   31.279086] pnp: 00:07: ioport range 0x2e8-0x2ef has been reserved
[   31.279088] pnp: 00:07: ioport range 0x2f0-0x2f7 has been reserved
[   31.279090] pnp: 00:07: ioport range 0x2f8-0x2ff has been reserved
[   31.279092] pnp: 00:07: ioport range 0x300-0x377 has been reserved
[   31.279094] pnp: 00:07: ioport range 0x380-0x3bb has been reserved
[   31.279097] pnp: 00:07: iomem range 0xe0000000-0xefffffff could not be reserved
[   31.279099] pnp: 00:07: iomem range 0xfeda0000-0xfedacfff has been reserved
[   31.280850] Time: tsc clocksource has been installed.
[   31.280859] Switched to high resolution mode on CPU 0
[   31.280923] Switched to high resolution mode on CPU 1
[   31.309315] PCI: Bridge: 0000:00:01.0
[   31.309317]   IO window: d000-dfff
[   31.309320]   MEM window: dc000000-dfefffff
[   31.309323]   PREFETCH window: c0000000-cfffffff
[   31.309326] PCI: Bridge: 0000:00:1c.0
[   31.309327]   IO window: disabled.
[   31.309331]   MEM window: dbf00000-dbffffff
[   31.309334]   PREFETCH window: disabled.
[   31.309337] PCI: Bridge: 0000:00:1c.4
[   31.309338]   IO window: disabled.
[   31.309342]   MEM window: disabled.
[   31.309345]   PREFETCH window: disabled.
[   31.309348] PCI: Bridge: 0000:00:1e.0
[   31.309351]   IO window: c000-cfff
[   31.309355]   MEM window: dbe00000-dbefffff
[   31.309357]   PREFETCH window: disabled.
[   31.309369] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   31.309373] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   31.309387] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   31.309391] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   31.309404] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
[   31.309408] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   31.309417] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   31.309425] NET: Registered protocol family 2
[   31.360749] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   31.360807] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   31.361320] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   31.361485] TCP: Hash tables configured (established 131072 bind 65536)
[   31.361487] TCP reno registered
[   31.376836] checking if image is initramfs... it is
[   31.901699] Freeing initrd memory: 7305k freed
[   31.901785] Simple Boot Flag at 0x7a set to 0x1
[   31.902178] audit: initializing netlink socket (disabled)
[   31.902190] audit(1193173487.488:1): initialized
[   31.902265] highmem bounce pool size: 64 pages
[   31.903744] VFS: Disk quotas dquot_6.5.1
[   31.903781] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   31.903852] io scheduler noop registered
[   31.903854] io scheduler anticipatory registered
[   31.903856] io scheduler deadline registered
[   31.903866] io scheduler cfq registered (default)
[   31.916562] Boot video device is 0000:01:00.0
[   31.916640] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   31.916675] assign_interrupt_mode Found MSI capability
[   31.916678] Allocate Port Service[0000:00:01.0:pcie00]
[   31.916763] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   31.916796] assign_interrupt_mode Found MSI capability
[   31.916798] Allocate Port Service[0000:00:1c.0:pcie00]
[   31.916823] Allocate Port Service[0000:00:1c.0:pcie02]
[   31.916887] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   31.916920] assign_interrupt_mode Found MSI capability
[   31.916922] Allocate Port Service[0000:00:1c.4:pcie00]
[   31.916949] Allocate Port Service[0000:00:1c.4:pcie02]
[   31.917063] isapnp: Scanning for PnP cards...
[   32.269733] isapnp: No Plug & Play device found
[   32.285531] Real Time Clock Driver v1.12ac
[   32.285822] hpet_resources: 0xfed00000 is busy
[   32.285832] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   32.286613] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   32.286712] input: Macintosh mouse button emulation as /class/input/input0
[   32.286804] PNP: No PS/2 controller found. Probing ports directly.
[   32.289310] serio: i8042 KBD port at 0x60,0x64 irq 1
[   32.289314] serio: i8042 AUX port at 0x60,0x64 irq 12
[   32.289393] mice: PS/2 mouse device common for all mice
[   32.289466] EISA: Probing bus 0 at eisa.0
[   32.289491] EISA: Detected 0 cards.
[   32.289551] TCP cubic registered
[   32.289560] NET: Registered protocol family 1
[   32.289575] Using IPI No-Shortcut mode
[   32.289695]   Magic number: 11:494:96
[   32.289929] Freeing unused kernel memory: 364k freed
[   33.447657] AppArmor: AppArmor initializedaudit(1193173488.988:2):  type=1505 info="AppArmor initialized" pid=1192
[   33.453647] fuse init (API version 7.8)
[   33.457796] Failure registering capabilities with primary security module.
[   33.475072] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   33.475080] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   33.780186] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
[   33.780189] Copyright (c) 1999-2006 Intel Corporation.
[   33.780222] ACPI: PCI Interrupt 0000:00:19.0[A] -> GSI 21 (level, low) -> IRQ 17
[   33.780231] PCI: Setting latency timer of device 0000:00:19.0 to 64
[   33.786437] usbcore: registered new interface driver usbfs
[   33.786454] usbcore: registered new interface driver hub
[   33.791741] usbcore: registered new device driver usb
[   33.792309] USB Universal Host Controller Interface driver v3.0
[   33.820385] e1000: 0000:00:19.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:19:d1:6a:d9:7c
[   33.856669] SCSI subsystem initialized
[   33.860411] libata version 2.21 loaded.
[   33.917531] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   33.917550] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[   33.917559] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   33.917562] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   33.917647] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   33.917672] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000ff20
[   33.917758] usb usb1: configuration #1 chosen from 1 choice
[   33.917777] hub 1-0:1.0: USB hub found
[   33.917782] hub 1-0:1.0: 2 ports detected
[   34.019665] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 17 (level, low) -> IRQ 18
[   34.019672] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   34.019676] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   34.019695] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   34.019719] uhci_hcd 0000:00:1a.1: irq 18, io base 0x0000ff00
[   34.019809] usb usb2: configuration #1 chosen from 1 choice
[   34.019840] hub 2-0:1.0: USB hub found
[   34.019844] hub 2-0:1.0: 2 ports detected
[   34.123556] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[   34.123563] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   34.123566] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   34.123585] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[   34.123609] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000ff80
[   34.123698] usb usb3: configuration #1 chosen from 1 choice
[   34.123722] hub 3-0:1.0: USB hub found
[   34.123728] hub 3-0:1.0: 2 ports detected
[   34.227524] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 18
[   34.227532] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   34.227535] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   34.227556] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[   34.227577] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000ff60
[   34.227666] usb usb4: configuration #1 chosen from 1 choice
[   34.227691] hub 4-0:1.0: USB hub found
[   34.227696] hub 4-0:1.0: 2 ports detected
[   34.259451] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   34.331516] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
[   34.331523] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   34.331526] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   34.331549] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[   34.331573] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000ff40
[   34.331661] usb usb5: configuration #1 chosen from 1 choice
[   34.331684] hub 5-0:1.0: USB hub found
[   34.331690] hub 5-0:1.0: 2 ports detected
[   34.435540] usb 1-1: configuration #1 chosen from 1 choice
[   34.436288] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 22 (level, low) -> IRQ 21
[   34.436298] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   34.436302] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   34.437111] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[   34.437134] ehci_hcd 0000:00:1a.7: debug port 1
[   34.437140] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   34.437146] ehci_hcd 0000:00:1a.7: irq 21, io mem 0xdffdec00
[   34.441216] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   34.441269] usb usb6: configuration #1 chosen from 1 choice
[   34.441288] hub 6-0:1.0: USB hub found
[   34.441293] hub 6-0:1.0: 4 ports detected
[   34.543387] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[   34.543397] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   34.543401] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   34.543423] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[   34.543450] ehci_hcd 0000:00:1d.7: debug port 1
[   34.543456] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   34.543462] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xff980800
[   34.547357] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   34.547417] usb usb7: configuration #1 chosen from 1 choice
[   34.547437] hub 7-0:1.0: USB hub found
[   34.547442] hub 7-0:1.0: 6 ports detected
[   34.599301] usb 1-1: USB disconnect, address 2
[   34.653051] ata_piix 0000:00:1f.2: version 2.11
[   34.653056] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   34.653074] ACPI: PCI Interrupt 0000:00:1f.2[C] -> GSI 20 (level, low) -> IRQ 22
[   34.653099] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   34.653140] scsi0 : ata_piix
[   34.653168] scsi1 : ata_piix
[   34.653186] ata1: SATA max UDMA/133 cmd 0x0001fe00 ctl 0x0001fe12 bmdma 0x0001fec0 irq 22
[   34.653189] ata2: SATA max UDMA/133 cmd 0x0001fe20 ctl 0x0001fe32 bmdma 0x0001fec8 irq 22
[   34.845461] ata1.00: ATA-7: ST3320620AS, 3.ADG, max UDMA/133
[   34.845465] ata1.00: 625142448 sectors, multi 8: LBA48 NCQ (depth 0/32)
[   34.912066] ata1.00: configured for UDMA/133
[   35.350945] usb 6-1: new high speed USB device using ehci_hcd and address 2
[   35.387077] ata2.00: ATAPI: TSSTcorp DVD+/-RW TS-H653A, D500, max UDMA/33
[   35.387080] ata2.00: applying bridge limits
[   35.485049] usb 6-1: configuration #1 chosen from 1 choice
[   35.559004] ata2.00: configured for UDMA/33
[   35.559104] scsi 0:0:0:0: Direct-Access     ATA      ST3320620AS      3.AD PQ: 0 ANSI: 5
[   35.559624] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-H653A D500 PQ: 0 ANSI: 5
[   35.559685] ata_piix 0000:00:1f.5: MAP [ P0 P2 P1 P3 ]
[   35.714789] ACPI: PCI Interrupt 0000:00:1f.5[C] -> GSI 20 (level, low) -> IRQ 22
[   35.714817] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   35.714848] scsi2 : ata_piix
[   35.714888] scsi3 : ata_piix
[   35.714910] ata3: SATA max UDMA/133 cmd 0x0001fe40 ctl 0x0001fe52 bmdma 0x0001fed0 irq 22
[   35.714913] ata4: SATA max UDMA/133 cmd 0x0001fe60 ctl 0x0001fe72 bmdma 0x0001fed8 irq 22
[   35.722766] usb 6-2: new high speed USB device using ehci_hcd and address 3
[   35.855141] usb 6-2: configuration #1 chosen from 1 choice
[   35.855226] hub 6-2:1.0: USB hub found
[   35.855325] hub 6-2:1.0: 4 ports detected
[   36.039783] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   36.039792] sd 0:0:0:0: [sda] Write Protect is off
[   36.039794] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   36.039806] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   36.039836] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   36.039843] sd 0:0:0:0: [sda] Write Protect is off
[   36.039845] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   36.039856] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   36.039859]  sda: sda1 sda2 sda3 sda4
[   36.079094] sd 0:0:0:0: [sda] Attached SCSI disk
[   36.081818] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   36.081832] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   36.086101] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   36.086104] Uniform CD-ROM driver Revision: 3.20
[   36.086231] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   36.626355] usb 7-5: new high speed USB device using ehci_hcd and address 4
[   36.760029] usb 7-5: configuration #1 chosen from 1 choice
[   36.761013] usbcore: registered new interface driver libusual
[   36.765847] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   36.765851] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   36.767079] Initializing USB Mass Storage driver...
[   36.998186] usb 4-1: new low speed USB device using uhci_hcd and address 2
[   37.011396] kjournald starting.  Commit interval 5 seconds
[   37.011400] EXT3-fs: mounted filesystem with ordered data mode.
[   37.156451] usb 4-1: configuration #1 chosen from 1 choice
[   37.398039] usb 4-2: new full speed USB device using uhci_hcd and address 3
[   37.436841] ISO 9660 Extensions: Microsoft Joliet Level 3
[   37.486190] ISO 9660 Extensions: RRIP_1991A
[   37.576268] usb 4-2: configuration #1 chosen from 1 choice
[   37.582225] hub 4-2:1.0: USB hub found
[   37.584190] hub 4-2:1.0: 3 ports detected
[   37.692266] scsi4 : SCSI emulation for USB Mass Storage devices
[   37.692336] usb-storage: device found at 2
[   37.692338] usb-storage: waiting for device to settle before scanning
[   37.738098] Registering unionfs 1.4
[   37.738100] unionfs: debugging is not enabled
[   37.745875] loop: module loaded
[   37.895061] usb 4-2.1: new full speed USB device using uhci_hcd and address 4
[   38.032074] usb 4-2.1: configuration #1 chosen from 1 choice
[   38.045014] usbcore: registered new interface driver usb-storage
[   38.045017] usbcore: registered new interface driver hiddev
[   38.045019] USB Mass Storage support registered.
[   38.059184] input: HID 0461:4d09 as /class/input/input1
[   38.059204] input: USB HID v1.00 Mouse [HID 0461:4d09] on usb-0000:00:1d.1-1
[   38.062152] input: Dell Dell USB Keyboard Hub as /class/input/input2
[   38.062158] input: USB HID v1.10 Keyboard [Dell Dell USB Keyboard Hub] on usb-0000:00:1d.1-2.1
[   38.072024] input: Dell Dell USB Keyboard Hub as /class/input/input3
[   38.072030] input: USB HID v1.10 Device [Dell Dell USB Keyboard Hub] on usb-0000:00:1d.1-2.1
[   38.072038] usbcore: registered new interface driver usbhid
[   38.072041] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   38.316895] squashfs: version 3.2-UBUNTU (2007/07/26) Phillip Lougher
[   42.688094] usb-storage: device scan complete
[   42.688844] scsi 4:0:0:0: Direct-Access     Canon    MP600Storage     0103 PQ: 0 ANSI: 2
[   42.691105] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   42.691144] sd 4:0:0:0: Attached scsi generic sg2 type 0
[   78.655322] Linux agpgart interface v0.102 (c) Dave Jones
[   78.842847] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   78.983396] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   79.042013] iTCO_vendor_support: vendor-support=0
[   79.043046] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   79.043118] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   79.043125] iTCO_wdt: No card detected
[   79.260243] input: PC Speaker as /class/input/input4
[   79.505813] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x04A9 pid 0x1718
[   79.505830] usbcore: registered new interface driver usblp
[   79.505832] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   79.784919] usbcore: registered new interface driver xpad
[   79.784923] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   80.084582] ACPI: PCI Interrupt 0000:04:04.0[A] -> GSI 16 (level, low) -> IRQ 16
[   80.084599] snd-ca0106: Model 100a Rev 00000000 Serial 100a1102
[   80.999157] Adding 996020k swap on /dev/sda1.  Priority:-1 extents:1 across:996020k
[   82.257476] No dock devices found.
[   82.325505] input: Power Button (FF) as /class/input/input5
[   82.325648] ACPI: Power Button (FF) [PWRF]
[   82.326314] input: Power Button (CM) as /class/input/input6
[   82.326431] ACPI: Power Button (CM) [VBTN]
[   86.938969] lp: driver loaded but no devices found
[   86.963770] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   86.963774] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[   86.976984] ppdev: user-space parallel port driver
[   89.739380] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   89.739384] apm: disabled - APM is not SMP safe.
[   91.875194] Failure registering capabilities with primary security module.
[   95.843294] Bluetooth: Core ver 2.11
[   95.843344] NET: Registered protocol family 31
[   95.843346] Bluetooth: HCI device and connection manager initialized
[   95.843348] Bluetooth: HCI socket layer initialized
[   96.237074] Bluetooth: L2CAP ver 2.8
[   96.237077] Bluetooth: L2CAP socket layer initialized
[   96.258761] Bluetooth: RFCOMM socket layer initialized
[   96.258770] Bluetooth: RFCOMM TTY layer initialized
[   96.258772] Bluetooth: RFCOMM ver 1.8
[   99.833946] NET: Registered protocol family 17
[  108.527164] NET: Registered protocol family 10
[  108.527237] lo: Disabled Privacy Extensions
[  119.040771] eth0: no IPv6 routers present
[  244.338377] kjournald starting.  Commit interval 5 seconds
[  244.338629] EXT3 FS on sda4, internal journal
[  244.338697] EXT3-fs: mounted filesystem with ordered data mode.

---

### Post by Go2doug on 2007-10-23
**Results of "dmesg > /tmp/kernel.panic.txt"**

[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fe53c00 (usable)
[    0.000000]  BIOS-e820: 000000007fe53c00 - 000000007fe55c00 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fe55c00 - 000000007fe57c00 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fe57c00 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fe710
[    0.000000] Entering add_active_range(0, 0, 523859) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   523859
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   523859
[    0.000000] On node 0 totalpages: 523859
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2300 pages used for memmap
[    0.000000]   HighMem zone: 292183 pages, LIFO batch:31
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FEBF0 checksum 0
[    0.000000] ACPI: RSDP 000FEBF0, 0024 (r2 DELL  )
[    0.000000] ACPI: XSDT 000FD08B, 0064 (r1 DELL    B8K           14 ASL        61)
[    0.000000] ACPI: FACP 000FD1AB, 00F4 (r3 DELL    B8K           14 ASL        61)
[    0.000000] ACPI: DSDT FFFCD3BD, 333E (r1   DELL    dt_ex     1000 INTL 20050624)
[    0.000000] ACPI: FACS 7FE53C00, 0040
[    0.000000] ACPI: SSDT FFFD09D9, 009C (r1   DELL    st_ex     1000 INTL 20050624)
[    0.000000] ACPI: APIC 000FD29F, 0092 (r1 DELL    B8K           14 ASL        61)
[    0.000000] ACPI: BOOT 000FD331, 0028 (r1 DELL    B8K           14 ASL        61)
[    0.000000] ACPI: MCFG 000FD359, 003E (r1 DELL    B8K           14 ASL        61)
[    0.000000] ACPI: HPET 000FD397, 0038 (r1 DELL    B8K           14 ASL        61)
[    0.000000] ACPI: DUMY 7FE55C00, 0024 (r1 DELL    B8K           14 ASL        61)
[    0.000000] ACPI: SLIC 000FD3CF, 0176 (r1 DELL    B8K           14 ASL        61)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x05] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x07] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high level lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] Built 1 zonelists.  Total pages: 519767
[    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2128.049 MHz processor.
[   29.103653] Console: colour VGA+ 80x25
[   29.103946] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   29.104220] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   29.168590] Memory: 2065716k/2095436k available (2015k kernel code, 28428k reserved, 916k data, 364k init, 1177932k highmem)
[   29.168597] virtual kernel memory layout:
[   29.168598]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   29.168598]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   29.168599]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   29.168600]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   29.168601]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   29.168602]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   29.168603]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   29.168605] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   29.168634] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   29.168748] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   29.168752] hpet0: 3 64-bit timers, 14318180 Hz
[   29.249731] Calibrating delay using timer specific routine.. 4259.06 BogoMIPS (lpj=8518137)
[   29.249748] Security Framework v1.0.0 initialized
[   29.249753] SELinux:  Disabled at boot.
[   29.249762] Mount-cache hash table entries: 512
[   29.249860] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[   29.249866] monitor/mwait feature present.
[   29.249867] using mwait in idle threads.
[   29.249871] CPU: L1 I cache: 32K, L1 D cache: 32K
[   29.249873] CPU: L2 cache: 4096K
[   29.249875] CPU: Physical Processor ID: 0
[   29.249876] CPU: Processor Core ID: 0
[   29.249878] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
[   29.249885] Compat vDSO mapped to ffffe000.
[   29.249896] Checking 'hlt' instruction... OK.
[   29.265820] SMP alternatives: switching to UP code
[   29.266176] Early unpacking initramfs... done
[   29.531026] ACPI: Core revision 20070126
[   29.585625] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   29.684758] CPU0: Intel(R) Core(TM)2 CPU          6420  @ 2.13GHz stepping 06
[   29.684770] SMP alternatives: switching to SMP code
[   29.684822] Booting processor 1/1 eip 3000
[   29.695174] Initializing CPU#1
[   29.773501] Calibrating delay using timer specific routine.. 4256.01 BogoMIPS (lpj=8512028)
[   29.773506] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[   29.773510] monitor/mwait feature present.
[   29.773513] CPU: L1 I cache: 32K, L1 D cache: 32K
[   29.773514] CPU: L2 cache: 4096K
[   29.773516] CPU: Physical Processor ID: 0
[   29.773517] CPU: Processor Core ID: 1
[   29.773518] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
[   29.774120] CPU1: Intel(R) Core(TM)2 CPU          6420  @ 2.13GHz stepping 06
[   29.774136] Total of 2 processors activated (8515.08 BogoMIPS).
[   29.774274] ENABLING IO-APIC IRQs
[   29.774436] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   29.921507] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   29.941512] Brought up 2 CPUs
[   30.094500] migration_cost=42
[   30.094602] Booting paravirtualized kernel on bare hardware
[   30.094651] Time: 21:04:46  Date: 09/23/107
[   30.094666] NET: Registered protocol family 16
[   30.094729] EISA bus registered
[   30.094733] ACPI: bus type pci registered
[   30.128813] PCI: PCI BIOS revision 2.10 entry at 0xfb78a, last bus=4
[   30.128815] PCI: Using configuration type 1
[   30.128816] Setting up standard PCI resources
[   30.140609] ACPI: EC: Look up EC in DSDT
[   30.182835] ACPI: System BIOS is requesting _OSI(Linux)
[   30.182837] ACPI: Please test with "acpi_osi=!Linux"
[   30.182838] Please send dmidecode to [email]linux-acpi@vger.kernel.org[/email]
[   30.199656] ACPI: Interpreter enabled
[   30.199659] ACPI: (supports S0 S3 S4 S5)
[   30.199672] ACPI: Using IOAPIC for interrupt routing
[   30.281750] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   30.281767] PCI: Probing PCI hardware (bus 00)
[   30.282301] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[   30.282305] PCI quirk: region 0880-08bf claimed by ICH6 GPIO
[   30.282778] PCI: Transparent bridge - 0000:00:1e.0
[   30.282823] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   30.283527] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI4._PRT]
[   30.284111] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
[   30.284596] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   30.285070] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI5._PRT]
[   31.219677] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[   31.220446] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[   31.221205] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 15)
[   31.221951] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[   31.222713] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[   31.223469] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[   31.224235] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[   31.224986] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 5 6 7 9 10 11 12 15)
[   31.225222] Linux Plug and Play Support v0.97 (c) Adam Belay
[   31.225231] pnp: PnP ACPI init
[   31.225237] ACPI: bus type pnp registered
[   31.268345] pnp: PnP ACPI: found 9 devices
[   31.268346] ACPI: ACPI bus type pnp unregistered
[   31.268350] PnPBIOS: Disabled by ACPI PNP
[   31.268383] PCI: Using ACPI for IRQ routing
[   31.268385] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   31.279020] NET: Registered protocol family 8
[   31.279022] NET: Registered protocol family 20
[   31.279058] pnp: 00:01: ioport range 0x800-0x85f has been reserved
[   31.279060] pnp: 00:01: ioport range 0xc00-0xc7f has been reserved
[   31.279063] pnp: 00:01: ioport range 0x860-0x8ff could not be reserved
[   31.279069] pnp: 00:06: iomem range 0x0-0x9ffff could not be reserved
[   31.279071] pnp: 00:06: iomem range 0x100000-0xffffff could not be reserved
[   31.279074] pnp: 00:06: iomem range 0x1000000-0x7fe53bff could not be reserved
[   31.279076] pnp: 00:06: iomem range 0xf0000-0xfffff could not be reserved
[   31.279080] pnp: 00:07: ioport range 0x100-0x1fe has been reserved
[   31.279082] pnp: 00:07: ioport range 0x200-0x277 has been reserved
[   31.279084] pnp: 00:07: ioport range 0x280-0x2e7 has been reserved
[   31.279086] pnp: 00:07: ioport range 0x2e8-0x2ef has been reserved
[   31.279088] pnp: 00:07: ioport range 0x2f0-0x2f7 has been reserved
[   31.279090] pnp: 00:07: ioport range 0x2f8-0x2ff has been reserved
[   31.279092] pnp: 00:07: ioport range 0x300-0x377 has been reserved
[   31.279094] pnp: 00:07: ioport range 0x380-0x3bb has been reserved
[   31.279097] pnp: 00:07: iomem range 0xe0000000-0xefffffff could not be reserved
[   31.279099] pnp: 00:07: iomem range 0xfeda0000-0xfedacfff has been reserved
[   31.280850] Time: tsc clocksource has been installed.
[   31.280859] Switched to high resolution mode on CPU 0
[   31.280923] Switched to high resolution mode on CPU 1
[   31.309315] PCI: Bridge: 0000:00:01.0
[   31.309317]   IO window: d000-dfff
[   31.309320]   MEM window: dc000000-dfefffff
[   31.309323]   PREFETCH window: c0000000-cfffffff
[   31.309326] PCI: Bridge: 0000:00:1c.0
[   31.309327]   IO window: disabled.
[   31.309331]   MEM window: dbf00000-dbffffff
[   31.309334]   PREFETCH window: disabled.
[   31.309337] PCI: Bridge: 0000:00:1c.4
[   31.309338]   IO window: disabled.
[   31.309342]   MEM window: disabled.
[   31.309345]   PREFETCH window: disabled.
[   31.309348] PCI: Bridge: 0000:00:1e.0
[   31.309351]   IO window: c000-cfff
[   31.309355]   MEM window: dbe00000-dbefffff
[   31.309357]   PREFETCH window: disabled.
[   31.309369] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   31.309373] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   31.309387] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   31.309391] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   31.309404] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
[   31.309408] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   31.309417] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   31.309425] NET: Registered protocol family 2
[   31.360749] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   31.360807] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   31.361320] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   31.361485] TCP: Hash tables configured (established 131072 bind 65536)
[   31.361487] TCP reno registered
[   31.376836] checking if image is initramfs... it is
[   31.901699] Freeing initrd memory: 7305k freed
[   31.901785] Simple Boot Flag at 0x7a set to 0x1
[   31.902178] audit: initializing netlink socket (disabled)
[   31.902190] audit(1193173487.488:1): initialized
[   31.902265] highmem bounce pool size: 64 pages
[   31.903744] VFS: Disk quotas dquot_6.5.1
[   31.903781] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   31.903852] io scheduler noop registered
[   31.903854] io scheduler anticipatory registered
[   31.903856] io scheduler deadline registered
[   31.903866] io scheduler cfq registered (default)
[   31.916562] Boot video device is 0000:01:00.0
[   31.916640] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   31.916675] assign_interrupt_mode Found MSI capability
[   31.916678] Allocate Port Service[0000:00:01.0:pcie00]
[   31.916763] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   31.916796] assign_interrupt_mode Found MSI capability
[   31.916798] Allocate Port Service[0000:00:1c.0:pcie00]
[   31.916823] Allocate Port Service[0000:00:1c.0:pcie02]
[   31.916887] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   31.916920] assign_interrupt_mode Found MSI capability
[   31.916922] Allocate Port Service[0000:00:1c.4:pcie00]
[   31.916949] Allocate Port Service[0000:00:1c.4:pcie02]
[   31.917063] isapnp: Scanning for PnP cards...
[   32.269733] isapnp: No Plug & Play device found
[   32.285531] Real Time Clock Driver v1.12ac
[   32.285822] hpet_resources: 0xfed00000 is busy
[   32.285832] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   32.286613] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   32.286712] input: Macintosh mouse button emulation as /class/input/input0
[   32.286804] PNP: No PS/2 controller found. Probing ports directly.
[   32.289310] serio: i8042 KBD port at 0x60,0x64 irq 1
[   32.289314] serio: i8042 AUX port at 0x60,0x64 irq 12
[   32.289393] mice: PS/2 mouse device common for all mice
[   32.289466] EISA: Probing bus 0 at eisa.0
[   32.289491] EISA: Detected 0 cards.
[   32.289551] TCP cubic registered
[   32.289560] NET: Registered protocol family 1
[   32.289575] Using IPI No-Shortcut mode
[   32.289695]   Magic number: 11:494:96
[   32.289929] Freeing unused kernel memory: 364k freed
[   33.447657] AppArmor: AppArmor initializedaudit(1193173488.988:2):  type=1505 info="AppArmor initialized" pid=1192
[   33.453647] fuse init (API version 7.8)
[   33.457796] Failure registering capabilities with primary security module.
[   33.475072] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   33.475080] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   33.780186] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
[   33.780189] Copyright (c) 1999-2006 Intel Corporation.
[   33.780222] ACPI: PCI Interrupt 0000:00:19.0[A] -> GSI 21 (level, low) -> IRQ 17
[   33.780231] PCI: Setting latency timer of device 0000:00:19.0 to 64
[   33.786437] usbcore: registered new interface driver usbfs
[   33.786454] usbcore: registered new interface driver hub
[   33.791741] usbcore: registered new device driver usb
[   33.792309] USB Universal Host Controller Interface driver v3.0
[   33.820385] e1000: 0000:00:19.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:19:d1:6a:d9:7c
[   33.856669] SCSI subsystem initialized
[   33.860411] libata version 2.21 loaded.
[   33.917531] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   33.917550] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[   33.917559] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   33.917562] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   33.917647] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   33.917672] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000ff20
[   33.917758] usb usb1: configuration #1 chosen from 1 choice
[   33.917777] hub 1-0:1.0: USB hub found
[   33.917782] hub 1-0:1.0: 2 ports detected
[   34.019665] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 17 (level, low) -> IRQ 18
[   34.019672] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   34.019676] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   34.019695] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   34.019719] uhci_hcd 0000:00:1a.1: irq 18, io base 0x0000ff00
[   34.019809] usb usb2: configuration #1 chosen from 1 choice
[   34.019840] hub 2-0:1.0: USB hub found
[   34.019844] hub 2-0:1.0: 2 ports detected
[   34.123556] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[   34.123563] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   34.123566] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   34.123585] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[   34.123609] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000ff80
[   34.123698] usb usb3: configuration #1 chosen from 1 choice
[   34.123722] hub 3-0:1.0: USB hub found
[   34.123728] hub 3-0:1.0: 2 ports detected
[   34.227524] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 18
[   34.227532] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   34.227535] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   34.227556] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[   34.227577] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000ff60
[   34.227666] usb usb4: configuration #1 chosen from 1 choice
[   34.227691] hub 4-0:1.0: USB hub found
[   34.227696] hub 4-0:1.0: 2 ports detected
[   34.259451] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   34.331516] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
[   34.331523] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   34.331526] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   34.331549] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[   34.331573] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000ff40
[   34.331661] usb usb5: configuration #1 chosen from 1 choice
[   34.331684] hub 5-0:1.0: USB hub found
[   34.331690] hub 5-0:1.0: 2 ports detected
[   34.435540] usb 1-1: configuration #1 chosen from 1 choice
[   34.436288] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 22 (level, low) -> IRQ 21
[   34.436298] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   34.436302] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   34.437111] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[   34.437134] ehci_hcd 0000:00:1a.7: debug port 1
[   34.437140] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   34.437146] ehci_hcd 0000:00:1a.7: irq 21, io mem 0xdffdec00
[   34.441216] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   34.441269] usb usb6: configuration #1 chosen from 1 choice
[   34.441288] hub 6-0:1.0: USB hub found
[   34.441293] hub 6-0:1.0: 4 ports detected
[   34.543387] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[   34.543397] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   34.543401] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   34.543423] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[   34.543450] ehci_hcd 0000:00:1d.7: debug port 1
[   34.543456] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   34.543462] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xff980800
[   34.547357] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   34.547417] usb usb7: configuration #1 chosen from 1 choice
[   34.547437] hub 7-0:1.0: USB hub found
[   34.547442] hub 7-0:1.0: 6 ports detected
[   34.599301] usb 1-1: USB disconnect, address 2
[   34.653051] ata_piix 0000:00:1f.2: version 2.11
[   34.653056] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   34.653074] ACPI: PCI Interrupt 0000:00:1f.2[C] -> GSI 20 (level, low) -> IRQ 22
[   34.653099] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   34.653140] scsi0 : ata_piix
[   34.653168] scsi1 : ata_piix
[   34.653186] ata1: SATA max UDMA/133 cmd 0x0001fe00 ctl 0x0001fe12 bmdma 0x0001fec0 irq 22
[   34.653189] ata2: SATA max UDMA/133 cmd 0x0001fe20 ctl 0x0001fe32 bmdma 0x0001fec8 irq 22
[   34.845461] ata1.00: ATA-7: ST3320620AS, 3.ADG, max UDMA/133
[   34.845465] ata1.00: 625142448 sectors, multi 8: LBA48 NCQ (depth 0/32)
[   34.912066] ata1.00: configured for UDMA/133
[   35.350945] usb 6-1: new high speed USB device using ehci_hcd and address 2
[   35.387077] ata2.00: ATAPI: TSSTcorp DVD+/-RW TS-H653A, D500, max UDMA/33
[   35.387080] ata2.00: applying bridge limits
[   35.485049] usb 6-1: configuration #1 chosen from 1 choice
[   35.559004] ata2.00: configured for UDMA/33
[   35.559104] scsi 0:0:0:0: Direct-Access     ATA      ST3320620AS      3.AD PQ: 0 ANSI: 5
[   35.559624] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-H653A D500 PQ: 0 ANSI: 5
[   35.559685] ata_piix 0000:00:1f.5: MAP [ P0 P2 P1 P3 ]
[   35.714789] ACPI: PCI Interrupt 0000:00:1f.5[C] -> GSI 20 (level, low) -> IRQ 22
[   35.714817] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   35.714848] scsi2 : ata_piix
[   35.714888] scsi3 : ata_piix
[   35.714910] ata3: SATA max UDMA/133 cmd 0x0001fe40 ctl 0x0001fe52 bmdma 0x0001fed0 irq 22
[   35.714913] ata4: SATA max UDMA/133 cmd 0x0001fe60 ctl 0x0001fe72 bmdma 0x0001fed8 irq 22
[   35.722766] usb 6-2: new high speed USB device using ehci_hcd and address 3
[   35.855141] usb 6-2: configuration #1 chosen from 1 choice
[   35.855226] hub 6-2:1.0: USB hub found
[   35.855325] hub 6-2:1.0: 4 ports detected
[   36.039783] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   36.039792] sd 0:0:0:0: [sda] Write Protect is off
[   36.039794] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   36.039806] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   36.039836] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   36.039843] sd 0:0:0:0: [sda] Write Protect is off
[   36.039845] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   36.039856] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   36.039859]  sda: sda1 sda2 sda3 sda4
[   36.079094] sd 0:0:0:0: [sda] Attached SCSI disk
[   36.081818] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   36.081832] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   36.086101] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   36.086104] Uniform CD-ROM driver Revision: 3.20
[   36.086231] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   36.626355] usb 7-5: new high speed USB device using ehci_hcd and address 4
[   36.760029] usb 7-5: configuration #1 chosen from 1 choice
[   36.761013] usbcore: registered new interface driver libusual
[   36.765847] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   36.765851] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   36.767079] Initializing USB Mass Storage driver...
[   36.998186] usb 4-1: new low speed USB device using uhci_hcd and address 2
[   37.011396] kjournald starting.  Commit interval 5 seconds
[   37.011400] EXT3-fs: mounted filesystem with ordered data mode.
[   37.156451] usb 4-1: configuration #1 chosen from 1 choice
[   37.398039] usb 4-2: new full speed USB device using uhci_hcd and address 3
[   37.436841] ISO 9660 Extensions: Microsoft Joliet Level 3
[   37.486190] ISO 9660 Extensions: RRIP_1991A
[   37.576268] usb 4-2: configuration #1 chosen from 1 choice
[   37.582225] hub 4-2:1.0: USB hub found
[   37.584190] hub 4-2:1.0: 3 ports detected
[   37.692266] scsi4 : SCSI emulation for USB Mass Storage devices
[   37.692336] usb-storage: device found at 2
[   37.692338] usb-storage: waiting for device to settle before scanning
[   37.738098] Registering unionfs 1.4
[   37.738100] unionfs: debugging is not enabled
[   37.745875] loop: module loaded
[   37.895061] usb 4-2.1: new full speed USB device using uhci_hcd and address 4
[   38.032074] usb 4-2.1: configuration #1 chosen from 1 choice
[   38.045014] usbcore: registered new interface driver usb-storage
[   38.045017] usbcore: registered new interface driver hiddev
[   38.045019] USB Mass Storage support registered.
[   38.059184] input: HID 0461:4d09 as /class/input/input1
[   38.059204] input: USB HID v1.00 Mouse [HID 0461:4d09] on usb-0000:00:1d.1-1
[   38.062152] input: Dell Dell USB Keyboard Hub as /class/input/input2
[   38.062158] input: USB HID v1.10 Keyboard [Dell Dell USB Keyboard Hub] on usb-0000:00:1d.1-2.1
[   38.072024] input: Dell Dell USB Keyboard Hub as /class/input/input3
[   38.072030] input: USB HID v1.10 Device [Dell Dell USB Keyboard Hub] on usb-0000:00:1d.1-2.1
[   38.072038] usbcore: registered new interface driver usbhid
[   38.072041] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   38.316895] squashfs: version 3.2-UBUNTU (2007/07/26) Phillip Lougher
[   42.688094] usb-storage: device scan complete
[   42.688844] scsi 4:0:0:0: Direct-Access     Canon    MP600Storage     0103 PQ: 0 ANSI: 2
[   42.691105] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   42.691144] sd 4:0:0:0: Attached scsi generic sg2 type 0
[   78.655322] Linux agpgart interface v0.102 (c) Dave Jones
[   78.842847] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   78.983396] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   79.042013] iTCO_vendor_support: vendor-support=0
[   79.043046] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   79.043118] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   79.043125] iTCO_wdt: No card detected
[   79.260243] input: PC Speaker as /class/input/input4
[   79.505813] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x04A9 pid 0x1718
[   79.505830] usbcore: registered new interface driver usblp
[   79.505832] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   79.784919] usbcore: registered new interface driver xpad
[   79.784923] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   80.084582] ACPI: PCI Interrupt 0000:04:04.0[A] -> GSI 16 (level, low) -> IRQ 16
[   80.084599] snd-ca0106: Model 100a Rev 00000000 Serial 100a1102
[   80.999157] Adding 996020k swap on /dev/sda1.  Priority:-1 extents:1 across:996020k
[   82.257476] No dock devices found.
[   82.325505] input: Power Button (FF) as /class/input/input5
[   82.325648] ACPI: Power Button (FF) [PWRF]
[   82.326314] input: Power Button (CM) as /class/input/input6
[   82.326431] ACPI: Power Button (CM) [VBTN]
[   86.938969] lp: driver loaded but no devices found
[   86.963770] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   86.963774] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[   86.976984] ppdev: user-space parallel port driver
[   89.739380] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   89.739384] apm: disabled - APM is not SMP safe.
[   91.875194] Failure registering capabilities with primary security module.
[   95.843294] Bluetooth: Core ver 2.11
[   95.843344] NET: Registered protocol family 31
[   95.843346] Bluetooth: HCI device and connection manager initialized
[   95.843348] Bluetooth: HCI socket layer initialized
[   96.237074] Bluetooth: L2CAP ver 2.8
[   96.237077] Bluetooth: L2CAP socket layer initialized
[   96.258761] Bluetooth: RFCOMM socket layer initialized
[   96.258770] Bluetooth: RFCOMM TTY layer initialized
[   96.258772] Bluetooth: RFCOMM ver 1.8
[   99.833946] NET: Registered protocol family 17
[  108.527164] NET: Registered protocol family 10
[  108.527237] lo: Disabled Privacy Extensions
[  119.040771] eth0: no IPv6 routers present
[  244.338377] kjournald starting.  Commit interval 5 seconds
[  244.338629] EXT3 FS on sda4, internal journal
[  244.338697] EXT3-fs: mounted filesystem with ordered data mode.

---

### Post by Go2doug on 2007-10-24
I just got 5 of these bootup panics in a row...is there anybody on this forum who can make any suggestions regarding a troubleshooting process?

---

