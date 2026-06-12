---
title: "Hoary hangs, no apparent reason, SuSE does not"
date: 2005-05-10
forum: Desktop Environments
---

### Post by jd_za on 2005-05-10
I am running Kmail, Valknut (Direct Connect client), konsole, VMWare, Xmms and Openoffice.org on both systems.  Hoary hangs at least once a day, I cannot switch to a console, nothing.

```

May  7 23:28:36 localhost kernel: ACPI: Power Button (FF) [PWRF]
May  7 23:28:37 localhost kernel: agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
May  7 23:28:37 localhost kernel: agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
May  7 23:28:37 localhost kernel: agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
May  7 23:28:37 localhost kernel: apm: BIOS not found.
May  7 23:28:37 localhost kernel: agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
May  7 23:28:37 localhost kernel: agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
May  7 23:28:37 localhost kernel: agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
May  7 23:28:40 localhost kernel: bridge-eth0: already up
May  7 23:28:51 localhost gconfd (jgb-7786): starting (version 2.10.0), pid 7786 user 'jgb'
May  7 23:28:51 localhost gconfd (jgb-7786): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May  7 23:28:51 localhost gconfd (jgb-7786): Resolved address "xml:readwrite:/home/jgb/.gconf" to a writable configuration source at position 1
May  7 23:28:51 localhost gconfd (jgb-7786): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May  7 23:28:55 localhost gconfd (jgb-7786): Resolved address "xml:readwrite:/home/jgb/.gconf" to a writable configuration source at position 0
May  7 23:28:55 localhost kernel: UDF-fs: No VRS found
May  7 23:48:35 localhost -- MARK --
May  8 00:06:42 localhost syslogd 1.4.1#16ubuntu6: restart.
May  8 00:06:42 localhost kernel: Inspecting /boot/System.map-2.6.10-5-686
May  8 00:06:42 localhost kernel: Loaded 26802 symbols from /boot/System.map-2.6.10-5-686.
May  8 00:06:42 localhost kernel: Symbols match kernel version 2.6.10.
May  8 00:06:42 localhost kernel: No module symbols loaded - kernel modules not enabled. 
May  8 00:06:42 localhost kernel: q 9 high level)
May  8 00:06:42 localhost kernel: Enabling APIC mode:  Flat.  Using 1 I/O APICs
May  8 00:06:42 localhost kernel: Using ACPI (MADT) for SMP configuration information
May  8 00:06:42 localhost kernel: Built 1 zonelists
May  8 00:06:42 localhost kernel: Kernel command line: root=/dev/sda6 ro quiet splash
May  8 00:06:42 localhost kernel: Initializing CPU#0
May  8 00:06:42 localhost kernel: PID hash table entries: 4096 (order: 12, 65536 bytes)
May  8 00:06:42 localhost kernel: Detected 2606.484 MHz processor.
May  8 00:06:42 localhost kernel: Using pmtmr for high-res timesource
May  8 00:06:42 localhost kernel: Console: colour VGA+ 80x25
May  8 00:06:42 localhost kernel: Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
May  8 00:06:42 localhost kernel: Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
May  8 00:06:42 localhost kernel: Memory: 1031404k/1048512k available (1587k kernel code, 16328k reserved, 714k data, 164k init, 131008k highmem)
May  8 00:06:42 localhost kernel: Checking if this processor honours the WP bit even in supervisor mode... Ok.
May  8 00:06:42 localhost kernel: Security Framework v1.0.0 initialized
May  8 00:06:42 localhost kernel: SELinux:  Disabled at boot.
May  8 00:06:42 localhost kernel: Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
May  8 00:06:42 localhost kernel: CPU: Trace cache: 12K uops, L1 D cache: 8K
May  8 00:06:42 localhost kernel: CPU: L2 cache: 512K
May  8 00:06:42 localhost kernel: Intel machine check architecture supported.
May  8 00:06:42 localhost kernel: Intel machine check reporting enabled on CPU#0.
May  8 00:06:42 localhost kernel: CPU0: Intel P4/Xeon Extended MCE MSRs (12) available
May  8 00:06:42 localhost kernel: CPU0: Thermal monitoring enabled
May  8 00:06:42 localhost kernel: CPU: Intel(R) Pentium(R) 4 CPU 2.60GHz stepping 09
May  8 00:06:42 localhost kernel: Enabling fast FPU save and restore... done.
May  8 00:06:42 localhost kernel: Enabling unmasked SIMD FPU exception support... done.
May  8 00:06:42 localhost kernel: Checking 'hlt' instruction... OK.
May  8 00:06:42 localhost kernel: ACPI: Looking for DSDT in initrd... not found!
May  8 00:06:42 localhost kernel: ENABLING IO-APIC IRQs
May  8 00:06:42 localhost kernel: ..TIMER: vector=0x31 pin1=2 pin2=-1
May  8 00:06:42 localhost kernel: checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
May  8 00:06:42 localhost kernel: Freeing initrd memory: 4544k freed
May  8 00:06:42 localhost kernel: NET: Registered protocol family 16
May  8 00:06:42 localhost kernel: PCI: PCI BIOS revision 2.10 entry at 0xfbca0, last bus=3
May  8 00:06:42 localhost kernel: PCI: Using configuration type 1
May  8 00:06:42 localhost kernel: mtrr: v2.0 (20020519)
May  8 00:06:42 localhost kernel: ACPI: Subsystem revision 20050211
May  8 00:06:42 localhost kernel: ACPI: Interpreter enabled
May  8 00:06:42 localhost kernel: ACPI: Using IOAPIC for interrupt routing
May  8 00:06:42 localhost kernel: ACPI: PCI Root Bridge [PCI0] (00:00)
May  8 00:06:42 localhost kernel: PCI: Probing PCI hardware (bus 00)
May  8 00:06:42 localhost kernel: PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.2
May  8 00:06:42 localhost kernel: PCI: Transparent bridge - 0000:00:1e.0
May  8 00:06:42 localhost kernel: ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 11 *12 14 15)
May  8 00:06:42 localhost kernel: ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 9 10 11 12 14 15)
May  8 00:06:42 localhost kernel: ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12 14 15)
May  8 00:06:42 localhost kernel: ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 *10 11 12 14 15)
May  8 00:06:42 localhost kernel: ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
May  8 00:06:42 localhost kernel: ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
May  8 00:06:42 localhost kernel: ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
May  8 00:06:42 localhost kernel: ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 *7 9 10 11 12 14 15)
May  8 00:06:42 localhost kernel: ACPI: Power Resource [PFAN] (off)
May  8 00:06:42 localhost kernel: Linux Plug and Play Support v0.97 (c) Adam Belay
May  8 00:06:42 localhost kernel: pnp: PnP ACPI init
May  8 00:06:42 localhost kernel: pnp: PnP ACPI: found 10 devices
May  8 00:06:42 localhost kernel: PnPBIOS: Disabled by ACPI PNP
May  8 00:06:42 localhost kernel: PCI: Using ACPI for IRQ routing
May  8 00:06:42 localhost kernel: ** PCI interrupts are no longer routed automatically.  If this
May  8 00:06:42 localhost kernel: ** causes a device to stop working, it is probably because the
May  8 00:06:42 localhost kernel: ** driver failed to call pci_enable_device().  As a temporary
May  8 00:06:42 localhost kernel: ** workaround, the "pci=routeirq" argument restores the old
May  8 00:06:42 localhost kernel: ** behavior.  If this argument makes the device work again,
May  8 00:06:42 localhost kernel: ** please email the output of "lspci" to [email]bjorn.helgaas@hp.com[/email]
May  8 00:06:42 localhost kernel: ** so I can fix the driver.
May  8 00:06:42 localhost kernel: pnp: 00:07: ioport range 0x400-0x4bf could not be reserved
May  8 00:06:42 localhost kernel: audit: initializing netlink socket (disabled)
May  8 00:06:42 localhost kernel: highmem bounce pool size: 64 pages
May  8 00:06:42 localhost kernel: VFS: Disk quotas dquot_6.5.1
May  8 00:06:42 localhost kernel: Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
May  8 00:06:42 localhost kernel: devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
May  8 00:06:42 localhost kernel: devfs: boot_options: 0x0
May  8 00:06:42 localhost kernel: Initializing Cryptographic API
May  8 00:06:42 localhost kernel: isapnp: Scanning for PnP cards...
May  8 00:06:42 localhost kernel: isapnp: No Plug & Play device found
May  8 00:06:42 localhost kernel: serio: i8042 AUX port at 0x60,0x64 irq 12
May  8 00:06:42 localhost kernel: serio: i8042 KBD port at 0x60,0x64 irq 1
May  8 00:06:42 localhost kernel: Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
May  8 00:06:42 localhost kernel: io scheduler noop registered
May  8 00:06:42 localhost kernel: io scheduler anticipatory registered
May  8 00:06:42 localhost kernel: io scheduler deadline registered
May  8 00:06:42 localhost kernel: io scheduler cfq registered
May  8 00:06:42 localhost kernel: RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
May  8 00:06:42 localhost kernel: input: AT Translated Set 2 keyboard on isa0060/serio0
May  8 00:06:42 localhost kernel: NET: Registered protocol family 2
May  8 00:06:42 localhost kernel: IP: routing cache hash table of 8192 buckets, 64Kbytes
May  8 00:06:42 localhost kernel: TCP: Hash tables configured (established 262144 bind 65536)
May  8 00:06:42 localhost kernel: NET: Registered protocol family 8
May  8 00:06:42 localhost kernel: NET: Registered protocol family 20
May  8 00:06:42 localhost kernel: Restarting tasks...<6> Strange, kswapd0 not stopped
May  8 00:06:42 localhost kernel:  Strange, kseriod not stopped
May  8 00:06:42 localhost kernel:  done
May  8 00:06:42 localhost kernel: ACPI wakeup devices: 
May  8 00:06:42 localhost kernel: PCI0 CSAD HUB0 USB0 USB1 USB2 USB3 USBE MODM 
May  8 00:06:42 localhost kernel: ACPI: (supports S0 S1 S4 S5)
May  8 00:06:42 localhost kernel: RAMDISK: cramfs filesystem found at block 0
May  8 00:06:42 localhost kernel: RAMDISK: Loading 4544KiB [1 disk] into ram disk... |^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^Hdone.
May  8 00:06:42 localhost kernel: VFS: Mounted root (cramfs filesystem) readonly.
May  8 00:06:42 localhost kernel: Freeing unused kernel memory: 164k freed
May  8 00:06:42 localhost kernel: ACPI: Fan [FAN] (off)
May  8 00:06:42 localhost kernel: ACPI: Thermal Zone [THRM] (45 C)
May  8 00:06:42 localhost kernel: NET: Registered protocol family 1
May  8 00:06:42 localhost kernel: SCSI subsystem initialized
May  8 00:06:42 localhost kernel: ata_piix: combined mode detected
May  8 00:06:42 localhost kernel: ACPI: PCI interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 18
May  8 00:06:42 localhost kernel: ata1: PATA max UDMA/100 cmd 0x1F0 ctl 0x3F6 bmdma 0xF000 irq 14
May  8 00:06:42 localhost kernel: ata1: dev 1 ATAPI, max UDMA/44
May  8 00:06:42 localhost kernel: ata1: dev 1 configured for UDMA/44
May  8 00:06:42 localhost kernel: scsi0 : ata_piix
May  8 00:06:42 localhost kernel: elevator: using anticipatory as default io scheduler
May  8 00:06:42 localhost kernel:   Vendor: LITE-ON   Model: COMBO LTC-48161H  Rev: KH0R
May  8 00:06:42 localhost kernel:   Type:   CD-ROM                             ANSI SCSI revision: 05
May  8 00:06:42 localhost kernel: ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xF008 irq 15
May  8 00:06:42 localhost kernel: ata2: dev 0 ATA, max UDMA/133, 240121728 sectors:
May  8 00:06:42 localhost kernel: ata2: dev 1 ATA, max UDMA/133, 390721968 sectors: lba48
May  8 00:06:42 localhost kernel: ata2: dev 0 configured for UDMA/133
May  8 00:06:42 localhost kernel: ata2: dev 1 configured for UDMA/133
May  8 00:06:42 localhost kernel: scsi1 : ata_piix
May  8 00:06:42 localhost kernel:   Vendor: ATA       Model: Maxtor 6Y120M0    Rev: YAR5
May  8 00:06:42 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 05
May  8 00:06:42 localhost kernel:   Vendor: ATA       Model: ST3200822AS       Rev: 3.01
May  8 00:06:42 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 05
May  8 00:06:42 localhost kernel: ACPI: PCI interrupt 0000:03:03.0[A] -> GSI 19 (level, low) -> IRQ 19
May  8 00:06:42 localhost kernel: ata3: SATA max UDMA/100 cmd 0xF884A080 ctl 0xF884A08A bmdma 0xF884A000 irq 19
May  8 00:06:42 localhost kernel: ata4: SATA max UDMA/100 cmd 0xF884A0C0 ctl 0xF884A0CA bmdma 0xF884A008 irq 19
May  8 00:06:42 localhost kernel: ata5: SATA max UDMA/100 cmd 0xF884A280 ctl 0xF884A28A bmdma 0xF884A200 irq 19
May  8 00:06:42 localhost kernel: ata6: SATA max UDMA/100 cmd 0xF884A2C0 ctl 0xF884A2CA bmdma 0xF884A208 irq 19
May  8 00:06:42 localhost kernel: ata3: no device found (phy stat 00000000)
May  8 00:06:42 localhost kernel: scsi2 : sata_sil
May  8 00:06:42 localhost kernel: ata4: no device found (phy stat 00000000)
May  8 00:06:42 localhost kernel: scsi3 : sata_sil
May  8 00:06:42 localhost kernel: ata5: no device found (phy stat 00000000)
May  8 00:06:42 localhost kernel: scsi4 : sata_sil
May  8 00:06:42 localhost kernel: ata6: no device found (phy stat 00000000)
May  8 00:06:42 localhost kernel: scsi5 : sata_sil
May  8 00:06:42 localhost kernel: Attached scsi generic sg0 at scsi0, channel 0, id 1, lun 0,  type 5
May  8 00:06:42 localhost kernel: Attached scsi generic sg1 at scsi1, channel 0, id 0, lun 0,  type 0
May  8 00:06:42 localhost kernel: Attached scsi generic sg2 at scsi1, channel 0, id 1, lun 0,  type 0
May  8 00:06:42 localhost kernel: sr0: scsi3-mmc drive: 0x/40x writer cd/rw xa/form2 cdda tray
May  8 00:06:42 localhost kernel: Uniform CD-ROM driver Revision: 3.20
May  8 00:06:42 localhost kernel: SCSI device sda: 240121728 512-byte hdwr sectors (122942 MB)
May  8 00:06:42 localhost kernel: SCSI device sda: drive cache: write back
May  8 00:06:42 localhost kernel: SCSI device sda: 240121728 512-byte hdwr sectors (122942 MB)
May  8 00:06:42 localhost kernel: SCSI device sda: drive cache: write back
May  8 00:06:42 localhost kernel:  /dev/scsi/host1/bus0/target0/lun0: p1 p2 p3 < p5 p6 p7 p8 >
May  8 00:06:42 localhost kernel: Attached scsi disk sda at scsi1, channel 0, id 0, lun 0
May  8 00:06:42 localhost kernel: SCSI device sdb: 390721968 512-byte hdwr sectors (200050 MB)
May  8 00:06:42 localhost kernel: SCSI device sdb: drive cache: write back
May  8 00:06:42 localhost kernel: SCSI device sdb: 390721968 512-byte hdwr sectors (200050 MB)
May  8 00:06:42 localhost kernel: SCSI device sdb: drive cache: write back
May  8 00:06:42 localhost kernel:  /dev/scsi/host1/bus0/target1/lun0: p1
May  8 00:06:42 localhost kernel: Attached scsi disk sdb at scsi1, channel 0, id 1, lun 0
May  8 00:06:42 localhost kernel: Stopping tasks: ==|
May  8 00:06:42 localhost kernel: Freeing memory...  ^H-^H\^H|^H/^H-^Hdone (425 pages freed)
May  8 00:06:42 localhost kernel: Restarting tasks... done
May  8 00:06:42 localhost kernel: VFS: Can't find an ext2 filesystem on dev sda6.
May  8 00:06:42 localhost kernel: ReiserFS: sda6: found reiserfs format "3.6" with standard journal
May  8 00:06:42 localhost kernel: ReiserFS: sda6: using ordered data mode
May  8 00:06:42 localhost kernel: ReiserFS: sda6: journal params: device sda6, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
May  8 00:06:42 localhost kernel: ReiserFS: sda6: checking transaction log (sda6)
May  8 00:06:42 localhost kernel: ReiserFS: sda6: replayed 299 transactions in 8 seconds
May  8 00:06:42 localhost kernel: ReiserFS: sda6: Using r5 hash to sort names
May  8 00:06:42 localhost kernel: Adding 2104504k swap on /dev/sda2.  Priority:-1 extents:1
May  8 00:06:42 localhost kernel: ReiserFS: sda6: Removing [55637 55670 0x0 SD]..done
May  8 00:06:42 localhost kernel: ReiserFS: sda6: Removing [291 55637 0x0 SD]..done
May  8 00:06:42 localhost kernel: ReiserFS: sda6: There were 2 uncompleted unlinks/truncates. Completed
May  8 00:06:42 localhost kernel: lp: driver loaded but no devices found
May  8 00:06:42 localhost kernel: mice: PS/2 mouse device common for all mice
May  8 00:06:42 localhost kernel: sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
May  8 00:06:42 localhost kernel: Linux agpgart interface v0.100 (c) Dave Jones
May  8 00:06:42 localhost kernel: nvidia: module license 'NVIDIA' taints kernel.
May  8 00:06:42 localhost kernel: ACPI: PCI interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
May  8 00:06:42 localhost kernel: NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7174  Tue Mar 22 06:44:39 PST 2005
May  8 00:06:42 localhost kernel: Capability LSM initialized
May  8 00:06:42 localhost kernel: device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email]dm-devel@redhat.com[/email]
May  8 00:06:42 localhost kernel: md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
May  8 00:06:42 localhost kernel: cdrom: open failed.
May  8 00:06:42 localhost kernel: ReiserFS: sdb1: found reiserfs format "3.6" with standard journal
May  8 00:06:42 localhost kernel: ReiserFS: sdb1: using ordered data mode
May  8 00:06:42 localhost kernel: ReiserFS: sdb1: journal params: device sdb1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
May  8 00:06:42 localhost kernel: ReiserFS: sdb1: checking transaction log (sdb1)
May  8 00:06:42 localhost kernel: ReiserFS: sdb1: replayed 14 transactions in 25 seconds
May  8 00:06:42 localhost kernel: ReiserFS: sdb1: Using r5 hash to sort names
May  8 00:06:42 localhost kernel: ReiserFS: sdb1: Removing [16 364 0x0 SD]..done
May  8 00:06:42 localhost kernel: ReiserFS: sdb1: There were 1 uncompleted unlinks/truncates. Completed
May  8 00:06:42 localhost kernel: ReiserFS: sda8: found reiserfs format "3.6" with standard journal
May  8 00:06:42 localhost kernel: ReiserFS: sda8: using ordered data mode
May  8 00:06:42 localhost kernel: ReiserFS: sda8: journal params: device sda8, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
May  8 00:06:42 localhost kernel: ReiserFS: sda8: checking transaction log (sda8)
May  8 00:06:42 localhost kernel: ReiserFS: sda8: replayed 18 transactions in 0 seconds
May  8 00:06:42 localhost kernel: ReiserFS: sda8: Using r5 hash to sort names
May  8 00:06:42 localhost kernel: Real Time Clock Driver v1.12
May  8 00:06:42 localhost kernel: input: PC Speaker
May  8 00:06:42 localhost kernel: inserting floppy driver for 2.6.10-5-686
May  8 00:06:42 localhost kernel: Floppy drive(s): fd0 is 1.44M
May  8 00:06:42 localhost kernel: FDC 0 is a post-1991 82077
May  8 00:06:42 localhost kernel: agpgart: Detected an Intel i875 Chipset.
May  8 00:06:42 localhost kernel: agpgart: Maximum main memory to use for agp memory: 941M
May  8 00:06:42 localhost kernel: agpgart: AGP aperture is 32M @ 0xf4000000
May  8 00:06:42 localhost kernel: cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
May  8 00:06:42 localhost kernel: pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May  8 00:06:42 localhost kernel: shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
May  8 00:06:42 localhost kernel: usbcore: registered new driver usbfs
May  8 00:06:42 localhost kernel: usbcore: registered new driver hub
May  8 00:06:42 localhost kernel: USB Universal Host Controller Interface driver v2.2
May  8 00:06:42 localhost kernel: ACPI: PCI interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
May  8 00:06:42 localhost kernel: uhci_hcd 0000:00:1d.0: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #1
May  8 00:06:42 localhost kernel: uhci_hcd 0000:00:1d.0: irq 16, io base 0xbc00
May  8 00:06:42 localhost kernel: uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
May  8 00:06:42 localhost kernel: hub 1-0:1.0: USB hub found
May  8 00:06:42 localhost kernel: hub 1-0:1.0: 2 ports detected
May  8 00:06:42 localhost kernel: ACPI: PCI interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
May  8 00:06:42 localhost kernel: uhci_hcd 0000:00:1d.1: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #2
May  8 00:06:42 localhost kernel: uhci_hcd 0000:00:1d.1: irq 19, io base 0xb000
May  8 00:06:42 localhost kernel: uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
May  8 00:06:42 localhost kernel: hub 2-0:1.0: USB hub found
May  8 00:06:42 localhost kernel: hub 2-0:1.0: 2 ports detected
May  8 00:06:42 localhost kernel: ACPI: PCI interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
May  8 00:06:42 localhost kernel: uhci_hcd 0000:00:1d.2: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #3
May  8 00:06:42 localhost kernel: uhci_hcd 0000:00:1d.2: irq 18, io base 0xb400
May  8 00:06:42 localhost kernel: uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
May  8 00:06:42 localhost kernel: hub 3-0:1.0: USB hub found
May  8 00:06:42 localhost kernel: hub 3-0:1.0: 2 ports detected
May  8 00:06:42 localhost kernel: ACPI: PCI interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
May  8 00:06:42 localhost kernel: uhci_hcd 0000:00:1d.3: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #4
May  8 00:06:42 localhost kernel: uhci_hcd 0000:00:1d.3: irq 16, io base 0xb800
May  8 00:06:42 localhost kernel: uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
May  8 00:06:42 localhost kernel: hub 4-0:1.0: USB hub found
May  8 00:06:42 localhost kernel: hub 4-0:1.0: 2 ports detected
May  8 00:06:42 localhost kernel: usb 2-1: new low speed USB device using uhci_hcd and address 2
May  8 00:06:42 localhost kernel: ACPI: PCI interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 23
May  8 00:06:42 localhost kernel: ehci_hcd 0000:00:1d.7: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
May  8 00:06:42 localhost kernel: ehci_hcd 0000:00:1d.7: irq 23, pci mem 0xfa100000
May  8 00:06:42 localhost kernel: ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
May  8 00:06:42 localhost kernel: ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
May  8 00:06:42 localhost kernel: hub 5-0:1.0: USB hub found
May  8 00:06:42 localhost kernel: hub 5-0:1.0: 8 ports detected
May  8 00:06:42 localhost kernel: usb 2-1: USB disconnect, address 2
May  8 00:06:42 localhost kernel: usbcore: registered new driver hiddev
May  8 00:06:42 localhost kernel: usbcore: registered new driver usbhid
May  8 00:06:42 localhost kernel: drivers/usb/input/hid-core.c: v2.0:USB HID core driver
May  8 00:06:42 localhost kernel: hw_random hardware driver 1.0.0 loaded
May  8 00:06:42 localhost kernel: usb 2-1: new low speed USB device using uhci_hcd and address 3
May  8 00:06:42 localhost kernel: input: USB HID v1.10 Mouse [B16_b_02 USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-1
May  8 00:06:42 localhost kernel: ts: Compaq touchscreen protocol output
May  8 00:06:42 localhost kernel: ACPI: PCI interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 17
May  8 00:06:42 localhost kernel: intel8x0_measure_ac97_clock: measured 49493 usecs
May  8 00:06:42 localhost kernel: intel8x0: clocking to 48000
May  8 00:06:42 localhost kernel: Intel(R) PRO/1000 Network Driver - version 5.5.4-k2
May  8 00:06:42 localhost kernel: Copyright (c) 1999-2004 Intel Corporation.
May  8 00:06:42 localhost kernel: ACPI: PCI interrupt 0000:02:01.0[A] -> GSI 18 (level, low) -> IRQ 18
May  8 00:06:42 localhost kernel: e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
May  8 00:06:42 localhost kernel: ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
May  8 00:06:42 localhost kernel: ACPI: PCI interrupt 0000:03:02.0[A] -> GSI 18 (level, low) -> IRQ 18
May  8 00:06:42 localhost kernel: ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[f9005000-f90057ff]  Max Packet=[2048]
May  8 00:06:42 localhost kernel: NET: Registered protocol family 17
May  8 00:06:42 localhost kernel: e1000: eth0: e1000_watchdog: NIC Link is Up 10 Mbps Half Duplex
May  8 00:06:42 localhost kernel: NET: Registered protocol family 10
May  8 00:06:42 localhost kernel: Disabled Privacy Extensions on device c0313ce0(lo)
May  8 00:06:42 localhost kernel: IPv6 over IPv4 tunneling driver
May  8 00:06:43 localhost kernel: ACPI: Power Button (FF) [PWRF]
May  8 00:06:43 localhost kernel: apm: BIOS not found.
May  8 00:06:44 localhost kernel: agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
May  8 00:06:44 localhost kernel: agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
May  8 00:06:44 localhost kernel: agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
May  8 00:06:44 localhost kernel: agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
May  8 00:06:44 localhost kernel: agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
May  8 00:06:44 localhost kernel: agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
May  8 00:06:47 localhost kernel: bridge-eth0: already up
May  8 00:06:57 localhost gconfd (jgb-7717): starting (version 2.10.0), pid 7717 user 'jgb'
May  8 00:06:57 localhost gconfd (jgb-7717): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May  8 00:06:57 localhost gconfd (jgb-7717): Resolved address "xml:readwrite:/home/jgb/.gconf" to a writable configuration source at position 1
May  8 00:06:57 localhost gconfd (jgb-7717): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May  8 00:07:01 localhost gconfd (jgb-7717): Resolved address "xml:readwrite:/home/jgb/.gconf" to a writable configuration source at position 0
May  8 00:26:42 localhost -- MARK --
May  8 00:34:57 localhost exiting on signal 15
May  8 00:34:58 localhost syslogd 1.4.1#16ubuntu6: restart.

```

---

### Post by liljencrantz on 2005-05-10
You should consider editing your message to remove the line that breaks the forum layout from the logs.

As to you problem, I think a bit more investigation is needed. Some things to investigate:

How crashed is the computer? Can you ping it, ssh to it, does the caps lock key work, etc?

Does the crash happen when the computer is idle, or do you have to be using it for the crash to occur?

Which of the programs have to be running for the system to crash? Try using your computer without OpenOffice, Konsole, KMail, etc and see what software causes the crash.

Does your Suse installation use the same hardware and drivers, i.e. is there some piece of hardware that is not installed under Suse, like a Wireles card, etc.? Are you using the same drivers (like proprietary nVidia driver, etc.) on both systems? Are the Kernel versions of roughly the same age?

---

### Post by jd_za on 2005-05-14
Some more info:

2.6.10-5-686

```

lsmod
Module                  Size  Used by
vmnet                  30460  12 
vmmon                 108364  0 
ipv6                  257888  12 
proc_intf               3908  0 
cpufreq_powersave       1632  0 
cpufreq_userspace       4348  0 
cpufreq_ondemand        6140  0 
freq_table              4004  0 
video                  15972  0 
battery                 9988  0 
container               4320  0 
button                  6480  0 
pcc_acpi               11008  0 
sony_acpi               5928  0 
ac                      4676  0 
af_packet              21992  2 
ohci1394               34596  0 
e1000                  85620  0 
tsdev                   7520  0 
snd_intel8x0           32352  3 
snd_ac97_codec         74144  1 snd_intel8x0
snd_pcm_oss            52132  0 
snd_mixer_oss          19680  3 snd_pcm_oss
usbhid                 31936  0 
snd_pcm                94696  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25060  1 snd_pcm
snd                    55012  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10016  3 snd
snd_page_alloc          9732  2 snd_intel8x0,snd_pcm
i2c_i801                8364  0 
i2c_core               22320  1 i2c_i801
hw_random               5300  0 
ehci_hcd               32708  0 
uhci_hcd               32816  0 
usbcore               119000  4 usbhid,ehci_hcd,uhci_hcd
shpchp                 99172  0 
pci_hotplug            33488  1 shpchp
intel_agp              22140  0 
intel_mch_agp          10256  1 
floppy                 58864  0 
pcspkr                  3496  0 
rtc                    12472  0 
evdev                   9344  0 
md                     47440  0 
dm_mod                 59420  1 
capability              4648  0 
commoncap               7712  1 capability
nvidia               3923452  12 
agpgart                33608  3 intel_agp,intel_mch_agp,nvidia
sbp2                   23816  0 
ieee1394              108312  2 ohci1394,sbp2
psmouse                21320  0 
mousedev               11288  1 
parport_pc             37252  0 
lp                     11144  0 
parport                36744  2 parport_pc,lp
reiserfs              262960  3 
ext2                   66632  0 
ext3                  137256  0 
jbd                    60536  1 ext3
mbcache                 8356  2 ext2,ext3
sd_mod                 17776  6 
sr_mod                 17188  0 
cdrom                  40220  1 sr_mod
sg                     38400  0 
sata_sil                8100  0 
ata_piix                9124  11 
libata                 49316  2 sata_sil,ata_piix
scsi_mod              127552  5 sbp2,sd_mod,sr_mod,sg,libata
unix                   28276  837 
thermal                13320  0 
processor              22452  1 thermal
fan                     4388  0 
fbcon                  37504  0 
font                    8192  1 fbcon
bitblit                 5472  1 fbcon
vesafb                  6724  0 
cfbcopyarea             3808  1 vesafb
cfbimgblt               2912  1 vesafb
cfbfillrect             3488  1 vesafb

ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.1  0.0   1552   508 ?        S    14:58   0:00 init [2]         
root         2  0.0  0.0      0     0 ?        SN   14:58   0:00 [ksoftirqd/0]
root         3  0.0  0.0      0     0 ?        S<   14:58   0:00 [events/0]
root         4  0.0  0.0      0     0 ?        S<   14:58   0:00 [khelper]
root        16  0.0  0.0      0     0 ?        S<   14:58   0:00 [kacpid]
root       109  0.0  0.0      0     0 ?        S<   14:58   0:00 [kblockd/0]
root       143  0.0  0.0      0     0 ?        S    14:58   0:00 [pdflush]
root       144  0.0  0.0      0     0 ?        S    14:58   0:00 [pdflush]
root       146  0.0  0.0      0     0 ?        S<   14:58   0:00 [aio/0]
root       145  0.0  0.0      0     0 ?        S    14:58   0:00 [kswapd0]
root       733  0.0  0.0      0     0 ?        S    14:58   0:00 [kseriod]
root       866  0.0  0.0      0     0 ?        S<   14:58   0:00 [ata/0]
root       870  0.0  0.0      0     0 ?        S    14:58   0:00 [scsi_eh_0]
root       874  0.0  0.0      0     0 ?        S    14:58   0:00 [scsi_eh_1]
root       884  0.0  0.0      0     0 ?        S    14:58   0:00 [scsi_eh_2]
root       885  0.0  0.0      0     0 ?        S    14:58   0:00 [scsi_eh_3]
root       886  0.0  0.0      0     0 ?        S    14:58   0:00 [scsi_eh_4]
root       887  0.0  0.0      0     0 ?        S    14:58   0:00 [scsi_eh_5]
root       952  0.0  0.0      0     0 ?        S<   14:58   0:00 [reiserfs/0]
root       979  0.0  0.0   1532   360 ?        S<s  14:58   0:00 udevd
root      2228  0.0  0.0      0     0 ?        S    14:58   0:00 [khpsbpkt]
root      3628  0.0  0.0      0     0 ?        S    14:58   0:00 [shpchpd_event]
root      3869  0.1  0.0      0     0 ?        S    14:58   0:00 [khubd]
root      5672  0.0  0.0      0     0 ?        S    14:58   0:00 [knodemgrd_0]
root      6065  0.0  0.0   2136   952 ?        S<s  14:59   0:00 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/run/dhclient.eth0.leases eth0
syslog    6383  0.0  0.0   1864   704 ?        Ss   14:59   0:00 /sbin/syslogd -u syslog
root      6398  0.0  0.0   1552   380 ?        Ss   14:59   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      6400  0.0  0.1   2544  1444 ?        Ss   14:59   0:00 /sbin/klogd -P /var/run/klogd/kmsg
root      6427  0.0  0.2  10124  2372 ?        Ss   14:59   0:00 /usr/bin/gdm
root      6437  0.0  0.2  10452  2828 ?        S    14:59   0:00 /usr/bin/gdm
root      6472  2.6  3.9  46056 40724 ?        SL   14:59   0:08 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
cupsys    6634  0.0  0.2   5584  2544 ?        Ss   14:59   0:00 /usr/sbin/cupsd -F
root      6991  0.0  0.0   1812   788 ?        Ss   14:59   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
101       7055  0.0  0.1   2120  1056 ?        Ss   14:59   0:00 /usr/bin/dbus-daemon-1 --system
hal       7068  0.1  0.6   8428  6964 ?        Ss   14:59   0:00 /usr/sbin/hald --drop-privileges
root      7082  0.0  0.0   1580   528 ?        Ss   14:59   0:00 /usr/sbin/inetd
root      7236  0.0  0.1   2988  1132 ?        Ss   14:59   0:00 /usr/lib/postfix/master
postfix   7246  0.0  0.1   3000  1064 ?        S    14:59   0:00 pickup -l -t fifo -u -c
postfix   7247  0.0  0.1   3032  1084 ?        S    14:59   0:00 qmgr -l -t fifo -u -c
root      7423  0.0  0.1   3472  1504 ?        Ss   14:59   0:00 /usr/sbin/sshd
daemon    7484  0.0  0.0   1852   604 ?        Ss   14:59   0:00 /usr/sbin/atd
root      7496  0.0  0.0   1908   812 ?        Ss   14:59   0:00 /usr/sbin/cron
root      7572  0.0  0.0   1400   300 ?        S    14:59   0:00 /usr/bin/vmnet-bridge -d /var/run/vmnet-bridge-0.pid /dev/vmnet0 eth0
root      7594  0.0  0.0   1396   296 ?        S    14:59   0:00 /usr/bin/vmnet-netifup -d /var/run/vmnet-netifup-vmnet1.pid /dev/vmnet1 vmnet1
root      7605  0.0  0.0   1396   296 ?        S    14:59   0:00 /usr/bin/vmnet-netifup -d /var/run/vmnet-netifup-vmnet8.pid /dev/vmnet8 vmnet8
root      7655  0.0  0.0   1644   520 ?        Ss   14:59   0:00 /usr/bin/vmnet-natd -d /var/run/vmnet-natd-8.pid -m /var/run/vmnet-natd-8.mac -c /etc/vmware/vmnet8/nat/nat.conf
root      7661  0.0  0.0   1832   684 ?        Ss   14:59   0:00 /usr/bin/vmnet-dhcpd -cf /etc/vmware/vmnet8/dhcpd/dhcpd.conf -lf /etc/vmware/vmnet8/dhcpd/dhcpd.leases -pf /var/run/vmnet-dhcpd-vmnet8.pid vmnet8
root      7664  0.0  0.0   1832   672 ?        Ss   14:59   0:00 /usr/bin/vmnet-dhcpd -cf /etc/vmware/vmnet1/dhcpd/dhcpd.conf -lf /etc/vmware/vmnet1/dhcpd/dhcpd.leases -pf /var/run/vmnet-dhcpd-vmnet1.pid vmnet1
root      7665  0.0  0.2   7124  2780 ?        Ss   14:59   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  7666  0.0  0.2   6916  2556 ?        S    14:59   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  7667  0.0  0.2 228460  2932 ?        Sl   14:59   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  7669  0.0  0.2 228460  2932 ?        Sl   14:59   0:00 /usr/sbin/apache2 -k start -DSSL
root      7744  0.0  0.0   1548   472 tty1     Ss+  14:59   0:00 /sbin/getty 38400 tty1
root      7745  0.0  0.0   1548   472 tty2     Ss+  14:59   0:00 /sbin/getty 38400 tty2
root      7746  0.0  0.0   1548   472 tty3     Ss+  14:59   0:00 /sbin/getty 38400 tty3
root      7747  0.0  0.0   1548   472 tty4     Ss+  14:59   0:00 /sbin/getty 38400 tty4
root      7748  0.0  0.0   1548   472 tty5     Ss+  14:59   0:00 /sbin/getty 38400 tty5
root      7749  0.0  0.0   1548   472 tty6     Ss+  14:59   0:00 /sbin/getty 38400 tty6
jgb       7846  0.0  0.8  17392  8768 ?        Ss   15:00   0:00 x-session-manager
jgb       7892  0.0  0.0   3536   780 ?        Ss   15:00   0:00 gpg-agent --daemon
jgb       7895  0.0  0.0   2992   896 ?        Ss   15:00   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session x-session-manager
jgb       7898  0.0  0.0   2552   716 ?        S    15:00   0:00 /usr/bin/dbus-launch --exit-with-session x-session-manager
jgb       7899  0.0  0.0   2016   736 ?        Ss   15:00   0:00 dbus-daemon-1 --fork --print-pid 8 --print-address 6 --session
jgb       7901  0.2  0.7  10980  8292 ?        S    15:00   0:00 /usr/lib/gconf2/gconfd-2 5
jgb       7904  0.0  0.0   2272   984 ?        S    15:00   0:00 /usr/bin/gnome-keyring-daemon
jgb       7906  0.0  0.2   6212  2784 ?        Ss   15:00   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=19
jgb       7908  0.1  0.7  18676  8024 ?        S    15:00   0:00 /usr/lib/control-center/gnome-settings-daemon --oaf-activate-iid=OAFIID:GNOME_SettingsDaemon --oaf-ior-fd=23
jgb       7911  0.0  0.1   3044  1824 ?        S    15:00   0:00 /usr/lib/gamin/gam_server
jgb       7920  0.0  0.2   4672  2160 ?        S    15:00   0:00 xscreensaver -nosplash
jgb       7944  0.0  0.2   7724  2736 ?        Ss   15:00   0:00 gnome-smproxy --sm-client-id default0
jgb       7946  0.2  0.7  12992  7444 ?        Ss   15:00   0:00 /usr/bin/metacity --sm-client-id=default1
jgb       7954  0.3  1.1  27248 11584 ?        Ssl  15:00   0:00 gnome-panel --sm-client-id default2
jgb       7956  0.2  1.6  44064 17500 ?        Ssl  15:00   0:00 nautilus --no-default-window --sm-client-id default3
jgb       7958  0.0  0.8  17012  8932 ?        Ss   15:00   0:00 gnome-volume-manager --sm-client-id default5
jgb       7964  0.0  0.8  16572  8896 ?        Ss   15:00   0:00 update-notifier --sm-client-id default8
jgb       7966  0.0  0.6  33104  7016 ?        Ss   15:00   0:00 gnome-cups-icon --sm-client-id default4
jgb       7969  0.0  0.3  16232  3440 ?        Sl   15:00   0:00 /usr/lib/gnome-vfs2/gnome-vfs-daemon --oaf-activate-iid=OAFIID:GNOME_VFS_Daemon_Factory --oaf-ior-fd=27
jgb       7971  0.2  0.9  17896  9784 ?        S    15:00   0:00 /usr/lib/gnome-panel/wnck-applet --oaf-activate-iid=OAFIID:GNOME_Wncklet_Factory --oaf-ior-fd=28
jgb       7973  0.0  0.8  26388  8444 ?        Sl   15:00   0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=29
jgb       7986  0.0  0.0   2216   736 ?        S    15:00   0:00 /usr/lib/nautilus-cd-burner/mapping-daemon
jgb       7999  0.0  0.8  17840  8496 ?        S    15:00   0:00 /usr/lib/gnome-panel/clock-applet --oaf-activate-iid=OAFIID:GNOME_ClockApplet_Factory --oaf-ior-fd=37
jgb       8001  0.0  0.9  19184  9560 ?        S    15:00   0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=39
jgb       8003  0.0  0.6  15828  7004 ?        S    15:00   0:00 /usr/lib/gnome-panel/notification-area-applet --oaf-activate-iid=OAFIID:GNOME_NotificationAreaApplet_Factory --oaf-ior-fd=41
jgb       8069  0.0  0.1   3772  1228 ?        S    15:00   0:00 /bin/sh /usr/bin/gnome-volume-manager-gthumb /org/freedesktop/Hal/devices/usb_device_4a9_30b9_1_-1_noserial
jgb       8071  1.4  1.9 101836 19892 ?        Sl   15:00   0:03 gthumb --import-photos
jgb       8095  0.8  2.7  52192 28212 ?        S    15:01   0:01 /usr/lib/opera/7.54-20050131.5/opera
jgb       8114  0.1  1.2  35928 12956 ?        Sl   15:01   0:00 xmms
jgb       8116  0.2  1.3  37752 13496 ?        Sl   15:01   0:00 gnome-terminal
jgb       8119  0.8  2.7  46580 28788 ?        S    15:01   0:01 kmail
jgb       8124  0.0  0.0   2224   656 ?        S    15:01   0:00 gnome-pty-helper
jgb       8125  0.0  0.1   4136  1736 pts/0    Ss   15:01   0:00 bash
jgb       8137  0.0  0.2  10772  2524 ?        S    15:01   0:00 /usr/lib/opera/plugins/operaplugincleaner 8095
jgb       8138  0.2  0.6  15776  6424 ?        S    15:01   0:00 /usr/lib/opera/plugins/operamotifwrapper-2 21 24 /usr/lib/mozilla/plugins/libflashplayer.so
jgb       8146  0.0  0.9  23780 10088 ?        Ss   15:01   0:00 kdeinit Running...        
jgb       8150  0.0  0.8  22840  8824 ?        S    15:01   0:00 dcopserver [kdeinit] dcopserver --nosid --suicide
jgb       8152  0.0  0.9  23892  9676 ?        S    15:01   0:00 klauncher [kdeinit] klauncher
jgb       8154  0.7  1.3  27264 14300 ?        S    15:01   0:01 kded [kdeinit] kded       
jgb       8159  0.0  1.4  31680 15188 ?        S    15:01   0:00 knotify [kdeinit] knotify 
root      8164  0.0  0.1   4184  1812 pts/0    R    15:01   0:00 bash
jgb       8173  0.0  1.1  52304 11960 ?        S    15:02   0:00 kio_imap4 [kdeinit] kio_imap4 imap /tmp/ksocket-jgb/klauncherVGkIlb.slave-socket /tmp/ksocket-jgb/kmailQOqK8b.slave-socket
jgb       8177  0.0  1.0  24736 10784 ?        S    15:02   0:00 kio_file [kdeinit] kio_file file /tmp/ksocket-jgb/klauncherVGkIlb.slave-socket /tmp/ksocket-jgb/kmailp2rm0a.slave-socket
jgb       8178  0.0  1.0  50800 11308 ?        S    15:02   0:00 kio_pop3 [kdeinit] kio_pop3 pop3 /tmp/ksocket-jgb/klauncherVGkIlb.slave-socket /tmp/ksocket-jgb/kmaildg6gAa.slave-socket
jgb       8185  9.1  5.1  81168 53280 ?        Sl   15:02   0:13 valknut
jgb       8191  1.0  2.3  40264 24328 ?        S    15:02   0:01 k3b
jgb       8217  0.0  1.0  24292 10936 ?        S    15:02   0:00 kio_file [kdeinit] kio_file file /tmp/ksocket-jgb/klauncherVGkIlb.slave-socket /tmp/ksocket-jgb/k3b8xFyjb.slave-socket
jgb       8218  0.0  1.0  24156 10752 ?        S    15:02   0:00 kio_file [kdeinit] kio_file file /tmp/ksocket-jgb/klauncherVGkIlb.slave-socket /tmp/ksocket-jgb/k3bOnCBfa.slave-socket
root      8261  0.0  0.0   3960  1012 pts/0    R+   15:04   0:00 ps aux

```

---

### Post by wiraone on 2005-05-14
I've had problem before with my video card, network etc .. and it was caused by ACPI. I add the noacpi option at the kernel line inside my GRUB config file and everything went smoothly well. SUSE, FC and some other distros may have noacpi option as default. Give it a try and see if this solve the problem.

---

### Post by nad on 2005-05-14
Please edit your posts to put the posted information in a code box,  <code> ... </code> .

---

### Post by jd_za on 2005-05-20
I disabled ACPI and CPUFREQ.
These are the modules loaded on Hoary and not SuSE:
```

bitblit                 5472  1 fbcon
capability              4648  0
cfbcopyarea             3808  1 vesafb
cfbfillrect             3488  1 vesafb
cfbimgblt               2912  1 vesafb
commoncap               7712  1 capability
container               4320  0
ext2                   66632  0
ext3                  137256  0
fbcon                  37504  0
floppy                 58864  0
font                    8192  1 fbcon
i2c_core               22320  1 i2c_i801
i2c_i801                8364  0
intel_agp              22140  0
jbd                    60536  1 ext3
mbcache                 8356  2 ext2,ext3
md                     47440  0
mousedev               11288  1
pcc_acpi               11008  0
pci_hotplug            33488  1 shpchp
pcspkr                  3496  0
proc_intf               3908  0
psmouse                21320  0
rtc                    12472  0
sbp2                   23816  0
scsi_mod              127552  5 sbp2,sd_mod,sr_mod,sg,libata
shpchp                 99172  0
sony_acpi               5928  0
sr_mod                 17188  0
tsdev                   7520  0
unix                   28276  837
vesafb                  6724  0
video                  15972  0

```
On SuSE agpgart is not used by nvidia

Sometimes Hoary hangs completely, sometimes I can move the mouse, but cannot switch to to a tty or anything else.

---

### Post by Omarkj on 2005-05-20
Actually, I had the same problem once running Hoary, but I had updated from Warty with dist-upgrade. I was unable to solve it, but I did most of the things people have been talking about in this thread, I disabled ACPI and so on.

The system often hung (is this the correct verb?) when I was viewing webpages in Firefox that contained flash or other embedded things which I do not have support for. Anyway, as I said, I was unable to fix it so I ended up reinstalling Hoary (now with an official Hoary CD) and since then everything has been running rather smoothly.

I think it might be a bug, since other people are having the exact same problem. But I don't have the logs anymore (not that they contained anything interesting) so i wont be able to post a bugreport.

Best wishes,
Omar K.

---

