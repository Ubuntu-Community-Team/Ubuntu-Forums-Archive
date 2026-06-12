---
title: "Strange networking problem..."
date: 2005-12-29
forum: General Help
---

### Post by snakedog on 2005-12-29
...this computer oftens fails to pull an ip address when it boots up.  I get this when I run ifconfig:

larry@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:04:76:D4:69:D6
          inet6 addr: fe80::204:76ff:fed4:69d6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1240 (1.2 KiB)  TX bytes:1404 (1.3 KiB)
          Interrupt:3 Base address:0x1400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:645 errors:0 dropped:0 overruns:0 frame:0
          TX packets:645 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:57108 (55.7 KiB)  TX bytes:57108 (55.7 KiB)

It's strange because 5 minutes later I'll run ifconfig and get this:

larry@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:04:76:D4:69:D6
          inet addr:172.23.1.100  Bcast:172.23.1.255  Mask:255.255.255.0
          inet6 addr: fe80::204:76ff:fed4:69d6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1240 (1.2 KiB)  TX bytes:1404 (1.3 KiB)
          Interrupt:3 Base address:0x1400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:645 errors:0 dropped:0 overruns:0 frame:0
          TX packets:645 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:57108 (55.7 KiB)  TX bytes:57108 (55.7 KiB)

Voila, there's my ip address.  My gut reaction is that it is a hardware issue, but I'm just not sure.  I often boot into this computer using Insert Linux (live cd) and have no problem with the nic.  Maybe it's my router, but I' haven't had any other problems with it if it is (Netgear MR814v2).  I guess I could try a different cable, or test the one in here.  I am curious why I seem to be pulling an IP6 address with this computer.  

Any suggestions appreciated.  TIA.

---

### Post by FLeiXiuS on 2005-12-29
Well let me start out by saying IPv6 is enabled by default.  There are guides on the forum which you could search for to remove IPv6.  It will greatly increase speeds on most network applications mainly because they will attempt IPv6 before IPv4 unless specified to do otherwise.

What I may ask for is a print out of 'dmesg'.

Simply type:
$ dmesg > ~/dmesg.out
$ gedit ~/dmesg.out

This will take the output of dmesg and place it into a file in your home directory called dmesg.out.  From there it'll open gedit so you can display the file easier. 

To me this is the best route, this way you won't have to go about highlighting several terminals.

---

### Post by snakedog on 2005-12-31
OK, here we go.

[4294667.296000] Linux version 2.6.12-10-386 (buildd@terranova) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Thu Dec 22 11:37:10 UTC 2005
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[4294667.296000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000ec000 - 00000000000f0000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000000c000000 (usable)
[4294667.296000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 192MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 49152
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:1
[4294667.296000]   Normal zone: 45056 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:1
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v000 COMPAQ                                ) @ 0x000ec010
[4294667.296000] ACPI: RSDT (v001 COMPAQ HAWA7K11 0x00000001  0x00000000) @ 0x000ec080
[4294667.296000] ACPI: FADT (v001 COMPAQ HAWA7K11 0x00000001  0x00000000) @ 0x000ec0cc
[4294667.296000] ACPI: SSDT (v001 COMPAQ HAWA7K1  0x00000001 MSFT 0x0100000c) @ 0x000ec177
[4294667.296000] ACPI: DSDT (v001 COMPAQ DSDTTBL  0x00000001 MSFT 0x0100000c) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0xee08
[4294667.296000] Allocating PCI resources starting at 0c000000 (gap: 0c000000:f3fc0000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash
[4294667.296000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[4294667.296000] mapped APIC to ffffd000 (01181000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[4294667.296000] Detected 751.759 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294670.403000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[4294670.404000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[4294670.417000] Memory: 186500k/196608k available (1416k kernel code, 9588k reserved, 762k data, 224k init, 0k highmem)
[4294670.417000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294670.417000] Calibrating delay loop... 1486.84 BogoMIPS (lpj=743424)
[4294670.438000] Security Framework v1.0.0 initialized
[4294670.438000] SELinux:  Disabled at boot.
[4294670.438000] Mount-cache hash table entries: 512
[4294670.438000] CPU: After generic identify, caps: 0183f9ff c1c7f9ff 00000000 00000000 00000000 00000000 00000000
[4294670.438000] CPU: After vendor identify, caps: 0183f9ff c1c7f9ff 00000000 00000000 00000000 00000000 00000000
[4294670.438000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[4294670.438000] CPU: L2 Cache: 64K (64 bytes/line)
[4294670.438000] CPU: After all inits, caps: 0183f9ff c1c7f9ff 00000000 00000020 00000000 00000000 00000000
[4294670.438000] CPU: AMD Duron(tm) Processor stepping 01
[4294670.438000] Enabling fast FPU save and restore... done.
[4294670.438000] Checking 'hlt' instruction... OK.
[4294670.442000] Checking for popad bug... OK.
[4294670.442000] checking if image is initramfs... it is
[4294671.502000] Freeing initrd memory: 5171k freed
[4294671.508000] ACPI: Looking for DSDT in initrd... not found!
[4294671.652000]  not found!
[4294671.658000] ACPI: setting ELCR to 0200 (from 0c08)
[4294671.664000] NET: Registered protocol family 16
[4294671.664000] EISA bus registered
[4294671.664000] ACPI: bus type pci registered
[4294671.673000] PCI: PCI BIOS revision 2.10 entry at 0xfa174, last bus=1
[4294671.673000] PCI: Using configuration type 1
[4294671.673000] mtrr: v2.0 (20020519)
[4294671.674000] ACPI: Subsystem revision 20050729
[4294671.682000] ACPI: Interpreter enabled
[4294671.682000] ACPI: Using PIC for interrupt routing
[4294671.683000] ACPI: PCI Interrupt Link [LNKA] (IRQs *3 4 5 6 7 10 11 15)
[4294671.683000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11 15) *0, disabled.
[4294671.684000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 15)
[4294671.685000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 15)
[4294671.685000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294671.685000] PCI: Probing PCI hardware (bus 00)
[4294671.685000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294671.685000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[4294671.687000] Boot video device is 0000:01:00.0
[4294671.689000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294671.693000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294671.693000] pnp: PnP ACPI init
[4294671.698000] pnp: PnP ACPI: found 11 devices
[4294671.698000] PnPBIOS: Disabled by ACPI PNP
[4294671.698000] PCI: Using ACPI for IRQ routing
[4294671.698000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294671.718000] pnp: 00:01: ioport range 0x4d0-0x4d1 has been reserved
[4294671.718000] pnp: 00:01: ioport range 0xee00-0xee7f could not be reserved
[4294671.718000] pnp: 00:01: ioport range 0xee80-0xeeff has been reserved
[4294671.720000] audit: initializing netlink socket (disabled)
[4294671.720000] audit: initialized
[4294671.720000] VFS: Disk quotas dquot_6.5.1
[4294671.720000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294671.720000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294671.720000] devfs: boot_options: 0x0
[4294671.720000] Initializing Cryptographic API
[4294671.720000] PCI: Disabling Via external APIC routing
[4294671.720000] isapnp: Scanning for PnP cards...
[4294672.074000] isapnp: No Plug & Play device found
[4294672.128000] PNP: PS/2 Controller [PNP0303:KBD,PNP0f0e:PS2M] at 0x60,0x64 irq 1,12
[4294672.128000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294672.128000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294672.129000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294672.129000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294672.134000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294672.134000] io scheduler noop registered
[4294672.134000] io scheduler anticipatory registered
[4294672.134000] io scheduler deadline registered
[4294672.134000] io scheduler cfq registered
[4294672.135000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294672.135000] EISA: Probing bus 0 at eisa.0
[4294672.135000] Cannot allocate resource for EISA slot 1
[4294672.135000] EISA: Detected 0 cards.
[4294672.135000] NET: Registered protocol family 2
[4294672.144000] IP: routing cache hash table of 2048 buckets, 16Kbytes
[4294672.144000] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[4294672.144000] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
[4294672.144000] TCP: Hash tables configured (established 8192 bind 8192)
[4294672.145000] NET: Registered protocol family 8
[4294672.145000] NET: Registered protocol family 20
[4294672.145000] ACPI wakeup devices: 
[4294672.145000] PBTN PCI0 USB1 USB0 PS2M  KBD 
[4294672.145000] ACPI: (supports S0 S1 S5)
[4294672.146000] Freeing unused kernel memory: 224k freed
[4294672.179000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294672.198000] vga16fb: initializing
[4294672.198000] vga16fb: mapped to 0xc00a0000
[4294672.342000] Console: switching to colour frame buffer device 80x30
[4294672.342000] fb0: VGA16 VGA frame buffer device
[4294673.547000] Capability LSM initialized
[4294673.578000] NET: Registered protocol family 1
[4294673.613000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294673.613000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294673.613000] ACPI: bus type ide registered
[4294673.629000] VP_IDE: IDE controller at PCI slot 0000:00:14.1
[4294673.629000] VP_IDE: chipset revision 16
[4294673.629000] VP_IDE: not 100% native mode: will probe irqs later
[4294673.629000] VP_IDE: VIA vt82c686a (rev 22) IDE UDMA66 controller on pci0000:00:14.1
[4294673.629000]     ide0: BM-DMA at 0x14c0-0x14c7, BIOS settings: hda:DMA, hdb:pio
[4294673.629000]     ide1: BM-DMA at 0x14c8-0x14cf, BIOS settings: hdc:DMA, hdd:pio
[4294673.629000] Probing IDE interface ide0...
[4294674.013000] hda: Maxtor 90340D2, ATA DISK drive
[4294674.625000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294674.625000] Probing IDE interface ide1...
[4294675.417000] hdc: Hewlett-Packard CD-Writer Plus 8000, ATAPI CD/DVD-ROM drive
[4294675.723000] ide1 at 0x170-0x177,0x376 on irq 15
[4294675.723000] Probing IDE interface ide2...
[4294676.236000] Probing IDE interface ide3...
[4294676.749000] Probing IDE interface ide4...
[4294677.262000] Probing IDE interface ide5...
[4294677.783000] hda: max request size: 128KiB
[4294677.800000] hda: 6640704 sectors (3400 MB) w/512KiB Cache, CHS=6588/16/63, UDMA(33)
[4294677.800000] hda: cache flushes not supported
[4294677.800000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
[4294677.840000] hdc: ATAPI 20X CD-ROM CD-R/RW drive, 2048kB Cache
[4294677.840000] Uniform CD-ROM driver Revision: 3.20
[4294678.808000] Attempting manual resume
[4294678.809000] swsusp: Suspend partition has wrong signature?
[4294678.873000] PCI: Enabling device 0000:00:03.0 (0004 -> 0007)
[4294678.873000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 3
[4294678.873000] PCI: setting IRQ 3 as level-triggered
[4294678.873000] ACPI: PCI Interrupt 0000:00:03.0[A] -> Link [LNKA] -> GSI 3 (level, low) -> IRQ 3
[4294678.873000] 3c59x: Donald Becker and others. [www.scyld.com/network/vortex.html](www.scyld.com/network/vortex.html)
[4294678.873000] 0000:00:03.0: 3Com PCI 3c900 Cyclone 10Mbps TPO at 0x1400. Vers LK1.1.19
[4294678.960000] usbcore: registered new driver usbfs
[4294678.960000] usbcore: registered new driver hub
[4294678.962000] USB Universal Host Controller Interface driver v2.2
[4294678.963000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[4294678.963000] PCI: setting IRQ 11 as level-triggered
[4294678.963000] ACPI: PCI Interrupt 0000:00:14.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294678.963000] uhci_hcd 0000:00:14.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
[4294679.025000] uhci_hcd 0000:00:14.2: new USB bus registered, assigned bus number 1
[4294679.025000] uhci_hcd 0000:00:14.2: irq 11, io base 0x00001480
[4294679.025000] hub 1-0:1.0: USB hub found
[4294679.025000] hub 1-0:1.0: 2 ports detected
[4294679.028000] ACPI: PCI Interrupt 0000:00:14.3[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294679.028000] uhci_hcd 0000:00:14.3: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
[4294679.090000] uhci_hcd 0000:00:14.3: new USB bus registered, assigned bus number 2
[4294679.090000] uhci_hcd 0000:00:14.3: irq 11, io base 0x000014a0
[4294679.090000] hub 2-0:1.0: USB hub found
[4294679.090000] hub 2-0:1.0: 2 ports detected
[4294682.320000] ACPI: CPU0 (power states: C1[C1])
[4294682.595000] Attempting manual resume
[4294682.623000] swsusp: Suspend partition has wrong signature?
[4294682.677000] kjournald starting.  Commit interval 5 seconds
[4294682.677000] EXT3-fs: mounted filesystem with ordered data mode.
[4294684.714000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294691.314000] Adding 168640k swap on /dev/hda5.  Priority:-1 extents:1
[4294691.718000] EXT3 FS on hda1, internal journal
[4294708.135000] parport_pc: VIA 686A/8231 detected
[4294708.135000] parport_pc: probing current configuration
[4294708.135000] parport_pc: Current parallel port base: 0x378
[4294708.135000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[4294708.218000] parport_pc: VIA parallel port: io=0x378, irq=7
[4294708.225000] lp0: using parport0 (interrupt-driven).
[4294708.298000] mice: PS/2 mouse device common for all mice
[4294708.758000] input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
[4294709.508000] ts: Compaq touchscreen protocol output
[4294712.638000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294714.562000] cdrom: open failed.
[4294718.971000] Linux agpgart interface v0.101 (c) Dave Jones
[4294718.994000] agpgart: Detected VIA Apollo Pro 133 chipset
[4294719.008000] agpgart: AGP aperture is 64M @ 0x50000000
[4294719.264000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294719.279000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294719.279000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294720.253000] via686a 0000:00:14.4: base address not set - upgrade BIOS or use force_addr=0xaddr
[4294720.406000] vt596_smbus 0000:00:14.4: SMBUS: Error: Host SMBus controller not enabled! - upgrade BIOS or use force=1
[4294720.932000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[4294720.932000] PCI: setting IRQ 10 as level-triggered
[4294720.932000] ACPI: PCI Interrupt 0000:00:14.5[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[4294720.932000] PCI: Setting latency timer of device 0000:00:14.5 to 64
[4294724.961000] Real Time Clock Driver v1.12
[4294725.188000] input: PC Speaker
[4294725.906000] Floppy drive(s): fd0 is 1.44M
[4294725.919000] FDC 0 is a post-1991 82077
[4294728.487000] ACPI: PCI Interrupt 0000:00:03.0[A] -> Link [LNKA] -> GSI 3 (level, low) -> IRQ 3
[4294728.514000] NET: Registered protocol family 17
[4294796.963000] ACPI: Power Button (FF) [PWRF]
[4294796.963000] ACPI: Power Button (CM) [PBTN]
[4294797.242000] ibm_acpi: ec object not found
[4294811.858000] apm: BIOS not found.
[4294814.568000] powernow: No powernow capabilities detected
[4294814.930000] Bluetooth: Core ver 2.7
[4294814.930000] NET: Registered protocol family 31
[4294814.930000] Bluetooth: HCI device and connection manager initialized
[4294814.930000] Bluetooth: HCI socket layer initialized
[4294814.982000] Bluetooth: L2CAP ver 2.7
[4294814.982000] Bluetooth: L2CAP socket layer initialized
[4294815.028000] Bluetooth: RFCOMM ver 1.5
[4294815.028000] Bluetooth: RFCOMM socket layer initialized
[4294815.028000] Bluetooth: RFCOMM TTY layer initialized
[4294833.667000] NET: Registered protocol family 10
[4294833.668000] Disabled Privacy Extensions on device c02eb280(lo)
[4294833.668000] IPv6 over IPv4 tunneling driver
[4294844.640000] eth0: no IPv6 routers present

---

### Post by snakedog on 2005-12-31
...an addendum: this is a 3com card.  Model# 3C900B-TPO.  

I've been on and off the computer the last day or so.  It's not pulling an ip address until 7-8 minutes after logging in.  After that, no problems.  TCP/IP stays up.  

TIA.

---

### Post by Lambert on 2005-12-31
This is just a thought, I don't know the answer and I could be completely wrong with what I'm going to say. Somebody correct me if I'm wrong.

When dhclient is started, it runs in the foreground trying to contact a dhcp server. It actually stays in the foreground running until it finds a server. I'm not sure what the interval is but I don't believe it's constant. This is why I believe you get an ip a few minutes later.

So why are you not getting information on first try when booting  but later? When the os sends out the dhcp request, there's no path to the router set up yet so no data is transferred between your box and the router.

So here is something to test. 

Open your /etc/network/interfaces file in editor (need root user privledges)

add this line to the end of the interface 

post-up dhclient eth0 (may need to add sudo before dhclient)


Now when you boot are you connected immediately?

---

