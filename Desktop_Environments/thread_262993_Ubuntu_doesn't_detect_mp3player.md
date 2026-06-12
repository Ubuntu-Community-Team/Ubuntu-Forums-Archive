---
title: "Ubuntu doesn't detect mp3player"
date: 2006-09-22
forum: Desktop Environments
---

### Post by DAFORZE on 2006-09-22
Hey guys!
I just bought a mp3player (Grundig mpaxx 560/1gb)
But my ubuntu doesn't detect it at all.
The mp3player itself says it's connected to usb, but no sign on ubuntu, it also isn't listed on /media or as /dev/sda1.
Does somebody know what to do?
Thx! :p

---

### Post by Lord Illidan on 2006-09-22
Can you run dmesg in the terminal after you connect it and post the output here, please?

---

### Post by DAFORZE on 2006-09-22
edit:

a lot of useless output

---

### Post by DAFORZE on 2006-09-22
edit:

a lot of useless output

---

### Post by Lord Illidan on 2006-09-22
WHOA there....that is not the output I expected...Have you got wireless internet or something?

---

### Post by DAFORZE on 2006-09-22
No im just connected with a cable to a dhcp network and radius server, or something like that :rolleyes:

---

### Post by DAFORZE on 2006-09-22
Oh wait now i get this output at the beggining:

17179569.184000] Linux version 2.6.15-25-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Wed Jun 14 11:25:49 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 511MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 131056
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 126960 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.2 present.
[17179569.184000] ACPI: RSDP (v000 VIA694                                ) @ 0x000f7400
[17179569.184000] ACPI: RSDT (v001 VIA694 AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff3000
[17179569.184000] ACPI: FADT (v001 VIA694 AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff3040
[17179569.184000] ACPI: DSDT (v001 VIA694 AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x4008
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfff0000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hdb1 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (01402000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[17179569.184000] Detected 1400.264 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179573.084000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179573.088000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179573.104000] Memory: 508852k/524224k available (1976k kernel code, 14808k reserved, 606k data, 288k init, 0k highmem)
[17179573.104000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179573.184000] Calibrating delay using timer specific routine.. 2803.02 BogoMIPS (lpj=5606058)
[17179573.184000] Security Framework v1.0.0 initialized
[17179573.184000] SELinux:  Disabled at boot.
[17179573.184000] Mount-cache hash table entries: 512
[17179573.184000] CPU: After generic identify, caps: 0383f9ff c1cbf9ff 00000000 00000000 00000000 00000000 00000000
[17179573.184000] CPU: After vendor identify, caps: 0383f9ff c1cbf9ff 00000000 00000000 00000000 00000000 00000000
[17179573.184000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179573.184000] CPU: L2 Cache: 256K (64 bytes/line)
[17179573.184000] CPU: After all inits, caps: 0383f9ff c1cbf9ff 00000000 00000420 00000000 00000000 00000000
[17179573.184000] mtrr: v2.0 (20020519)
[17179573.184000] CPU: AMD Athlon(tm) XP processor 1600+ stepping 02
[17179573.184000] Enabling fast FPU save and restore... done.
[17179573.184000] Enabling unmasked SIMD FPU exception support... done.
[17179573.184000] Checking 'hlt' instruction... OK.
[17179573.200000] checking if image is initramfs... it is
[17179573.940000] Freeing initrd memory: 6613k freed
[17179574.028000] ACPI: Looking for DSDT ... not found!
[17179574.028000] ACPI: setting ELCR to 0200 (from 1a20)
[17179574.028000] NET: Registered protocol family 16
[17179574.028000] EISA bus registered
[17179574.028000] ACPI: bus type pci registered
[17179574.104000] PCI: PCI BIOS revision 2.10 entry at 0xfb010, last bus=1
[17179574.104000] PCI: Using configuration type 1
[17179574.104000] ACPI: Subsystem revision 20051216
[17179574.144000] ACPI: Interpreter enabled
[17179574.144000] ACPI: Using PIC for interrupt routing
[17179574.144000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179574.144000] PCI: Probing PCI hardware (bus 00)
[17179574.144000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179574.148000] Boot video device is 0000:01:00.0
[17179574.148000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179574.164000] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[17179574.168000] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179574.168000] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 *5 6 7 10 11 12 14 15)
[17179574.168000] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 10 11 *12 14 15)
[17179574.172000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179574.172000] pnp: PnP ACPI init
[17179574.176000] pnp: PnP ACPI: found 13 devices
[17179574.176000] PnPBIOS: Disabled by ACPI PNP
[17179574.176000] PCI: Using ACPI for IRQ routing
[17179574.176000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179574.196000] PCI: Bridge: 0000:00:01.0
[17179574.196000]   IO window: disabled.
[17179574.196000]   MEM window: e4000000-e5ffffff
[17179574.196000]   PREFETCH window: d0000000-dfffffff
[17179574.196000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179574.196000] audit: initializing netlink socket (disabled)
[17179574.196000] audit(1158923952.196:1): initialized
[17179574.196000] VFS: Disk quotas dquot_6.5.1
[17179574.196000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179574.196000] Initializing Cryptographic API
[17179574.196000] io scheduler noop registered
[17179574.196000] io scheduler anticipatory registered
[17179574.196000] io scheduler deadline registered
[17179574.196000] io scheduler cfq registered
[17179574.196000] isapnp: Scanning for PnP cards...
[17179574.548000] isapnp: No Plug & Play device found
[17179574.568000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[17179574.568000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[17179574.568000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179574.568000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179574.568000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179574.568000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.568000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179574.568000] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.568000] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179574.568000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179574.568000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179574.568000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179574.572000] mice: PS/2 mouse device common for all mice
[17179574.572000] EISA: Probing bus 0 at eisa.0
[17179574.572000] Cannot allocate resource for EISA slot 4
[17179574.572000] EISA: Detected 0 cards.
[17179574.572000] NET: Registered protocol family 2
[17179574.608000] IP route cache hash table entries: 8192 (order: 3, 32768 bytes)
[17179574.608000] TCP established hash table entries: 32768 (order: 5, 131072 bytes)
[17179574.608000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
[17179574.608000] TCP: Hash tables configured (established 32768 bind 32768)
[17179574.608000] TCP reno registered
[17179574.608000] TCP bic registered
[17179574.608000] NET: Registered protocol family 1
[17179574.608000] NET: Registered protocol family 8
[17179574.608000] NET: Registered protocol family 20
[17179574.608000] Using IPI Shortcut mode
[17179574.608000] ACPI wakeup devices:
[17179574.608000] SLPB PCI0 USB0 USB1 USB2 AC97 MC97 LAN0 UAR1 ECP1
[17179574.608000] ACPI: (supports S0 S1 S4 S5)
[17179574.608000] Freeing unused kernel memory: 288k freed
[17179574.668000] vga16fb: initializing
[17179574.668000] vga16fb: mapped to 0xc00a0000
[17179574.688000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179574.800000] Console: switching to colour frame buffer device 80x25
[17179574.800000] fb0: VGA16 VGA frame buffer device
[17179575.864000] Capability LSM initialized
[17179575.996000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179575.996000] ACPI: Processor [CPU0] (supports 2 throttling states)
[17179576.660000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[17179576.660000] **** SET: Misaligned resource pointer: dfea11c2 Type 07 Len 0
[17179576.660000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[17179576.660000] PCI: setting IRQ 11 as level-triggered
[17179576.660000] ACPI: PCI Interrupt 0000:00:11.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179576.660000] PCI: Via IRQ fixup for 0000:00:11.1, from 255 to 11
[17179576.660000] VP_IDE: chipset revision 6
[17179576.660000] VP_IDE: not 100% native mode: will probe irqs later
[17179576.660000] VP_IDE: VIA vt8233 (rev 00) IDE UDMA100 controller on pci0000:00:11.1
[17179576.660000]     ide0: BM-DMA at 0xd400-0xd407, BIOS settings: hda:pio, hdb:DMA
[17179576.660000]     ide1: BM-DMA at 0xd408-0xd40f, BIOS settings: hdc:DMA, hdd:DMA
[17179576.660000] Probing IDE interface ide0...
[17179577.300000] hdb: QUANTUM FIREBALL CR4.3A, ATA DISK drive
[17179577.356000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179577.356000] Probing IDE interface ide1...
[17179578.220000] hdc: AOpen Inc. DVD-ROM DVD-1640 PRO 0122, ATAPI CD/DVD-ROM drive
[17179579.004000] hdd: LITE-ON LTR-40125S, ATAPI CD/DVD-ROM drive
[17179579.060000] ide1 at 0x170-0x177,0x376 on irq 15
[17179579.072000] hdb: max request size: 128KiB
[17179579.088000] hdb: 8418816 sectors (4310 MB) w/418KiB Cache, CHS=14848/9/63
[17179579.088000] hdb: cache flushes not supported
[17179579.088000]  hdb: hdb1 hdb2 < hdb5 >
[17179579.120000] hdc: ATAPI 40X DVD-ROM drive, 256kB Cache, UDMA(33)
[17179579.120000] Uniform CD-ROM driver Revision: 3.20
[17179579.128000] hdd: ATAPI 48X CD-ROM CD-R/RW drive, 1984kB Cache, UDMA(33)
[17179579.444000] usbcore: registered new driver usbfs
[17179579.444000] usbcore: registered new driver hub
[17179579.444000] USB Universal Host Controller Interface driver v2.3
[17179579.444000] **** SET: Misaligned resource pointer: dfc751e2 Type 07 Len 0
[17179579.448000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 12
[17179579.448000] PCI: setting IRQ 12 as level-triggered
[17179579.448000] ACPI: PCI Interrupt 0000:00:11.2[D] -> Link [LNKD] -> GSI 12 (level, low) -> IRQ 12
[17179579.448000] uhci_hcd 0000:00:11.2: UHCI Host Controller
[17179579.448000] uhci_hcd 0000:00:11.2: new USB bus registered, assigned bus number 1
[17179579.448000] uhci_hcd 0000:00:11.2: irq 12, io base 0x0000d800
[17179579.448000] hub 1-0:1.0: USB hub found
[17179579.448000] hub 1-0:1.0: 2 ports detected
[17179579.552000] ACPI: PCI Interrupt 0000:00:11.3[D] -> Link [LNKD] -> GSI 12 (level, low) -> IRQ 12
[17179579.552000] uhci_hcd 0000:00:11.3: UHCI Host Controller
[17179579.552000] uhci_hcd 0000:00:11.3: new USB bus registered, assigned bus number 2
[17179579.552000] uhci_hcd 0000:00:11.3: irq 12, io base 0x0000dc00
[17179579.552000] hub 2-0:1.0: USB hub found
[17179579.552000] hub 2-0:1.0: 2 ports detected
[17179579.656000] ACPI: PCI Interrupt 0000:00:11.4[D] -> Link [LNKD] -> GSI 12 (level, low) -> IRQ 12
[17179579.656000] uhci_hcd 0000:00:11.4: UHCI Host Controller
[17179579.656000] uhci_hcd 0000:00:11.4: new USB bus registered, assigned bus number 3
[17179579.656000] uhci_hcd 0000:00:11.4: irq 12, io base 0x0000e000
[17179579.656000] hub 3-0:1.0: USB hub found
[17179579.656000] hub 3-0:1.0: 2 ports detected
[17179579.792000] usb 1-1: new low speed USB device using uhci_hcd and address 2
[17179579.880000] Attempting manual resume
[17179579.932000] EXT3-fs: mounted filesystem with ordered data mode.
[17179579.936000] kjournald starting.  Commit interval 5 seconds
[17179580.212000] usb 1-2: new full speed USB device using uhci_hcd and address 3
[17179598.520000] Linux agpgart interface v0.101 (c) Dave Jones
[17179598.548000] agpgart: Detected VIA KT266/KY266x/KT333 chipset
[17179598.552000] agpgart: AGP aperture is 64M @ 0xe0000000
[17179598.736000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179598.780000] 8139too Fast Ethernet driver 0.9.27
[17179598.780000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKD] -> GSI 12 (level, low) -> IRQ 12
[17179598.780000] eth0: RealTek RTL8139 at 0xe08ac000, 00:e0:4c:eb:57:cb, IRQ 12
[17179598.780000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179598.816000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179598.836000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179598.956000] irda_init()
[17179598.956000] NET: Registered protocol family 23
[17179599.112000] input: PC Speaker as /class/input/input1
[17179599.648000] usbcore: registered new driver hiddev
[17179599.660000] Linux video capture interface: v1.00
[17179599.680000] input: Microsoft Microsoft IntelliMouse Explorer as /class/input/input2
[17179599.680000] input: USB HID v1.00 Mouse [Microsoft Microsoft IntelliMouse Explorer] on usb-0000:00:11.2-1
[17179599.680000] usbcore: registered new driver usbhid
[17179599.680000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179599.732000] Real Time Clock Driver v1.12
[17179599.740000] /home/daforze/spca5xx-20060501/drivers/usb/spca5xx.c: USB SPCA5XX camera found. Logitech QC Messenger
[17179599.740000] /home/daforze/spca5xx-20060501/drivers/usb/spca5xx.c: [spca5xx_probe:5480] Camera type JPEG
[17179599.904000] nvidia: module license 'NVIDIA' taints kernel.
[17179599.912000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179599.912000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT 2006
[17179600.328000] /home/daforze/spca5xx-20060501/drivers/usb/zc3xx.h: [zc3xx_config:558] Find Sensor HV7131R(c)
[17179600.332000] /home/daforze/spca5xx-20060501/drivers/usb/spca5xx.c: [spca5xx_getcapability:1765] maxw 640 maxh 480 minw 176 minh 144
[17179600.332000] usbcore: registered new driver spca5xx
[17179600.332000] /home/daforze/spca5xx-20060501/drivers/usb/spca5xx.c: spca5xx driver 00.60.00 registered
[17179600.360000] parport: PnPBIOS parport detected.
[17179600.360000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179600.472000] FDC 0 is a post-1991 82077
[17179600.676000] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[17179600.856000] usbcore: registered new driver snd-usb-audio
[17179601.104000] ts: Compaq touchscreen protocol output
[17179601.256000] **** SET: Misaligned resource pointer: dc7b8702 Type 07 Len 0
[17179601.256000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
[17179601.256000] PCI: setting IRQ 5 as level-triggered
[17179601.256000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[17179601.256000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[17179601.728000] NET: Registered protocol family 17
[17179602.316000] Intel ISA PCIC probe: not found.
[17179602.524000] lp0: using parport0 (interrupt-driven).
[17179602.644000] Adding 208804k swap on /dev/hdb5.  Priority:-1 extents:1 across:208804k
[17179602.792000] EXT3 FS on hdb1, internal journal
[17179603.032000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179603.032000] md: bitmap version 4.39
[17179603.892000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179604.224000] cdrom: open failed.
[17179604.724000] cdrom: open failed.
[17179604.764000] cdrom: open failed.
[17179606.856000] NET: Registered protocol family 10
[17179606.856000] lo: Disabled Privacy Extensions
[17179606.860000] IPv6 over IPv4 tunneling driver
[17179610.512000] ACPI: Power Button (FF) [PWRF]
[17179610.512000] ACPI: Power Button (CM) [PWRB]
[17179610.512000] ACPI: Sleep Button (CM) [SLPB]
[17179610.652000] ibm_acpi: ec object not found
[17179610.692000] pcc_acpi: loading...
[17179617.720000] eth0: no IPv6 routers present
[17179618.320000] ppdev: user-space parallel port driver
[17179619.640000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179619.640000] apm: overridden by ACPI.
[17179620.104000] ip_tables: (C) 2000-2002 Netfilter core team
[17179620.408000] Netfilter messages via NETLINK v0.30.
[17179620.488000] ip_conntrack version 2.4 (4095 buckets, 32760 max) - 232 bytes per conntrack
[17179622.056000] Bluetooth: Core ver 2.8
[17179622.056000] NET: Registered protocol family 31
[17179622.056000] Bluetooth: HCI device and connection manager initialized
[17179622.056000] Bluetooth: HCI socket layer initialized
[17179622.112000] Bluetooth: L2CAP ver 2.8
[17179622.112000] Bluetooth: L2CAP socket layer initialized
[17179622.128000] Bluetooth: RFCOMM socket layer initialized
[17179622.128000] Bluetooth: RFCOMM TTY layer initialized
[17179622.128000] Bluetooth: RFCOMM ver 1.7

---

### Post by DAFORZE on 2006-09-22
and after that, all that eth output.
But is this the output we are looking for? :p

---

### Post by brandon moore on 2006-09-22
unplug all usb devices and run this command
> sudo modprobe -r ehci_hcd
that's the only way i have been able to get USB working on my machine.  i run it once when i need to connect something and it's good until i restart.

---

### Post by DAFORZE on 2006-09-22
wow THANX it worked!!! :D 
:biggrin: :biggrin: :biggrin:

---

### Post by prokrast on 2007-06-04
i have a ipod nano 8gb. i cant get the "do not disco" off the ipod screen. i have ubuntu 6.10 and my hot plug works with my mcatch but not the ipod.i did one how-to it told me to unplug all usbs and enter "sudo modprobe -r ehci_hcd" i did that and my dmesg reads
[17238564.324000] ohci_hcd 0000:01:0e.1: wakeup
[17238564.708000] usb 3-1: new full speed USB device using ohci_hcd and address 5
[17238564.928000] usb 3-1: configuration #1 chosen from 2 choices
[17238564.932000] scsi9 : SCSI emulation for USB Mass Storage devices
[17238564.932000] usb-storage: device found at 5
[17238564.932000] usb-storage: waiting for device to settle before scanning
[17238566.504000] Inbound IN=eth0 OUT= MAC=00:a0:cc:73:90:97:00:11:50:8d:a1:5e:08:00 SRC=192.168.2.1 DST=192.168.2.3 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=957 PROTO=UDP SPT=39714 DPT=137 LEN=58 
[17238569.932000] usb-storage: device scan complete
[17238569.940000]   Vendor: Apple     Model: iPod              Rev: 1.62
[17238569.940000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17238569.952000] SCSI device sda: 3964928 2048-byte hdwr sectors (8120 MB)
[17238569.960000] sda: Write Protect is off
[17238569.960000] sda: Mode Sense: 68 00 00 08
[17238569.960000] sda: assuming drive cache: write through
[17238569.980000] SCSI device sda: 3964928 2048-byte hdwr sectors (8120 MB)
[17238569.988000] sda: Write Protect is off
[17238569.988000] sda: Mode Sense: 68 00 00 08
[17238569.988000] sda: assuming drive cache: write through
[17238569.988000]  sda: sda1 sda2
[17238570.000000] sd 9:0:0:0: Attached scsi removable disk sda
[17238570.000000] sd 9:0:0:0: Attached scsi generic sg0 type 0
but it will still not hot plug and i can do anything with my ipod:(
ive got floola,amarok,banshee,gtkpod,and rhythmbox. and all do not read my 8gb nano:(
my ipod was given to me by a friend so i dont have start-up disks of books! i do have online man but it just tells me to talk with itunes and being linux we know what that means
help please!

---

