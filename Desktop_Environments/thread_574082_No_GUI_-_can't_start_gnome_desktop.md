---
title: "No GUI - can't start gnome desktop"
date: 2007-10-12
forum: Desktop Environments
---

### Post by leond on 2007-10-12
I tried sudo /etc/init.d/gdm restart
it says gnome is started, flickering the screen a couple of times.  I switched to ctl-alt-F7 , but saw only a cursor.
The /var/log says "Fatal server error:  no screens found".  I'm attaching the serial boot log and dmesg.
menu: hda1:/boot/grub/menu.lst
hda: LBA 20GB: ST320413A 
Mounted ext2fs
Found Linux version 2.6.20-16-generic (root@terranova) #2 SMP Sun Sep 23 19:50:3
9 UTC 2007 (protocol 0x205) (loadflags 0x1) bzImage.
init_linux_params: Setting up paramters at 0x90000
set_memory_size: 0000000000001000 - 00000000000a0000
set_memory_size: 00000000000c0000 - 00000000000f0000
set_memory_size: 0000000000100000 - 0000000040000000
set_memory_size: ramtop=0x40000000
set_memory_size: ext_mem_k=64512, alt_mem_k=1047552
parse_command_line: original command line: "root=UUID=5b3a4606-2585-402e-87be-4b
314cc7edd0 ro console=tty0 console=ttyS0,115200 quiet splash initrd=/boot/initrd
.img-2.6.20-16-generic"
parse_command_line: kernel command line at 0x91000
parse_command_line: initrd=/boot/initrd.img-2.6.20-16-generic
parse_command_line: kernel command line (96 bytes): "root=UUID=5b3a4606-2585-402
e-87be-4b314cc7edd0 ro console=tty0 console=ttyS0,115200 quiet splash"
load_linux_kernel: offset=0x1e00 addr=0x100000 size=0x1a8bac
Loading kernel... ok
load_initrd: start=0x1f961000 end=0x1ffffead
Loading initrd... ok
start_linux: eip=0x100000
Jumping to entry point...
[ 0.000000] ACPI: Unable to locate RSDP
[ 0.173372] PCI: Unable to handle 64-bit address space for bridge 0000:01:0a.
0
Loading, please wait...
usplash: libusplash.c:260: switch_console: Assertion `(saved_vt >= 0) && (saved_
vt < 10)' failed.
kinit: name_to_dev_t(/dev/disk/by-uuid/de4789bd-6c3e-4035-8587-c3d7d86e9c49) = h
da5(3,5)
kinit: trying to resume from /dev/disk/by-uuid/de4789bd-6c3e-4035-8587-c3d7d86e9
c49
kinit: No resume image, doing normal boot...
* Reading files needed to boot... [ OK ]
* Setting preliminary keymap... [ OK ]
* Preparing restricted drivers... [ OK ]
* Starting basic networking... [ OK ]
* Starting kernel event manager... [ OK ]
* Loading hardware drivers... 
[ 24.152000] shpchp: shpc_init: cannot reserve MMIO region
[ 24.156000] shpchp: shpc_init: cannot reserve MMIO region
[ 24.160000] shpchp: shpc_init: cannot reserve MMIO region
[ OK ]
* Loading kernel modules... 
* Loading manual drivers... [ OK ]
* Activating swap... [ OK ]
* Checking root file system... 
fsck 1.40-WIP (14-Nov-2006)
/dev/hda1: clean, 139655/2338336 files, 735473/4672899 blocks
[ OK ]
* Checking file systems... 
fsck 1.40-WIP (14-Nov-2006)
[ OK ]
* Mounting local filesystems... [ OK ]
* Activating swapfile swap... [ OK ]
* Configuring network interfaces... [ OK ]
* Starting system log daemon... [ OK ]
* Doing Wacom setup... 
cat: */id: No such file or directory
[ OK ]
* Starting kernel log... [ OK ]
* Starting system message bus dbus [ OK ]
* Starting Hardware abstraction layer hald [ OK ]
* Starting DHCP D-Bus daemon dhcdbd [ OK ]
* Starting network connection manager NetworkManager [ OK ]
* Starting Avahi mDNS/DNS-SD Daemon: avahi-daemon [ OK ]
* Starting network events dispatcher NetworkManagerDispatcher [ OK ]
* Starting System Tools Backends system-tools-backends [ OK ]
* Starting GNOME Display Manager... [ OK ]
* Starting Common Unix Printing System: cupsd [ OK ]
* Starting HP Linux Printing and Imaging System [ OK ]
* Starting powernowd... 
/etc/rc2.d/S20powernowd: 156: cannot create /sys/devices/system/cpu/cpu0//cpufre
q/scaling_governor: Directory nonexistent
* CPU frequency scaling not supported
[ OK ]
* Starting Bluetooth services [ OK ]
* Starting anac(h)ronistic cron anacron [ OK ]
* Starting deferred execution scheduler atd [ OK ]
* Starting periodic command scheduler crond [ OK ]
* Enabling additional executable binary formats binfmt-support [ OK ]
* Checking battery state... [ OK ]
* Running local boot scripts (/etc/rc.local) [ OK ]

dmseg:
======
[ 0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Sep 23 19:50:39 UTC 2007 (Ubuntu 2.6.20-16.32-generic)
[ 0.000000] BIOS-provided physical RAM map:
[ 0.000000] sanitize start
[ 0.000000] sanitize end
[ 0.000000] copy_e820_map() start: 0000000000001000 size: 000000000009f000 end: 00000000000a0000 type: 1
[ 0.000000] copy_e820_map() type is E820_RAM
[ 0.000000] copy_e820_map() start: 00000000000c0000 size: 0000000000030000 end: 00000000000f0000 type: 1
[ 0.000000] copy_e820_map() type is E820_RAM
[ 0.000000] copy_e820_map() lies in range...
[ 0.000000] copy_e820_map() end <= 0x100000ULL
[ 0.000000] copy_e820_map() start: 0000000000100000 size: 000000003ff00000 end: 0000000040000000 type: 1
[ 0.000000] copy_e820_map() type is E820_RAM
[ 0.000000] BIOS-e820: 0000000000001000 - 00000000000a0000 (usable)
[ 0.000000] BIOS-e820: 0000000000100000 - 0000000040000000 (usable)
[ 0.000000] 128MB HIGHMEM available.
[ 0.000000] 896MB LOWMEM available.
[ 0.000000] found SMP MP-table at 00000010
[ 0.000000] Entering add_active_range(0, 0, 262144) 0 entries of 256 used
[ 0.000000] Zone PFN ranges:
[ 0.000000] DMA 0 -> 4096
[ 0.000000] Normal 4096 -> 229376
[ 0.000000] HighMem 229376 -> 262144
[ 0.000000] early_node_map[1] active PFN ranges
[ 0.000000] 0: 0 -> 262144
[ 0.000000] On node 0 totalpages: 262144
[ 0.000000] DMA zone: 32 pages used for memmap
[ 0.000000] DMA zone: 0 pages reserved
[ 0.000000] DMA zone: 4064 pages, LIFO batch:0
[ 0.000000] Normal zone: 1760 pages used for memmap
[ 0.000000] Normal zone: 223520 pages, LIFO batch:31
[ 0.000000] HighMem zone: 256 pages used for memmap
[ 0.000000] HighMem zone: 32512 pages, LIFO batch:7
[ 0.000000] DMI not present or invalid.
[ 0.000000] ACPI: Unable to locate RSDP
[ 0.000000] Intel MultiProcessor Specification v1.4
[ 0.000000] Virtual Wire compatibility mode.
[ 0.000000] OEM ID: TYAN Product ID: S2881 APIC at: 0xFEE00000
[ 0.000000] Processor #0 15:1 APIC version 16
[ 0.000000] Processor #1 15:1 APIC version 16
[ 0.000000] I/O APIC #2 Version 17 at 0xFEC00000.
[ 0.000000] I/O APIC #3 Version 17 at 0xFD200000.
[ 0.000000] I/O APIC #4 Version 17 at 0xFD201000.
[ 0.000000] Enabling APIC mode: Flat. Using 3 I/O APICs
[ 0.000000] Processors: 2
[ 0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:c0000000)
[ 0.000000] Detected 2191.253 MHz processor.
[ 76.672598] Built 1 zonelists. Total pages: 260096
[ 76.672601] Kernel command line: root=UUID=5b3a4606-2585-402e-87be-4b314cc7edd0 ro console=tty0 console=ttyS0,115200 quiet splash
[ 76.672724] mapped APIC to ffffd000 (fee00000)
[ 76.672726] mapped IOAPIC to ffffc000 (fec00000)
[ 76.672728] mapped IOAPIC to ffffb000 (fd200000)
[ 76.672730] mapped IOAPIC to ffffa000 (fd201000)
[ 76.672732] Enabling fast FPU save and restore... done.
[ 76.672734] Enabling unmasked SIMD FPU exception support... done.
[ 76.672742] Initializing CPU#0
[ 76.672806] PID hash table entries: 4096 (order: 12, 16384 bytes)
[ 76.675390] Console: colour VGA+ 80x25
[ 76.679884] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[ 76.680249] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[ 76.697022] Memory: 1028524k/1048576k available (1993k kernel code, 19496k reserved, 900k data, 328k init, 131072k highmem)
[ 76.697031] virtual kernel memory layout:
[ 76.697032] fixmap : 0xfff4e000 - 0xfffff000 ( 708 kB)
[ 76.697033] pkmap : 0xff800000 - 0xffc00000 (4096 kB)
[ 76.697034] vmalloc : 0xf8800000 - 0xff7fe000 ( 111 MB)
[ 76.697035] lowmem : 0xc0000000 - 0xf8000000 ( 896 MB)
[ 76.697036] .init : 0xc03d9000 - 0xc042b000 ( 328 kB)
[ 76.697037] .data : 0xc02f2429 - 0xc03d36d4 ( 900 kB)
[ 76.697038] .text : 0xc0100000 - 0xc02f2429 (1993 kB)
[ 76.697041] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[ 76.776739] Calibrating delay using timer specific routine.. 4386.55 BogoMIPS (lpj=8773117)
[ 76.776774] Security Framework v1.0.0 initialized
[ 76.776779] SELinux: Disabled at boot.
[ 76.776792] Mount-cache hash table entries: 512
[ 76.776908] CPU: After generic identify, caps: 178bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000003
[ 76.776916] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[ 76.776918] CPU: L2 Cache: 1024K (64 bytes/line)
[ 76.776920] CPU 0(2) -> Core 0
[ 76.776922] CPU: After all inits, caps: 178bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000003
[ 76.776932] Compat vDSO mapped to ffffe000.
[ 76.776935] Remapping vsyscall page to ffffe000
[ 76.776944] Checking 'hlt' instruction... OK.
[ 76.792851] SMP alternatives: switching to UP code
[ 76.793231] Early unpacking initramfs... done
[ 77.047725] CPU0: AMD Dual Core AMD Opteron(tm) Processor 275 stepping 02
[ 77.047744] SMP alternatives: switching to SMP code
[ 77.047840] Booting processor 1/1 eip 3000
[ 77.058051] Initializing CPU#1
[ 77.136478] Calibrating delay using timer specific routine.. 4382.41 BogoMIPS (lpj=8764835)
[ 77.136484] CPU: After generic identify, caps: 178bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000003
[ 77.136490] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[ 77.136492] CPU: L2 Cache: 1024K (64 bytes/line)
[ 77.136494] CPU 1(2) -> Core 1
[ 77.136495] CPU: After all inits, caps: 178bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000003
[ 77.136686] CPU1: AMD Dual Core AMD Opteron(tm) Processor 275 stepping 02
[ 77.136700] Total of 2 processors activated (8768.97 BogoMIPS).
[ 77.136923] ENABLING IO-APIC IRQs
[ 77.137192] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[ 77.284380] checking TSC synchronization across 2 CPUs: passed.
[ 0.003997] Brought up 2 CPUs
[ 0.171190] migration_cost=524
[ 0.171415] Booting paravirtualized kernel on bare hardware
[ 0.171502] Time: 18:46:21 Date: 09/06/107
[ 0.171528] NET: Registered protocol family 16
[ 0.171597] EISA bus registered
[ 0.172005] PCI: Using configuration type 1
[ 0.172007] Setting up standard PCI resources
[ 0.172475] ACPI: Interpreter disabled.
[ 0.172477] Linux Plug and Play Support v0.97 (c) Adam Belay
[ 0.172483] pnp: PnP ACPI: disabled
[ 0.172484] PnPBIOS: Scanning system for PnP BIOS support...
[ 0.172493] PnPBIOS: PnP BIOS support was not detected.
[ 0.172524] PCI: Probing PCI hardware
[ 0.172526] PCI: Probing PCI hardware (bus 00)
[ 0.173220] Boot video device is 0000:02:06.0
[ 0.173372] PCI: Unable to handle 64-bit address space for bridge 0000:01:0a.0
[ 0.181144] PCI: Discovered primary peer bus 01 [IRQ]
[ 0.181149] PCI: Using IRQ router default [1022/7468] at 0000:01:07.0
[ 0.181159] PCI->APIC IRQ transform: 0000:01:07.2[D] -> IRQ 19
[ 0.181166] PCI->APIC IRQ transform: 0000:02:00.0[D] -> IRQ 19
[ 0.181169] PCI->APIC IRQ transform: 0000:02:00.1[D] -> IRQ 19
[ 0.181172] PCI->APIC IRQ transform: 0000:02:06.0[A] -> IRQ 18
[ 0.181175] PCI->APIC IRQ transform: 0000:03:09.0[A] -> IRQ 24
[ 0.181178] PCI->APIC IRQ transform: 0000:03:09.1[B] -> IRQ 25
[ 0.181224] NET: Registered protocol family 8
[ 0.181225] NET: Registered protocol family 20
[ 0.181445] PCI: Bridge: 0000:01:06.0
[ 0.181448] IO window: 1000-1fff
[ 0.181452] MEM window: fc000000-fd0fffff
[ 0.181456] PREFETCH window: 50000000-500fffff
[ 0.181461] PCI: Bridge: 0000:01:0a.0
[ 0.181462] IO window: disabled.
[ 0.181465] MEM window: fd100000-fd1fffff
[ 0.181468] PREFETCH window: 50100000-501fffff
[ 0.181470] PCI: Bridge: 0000:01:0b.0
[ 0.181472] IO window: disabled.
[ 0.181474] MEM window: disabled.
[ 0.181476] PREFETCH window: disabled.
[ 0.181522] NET: Registered protocol family 2
[ 0.215878] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[ 0.215998] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[ 0.216815] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[ 0.217213] TCP: Hash tables configured (established 131072 bind 65536)
[ 0.217215] TCP reno registered
[ 0.231932] checking if image is initramfs... it is
[ 0.734631] Freeing initrd memory: 6779k freed
[ 1.244000] audit: initializing netlink socket (disabled)
[ 1.244000] audit(1191696382.428:1): initialized
[ 1.244000] highmem bounce pool size: 64 pages
[ 1.244000] VFS: Disk quotas dquot_6.5.1
[ 1.244000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[ 1.244000] io scheduler noop registered
[ 1.244000] io scheduler anticipatory registered
[ 1.244000] io scheduler deadline registered
[ 1.244000] io scheduler cfq registered (default)
[ 1.244000] PCI: MSI quirk detected. PCI_BUS_FLAGS_NO_MSI set for 0000:01:0a.0 subordinate bus.
[ 1.244000] PCI: MSI quirk detected. PCI_BUS_FLAGS_NO_MSI set for 0000:01:0b.0 subordinate bus.
[ 1.248000] isapnp: Scanning for PnP cards...
[ 1.600000] isapnp: No Plug & Play device found
[ 1.620000] Real Time Clock Driver v1.12ac
[ 1.620000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[ 1.620000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 1.620000] mice: PS/2 mouse device common for all mice
[ 1.620000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[ 1.620000] input: Macintosh mouse button emulation as /class/input/input0
[ 1.620000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[ 1.620000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[ 1.620000] PNP: No PS/2 controller found. Probing ports directly.
[ 1.624000] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 1.624000] serio: i8042 AUX port at 0x60,0x64 irq 12
[ 1.624000] EISA: Probing bus 0 at eisa.0
[ 1.624000] Cannot allocate resource for EISA slot 1
[ 1.624000] Cannot allocate resource for EISA slot 2
[ 1.624000] EISA: Detected 0 cards.
[ 1.624000] TCP cubic registered
[ 1.624000] NET: Registered protocol family 1
[ 1.624000] Starting balanced_irq
[ 1.624000] Using IPI No-Shortcut mode
[ 1.624000] Magic number: 11:619:796
[ 1.624000] hash matches device ptyr4
[ 1.624000] Freeing unused kernel memory: 328k freed
[ 1.640000] input: AT Translated Set 2 keyboard as /class/input/input1
[ 2.836000] Capability LSM initialized
[ 2.896000] thermal: Unknown symbol acpi_processor_set_thermal_limit
[ 3.236000] SCSI subsystem initialized
[ 3.240000] libata version 2.20 loaded.
[ 3.252000] AMD8111: IDE controller at PCI slot 0000:01:07.1
[ 3.252000] AMD8111: chipset revision 3
[ 3.252000] AMD8111: not 100% native mode: will probe irqs later
[ 3.252000] AMD8111: 0000:01:07.1 (rev 03) UDMA133 controller
[ 3.252000] ide0: BM-DMA at 0x2420-0x2427, BIOS settings: hda:pio, hdb:pio
[ 3.252000] ide1: BM-DMA at 0x2428-0x242f, BIOS settings: hdc:pio, hdd:pio
[ 3.252000] Probing IDE interface ide0...
[ 3.296000] usbcore: registered new interface driver usbfs
[ 3.296000] usbcore: registered new interface driver hub
[ 3.296000] usbcore: registered new device driver usb
[ 3.296000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[ 3.548000] hda: ST320413A, ATA DISK drive
[ 4.224000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[ 4.224000] Probing IDE interface ide1...
[ 4.792000] ohci_hcd 0000:02:00.0: OHCI Host Controller
[ 4.796000] ohci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 1
[ 4.796000] ohci_hcd 0000:02:00.0: irq 19, io mem 0xfd000000
[ 4.856000] usb usb1: configuration #1 chosen from 1 choice
[ 4.856000] hub 1-0:1.0: USB hub found
[ 4.856000] hub 1-0:1.0: 3 ports detected
[ 4.960000] ohci_hcd 0000:02:00.1: OHCI Host Controller
[ 4.960000] ohci_hcd 0000:02:00.1: new USB bus registered, assigned bus number 2
[ 4.960000] ohci_hcd 0000:02:00.1: irq 19, io mem 0xfd001000
[ 5.020000] usb usb2: configuration #1 chosen from 1 choice
[ 5.020000] hub 2-0:1.0: USB hub found
[ 5.020000] hub 2-0:1.0: 3 ports detected
[ 5.128000] tg3.c:v3.72.1 (January 8, 2007)
[ 5.160000] eth0: Tigon3 [partno(BCM95704A7) rev 2003 PHY(5704)] (PCIX:100MHz:64-bit) 10/100/1000Base-T Ethernet 00:e0:81:2f:6d:8c
[ 5.160000] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] Split[0] WireSpeed[1] TSOcap[1] 
[ 5.160000] eth0: dma_rwctrl[769f4000] dma_mask[64-bit]
[ 5.192000] eth1: Tigon3 [partno(BCM95704A7) rev 2003 PHY(5704)] (PCIX:100MHz:64-bit) 10/100/1000Base-T Ethernet 00:e0:81:2f:6d:8d
[ 5.192000] eth1: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] Split[0] WireSpeed[1] TSOcap[1] 
[ 5.192000] eth1: dma_rwctrl[769f4000] dma_mask[64-bit]
[ 5.196000] hda: max request size: 128KiB
[ 5.200000] hda: 39102336 sectors (20020 MB) w/512KiB Cache, CHS=38792/16/63, UDMA(100)
[ 5.200000] hda: cache flushes not supported
[ 5.200000] hda:<6>usb 1-2: new full speed USB device using ohci_hcd and address 2
[ 5.492000] usb 1-2: configuration #1 chosen from 1 choice
[ 5.708000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[ 5.708000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
[ 5.708000] ide: failed opcode was: unknown
[ 5.804000] usb 1-3: new low speed USB device using ohci_hcd and address 3
[ 6.020000] usb 1-3: configuration #1 chosen from 1 choice
[ 6.024000] usbcore: registered new interface driver libusual
[ 6.028000] Initializing USB Mass Storage driver...
[ 6.028000] scsi0 : SCSI emulation for USB Mass Storage devices
[ 6.028000] usb-storage: device found at 2
[ 6.028000] usb-storage: waiting for device to settle before scanning
[ 6.028000] usbcore: registered new interface driver usb-storage
[ 6.028000] USB Mass Storage support registered.
[ 6.032000] usbcore: registered new interface driver hiddev
[ 6.040000] input: HID 1241:1111 as /class/input/input2
[ 6.040000] input: USB HID v1.00 Mouse [HID 1241:1111] on usb-0000:02:00.0-3
[ 6.040000] usbcore: registered new interface driver usbhid
[ 6.040000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[ 6.212000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[ 6.212000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
[ 6.212000] ide: failed opcode was: unknown
[ 6.660000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[ 6.660000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
[ 6.660000] ide: failed opcode was: unknown
[ 7.152000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[ 7.152000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
[ 7.152000] ide: failed opcode was: unknown
[ 7.200000] ide0: reset: success
[ 7.220000] hda1 hda2 < hda5 >
[ 7.564000] Attempting manual resume
[ 7.564000] swsusp: Resume From Partition 3:5
[ 7.564000] PM: Checking swsusp image.
[ 7.600000] PM: Resume from disk failed.
[ 7.664000] kjournald starting. Commit interval 5 seconds
[ 7.664000] EXT3-fs: mounted filesystem with ordered data mode.
[ 8.252000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[ 8.252000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
[ 8.252000] ide: failed opcode was: unknown
[ 8.724000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[ 8.724000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
[ 8.724000] ide: failed opcode was: unknown
[ 9.176000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[ 9.176000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
[ 9.176000] ide: failed opcode was: unknown
[ 9.664000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[ 9.664000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
[ 9.664000] ide: failed opcode was: unknown
[ 9.712000] ide0: reset: success
[ 11.028000] usb-storage: device scan complete
[ 11.060000] scsi 0:0:0:0: Direct-Access NEC USB UF000x 1.50 PQ: 0 ANSI: 0 CCS
[ 20.620000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[ 20.620000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
[ 20.620000] ide: failed opcode was: unknown
[ 23.132000] PM: Writing back config space on device 0000:03:09.1 at offset b (was 164814e4, writing 164414e4)
[ 23.132000] PM: Writing back config space on device 0000:03:09.1 at offset 3 (was 804000, writing 804010)
[ 23.132000] PM: Writing back config space on device 0000:03:09.1 at offset 2 (was 2000000, writing 2000003)
[ 23.132000] PM: Writing back config space on device 0000:03:09.1 at offset 1 (was 2b00000, writing 2b00006)
[ 23.252000] PM: Writing back config space on device 0000:03:09.0 at offset b (was 164814e4, writing 164414e4)
[ 23.252000] PM: Writing back config space on device 0000:03:09.0 at offset 3 (was 804000, writing 804010)
[ 23.252000] PM: Writing back config space on device 0000:03:09.0 at offset 2 (was 2000000, writing 2000003)
[ 23.252000] PM: Writing back config space on device 0000:03:09.0 at offset 1 (was 2b00000, writing 2b00006)
[ 24.020000] AMD768 RNG detected
[ 24.136000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[ 24.148000] shpchp: Unknown symbol acpi_run_oshp
[ 24.148000] shpchp: Unknown symbol pci_hp_change_slot_info
[ 24.148000] shpchp: Unknown symbol pci_hp_register
[ 24.148000] shpchp: Unknown symbol pci_hp_deregister
[ 24.148000] shpchp: Unknown symbol acpi_get_hp_params_from_firmware
[ 24.152000] shpchp: Unknown symbol acpi_run_oshp
[ 24.152000] shpchp: Unknown symbol pci_hp_change_slot_info
[ 24.152000] shpchp: Unknown symbol pci_hp_register
[ 24.152000] shpchp: Unknown symbol pci_hp_deregister
[ 24.152000] shpchp: Unknown symbol acpi_get_hp_params_from_firmware
[ 24.152000] shpchp: HPC vendor_id 1022 device_id 7460 ss_vid 0 ss_did 0
[ 24.152000] shpchp: shpc_init: cannot reserve MMIO region
[ 24.156000] shpchp: HPC vendor_id 1022 device_id 7450 ss_vid 0 ss_did 0
[ 24.156000] shpchp: shpc_init: cannot reserve MMIO region
[ 24.160000] shpchp: HPC vendor_id 1022 device_id 7450 ss_vid 0 ss_did 0
[ 24.160000] shpchp: shpc_init: cannot reserve MMIO region
[ 24.164000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[ 24.444000] NET: Registered protocol family 17
[ 24.908000] sd 0:0:0:0: Attached scsi removable disk sda
[ 24.920000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[ 25.056000] fuse init (API version 7.8)
[ 25.116000] lp: driver loaded but no devices found
[ 25.144000] Adding 859436k swap on /dev/disk/by-uuid/de4789bd-6c3e-4035-8587-c3d7d86e9c49. Priority:-1 extents:1 across:859436k
[ 25.280000] EXT3 FS on hda1, internal journal
[ 29.492000] powernow_k8: Unknown symbol acpi_processor_notify_smm
[ 29.492000] powernow_k8: Unknown symbol acpi_processor_unregister_performance
[ 29.492000] powernow_k8: Unknown symbol acpi_processor_register_performance
[ 29.536000] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[ 29.536000] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[ 29.536000] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[ 29.536000] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[ 32.792000] ppdev: user-space parallel port driver
[ 33.580000] apm: BIOS not found.
[ 33.736000] Bluetooth: Core ver 2.11
[ 33.736000] NET: Registered protocol family 31
[ 33.736000] Bluetooth: HCI device and connection manager initialized
[ 33.736000] Bluetooth: HCI socket layer initialized
[ 33.772000] Bluetooth: L2CAP ver 2.8
[ 33.772000] Bluetooth: L2CAP socket layer initialized
[ 33.828000] Bluetooth: RFCOMM socket layer initialized
[ 33.828000] Bluetooth: RFCOMM TTY layer initialized
[ 33.828000] Bluetooth: RFCOMM ver 1.8
[ 66.780000] NET: Registered protocol family 10
[ 66.780000] lo: Disabled Privacy Extensions
[ 66.780000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 66.780000] ADDRCONF(NETDEV_UP): eth1: link is not ready

---

### Post by swisscow on 2007-10-12
Possibly your xorg.conf is stuffed up. If it is then:

From the command line login and type

```
cd /etc/X11/xorg.conf
```    (note the capitals)

Make a backup ```
sudo cp xorg.conf xorg.conf.bup
```    (just in case)

then type

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will rebuild the xorg to hopefuly something that works

than```
 startx
```

If it doesn't work you can restore the backup by ```
sudo cp xorg.conf.bup xorg.conf
``` and then you'll be back where you started.

---

