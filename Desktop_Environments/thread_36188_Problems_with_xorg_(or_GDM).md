---
title: "Problems with xorg (or GDM)"
date: 2005-05-22
forum: Desktop Environments
---

### Post by dpaleo on 2005-05-22
Hello, I have installed Ubuntu 4.10, then updated to 5.04. 
After the upgrade, every 2 or 3 boots, in +-30 seconds after Gnome is up, it freezes, the screen goes blank and I return to the login screen again. 
I have installed the 2.6.10.5-k7 Ubuntu kernel.
I have tried to reinstall GDM and xorg, also tried to append noinotify to GRUB options but it does not work. What I get when I do a dmesg is:

NET: Registered protocol family 16
PCI: PCI BIOS revision 2.10 entry at 0xf10e0, last bus=1
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter enabled
ACPI: Using PIC for interrupt routing
ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
PCI: Via IRQ fixup
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 13 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to [email]bjorn.helgaas@hp.com[/email]
** so I can fix the driver.
pnp: 00:02: ioport range 0xe400-0xe47f could not be reserved
pnp: 00:02: ioport range 0xe800-0xe80f has been reserved
pnp: 00:02: ioport range 0xe200-0xe27f has been reserved
Simple Boot Flag at 0x3a set to 0x1
audit: initializing netlink socket (disabled)
audit(1116770873.800:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
Applying VIA southbridge workaround.
PCI: Disabling Via external APIC routing
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
NET: Registered protocol family 2
IP: routing cache hash table of 2048 buckets, 16Kbytes
TCP: Hash tables configured (established 16384 bind 32768)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices: 
PCI0 PCI1 UAR1 UAR2 USB0 USB1 AC97 
ACPI: (supports S0 S1 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4536KiB [1 disk] into ram disk... |/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 164k freed
ACPI: CPU0 (power states: C1[C1] C2[C2])
ACPI: Processor [CPU0] (supports 16 throttling states)
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
VP_IDE: IDE controller at PCI slot 0000:00:07.1
VP_IDE: chipset revision 6
VP_IDE: not 100% native mode: will probe irqs later
VP_IDE: VIA vt82c686b (rev 40) IDE UDMA100 controller on pci0000:00:07.1
    ide0: BM-DMA at 0xb800-0xb807, BIOS settings: hda:DMA, hdb:DMA
    ide1: BM-DMA at 0xb808-0xb80f, BIOS settings: hdc:pio, hdd:pio
Probing IDE interface ide0...
hda: ST340823A, ATA DISK drive
hdb: LG CD-ROM CRD-8522B, ATAPI CD/DVD-ROM drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 78165360 sectors (40020 MB) w/512KiB Cache, CHS=65535/16/63, UDMA(100)
hda: cache flushes not supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
Probing IDE interface ide1...
Probing IDE interface ide1...
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ==|
Freeing memory...  -\|/done (463 pages freed)
Restarting tasks... done
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
Adding 500432k swap on /dev/hda5.  Priority:-1 extents:1
EXT3 FS on hda1, internal journal
input: ImExPS/2 Generic Explorer Mouse on isa0060/serio1
mice: PS/2 mouse device common for all mice
ts: Compaq touchscreen protocol output
hdb: ATAPI 48X CD-ROM drive, 128kB Cache
Uniform CD-ROM driver Revision: 3.20
parport_pc: VIA 686A/8231 detected
parport_pc: probing current configuration
parport_pc: Current parallel port base: 0x378
parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
parport_pc: VIA parallel port: io=0x378, irq=7
lp0: using parport0 (interrupt-driven).
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email]dm-devel@redhat.com[/email]
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
cdrom: open failed.
Real Time Clock Driver v1.12
input: PC Speaker
inserting floppy driver for 2.6.10-5-k7
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected VIA Twister-K/KT133x/KM133 chipset
agpgart: Maximum main memory to use for agp memory: 203M
agpgart: AGP aperture is 16M @ 0xfd000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
PCI: setting IRQ 10 as level-triggered
ACPI: PCI interrupt 0000:00:07.2[D] -> GSI 10 (level, low) -> IRQ 10
uhci_hcd 0000:00:07.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
uhci_hcd 0000:00:07.2: irq 10, io base 0xb400
uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:07.3[D] -> GSI 10 (level, low) -> IRQ 10
uhci_hcd 0000:00:07.3: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
uhci_hcd 0000:00:07.3: irq 10, io base 0xb000
uhci_hcd 0000:00:07.3: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
PCI: setting IRQ 11 as level-triggered
ACPI: PCI interrupt 0000:00:07.5[C] -> GSI 11 (level, low) -> IRQ 11
PCI: Setting latency timer of device 0000:00:07.5 to 64
8139too Fast Ethernet driver 0.9.27
ACPI: PCI interrupt 0000:00:0f.0[A] -> GSI 11 (level, low) -> IRQ 11
eth0: RealTek RTL8139 at 0x9400, 00:c0:ca:11:c9:aa, IRQ 11
eth0:  Identified 8139 chip type 'RTL-8139A'
8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
ACPI: Power Button (FF) [PWRF]
ibm_acpi: ec object not found
ip_tables: (C) 2000-2002 Netfilter core team
ip_conntrack version 2.1 (2047 buckets, 16376 max) - 336 bytes per conntrack
NET: Registered protocol family 10
Disabled Privacy Extensions on device c0315d40(lo)
IPv6 over IPv4 tunneling driver
eth0: no IPv6 routers present
------------[ cut here ]------------
kernel BUG at mm/page_alloc.c:320!
invalid operand: 0000 [#1]
PREEMPT 
Modules linked in: ipv6 ipt_limit iptable_mangle ipt_LOG ipt_MASQUERADE iptable_nat ipt_TOS ipt_REJECT ip_conntrack_irc ip_conntrack_ftp ipt_state ip_conntrack iptable_filter ip_tables video sony_acpi pcc_acpi button battery container ac 8139cp 8139too mii snd_via82xx snd_ac97_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd_page_alloc gameport snd_mpu401_uart snd_rawmidi snd_seq_device snd soundcore i2c_viapro i2c_core uhci_hcd usbcore pci_hotplug via_agp agpgart floppy pcspkr rtc md dm_mod capability commoncap parport_pc lp parport evdev tsdev ide_cd cdrom mousedev psmouse ext3 jbd mbcache ide_generic via82cxxx ide_disk ide_core unix thermal processor fan fbcon font bitblit vesafb cfbcopyarea cfbimgblt cfbfillrect
CPU:    0
EIP:    0060:[<c013a10b>]    Not tainted VLI
EFLAGS: 00013002   (2.6.10-5-k7) 
EIP is at __rmqueue+0x106/0x110
eax: 00000001   ebx: c02d243c   ecx: 00001000   edx: 00005b2c
esi: c10b6580   edi: 00000004   ebp: 00000002   esp: ccc3ddb8
ds: 007b   es: 007b   ss: 0068
Process Xorg (pid: 6037, threadinfo=ccc3c000 task=ce817580)
Stack: c02d23d0 c10b6580 00004b28 c10b6500 0000000c c02d23fc 0000000c 00003092 
       c013a171 c02d23d0 00000000 c02d23d0 00003246 ccc3c000 c02d23ec c013a5c9 
       c02d23d0 00000000 0000000e c02d23fc 00000000 c02d23d0 ccc3c000 00000000 
Call Trace:
 [<c013a171>] rmqueue_bulk+0x5c/0x82
 [<c013a5c9>] buffered_rmqueue+0x1a8/0x1b3
 [<c013a90e>] __alloc_pages+0x33a/0x35b
 [<c01452e0>] do_anonymous_page+0x63/0x17d
 [<c014545d>] do_no_page+0x63/0x33c
 [<c0145926>] handle_mm_fault+0xd6/0x171
 [<c01131b0>] do_page_fault+0x3a4/0x5c8
 [<c0120799>] update_process_times+0x46/0x52
 [<c011093e>] smp_local_timer_interrupt+0x17/0x61
 [<c01078da>] timer_interrupt+0xfc/0x139
 [<c01208ca>] run_timer_softirq+0x10f/0x1ae
 [<c028cdbc>] schedule+0x72/0x534
 [<c0102f22>] work_resched+0x5/0x16
 [<c0112e0c>] do_page_fault+0x0/0x5c8
 [<c0103933>] error_code+0x2b/0x30
Code: 42 04 89 56 18 89 58 04 89 03 83 43 0c 01 8b 43 08 8b 54 24 08 01 fa d3 ea 0f bb 10 3b 6c 24 28 7f ae 8b 44 24 0c e9 2d ff ff ff <0f> 0b 40 01 0f 10 2a c0 eb c2 55 57 31 ff 56 53 83 ec 08 8b 74 
 <6>note: Xorg[6037] exited with preempt_count 2
scheduling while atomic: Xorg/0x00000002/6037
 [<c028d279>] schedule+0x52f/0x534
 [<c0143dfd>] unmap_page_range+0x4b/0x71
 [<c0143fcb>] unmap_vmas+0x1a8/0x1b6
 [<c01484fa>] exit_mmap+0x84/0x15c
 [<c0115ec5>] mmput+0x37/0xa0
 [<c011a6d5>] do_exit+0x175/0x477
 [<c010442a>] do_invalid_op+0x0/0xc3
 [<c01040a1>] do_trap+0x0/0x110
 [<c01044d8>] do_invalid_op+0xae/0xc3
 [<c013a10b>] __rmqueue+0x106/0x110
 [<c022803d>] alloc_skb+0x47/0xe0
 [<c01b5918>] copy_from_user+0x42/0x6e
 [<c022a2f6>] memcpy_fromiovec+0x37/0x5c
 [<c0103933>] error_code+0x2b/0x30
 [<c013a10b>] __rmqueue+0x106/0x110
 [<c013a171>] rmqueue_bulk+0x5c/0x82
 [<c013a5c9>] buffered_rmqueue+0x1a8/0x1b3
 [<c013a90e>] __alloc_pages+0x33a/0x35b
 [<c01452e0>] do_anonymous_page+0x63/0x17d
 [<c014545d>] do_no_page+0x63/0x33c
 [<c0145926>] handle_mm_fault+0xd6/0x171
 [<c01131b0>] do_page_fault+0x3a4/0x5c8
 [<c0120799>] update_process_times+0x46/0x52
 [<c011093e>] smp_local_timer_interrupt+0x17/0x61
 [<c01078da>] timer_interrupt+0xfc/0x139
 [<c01208ca>] run_timer_softirq+0x10f/0x1ae
 [<c028cdbc>] schedule+0x72/0x534
 [<c0102f22>] work_resched+0x5/0x16
 [<c0112e0c>] do_page_fault+0x0/0x5c8
 [<c0103933>] error_code+0x2b/0x30
scheduling while atomic: Xorg/0x00000003/6037
 [<c028d279>] schedule+0x52f/0x534
 [<c0114bf7>] __wake_up_common+0x38/0x57
 [<c028d337>] wait_for_completion+0x76/0xca
 [<c0114bad>] default_wake_function+0x0/0x12
 [<c0114bad>] default_wake_function+0x0/0x12
 [<c012715e>] call_usermodehelper+0xb3/0xb9
 [<c0127046>] __call_usermodehelper+0x0/0x65
 [<c01b20ab>] kobject_hotplug+0x239/0x2dc
 [<c01b178c>] kobject_del+0x1b/0x33
 [<c020c8e5>] class_device_del+0x90/0xb6
 [<c020c91e>] class_device_unregister+0x13/0x23
 [<c01f7583>] vcs_remove_devfs+0x4a/0x67
 [<c01fea26>] con_close+0x76/0x78
 [<c01eeb7f>] release_dev+0x753/0x767
 [<c0226f88>] sk_free+0x6c/0xe2
 [<c015621e>] invalidate_inode_buffers+0x11/0x6b
 [<c016cecb>] clear_inode+0x11/0x112
 [<c01b3346>] rb_erase+0x65/0xfc
 [<c01ef037>] tty_release+0x14/0x1f
 [<c0155019>] __fput+0x173/0x185
 [<c0153778>] filp_close+0x59/0x86
 [<c0119983>] put_files_struct+0x82/0xe7
 [<c011a712>] do_exit+0x1b2/0x477
 [<c010442a>] do_invalid_op+0x0/0xc3
 [<c01040a1>] do_trap+0x0/0x110
 [<c01044d8>] do_invalid_op+0xae/0xc3
 [<c013a10b>] __rmqueue+0x106/0x110
 [<c022803d>] alloc_skb+0x47/0xe0
 [<c01b5918>] copy_from_user+0x42/0x6e
 [<c022a2f6>] memcpy_fromiovec+0x37/0x5c
 [<c0103933>] error_code+0x2b/0x30
 [<c013a10b>] __rmqueue+0x106/0x110
 [<c013a171>] rmqueue_bulk+0x5c/0x82
 [<c013a5c9>] buffered_rmqueue+0x1a8/0x1b3
 [<c013a90e>] __alloc_pages+0x33a/0x35b
 [<c01452e0>] do_anonymous_page+0x63/0x17d
 [<c014545d>] do_no_page+0x63/0x33c
 [<c0145926>] handle_mm_fault+0xd6/0x171
 [<c01131b0>] do_page_fault+0x3a4/0x5c8
 [<c0120799>] update_process_times+0x46/0x52
 [<c011093e>] smp_local_timer_interrupt+0x17/0x61
 [<c01078da>] timer_interrupt+0xfc/0x139
 [<c01208ca>] run_timer_softirq+0x10f/0x1ae
 [<c028cdbc>] schedule+0x72/0x534
 [<c0102f22>] work_resched+0x5/0x16
 [<c0112e0c>] do_page_fault+0x0/0x5c8
 [<c0103933>] error_code+0x2b/0x30
scheduling while atomic: Xorg/0x00000003/6037
 [<c028d279>] schedule+0x52f/0x534
 [<c0114bf7>] __wake_up_common+0x38/0x57
 [<c028d337>] wait_for_completion+0x76/0xca
 [<c0114bad>] default_wake_function+0x0/0x12
 [<c0114bad>] default_wake_function+0x0/0x12
 [<c012715e>] call_usermodehelper+0xb3/0xb9
 [<c0127046>] __call_usermodehelper+0x0/0x65
 [<c01b20ab>] kobject_hotplug+0x239/0x2dc
 [<c01b178c>] kobject_del+0x1b/0x33
 [<c020c8e5>] class_device_del+0x90/0xb6
 [<c020c91e>] class_device_unregister+0x13/0x23
 [<c01fea26>] con_close+0x76/0x78
 [<c01eeb7f>] release_dev+0x753/0x767
 [<c0226f88>] sk_free+0x6c/0xe2
 [<c015621e>] invalidate_inode_buffers+0x11/0x6b
 [<c016cecb>] clear_inode+0x11/0x112
 [<c01b3346>] rb_erase+0x65/0xfc
 [<c01ef037>] tty_release+0x14/0x1f
 [<c0155019>] __fput+0x173/0x185
 [<c0153778>] filp_close+0x59/0x86
 [<c0119983>] put_files_struct+0x82/0xe7
 [<c011a712>] do_exit+0x1b2/0x477
 [<c010442a>] do_invalid_op+0x0/0xc3
 [<c01040a1>] do_trap+0x0/0x110
 [<c01044d8>] do_invalid_op+0xae/0xc3
 [<c013a10b>] __rmqueue+0x106/0x110
 [<c022803d>] alloc_skb+0x47/0xe0
 [<c01b5918>] copy_from_user+0x42/0x6e
 [<c022a2f6>] memcpy_fromiovec+0x37/0x5c
 [<c0103933>] error_code+0x2b/0x30
 [<c013a10b>] __rmqueue+0x106/0x110
 [<c013a171>] rmqueue_bulk+0x5c/0x82
 [<c013a5c9>] buffered_rmqueue+0x1a8/0x1b3
 [<c013a90e>] __alloc_pages+0x33a/0x35b
 [<c01452e0>] do_anonymous_page+0x63/0x17d
 [<c014545d>] do_no_page+0x63/0x33c
 [<c0145926>] handle_mm_fault+0xd6/0x171
 [<c01131b0>] do_page_fault+0x3a4/0x5c8
 [<c0120799>] update_process_times+0x46/0x52
 [<c011093e>] smp_local_timer_interrupt+0x17/0x61
 [<c01078da>] timer_interrupt+0xfc/0x139
 [<c01208ca>] run_timer_softirq+0x10f/0x1ae
 [<c028cdbc>] schedule+0x72/0x534
 [<c0102f22>] work_resched+0x5/0x16
 [<c0112e0c>] do_page_fault+0x0/0x5c8
 [<c0103933>] error_code+0x2b/0x30

Please ask if you need some more data. Every clue is welcome. Thanks in advance and sorry for my English

---

### Post by testingubuntu on 2005-05-22
Try   after gnome tosses its cookies hit ALT CNTL F1 
log in as root 
type 

tail -40  /var/log/messages >/home/yourusername/msgs.txt 

post that output

---

### Post by dpaleo on 2005-05-22
testingubuntu, this is what I get:

May 22 18:52:40 meu kernel: Floppy drive(s): fd0 is 1.44M
May 22 18:52:40 meu kernel: FDC 0 is a post-1991 82077
May 22 18:52:40 meu kernel: Linux agpgart interface v0.100 (c) Dave Jones
May 22 18:52:40 meu kernel: agpgart: Detected VIA Twister-K/KT133x/KM133 chipset
May 22 18:52:40 meu kernel: agpgart: Maximum main memory to use for agp memory: 203M
May 22 18:52:40 meu kernel: agpgart: AGP aperture is 16M @ 0xfd000000
May 22 18:52:40 meu kernel: cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
May 22 18:52:40 meu kernel: pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May 22 18:52:40 meu kernel: usbcore: registered new driver usbfs
May 22 18:52:40 meu kernel: usbcore: registered new driver hub
May 22 18:52:40 meu kernel: USB Universal Host Controller Interface driver v2.2
May 22 18:52:40 meu kernel: ACPI: PCI interrupt 0000:00:07.2[D] -> GSI 10 (level, low) -> IRQ 10
May 22 18:52:40 meu kernel: uhci_hcd 0000:00:07.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
May 22 18:52:40 meu kernel: uhci_hcd 0000:00:07.2: irq 10, io base 0xb400
May 22 18:52:40 meu kernel: uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
May 22 18:52:40 meu kernel: hub 1-0:1.0: USB hub found
May 22 18:52:40 meu kernel: hub 1-0:1.0: 2 ports detected
May 22 18:52:40 meu kernel: ACPI: PCI interrupt 0000:00:07.3[D] -> GSI 10 (level, low) -> IRQ 10
May 22 18:52:40 meu kernel: uhci_hcd 0000:00:07.3: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
May 22 18:52:40 meu kernel: uhci_hcd 0000:00:07.3: irq 10, io base 0xb000
May 22 18:52:40 meu kernel: uhci_hcd 0000:00:07.3: new USB bus registered, assigned bus number 2
May 22 18:52:40 meu kernel: hub 2-0:1.0: USB hub found
May 22 18:52:40 meu kernel: hub 2-0:1.0: 2 ports detected
May 22 18:52:40 meu kernel: ACPI: PCI interrupt 0000:00:07.5[C] -> GSI 11 (level, low) -> IRQ 11
May 22 18:52:40 meu kernel: 8139too Fast Ethernet driver 0.9.27
May 22 18:52:40 meu kernel: ACPI: PCI interrupt 0000:00:0f.0[A] -> GSI 11 (level, low) -> IRQ 11
May 22 18:52:40 meu kernel: eth0: RealTek RTL8139 at 0x9400, 00:c0:ca:11:c9:aa, IRQ 11
May 22 18:52:40 meu kernel: 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
May 22 18:52:40 meu kernel: eth0: link up, 10Mbps, half-duplex, lpa 0x0000
May 22 18:52:42 meu kernel: ACPI: Power Button (FF) [PWRF]
May 22 18:52:45 meu kernel: ip_tables: (C) 2000-2002 Netfilter core team
May 22 18:52:46 meu kernel: ip_conntrack version 2.1 (2047 buckets, 16376 max) - 336 bytes per conntrack
May 22 18:53:00 meu gconfd (xende-7198): comenzando (versión  2.10.0), pid 7198 usuario «xende»
May 22 18:53:00 meu gconfd (xende-7198): Se resolvió la dirección «xml:readonly:/etc/gconf/gconf.xml.mandatory» a una fuente de configuración de sólo lectura en la posición 0
May 22 18:53:00 meu gconfd (xende-7198): Se resolvió la dirección «xml:readwrite:/home/xende/.gconf» a una fuente de configuración escribible en la posición 1
May 22 18:53:00 meu gconfd (xende-7198): Se resolvió la dirección «xml:readonly:/etc/gconf/gconf.xml.defaults» a una fuente de configuración de sólo lectura en la posición 2
May 22 18:53:00 meu kernel: NET: Registered protocol family 10
May 22 18:53:00 meu kernel: Disabled Privacy Extensions on device c0315d40(lo)
May 22 18:53:00 meu kernel: IPv6 over IPv4 tunneling driver
May 22 18:53:14 meu gconfd (xende-7198): Se resolvió la dirección «xml:readwrite:/home/xende/.gconf» a una fuente de configuración escribible en la posición 0

---

### Post by dpaleo on 2005-05-22
BTW, I have tried to update to kernel 2.6.11.1-k7 but it is even worse, because with this one, the gnome panel does not load :( The system freezes and I must reboot.

---

