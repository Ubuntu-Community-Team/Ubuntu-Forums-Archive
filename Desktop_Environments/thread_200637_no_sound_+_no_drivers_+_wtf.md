---
title: "no sound + no drivers + wtf"
date: 2006-06-20
forum: Desktop Environments
---

### Post by WARMACHINE on 2006-06-20
I have 5.10, So yesturday i was looking through some stuff in my "System" tab and went to "Users And Groups", i added another user as a root user and myself as a root user(from "man"), just to see what the difference is. I restart, suddenly i have no sound/no video and none of my drivers are found, and i can't access "Users And Groups" or Synaptic anymore. So if anyone could help.

---

### Post by tehwa on 2006-06-20
what does ```
dmesg
``` and other logs say after logging in?

This is definitely a result of changes in permissions.

---

### Post by WARMACHINE on 2006-06-21
[QUOTE=tehwa]what does ```
dmesg
``` and other logs say after logging in?

This is definitely a result of changes in permissions.[/QUOTE]


```

rk v1.0.0 initialized
[4294671.361000] SELinux:  Disabled at boot.
[4294671.361000] Mount-cache hash table entries: 512
[4294671.361000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000041d 00000000 00000000
[4294671.361000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 0000041d 00000000 00000000
[4294671.361000] monitor/mwait feature present.
[4294671.361000] using mwait in idle threads.
[4294671.361000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[4294671.361000] CPU: L2 cache: 1024K
[4294671.361000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 0000041d 00000000 00000000
[4294671.361000] CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 03
[4294671.361000] Enabling fast FPU save and restore... done.
[4294671.361000] Enabling unmasked SIMD FPU exception support... done.
[4294671.361000] Checking 'hlt' instruction... OK.
[4294671.365000] Checking for popad bug... OK.
[4294671.365000] checking if image is initramfs... it is
[4294671.772000] Freeing initrd memory: 5165k freed
[4294671.773000] ACPI: Looking for DSDT in initrd... not found!
[4294671.815000]  not found!
[4294671.820000] ENABLING IO-APIC IRQs
[4294671.821000] ..TIMER: vector=0x31 pin1=2 pin2=-1
[4294671.932000] NET: Registered protocol family 16
[4294671.932000] EISA bus registered
[4294671.932000] ACPI: bus type pci registered
[4294671.932000] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
[4294671.932000] PCI: Using configuration type 1
[4294671.932000] mtrr: v2.0 (20020519)
[4294671.932000] ACPI: Subsystem revision 20050729
[4294671.937000] ACPI: Interpreter enabled
[4294671.937000] ACPI: Using IOAPIC for interrupt routing
[4294671.938000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294671.938000] PCI: Probing PCI hardware (bus 00)
[4294671.938000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294671.941000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[4294671.941000] Boot video device is 0000:01:00.0
[4294671.941000] PCI: Transparent bridge - 0000:00:1e.0
[4294671.950000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294671.950000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[4294671.956000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[4294671.956000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[4294671.957000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[4294671.957000] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
[4294671.957000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[4294671.957000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[4294671.958000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[4294671.958000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[4294671.958000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294671.958000] pnp: PnP ACPI init
[4294671.961000] pnp: PnP ACPI: found 12 devices
[4294671.961000] PnPBIOS: Disabled by ACPI PNP
[4294671.961000] PCI: Using ACPI for IRQ routing
[4294671.961000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294671.966000] pnp: 00:08: ioport range 0x680-0x6ff has been reserved
[4294671.966000] pnp: 00:08: ioport range 0x290-0x297 has been reserved
[4294671.967000] audit: initializing netlink socket (disabled)
[4294671.967000] audit: initialized
[4294671.967000] VFS: Disk quotas dquot_6.5.1
[4294671.967000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294671.967000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294671.967000] devfs: boot_options: 0x0
[4294671.967000] Initializing Cryptographic API
[4294671.967000] isapnp: Scanning for PnP cards...
[4294672.321000] isapnp: No Plug & Play device found
[4294672.339000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[4294672.341000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294672.341000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294672.341000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294672.343000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> GSI 17 (level, low) -> IRQ 17
[4294672.343000] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[4294672.343000] io scheduler noop registered
[4294672.343000] io scheduler anticipatory registered
[4294672.343000] io scheduler deadline registered
[4294672.343000] io scheduler cfq registered
[4294672.344000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294672.344000] EISA: Probing bus 0 at eisa.0
[4294672.344000] EISA: Detected 0 cards.
[4294672.344000] NET: Registered protocol family 2
[4294672.353000] IP: routing cache hash table of 4096 buckets, 32Kbytes
[4294672.353000] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
[4294672.353000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
[4294672.353000] TCP: Hash tables configured (established 32768 bind 32768)
[4294672.353000] NET: Registered protocol family 8
[4294672.353000] NET: Registered protocol family 20
[4294672.353000] ACPI wakeup devices:
[4294672.353000] P0P4 MC97 USB1 USB2 USB3 USB4 EUSB PS2K ILAN PWRB
[4294672.353000] ACPI: (supports S0 S1 S3 S4 S5)
[4294672.353000] Freeing unused kernel memory: 224k freed
[4294672.368000] vga16fb: initializing
[4294672.368000] vga16fb: mapped to 0xc00a0000
[4294672.480000] Console: switching to colour frame buffer device 80x30
[4294672.480000] fb0: VGA16 VGA frame buffer device
[4294672.488000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294673.627000] Capability LSM initialized
[4294673.637000] NET: Registered protocol family 1
[4294673.650000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294673.650000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294673.650000] ACPI: bus type ide registered
[4294673.656000] ICH5: IDE controller at PCI slot 0000:00:1f.1
[4294673.656000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[4294673.656000] ICH5: chipset revision 2
[4294673.656000] ICH5: not 100% native mode: will probe irqs later
[4294673.656000]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:DMA
[4294673.656000]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:DMA
[4294673.656000] Probing IDE interface ide0...
[4294673.920000] hda: WDC WD1600BB-98DWA0, ATA DISK drive
[4294674.175000] hdb: QUANTUM FIREBALLlct20 30, ATA DISK drive
[4294674.227000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294674.227000] Probing IDE interface ide1...
[4294674.899000] hdc: HL-DT-ST DVD-RW GWA-4040B, ATAPI CD/DVD-ROM drive
[4294675.613000] hdd: HL-DT-STDVD-ROM GDR8162B, ATAPI CD/DVD-ROM drive
[4294675.664000] ide1 at 0x170-0x177,0x376 on irq 15
[4294675.664000] Probing IDE interface ide2...
[4294676.177000] Probing IDE interface ide3...
[4294676.689000] Probing IDE interface ide4...
[4294677.201000] Probing IDE interface ide5...
[4294677.716000] hda: max request size: 1024KiB
[4294677.724000] hda: 312581808 sectors (160041 MB) w/2048KiB Cache, CHS=19457/255/63, UDMA(100)
[4294677.726000] hda: cache flushes supported
[4294677.726000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
[4294677.758000] hdb: max request size: 128KiB
[4294677.759000] hdb: 58633344 sectors (30020 MB) w/418KiB Cache, CHS=58168/16/63, UDMA(33)
[4294677.759000] hdb: cache flushes not supported
[4294677.760000]  /dev/ide/host0/bus0/target1/lun0:
[4294677.771000] hdc: ATAPI 32X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[4294677.771000] Uniform CD-ROM driver Revision: 3.20
[4294677.789000] hdd: ATAPI 48X DVD-ROM drive, 256kB Cache
[4294678.163000] Attempting manual resume
[4294678.167000] swsusp: Suspend partition has wrong signature?
[4294678.194000] usbcore: registered new driver usbfs
[4294678.194000] usbcore: registered new driver hub
[4294678.195000] USB Universal Host Controller Interface driver v2.2
[4294678.195000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294678.195000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294678.195000] uhci_hcd 0000:00:1d.0: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
[4294678.257000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294678.257000] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000e000
[4294678.257000] hub 1-0:1.0: USB hub found
[4294678.257000] hub 1-0:1.0: 2 ports detected
[4294678.260000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[4294678.260000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294678.260000] uhci_hcd 0000:00:1d.1: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
[4294678.322000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294678.322000] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e400
[4294678.322000] hub 2-0:1.0: USB hub found
[4294678.322000] hub 2-0:1.0: 2 ports detected
[4294678.325000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[4294678.325000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294678.325000] uhci_hcd 0000:00:1d.2: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI #3
[4294678.387000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294678.387000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e800
[4294678.387000] hub 3-0:1.0: USB hub found
[4294678.387000] hub 3-0:1.0: 2 ports detected
[4294678.390000] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
[4294678.390000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[4294678.390000] uhci_hcd 0000:00:1d.3: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
[4294678.452000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[4294678.452000] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000ec00
[4294678.452000] hub 4-0:1.0: USB hub found
[4294678.452000] hub 4-0:1.0: 2 ports detected
[4294678.479000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 23
[4294678.479000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294678.479000] ehci_hcd 0000:00:1d.7: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
[4294678.479000] ehci_hcd 0000:00:1d.7: debug port 1
[4294678.479000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[4294678.479000] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfebffc00
[4294678.483000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[4294678.483000] ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294678.483000] hub 5-0:1.0: USB hub found
[4294678.483000] hub 5-0:1.0: 8 ports detected
[4294678.550000] e100: Intel(R) PRO/100 Network Driver, 3.4.8-k2-NAPI
[4294678.550000] e100: Copyright(c) 1999-2005 Intel Corporation
[4294678.551000] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 20 (level, low) -> IRQ 20
[4294678.573000] e100: eth0: e100_probe: addr 0xfeaff000, irq 20, MAC addr 00:0E:A6:8B:C9:8F
[4294681.086000] ACPI: CPU0 (power states: C1[C1])
[4294681.307000] Attempting manual resume
[4294681.333000] swsusp: Suspend partition has wrong signature?
[4294681.375000] kjournald starting.  Commit interval 5 seconds
[4294681.375000] EXT3-fs: mounted filesystem with ordered data mode.
[4294682.510000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294685.808000] Adding 1510068k swap on /dev/hda5.  Priority:-1 extents:1
[4294686.087000] EXT3 FS on hda1, internal journal
[4294691.767000] parport: PnPBIOS parport detected.
[4294691.767000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[4294691.853000] lp0: using parport0 (interrupt-driven).
[4294691.875000] mice: PS/2 mouse device common for all mice
[4294691.908000] ieee1394: Initialized config rom entry `ip1394'
[4294691.914000] SCSI subsystem initialized
[4294691.922000] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[4294692.237000] input: ImPS/2 Logitech Wheel Mouse on isa0060/serio1
[4294692.777000] ts: Compaq touchscreen protocol output
[4294695.543000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294696.376000] cdrom: open failed.
[4294696.397000] cdrom: open failed.
[4294698.940000] Linux agpgart interface v0.101 (c) Dave Jones
[4294698.947000] agpgart: Detected an Intel 865 Chipset.
[4294698.964000] agpgart: AGP aperture is 64M @ 0xf8000000
[4294699.041000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294699.050000] shpchp: shpc_init : shpc_cap_offset == 0
[4294699.050000] shpchp: shpc_init : shpc_cap_offset == 0
[4294699.050000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294699.335000] hw_random: RNG not detected
[4294699.663000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 17
[4294699.663000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[4294700.473000] intel8x0_measure_ac97_clock: measured 49459 usecs
[4294700.473000] intel8x0: clocking to 48000
[4294701.704000] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[4294701.704000] ACPI: PCI Interrupt 0000:02:0e.0[A] -> GSI 18 (level, low) -> IRQ 18
[4294701.708000] ohci1394: fw-host0: Unexpected PCI resource length of 1000!
[4294701.759000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[feafd000-feafd7ff]  Max Packet=[2048]
[4294702.919000] Real Time Clock Driver v1.12
[4294703.025000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[080046030193a5e5][4294703.140000] input: PC Speaker
[4294703.205000] Floppy drive(s): fd0 is 1.44M
[4294703.238000] FDC 0 is a post-1991 82077
[4294704.966000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[4294704.975000] NET: Registered protocol family 17
[4294709.605000] NET: Registered protocol family 10
[4294709.605000] Disabled Privacy Extensions on device c02eb280(lo)
[4294709.605000] IPv6 over IPv4 tunneling driver
[4294711.071000] ACPI: Power Button (FF) [PWRF]
[4294711.071000] ACPI: Power Button (CM) [PWRB]
[4294711.165000] ibm_acpi: ec object not found
[4294716.770000] mtrr: type mismatch for e0000000,8000000 old: write-back new: write-combining
[4294716.991000] [drm] Initialized drm 1.0.0 20040925
[4294716.994000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294716.994000] mtrr: type mismatch for f8000000,4000000 old: write-back new: write-combining
[4294716.997000] [drm] Initialized radeon 1.16.0 20050311 on minor 0: ATI Technologies Inc RV280 [Radeon 9200]
[4294716.997000] mtrr: type mismatch for e0000000,8000000 old: write-back new: write-combining
[4294716.997000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[4294716.997000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
[4294716.998000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 4x mode
[4294717.002000] [drm] Loading R200 Microcode
[4294718.750000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294718.750000] apm: overridden by ACPI.
[4294718.872000] ip_tables: (C) 2000-2002 Netfilter core team
[4294718.898000] ip_conntrack version 2.1 (4094 buckets, 32752 max) - 248 bytes per conntrack
[4294720.087000] eth0: no IPv6 routers present
[4294721.098000] Bluetooth: Core ver 2.7
[4294721.098000] NET: Registered protocol family 31
[4294721.098000] Bluetooth: HCI device and connection manager initialized
[4294721.098000] Bluetooth: HCI socket layer initialized
[4294721.113000] Bluetooth: L2CAP ver 2.7
[4294721.113000] Bluetooth: L2CAP socket layer initialized
[4294721.142000] Bluetooth: RFCOMM ver 1.5
[4294721.142000] Bluetooth: RFCOMM socket layer initialized
[4294721.142000] Bluetooth: RFCOMM TTY layer initialized

```

when i enter it in, that's what comes up...i can't log into the other account i made, for some odd reason..but it wouldn't matter because i would have deleted it anyway.

---

### Post by garba on 2006-06-21
please fire up a terminal and type:

cat /etc/group

then post the output

---

### Post by WARMACHINE on 2006-06-21
[QUOTE=garba]please fire up a terminal and type:

cat /etc/group

then post the output[/QUOTE]


```

root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:
tty:x:5:
disk:x:6:
lp:x:7:cupsys
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:
fax:x:21:
voice:x:22:
cdrom:x:24:
floppy:x:25:
tape:x:26:
sudo:x:27:
audio:x:29:
dip:x:30:
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:cupsys
utmp:x:43:
video:x:44:
sasl:x:45:
plugdev:x:46:
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
max:x:1000:
lpadmin:x:104:
scanner:x:105:
admin:x:106:
crontab:x:107:
ssh:x:108:
slocate:x:109:
messagebus:x:110:
hal:x:111:
saned:x:112:
gdm:x:113:

```

---

