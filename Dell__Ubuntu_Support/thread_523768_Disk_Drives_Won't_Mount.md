---
title: "Disk Drives Won't Mount"
date: 2007-08-12
forum: Dell  Ubuntu Support
---

### Post by VerdantLightning on 2007-08-12
I'm having problems with my CDRW drive and DVD drive on Ubuntu. Specifically they won't mount. They neither mount automatically when media is inserted nor will they allow me to mount them manually with media inserted. When I try to mount manually it says "Unable to mount - there is probably no media present." The CDRW drive will mount a disc automatically only if I leave the disk in when I start the computer. When the desktop comes up the disk will be mounted. This only works in the CDRW drive.

I've asked this question at another board and gotten no solutions so this is sort of a last ditch type thing. Here is some information I was asked to gather when others tried to help if it will be useful. Thanks.

1.) Trying cat /etc/fstab and mount.
riley@riley-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=39fc69d4-511d-4cc9-a95f-9bd7086a200a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=72f5ebb1-3a07-4a60-84f4-48bdf8b1a3d7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
riley@riley-desktop:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdb2 on /med

2.) When trying mount /media/cdrom0 or cdrom1 nothing happens and after five minutes the system freezes.

3.) My /var/log/dmesg file
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 00000000000a0000 end: 00000000000a0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fd70000 end: 000000001fe70000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001fe70000 size: 0000000000002000 end: 000000001fe72000 type: 4
[    0.000000] copy_e820_map() start: 000000001fe72000 size: 0000000000021000 end: 000000001fe93000 type: 3
[    0.000000] copy_e820_map() start: 000000001fe93000 size: 000000000006d000 end: 000000001ff00000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
[    0.000000] copy_e820_map() start: 00000000fecf0000 size: 0000000000001000 end: 00000000fecf1000 type: 2
[    0.000000] copy_e820_map() start: 00000000fed20000 size: 0000000000070000 end: 00000000fed90000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000010000 end: 00000000fee10000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffb00000 size: 0000000000500000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fe70000 (usable)
[    0.000000]  BIOS-e820: 000000001fe70000 - 000000001fe72000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001fe72000 - 000000001fe93000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001fe93000 - 000000001ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fecf0000 - 00000000fecf1000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 510MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fe710
[    0.000000] Entering add_active_range(0, 0, 130672) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   130672
[    0.000000]   HighMem    130672 ->   130672
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   130672
[    0.000000] On node 0 totalpages: 130672
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 988 pages used for memmap
[    0.000000]   Normal zone: 125588 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 DELL                                  ) @ 0x000feb90
[    0.000000] ACPI: RSDT (v001 DELL    3000    0x00000008 ASL  0x00000061) @ 0x000fd28b
[    0.000000] ACPI: FADT (v001 DELL    3000    0x00000008 ASL  0x00000061) @ 0x000fd2bf
[    0.000000] ACPI: SSDT (v001   DELL    st_ex 0x00001000 MSFT 0x0100000d) @ 0xfffd1b7f
[    0.000000] ACPI: MADT (v001 DELL    3000    0x00000008 ASL  0x00000061) @ 0x000fd333
[    0.000000] ACPI: BOOT (v001 DELL    3000    0x00000008 ASL  0x00000061) @ 0x000fd39f
[    0.000000] ACPI: DSDT (v001   DELL    dt_ex 0x00001000 MSFT 0x0100000d) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:4 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1ff00000:ded00000)
[    0.000000] Detected 2793.238 MHz processor.
[    9.046903] Built 1 zonelists.  Total pages: 129652
[    9.046907] Kernel command line: root=UUID=39fc69d4-511d-4cc9-a95f-9bd7086a200a ro quiet splash
[    9.047077] mapped APIC to ffffd000 (fee00000)
[    9.047080] mapped IOAPIC to ffffc000 (fec00000)
[    9.047083] Enabling fast FPU save and restore... done.
[    9.047087] Enabling unmasked SIMD FPU exception support... done.
[    9.047096] Initializing CPU#0
[    9.047166] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    9.048685] Console: colour VGA+ 80x25
[    9.048918] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    9.049129] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    9.056942] Memory: 507192k/522688k available (1992k kernel code, 14964k reserved, 900k data, 328k init, 0k highmem)
[    9.056953] virtual kernel memory layout:
[    9.056954]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[    9.056955]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    9.056956]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[    9.056957]     lowmem  : 0xc0000000 - 0xdfe70000   ( 510 MB)
[    9.056958]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[    9.056959]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[    9.056961]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[    9.056964] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    9.135025] Calibrating delay using timer specific routine.. 5590.64 BogoMIPS (lpj=11181293)
[    9.135069] Security Framework v1.0.0 initialized
[    9.135075] SELinux:  Disabled at boot.
[    9.135092] Mount-cache hash table entries: 512
[    9.135226] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[    9.135235] monitor/mwait feature present.
[    9.135237] using mwait in idle threads.
[    9.135244] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    9.135247] CPU: L2 cache: 1024K
[    9.135250] CPU: Hyper-Threading is disabled
[    9.135252] CPU: After all inits, caps: bfebfbff 00000000 00000000 00003180 0000441d 00000000 00000000
[    9.135262] Compat vDSO mapped to ffffe000.
[    9.135266] Remapping vsyscall page to ffffe000
[    9.135282] Checking 'hlt' instruction... OK.
[    9.151090] SMP alternatives: switching to UP code
[    9.151255] Freeing SMP alternatives: 11k freed
[    9.151452] Early unpacking initramfs... done
[    9.442614] ACPI: Core revision 20060707
[    9.448308] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[    9.471759] CPU0: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 01
[    9.471801] Total of 1 processors activated (5590.64 BogoMIPS).
[    9.471934] ENABLING IO-APIC IRQs
[    9.472117] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    9.618262] Brought up 1 CPUs
[    9.618501] Booting paravirtualized kernel on bare hardware
[    9.618572] Time: 11:03:39  Date: 07/12/107
[    9.618598] NET: Registered protocol family 16
[    9.618683] EISA bus registered
[    9.618688] ACPI: bus type pci registered
[    9.643346] PCI: PCI BIOS revision 2.10 entry at 0xfbbf8, last bus=1
[    9.643348] PCI: Using configuration type 1
[    9.643350] Setting up standard PCI resources
[    9.675129] ACPI: Interpreter enabled
[    9.675132] ACPI: Using IOAPIC for interrupt routing
[    9.679659] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    9.679669] PCI: Probing PCI hardware (bus 00)
[    9.679691] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[    9.681896] Boot video device is 0000:00:02.0
[    9.682255] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[    9.682260] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
[    9.682540] PCI: Firmware left 0000:01:08.0 e100 interrupts enabled, disabling
[    9.682612] PCI: Transparent bridge - 0000:00:1e.0
[    9.682637] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    9.832811] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    9.849123] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[    9.849862] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 15)
[    9.850599] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[    9.851334] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    9.852075] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[    9.852824] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[    9.853562] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    9.854306] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[    9.854468] Linux Plug and Play Support v0.97 (c) Adam Belay
[    9.854478] pnp: PnP ACPI init
[    9.884631] pnp: PnP ACPI: found 11 devices
[    9.884637] PnPBIOS: Disabled by ACPI PNP
[    9.884680] PCI: Using ACPI for IRQ routing
[    9.884684] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    9.889648] NET: Registered protocol family 8
[    9.889651] NET: Registered protocol family 20
[    9.896423] pnp: 00:0a: ioport range 0x800-0x85f could not be reserved
[    9.896427] pnp: 00:0a: ioport range 0xc00-0xc7f has been reserved
[    9.896430] pnp: 00:0a: ioport range 0x860-0x8ff could not be reserved
[    9.896731] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[    9.896736] PCI: Bridge: 0000:00:1e.0
[    9.896739]   IO window: d000-dfff
[    9.896745]   MEM window: fea00000-feafffff
[    9.896750]   PREFETCH window: disabled.
[    9.896765] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    9.896788] NET: Registered protocol family 2
[    9.933768] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    9.933844] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    9.933924] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    9.933959] TCP: Hash tables configured (established 16384 bind 8192)
[    9.933962] TCP reno registered
[    9.945807] checking if image is initramfs... it is
[   10.512014] Freeing initrd memory: 6760k freed
[   10.512209] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
[   10.512212] Simple Boot Flag at 0x7a set to 0x1
[   10.512534] audit: initializing netlink socket (disabled)
[   10.512550] audit(1186916619.548:1): initialized
[   10.512671] VFS: Disk quotas dquot_6.5.1
[   10.512690] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   10.512751] io scheduler noop registered
[   10.512755] io scheduler anticipatory registered
[   10.512757] io scheduler deadline registered
[   10.512767] io scheduler cfq registered (default)
[   10.513024] isapnp: Scanning for PnP cards...
[   10.864407] isapnp: No Plug & Play device found
[   10.890541] Real Time Clock Driver v1.12ac
[   10.890591] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   10.890707] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   10.891418] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   10.891591] ACPI: PCI Interrupt 0000:01:01.0[A] -> GSI 22 (level, low) -> IRQ 16
[   10.891885] 0000:01:01.0: ttyS1 at I/O 0xde08 (irq = 16) is a 16450
[   10.892055] 0000:01:01.0: ttyS2 at I/O 0xde10 (irq = 16) is a 8250
[   10.892258] 0000:01:01.0: ttyS3 at I/O 0xde18 (irq = 16) is a 16450
[   10.892334] Couldn't register serial port 0000:01:01.0: -28
[   10.892403] mice: PS/2 mouse device common for all mice
[   10.893018] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   10.893249] input: Macintosh mouse button emulation as /class/input/input0
[   10.893287] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   10.893291] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   10.893533] PNP: PS/2 Controller [PNP0303:KBD] at 0x60,0x64 irq 1
[   10.893536] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   10.897133] serio: i8042 KBD port at 0x60,0x64 irq 1
[   10.897140] serio: i8042 AUX port at 0x60,0x64 irq 12
[   10.897289] EISA: Probing bus 0 at eisa.0
[   10.897327] EISA: Detected 0 cards.
[   10.927362] TCP cubic registered
[   10.927369] NET: Registered protocol family 1
[   10.927392] Using IPI No-Shortcut mode
[   10.927457] ACPI: (supports S0 S1 S3 S4 S5)
[   10.927503]   Magic number: 3:591:74
[   10.927847] Freeing unused kernel memory: 328k freed
[   10.928037] Time: tsc clocksource has been installed.
[   10.941841] input: AT Translated Set 2 keyboard as /class/input/input1
[   12.140064] Capability LSM initialized
[   12.464559] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   21.704333] usbcore: registered new interface driver usbfs
[   21.704362] usbcore: registered new interface driver hub
[   21.704391] usbcore: registered new device driver usb
[   21.705270] USB Universal Host Controller Interface driver v3.0
[   21.705318] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 17
[   21.705331] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   21.705335] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   21.705481] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   21.705508] uhci_hcd 0000:00:1d.0: irq 17, io base 0x0000ff80
[   21.705615] usb usb1: configuration #1 chosen from 1 choice
[   21.705643] hub 1-0:1.0: USB hub found
[   21.705649] hub 1-0:1.0: 2 ports detected
[   21.806104] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 18
[   21.806118] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   21.806123] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   21.806148] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   21.806175] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000ff60
[   21.806260] usb usb2: configuration #1 chosen from 1 choice
[   21.806289] hub 2-0:1.0: USB hub found
[   21.806296] hub 2-0:1.0: 2 ports detected
[   21.864196] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k2-NAPI
[   21.864200] e100: Copyright(c) 1999-2006 Intel Corporation
[   21.909903] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 17
[   21.909917] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   21.909921] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   21.909946] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 3
[   21.909970] uhci_hcd 0000:00:1d.3: irq 17, io base 0x0000ff20
[   21.910063] usb usb3: configuration #1 chosen from 1 choice
[   21.910092] hub 3-0:1.0: USB hub found
[   21.910100] hub 3-0:1.0: 2 ports detected
[   22.014160] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[   22.014176] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   22.014180] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   22.014211] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   22.014246] ehci_hcd 0000:00:1d.7: debug port 1
[   22.014253] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   22.014263] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xffa80800
[   22.018137] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   22.018213] usb usb4: configuration #1 chosen from 1 choice
[   22.018242] hub 4-0:1.0: USB hub found
[   22.018249] hub 4-0:1.0: 8 ports detected
[   22.045567] usb 1-2: new full speed USB device using uhci_hcd and address 2
[   22.121774] ACPI: PCI Interrupt 0000:01:08.0[A] -> GSI 20 (level, low) -> IRQ 20
[   22.140581] e100: eth0: e100_probe: addr 0xfeaff000, irq 20, MAC addr 00:13:20:49:19:81
[   22.149547] SCSI subsystem initialized
[   22.155336] libata version 2.20 loaded.
[   22.156882] ata_piix 0000:00:1f.1: version 2.10ac1
[   22.156904] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 21
[   22.156923] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   22.156972] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[   22.157003] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[   22.157024] scsi0 : ata_piix
[   22.183224] Floppy drive(s): fd0 is 1.44M
[   22.199401] FDC 0 is a post-1991 82077
[   22.317501] ata1.00: ata_hpa_resize 1: sectors = 156250000, hpa_sectors = 156250000
[   22.317506] ata1.00: ATA-7: Maxtor 6Y080L0, YAR41BW0, max UDMA/133
[   22.317509] ata1.00: 156250000 sectors, multi 8: LBA 
[   22.325480] ata1.00: ata_hpa_resize 1: sectors = 156250000, hpa_sectors = 156250000
[   22.325483] ata1.00: configured for UDMA/133
[   22.325496] scsi1 : ata_piix
[   22.824478] ata2.00: ATAPI, max UDMA/33
[   22.824483] ata2.01: ATAPI, max UDMA/33
[   22.972053] usb 4-8: new high speed USB device using ehci_hcd and address 4
[   23.004182] ata2.00: configured for UDMA/33
[   23.104821] usb 4-8: configuration #1 chosen from 1 choice
[   23.167922] ata2.01: configured for UDMA/33
[   23.171707] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6Y080L0   YAR4 PQ: 0 ANSI: 5
[   23.180469] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD-ROM TS-H352C DE02 PQ: 0 ANSI: 5
[   23.181841] scsi 1:0:1:0: CD-ROM            TSSTcorp CD-RW   TS-H292B DE03 PQ: 0 ANSI: 5
[   23.207592] SCSI device sda: 156250000 512-byte hdwr sectors (80000 MB)
[   23.207654] sda: Write Protect is off
[   23.207657] sda: Mode Sense: 00 3a 00 00
[   23.211636] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.215616] SCSI device sda: 156250000 512-byte hdwr sectors (80000 MB)
[   23.215630] sda: Write Protect is off
[   23.215632] sda: Mode Sense: 00 3a 00 00
[   23.215651] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.215655]  sda: sda1 sda2 < sda5 >
[   23.273126] sd 0:0:0:0: Attached scsi disk sda
[   23.277345] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   23.277368] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   23.277390] scsi 1:0:1:0: Attached scsi generic sg2 type 5
[   23.329734] sr0: scsi3-mmc drive: 4x/48x cd/rw xa/form2 cdda tray
[   23.329741] Uniform CD-ROM driver Revision: 3.20
[   23.329795] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   23.333399] sr1: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   23.333448] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   23.343414] usb 1-2: new full speed USB device using uhci_hcd and address 3
[   23.532175] usb 1-2: configuration #1 chosen from 1 choice
[   23.774692] usb 2-2: new low speed USB device using uhci_hcd and address 2
[   23.950241] usb 2-2: configuration #1 chosen from 1 choice
[   23.953295] usbcore: registered new interface driver libusual
[   23.957722] Initializing USB Mass Storage driver...
[   23.957785] scsi2 : SCSI emulation for USB Mass Storage devices
[   23.957830] usb-storage: device found at 4
[   23.957832] usb-storage: waiting for device to settle before scanning
[   23.957847] usbcore: registered new interface driver usb-storage
[   23.957849] USB Mass Storage support registered.
[   23.972024] usbcore: registered new interface driver hiddev
[   23.985307] input: Logitech Optical USB Mouse as /class/input/input2
[   23.985414] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.1-2
[   23.985429] usbcore: registered new interface driver usbhid
[   23.985432] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   24.945796] Attempting manual resume
[   24.945800] swsusp: Resume From Partition 8:5
[   24.945802] PM: Checking swsusp image.
[   25.044571] PM: Resume from disk failed.
[   25.755513] EXT3-fs: INFO: recovery required on readonly filesystem.
[   25.755518] EXT3-fs: write access will be enabled during recovery.
[   28.946223] usb-storage: device scan complete
[   28.950031] scsi 2:0:0:0: Direct-Access              Flash Drive      0.1  PQ: 0 ANSI: 2
[   28.965984] SCSI device sdb: 501759 512-byte hdwr sectors (257 MB)
[   28.969976] sdb: Write Protect is off
[   28.969979] sdb: Mode Sense: 03 00 00 00
[   28.969981] sdb: assuming drive cache: write through
[   28.981955] SCSI device sdb: 501759 512-byte hdwr sectors (257 MB)
[   28.985949] sdb: Write Protect is off
[   28.985952] sdb: Mode Sense: 03 00 00 00
[   28.985953] sdb: assuming drive cache: write through
[   28.985956]  sdb: sdb1
[   28.989148] sd 2:0:0:0: Attached scsi removable disk sdb
[   28.989350] sd 2:0:0:0: Attached scsi generic sg3 type 0
[   29.587967] kjournald starting.  Commit interval 5 seconds
[   29.587982] EXT3-fs: recovery complete.
[   29.597116] EXT3-fs: mounted filesystem with ordered data mode.
[   41.058040] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   42.378240] NET: Registered protocol family 17
[   42.556588] iTCO_vendor_support: vendor-support=0
[   42.670193] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   42.670521] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0860)
[   42.670564] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   42.682265] Linux agpgart interface v0.102 (c) Dave Jones
[   42.684015] agpgart: Detected an Intel 865 Chipset.
[   42.684231] agpgart: Detected 892K stolen memory.
[   42.699467] agpgart: AGP aperture is 128M @ 0xe8000000
[   42.715536] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   42.719122] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   42.747047] intel_rng: Firmware space is locked read-only. If you can't or
[   42.747051] intel_rng: don't want to disable this in firmware setup, and if
[   42.747053] intel_rng: you are certain that your system has a functional
[   42.747054] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   43.237616] input: PC Speaker as /class/input/input3
[   43.329943] parport: PnPBIOS parport detected.
[   43.329996] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   43.395505] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 0 alt 1 proto 2 vid 0x03F0 pid 0x1411
[   43.395522] usbcore: registered new interface driver usblp
[   43.395526] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   43.586389] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 22
[   43.586416] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   43.905292] intel8x0_measure_ac97_clock: measured 55700 usecs
[   43.905296] intel8x0: clocking to 48000
[   44.051047] fuse init (API version 7.8)
[   44.069284] lp0: using parport0 (interrupt-driven).
[   44.093573] Adding 1502036k swap on /dev/disk/by-uuid/72f5ebb1-3a07-4a60-84f4-48bdf8b1a3d7.  Priority:-1 extents:1 across:1502036k
[   44.215816] EXT3 FS on sda1, internal journal
[   44.438313] NET: Registered protocol family 10
[   44.438398] lo: Disabled Privacy Extensions

---

### Post by VerdantLightning on 2007-08-14
Bump

---

