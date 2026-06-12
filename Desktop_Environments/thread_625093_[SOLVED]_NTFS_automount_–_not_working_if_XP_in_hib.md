---
title: "[SOLVED] NTFS automount – not working if XP in hibernation"
date: 2007-11-27
forum: Desktop Environments
---

### Post by Berduchwal on 2007-11-27
NTFS automount is not working if Windows XP was hibernated. I am ok with that as this is caused by hard drive being left open for access by Windows.

Problem that I am trying to describe can be replicated by following steps:
Ubuntu boots when XP in hibernation (hard drive not mounted)
then Ubuntu restart and XP boot
XP shut down
Ubuntu boot

At this stage NTFS partition is not automounted in spite of the fact that NTFS is not longer locked by Windows. To get this resolved I follow following steps:
remove automount from fstab
reboot Ubutnu
mount NTFS manually
set automount in fstab
reboot Ubuntu

This is very painful process and ideally I would prefer to have this done quicker and in automated way.
Can anyone help me with this?

---

### Post by foolsh on 2007-11-27
Its not an error its a limitation of the ntfs modules in ubuntu. If windows does not shutdown properly ,ie blue screen of death and then you boot linux right after it won't auto mount because the ntfs partition was not unmounted cleanly. when windows hibernates the partition is not unmounted cleanly either.
I don't know of a work around to this sorry

---

### Post by Berduchwal on 2007-11-28
I am ok with that.

What I am looking for is how to then get it automount after windows was shut down properly. Because at the moment it will not automount if previous automount was not successful due to hibernation.

---

### Post by Jouke74 on 2007-11-28
You need to shutdown windows instead of hibernate. Hibernate will leave the files of the drive open, and the state of the disk "dirty". When you mount the hibernated drive into ubuntu it will see that the filesystem is not clean and it wil not mount automatically. If you shutdown windows the write back cache will be written to disk, and the files will be closed. The drive will be clean and mounted. 

Another big issue is that when you write to the NTFS drive while windows hibernates, there is a probability that windows may not find the files in the right condition, leading to problems within windows (blue screens etc.) E.g. I am trying to write a letter in Word, meanwhile you open the same file from another copmputer and start to delete stuff from my letter. Something I don't really like. However, none of the system files in Windows is used in Ubuntu, and therefore you won't notice much. 

To solve, run a chkdsk /f in windows to repair all current errors on the NTFS disk. 
Close windows and don't hibernate, or allow mounting of a drive with errors...

---

### Post by Berduchwal on 2007-11-28
Thanks,
I do understand the problem of automount not working. I am trying to highlight different issue:
- how to get NTFS automount again once it failed automounting because of hibernation

Problem is when after NTFS failed to automount and subsequently Windows was shut down then Ubuntu will not automount NTFS unless steps above are followed.

I am looking for better way of restoring automount then the one described above.

---

### Post by Berduchwal on 2007-12-10
I have tried changing fstab to use UUID but it did not work I have no other ideas can someone help?

---

### Post by Berduchwal on 2008-01-10
I can mount drive using normal command but does not automount with start up. Any help?

---

### Post by mexpolk on 2008-01-10
I have use the force option with the mount command. It is not recommended. I have done it many times without any problems or data loss.

sudo mount -t ntfs-3g /dev/sda9 /mnt/dos -o force

About automount with a clean shut down problem: Have you looked for the error with dmesg?

---

### Post by peitschie on 2008-01-10
Occasionally, I found the ntfs partition doesn't seem to clean itself automatically, and I find I need to run chkdsk from windows.  This can by done from linux by running the command 'ntfsfix' from a terminal (see [http://www.linux-ntfs.org/doku.php?id=ntfsfix](http://www.linux-ntfs.org/doku.php?id=ntfsfix) for information about this).

I suspect the latter problem is what is preventing your disks from appearing again.  
[LIST=1]
[*]Run ntfsfix on the appropriate drives under linux.  Alternatively, boot into windows and make chkdsk run on next restart.  I don't remember the arguments from this, but chkdsk /? from a command window should will give you the arguments list so you can find it yourself :)
[*]Allow chkdsk to run (warning: takes time and a few reboots to work!)
[*]Start linux again and see if the disks automount again
[/LIST]

---

### Post by Berduchwal on 2008-01-11
> **peitschie said:**
> 
[LIST=1]
[*]Run ntfsfix on the appropriate drives under linux
[/LIST]
```
root@berduchwal-laptop:~# ntfsfix /dev/sda5 
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
NTFS partition /dev/sda5 was processed successfully.

```
Still no automount
[QUOTE=mexpolk]
About automount with a clean shut down problem: Have you looked for the error with dmesg?[/QUOTE]

I can not see any errors but I included u result below so you can verify.

```
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 08:02:57 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffc0000 (usable)
[    0.000000]  BIOS-e820: 000000003ffc0000 - 000000003ffcf000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ffcf000 - 0000000040000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 262080) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262080
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262080
[    0.000000] On node 0 totalpages: 262080
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32449 pages, LIFO batch:7
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6980 checksum 0
[    0.000000] ACPI: RSDP 000F6980, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 3FFC0000, 0038 (r1 A M I  OEMRSDT   2000620 MSFT       97)
[    0.000000] ACPI: FACP 3FFC0200, 0084 (r2 A M I  OEMFACP   2000620 MSFT       97)
[    0.000000] ACPI: DSDT 3FFC0430, 8A00 (r1  0AAAA 0AAAA000        0 INTL  2002026)
[    0.000000] ACPI: FACS 3FFCF000, 0040
[    0.000000] ACPI: APIC 3FFC0390, 0054 (r1 A M I  OEMAPIC   2000620 MSFT       97)
[    0.000000] ACPI: MCFG 3FFC03F0, 003C (r1 A M I  OEMMCFG   2000620 MSFT       97)
[    0.000000] ACPI: OEMB 3FFCF040, 0040 (r1 A M I  AMI_OEM   2000620 MSFT       97)
[    0.000000] ACPI: SSDT 3FFC8E30, 02D2 (r1    AMI   CPU1PM        1 INTL  2002026)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:13 APIC version 20
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bed14000)
[    0.000000] Built 1 zonelists.  Total pages: 260033
[    0.000000] Kernel command line: root=UUID=e6ce7d17-7f3b-4668-890a-7f17dcb85872 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1862.088 MHz processor.
[   17.468192] Console: colour VGA+ 80x25
[   17.468483] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   17.468878] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   17.500992] Memory: 1025920k/1048320k available (2015k kernel code, 21760k reserved, 916k data, 364k init, 130816k highmem)
[   17.501001] virtual kernel memory layout:
[   17.501002]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   17.501003]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   17.501004]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   17.501006]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   17.501007]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   17.501008]       .data : 0xc02f7de6 - 0xc03dce84   ( 916 kB)
[   17.501009]       .text : 0xc0100000 - 0xc02f7de6   (2015 kB)
[   17.501012] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   17.501046] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   17.580935] Calibrating delay using timer specific routine.. 3727.24 BogoMIPS (lpj=7454499)
[   17.580958] Security Framework v1.0.0 initialized
[   17.580964] SELinux:  Disabled at boot.
[   17.580977] Mount-cache hash table entries: 512
[   17.581088] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000180 00000000 00000000
[   17.581099] CPU: L1 I cache: 32K, L1 D cache: 32K
[   17.581102] CPU: L2 cache: 2048K
[   17.581104] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002040 00000180 00000000 00000000
[   17.581112] Compat vDSO mapped to ffffe000.
[   17.581123] Checking 'hlt' instruction... OK.
[   17.596994] SMP alternatives: switching to UP code
[   17.597153] Freeing SMP alternatives: 11k freed
[   17.597384] Early unpacking initramfs... done
[   17.958010] ACPI: Core revision 20070126
[   17.958093] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   17.973480] CPU0: Intel(R) Pentium(R) M processor 1.86GHz stepping 08
[   17.973503] Total of 1 processors activated (3727.24 BogoMIPS).
[   17.973656] ENABLING IO-APIC IRQs
[   17.973841] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   18.120083] Brought up 1 CPUs
[   18.120179] Booting paravirtualized kernel on bare hardware
[   18.120246] Time:  6:13:47  Date: 00/11/108
[   18.120266] NET: Registered protocol family 16
[   18.120334] EISA bus registered
[   18.120348] ACPI: bus type pci registered
[   18.120481] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=3
[   18.120483] PCI: Using configuration type 1
[   18.120484] Setting up standard PCI resources
[   18.123866] ACPI: EC: Look up EC in DSDT
[   18.124657] ACPI: EC: GPE=0x1c, ports=0x66, 0x62
[   18.404854] ACPI: Interpreter enabled
[   18.404857] ACPI: (supports S0 S3 S4 S5)
[   18.404875] ACPI: Using IOAPIC for interrupt routing
[   18.412427] ACPI: EC: GPE=0x1c, ports=0x66, 0x62
[   18.412552] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   18.412570] PCI: Probing PCI hardware (bus 00)
[   18.413043] PCI: Enabled ICH6/i801 SMBus device
[   18.413049] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[   18.413053] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   18.413652] PCI: Transparent bridge - 0000:00:1e.0
[   18.413732] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   18.413911] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   18.414089] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[   18.417331] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *11 12)
[   18.417485] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 12) *11
[   18.417638] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 *4 5 6 7 12)
[   18.417789] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 *6 7 12)
[   18.417941] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 12)
[   18.418092] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 12) *0, disabled.
[   18.418244] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 12)
[   18.418402] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 12)
[   18.418553] ACPI: Power Resource [GFAN] (off)
[   18.418558] Linux Plug and Play Support v0.97 (c) Adam Belay
[   18.418569] pnp: PnP ACPI init
[   18.418575] ACPI: bus type pnp registered
[   18.422023] pnp: PnP ACPI: found 14 devices
[   18.422025] ACPI: ACPI bus type pnp unregistered
[   18.422029] PnPBIOS: Disabled by ACPI PNP
[   18.422068] PCI: Using ACPI for IRQ routing
[   18.422070] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   18.429394] NET: Registered protocol family 8
[   18.429396] NET: Registered protocol family 20
[   18.429445] pnp: 00:09: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   18.429448] pnp: 00:09: iomem range 0xfed20000-0xfed8ffff has been reserved
[   18.429451] pnp: 00:09: iomem range 0xffb00000-0xffbfffff could not be reserved
[   18.429455] pnp: 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[   18.429458] pnp: 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[   18.429462] pnp: 00:0b: ioport range 0xa00-0xa0f has been reserved
[   18.429466] pnp: 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[   18.429471] pnp: 00:0d: iomem range 0x0-0x9ffff could not be reserved
[   18.429473] pnp: 00:0d: iomem range 0xc0000-0xcffff could not be reserved
[   18.429476] pnp: 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[   18.429479] pnp: 00:0d: iomem range 0x100000-0x3fffffff could not be reserved
[   18.431538] Time: tsc clocksource has been installed.
[   18.459667] PCI: Bridge: 0000:00:01.0
[   18.459669]   IO window: a000-cfff
[   18.459673]   MEM window: fe900000-fe9fffff
[   18.459676]   PREFETCH window: cff00000-dfefffff
[   18.459685] PCI: Bus 3, cardbus bridge: 0000:02:01.0
[   18.459687]   IO window: 0000d000-0000d0ff
[   18.459691]   IO window: 0000d400-0000d4ff
[   18.459696]   PREFETCH window: 50000000-53ffffff
[   18.459700]   MEM window: 58000000-5bffffff
[   18.459704] PCI: Bridge: 0000:00:1e.0
[   18.459707]   IO window: d000-dfff
[   18.459712]   MEM window: fea00000-feafffff
[   18.459716]   PREFETCH window: 50000000-55ffffff
[   18.459730] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   18.459735] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   18.459746] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   18.459760] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 17 (level, low) -> IRQ 17
[   18.459772] NET: Registered protocol family 2
[   18.499451] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   18.499509] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   18.500754] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   18.501361] TCP: Hash tables configured (established 131072 bind 65536)
[   18.501365] TCP reno registered
[   18.511559] checking if image is initramfs... it is
[   18.962675] Switched to high resolution mode on CPU 0
[   19.220673] Freeing initrd memory: 8891k freed
[   19.221037] audit: initializing netlink socket (disabled)
[   19.221052] audit(1200032027.056:1): initialized
[   19.221123] highmem bounce pool size: 64 pages
[   19.222771] VFS: Disk quotas dquot_6.5.1
[   19.222816] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   19.222903] io scheduler noop registered
[   19.222905] io scheduler anticipatory registered
[   19.222907] io scheduler deadline registered
[   19.222920] io scheduler cfq registered (default)
[   19.223006] Boot video device is 0000:01:00.0
[   19.223083] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   19.223111] assign_interrupt_mode Found MSI capability
[   19.223114] Allocate Port Service[0000:00:01.0:pcie00]
[   19.223228] isapnp: Scanning for PnP cards...
[   19.576133] isapnp: No Plug & Play device found
[   19.597558] Real Time Clock Driver v1.12ac
[   19.597678] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   19.597873] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   19.598808] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   19.598980] input: Macintosh mouse button emulation as /class/input/input0
[   19.599048] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   19.601960] i8042.c: Detected active multiplexing controller, rev 1.1.
[   19.603554] serio: i8042 KBD port at 0x60,0x64 irq 1
[   19.603559] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   19.603562] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   19.603564] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   19.603566] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   19.603721] mice: PS/2 mouse device common for all mice
[   19.603941] EISA: Probing bus 0 at eisa.0
[   19.603971] EISA: Detected 0 cards.
[   19.604065] TCP cubic registered
[   19.604080] NET: Registered protocol family 1
[   19.604103] Using IPI No-Shortcut mode
[   19.604265]   Magic number: 8:595:215
[   19.604562] Freeing unused kernel memory: 364k freed
[   19.733285] input: AT Translated Set 2 keyboard as /class/input/input1
[   20.785934] AppArmor: AppArmor initialized<5>audit(1200032028.556:2):  type=1505 info="AppArmor initialized" pid=1266
[   20.790729] fuse init (API version 7.8)
[   20.794236] Failure registering capabilities with primary security module.
[   20.799005] ACPI: Transitioning device [FN00] to D3
[   20.799008] ACPI: Transitioning device [FN00] to D3
[   20.799010] ACPI: Fan [FN00] (off)
[   20.803656] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   20.803660] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.960000] Marking TSC unstable due to: possible TSC halt in C2.
[    2.964000] Time: acpi_pm clocksource has been installed.
[    2.968000] ACPI: Thermal Zone [THRM] (29 C)
[    3.356000] usbcore: registered new interface driver usbfs
[    3.356000] usbcore: registered new interface driver hub
[    3.356000] usbcore: registered new device driver usb
[    3.356000] USB Universal Host Controller Interface driver v3.0
[    3.356000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 18
[    3.356000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.356000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.356000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.356000] uhci_hcd 0000:00:1d.0: irq 18, io base 0x0000e480
[    3.360000] usb usb1: configuration #1 chosen from 1 choice
[    3.360000] hub 1-0:1.0: USB hub found
[    3.360000] hub 1-0:1.0: 2 ports detected
[    3.428000] SCSI subsystem initialized
[    3.432000] libata version 2.21 loaded.
[    3.464000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[    3.464000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.464000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.464000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.464000] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e800
[    3.464000] usb usb2: configuration #1 chosen from 1 choice
[    3.464000] hub 2-0:1.0: USB hub found
[    3.464000] hub 2-0:1.0: 2 ports detected
[    3.568000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
[    3.568000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.568000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.568000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.568000] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000e880
[    3.568000] usb usb3: configuration #1 chosen from 1 choice
[    3.568000] hub 3-0:1.0: USB hub found
[    3.568000] hub 3-0:1.0: 2 ports detected
[    3.672000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[    3.672000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    3.672000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.672000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.672000] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000ec00
[    3.672000] usb usb4: configuration #1 chosen from 1 choice
[    3.672000] hub 4-0:1.0: USB hub found
[    3.672000] hub 4-0:1.0: 2 ports detected
[    3.776000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 18
[    3.776000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.776000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.776000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.776000] ehci_hcd 0000:00:1d.7: debug port 1
[    3.776000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.776000] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xfebffc00
[    3.780000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.780000] usb usb5: configuration #1 chosen from 1 choice
[    3.780000] hub 5-0:1.0: USB hub found
[    3.780000] hub 5-0:1.0: 8 ports detected
[    3.884000] ata_piix 0000:00:1f.1: version 2.11
[    3.884000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 20
[    3.884000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    3.884000] scsi0 : ata_piix
[    3.884000] scsi1 : ata_piix
[    3.884000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[    3.884000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[    4.084000] Clocksource tsc unstable (delta = -362049244 ns)
[    4.268000] ata1.00: ATA-6: ST980829A, 3.04, max UDMA/100
[    4.268000] ata1.00: 156301488 sectors, multi 16: LBA48 
[    4.268000] ata1.01: ATAPI: TSSTcorpCD/DVDW TS-L632C, AS06, max UDMA/33
[    4.284000] ata1.00: configured for UDMA/100
[    4.296000] usb 5-5: new high speed USB device using ehci_hcd and address 2
[    4.428000] usb 5-5: configuration #1 chosen from 1 choice
[    4.456000] ata1.01: configured for UDMA/33
[    4.620000] scsi 0:0:0:0: Direct-Access     ATA      ST980829A        3.04 PQ: 0 ANSI: 5
[    4.632000] scsi 0:0:1:0: CD-ROM            TSSTcorp CD/DVDW TS-L632C AS06 PQ: 0 ANSI: 5
[    4.632000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 20 (level, low) -> IRQ 21
[    4.632000] skge 1.11 addr 0xfeafc000 irq 21 chip Yukon-Lite rev 9
[    4.632000] skge eth0: addr 00:15:f2:ac:43:8a
[    4.632000] ACPI: PCI Interrupt 0000:02:01.1[B] -> GSI 18 (level, low) -> IRQ 20
[    4.688000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[feafb000-feafb7ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.704000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    4.704000] sd 0:0:0:0: [sda] Write Protect is off
[    4.704000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.704000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.704000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    4.704000] sd 0:0:0:0: [sda] Write Protect is off
[    4.704000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.704000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.704000]  sda: sda1 sda2 sda3 < sda5 sda6 > sda4
[    4.764000] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.768000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.768000] scsi 0:0:1:0: Attached scsi generic sg1 type 5
[    4.856000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.856000] Uniform CD-ROM driver Revision: 3.20
[    4.856000] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    5.024000] usb 4-1: new full speed USB device using uhci_hcd and address 2
[    5.228000] usb 4-1: configuration #1 chosen from 1 choice
[    5.412000] Attempting manual resume
[    5.412000] swsusp: Resume From Partition 8:6
[    5.412000] PM: Checking swsusp image.
[    5.412000] PM: Resume from disk failed.
[    5.436000] kjournald starting.  Commit interval 5 seconds
[    5.436000] EXT3-fs: mounted filesystem with ordered data mode.
[    5.964000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e01800034c34cd]
[   17.184000] Linux agpgart interface v0.102 (c) Dave Jones
[   17.208000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   17.340000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.988000] intel_rng: FWH not detected
[   18.160000] Yenta: CardBus bridge found at 0000:02:01.0 [1043:1177]
[   18.180000] sdhci: Secure Digital Host Controller Interface driver
[   18.180000] sdhci: Copyright(c) Pierre Ossman
[   18.200000] iTCO_vendor_support: vendor-support=0
[   18.200000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   18.204000] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x0860)
[   18.204000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   18.288000] Yenta: ISA IRQ mask 0x04b8, PCI irq 17
[   18.288000] Socket status: 30000006
[   18.288000] Yenta: Raising subordinate bus# of parent bus (#02) from #03 to #06
[   18.288000] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xdfff
[   18.288000] cs: IO port probe 0xd000-0xdfff: clean.
[   18.288000] pcmcia: parent PCI bridge Memory window: 0xfea00000 - 0xfeafffff
[   18.288000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x55ffffff
[   18.288000] sdhci: SDHCI controller found at 0000:02:01.2 [1180:0822] (rev 17)
[   18.288000] ACPI: PCI Interrupt 0000:02:01.2[C] -> GSI 19 (level, low) -> IRQ 19
[   18.288000] mmc0: SDHCI at 0xfeafb800 irq 19 DMA
[   18.792000] Bluetooth: Core ver 2.11
[   18.792000] NET: Registered protocol family 31
[   18.792000] Bluetooth: HCI device and connection manager initialized
[   18.792000] Bluetooth: HCI socket layer initialized
[   18.804000] Bluetooth: HCI USB driver ver 2.9
[   18.808000] usbcore: registered new interface driver hci_usb
[   19.160000] input: PC Speaker as /class/input/input2
[   19.180000] ieee80211_crypt: registered algorithm 'NULL'
[   19.180000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   19.180000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   19.200000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   19.200000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   19.200000] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 22 (level, low) -> IRQ 22
[   19.200000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   19.204000] Synaptics Touchpad, model: 1, fw: 6.1, id: 0xa3a0b3, caps: 0xa04713/0x10008
[   19.240000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   19.268000] parport_pc 00:08: reported by Plug and Play ACPI
[   19.268000] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   19.456000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   19.576000] irda_init()
[   19.576000] NET: Registered protocol family 23
[   19.888000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   19.888000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   19.952000] cs: IO port probe 0x100-0x3af: clean.
[   19.952000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   19.952000] cs: IO port probe 0x820-0x8ff: clean.
[   19.952000] cs: IO port probe 0xc00-0xcf7: clean.
[   19.956000] cs: IO port probe 0xa00-0xaff: clean.
[   20.000000] usbcore: registered new interface driver snd-usb-audio
[   21.108000] lp0: using parport0 (interrupt-driven).
[   21.164000] Adding 337324k swap on /dev/sda6.  Priority:-1 extents:1 across:337324k
[   21.632000] EXT3 FS on sda4, internal journal
[   22.512000] loop: module loaded
[   23.384000] No dock devices found.
[   23.404000] Asus Laptop ACPI Extras version 0.30
[   23.404000]   unsupported model A6VA, trying default values
[   23.404000]   send /proc/acpi/dsdt to the developers
[   23.456000] input: Power Button (FF) as /class/input/input4
[   23.460000] ACPI: Power Button (FF) [PWRF]
[   23.496000] input: Lid Switch as /class/input/input5
[   23.500000] ACPI: Lid Switch [LID]
[   23.540000] input: Sleep Button (CM) as /class/input/input6
[   23.540000] ACPI: Sleep Button (CM) [SLPB]
[   23.620000] ACPI: Battery Slot [BAT0] (battery present)
[   23.632000] ACPI: AC Adapter [AC0] (on-line)
[   23.644000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   23.644000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   25.448000] skge eth0: enabling interface
[   27.700000] [drm] Initialized drm 1.1.0 20060810
[   27.720000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   27.724000] [drm] Initialized radeon 1.27.0 20060524 on minor 0
[   27.748000] ppdev: user-space parallel port driver
[   28.120000] audit(1200032054.971:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4891 profile="/usr/sbin/cupsd"
[   28.948000] NET: Registered protocol family 10
[   28.948000] lo: Disabled Privacy Extensions
[   28.948000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.836000] apm: BIOS not found.
[   31.776000] [drm] Setting GART location based on new memory map
[   31.776000] [drm] Loading R300 Microcode
[   31.776000] [drm] writeback test succeeded in 1 usecs
[   39.160000] eth1: no IPv6 routers present
[   48.528000] Failure registering capabilities with primary security module.
[   48.716000] Bluetooth: L2CAP ver 2.8
[   48.716000] Bluetooth: L2CAP socket layer initialized
[   48.892000] Bluetooth: RFCOMM socket layer initialized
[   48.892000] Bluetooth: RFCOMM TTY layer initialized
[   48.892000] Bluetooth: RFCOMM ver 1.8
[   49.900000] PPP generic driver version 2.4.2
[   50.036000] NET: Registered protocol family 17
[   87.752000] ieee80211_crypt: registered algorithm 'WEP'
[  109.584000] eth1: no IPv6 routers present
```

Normal mount works fine only automount does not.

---

### Post by peitschie on 2008-01-11
> **Berduchwal said:**
> ```
root@berduchwal-laptop:~# ntfsfix /dev/sda5 
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
NTFS partition /dev/sda5 was processed successfully.

```
Still no automount


It wasn't made explicit in your post... did you reboot into windows after doing ntfsfix?  Just clarifying... :)

---

### Post by Berduchwal on 2008-01-11
yes with no result.
-----------
created mount point to which ntfs was being mounted.
Strangely mount point was not needed via automount and needed without it!

---

### Post by peitschie on 2008-01-11
Ahh... ok.

Well.... thats the end of my shallow bag of tricks I'm sorry :(... I'll keep an eye out but I'm not sure what else to try.  Does mounting the drive manually give you any error messages?  Perhaps you can post the output of the following commands:
```
ls -R /dev/disk
```
```
sudo fdisk -l
```
```
cat /etc/fstab
```

This will give us all the partition information, disk information and current mount options.... Its a stab in the dark, but maybe we can find something here to indicate why your mounting isn't working...

---

