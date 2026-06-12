---
title: "Mounting local filesystem.................fail"
date: 2005-11-04
forum: Desktop Environments
---

### Post by vegetto on 2005-11-04
Everytime i boot the system, i get the same error message. but the partitions are mounted. the only thing wrong is that the partitions are not listed in "Computer". is there any fix for this?

---

### Post by phanboy_iv on 2005-11-04
What does your /etc/fstab file say?

---

### Post by vegetto on 2005-11-04
my fstab :-

/proc    /proc    proc    defaults   0 0
/sys     /sys     sysfs   defaults   0 0
/dev/hda3 /       ext3    defaults   0 1
/dev/fd0  /media/floppy vfat user,noauto,sync,exec,umask=000 0 0
/dev/cdrom /media/cdrom auto user,noauto,exec,ro   0 0
/dev/hda4 none    swap    defaults   0 0

/dev/hda5   /media/hda5   vfat   user,fmask=0111,dmask=0000   0   0
/dev/hda1   /media/hda1   ntfs   ro,auto,user,fmask=0111,dmask=0000

---

### Post by Micro Rotors on 2005-11-04
and this is what mine is saying;

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda7       /home           ext3    defaults        0       2
/dev/sda1       /media/sda1     ntfs    defaults        0       0
/dev/sda2       /media/sda2     ntfs    defaults        0       0
/dev/sda6       /media/sda6     ntfs    defaults        0       0
/dev/sdb1       /media/sdb1     vfat    defaults        0       0
/dev/sda8       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdc        /media/usb0     auto    rw,user,noauto  0       0

---

### Post by phanboy_iv on 2005-11-04
[QUOTE=vegetto]my fstab :-

/proc    /proc    proc    defaults   0 0
/sys     /sys     sysfs   defaults   0 0
/dev/hda3 /       ext3    defaults   0 1
/dev/fd0  /media/floppy vfat user,noauto,sync,exec,umask=000 0 0
/dev/cdrom /media/cdrom auto user,noauto,exec,ro   0 0
/dev/hda4 none    swap    defaults   0 0

/dev/hda5   /media/hda5   vfat   user,fmask=0111,dmask=0000   0   0
/dev/hda1   /media/hda1   ntfs   ro,auto,user,fmask=0111,dmask=0000[/QUOTE]


Just curious, what does > mount -l

give?

And have you edited your fstab file in the past?

---

### Post by Micro Rotors on 2005-11-04
No I have not changed a thing, mine has been giving me the Fail since I installed it.

This is what mine is saying;


/dev/sda5 on / type ext3 (rw,errors=remount-ro) [/]
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-9-386/volatile type tmpfs (rw,mode=0755)
/dev/sda7 on /home type ext3 (rw) [/home]
/dev/sda1 on /media/sda1 type ntfs (rw)
/dev/sda2 on /media/sda2 type ntfs (rw)
/dev/sda6 on /media/sda6 type ntfs (rw)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)

---

### Post by Kyral on 2005-11-04
Whats the exact error msg?

---

### Post by Micro Rotors on 2005-11-04
[QUOTE=Kyral]Whats the exact error msg?[/QUOTE]

When Ubuntu boots up, you see a list of everything fireing up and it says ok to each one of them, exept I get this;

Mounting local filesystem.................[COLOR="Red"]fail[/COLOR]

this has been going on since the istalation

Thanks Kyral
Bill

---

### Post by Kyral on 2005-11-04
Which FS is failing exactly? You should be able to check the bootlog, or switch over to the "1st" VT while booting (If you are using USplash) to see the verbose output

---

### Post by Micro Rotors on 2005-11-04
I am not sure ,, The exact line says,  
mounting local filesystems.................[COLOR="Red"]failed[/COLOR]

It looks just like that, in plural as in all of them, but its working as far as I knoe I am thyping this message from it. How do I look at the bootlog?

Bill

---

### Post by Kyral on 2005-11-04
Check the /var/log directory :P

---

### Post by Micro Rotors on 2005-11-04
Ok heres how new I am ,, how do I open up the  /var/log

---

### Post by Kyral on 2005-11-04
```
ls /var/log
```

Or, (Me being stupid forgot about this)

System Tools -> System Log

---

### Post by Micro Rotors on 2005-11-04
[QUOTE=Kyral]```
ls /var/log
```

[/QUOTE]

Ok this is what it says;

bill@ubmicro:~$ ls /var/log
acpid                   debug.0            faillog         messages.0
aptitude                dmesg              fontconfig.log  news
auth.log                dpkg.log           gdm             scrollkeeper.log
auth.log.0              evms-engine.1.log  installer       syslog
base-config.log         evms-engine.2.log  kern.log        syslog.0
base-config-pkgsel.log  evms-engine.3.log  kern.log.0      syslog.1.gz
base-config.timings     evms-engine.4.log  lastlog         syslog.2.gz
btmp                    evms-engine.5.log  lpr.log         user.log
cups                    evms-engine.6.log  mail.err        user.log.0
daemon.log              evms-engine.7.log  mail.info       uucp.log
daemon.log.0            evms-engine.8.log  mail.log        wtmp
debian-installer        evms-engine.9.log  mail.warn       Xorg.0.log
debug                   evms-engine.log    messages        Xorg.0.log.old
bill@ubmicro:~$

How do I open faillog  ?

---

### Post by Kyral on 2005-11-04
look in the Syslog files (normal text files, you can view them with GEdit) and scan for entries at the time you last booted up

---

### Post by Micro Rotors on 2005-11-04
here you go; LONG FILE

Nov  4 13:43:40 localhost gconfd (bill-8952): Exiting
Nov  4 13:43:40 localhost gdm[8296]: Master rebooting...
Nov  4 13:43:41 localhost shutdown[8296]: shutting down for system reboot
Nov  4 13:43:41 localhost init: Switching to runlevel: 6
Nov  4 13:43:46 localhost kernel: [4295772.078000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Nov  4 13:43:46 localhost kernel: [4295772.078000] apm: disabled on user request.
Nov  4 13:43:49 localhost sdpd[8765]: terminating...   
Nov  4 13:43:49 localhost kernel: Kernel logging (proc) stopped.
Nov  4 13:43:49 localhost kernel: Kernel log daemon terminating.
Nov  4 13:43:49 localhost exiting on signal 15
Nov  4 13:44:52 localhost syslogd 1.4.1#17ubuntu3: restart.
Nov  4 13:44:52 localhost kernel: Inspecting /boot/System.map-2.6.12-9-386
Nov  4 13:44:52 localhost kernel: Loaded 29002 symbols from /boot/System.map-2.6.12-9-386.
Nov  4 13:44:52 localhost kernel: Symbols match kernel version 2.6.12.
Nov  4 13:44:52 localhost kernel: No module symbols loaded - kernel modules not enabled. 
Nov  4 13:44:52 localhost kernel: 7 9 10 11 12 14 15) *0, disabled.
Nov  4 13:44:52 localhost kernel: [4294668.546000] ACPI: PCI Interrupt Link [LSMB] (IRQs *3 4 5 7 9 10 11 12 14 15)
Nov  4 13:44:52 localhost kernel: [4294668.546000] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 7 9 *10 11 12 14 15)
Nov  4 13:44:52 localhost kernel: [4294668.547000] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Nov  4 13:44:52 localhost kernel: [4294668.547000] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Nov  4 13:44:52 localhost kernel: [4294668.547000] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 5 7 9 *10 11 12 14 15)
Nov  4 13:44:52 localhost kernel: [4294668.548000] ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Nov  4 13:44:52 localhost kernel: [4294668.548000] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
Nov  4 13:44:52 localhost kernel: [4294668.548000] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
Nov  4 13:44:52 localhost kernel: [4294668.549000] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
Nov  4 13:44:52 localhost kernel: [4294668.549000] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
Nov  4 13:44:52 localhost kernel: [4294668.549000] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
Nov  4 13:44:52 localhost kernel: [4294668.549000] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
Nov  4 13:44:52 localhost kernel: [4294668.550000] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
Nov  4 13:44:52 localhost kernel: [4294668.550000] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
Nov  4 13:44:52 localhost kernel: [4294668.550000] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
Nov  4 13:44:52 localhost kernel: [4294668.551000] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
Nov  4 13:44:52 localhost kernel: [4294668.551000] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
Nov  4 13:44:52 localhost kernel: [4294668.551000] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
Nov  4 13:44:52 localhost kernel: [4294668.552000] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
Nov  4 13:44:52 localhost kernel: [4294668.552000] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0, disabled.
Nov  4 13:44:52 localhost kernel: [4294668.552000] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
Nov  4 13:44:52 localhost kernel: [4294668.553000] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
Nov  4 13:44:52 localhost kernel: [4294668.555000] Linux Plug and Play Support v0.97 (c) Adam Belay
Nov  4 13:44:52 localhost kernel: [4294668.555000] pnp: PnP ACPI init
Nov  4 13:44:52 localhost kernel: [4294668.559000] pnp: PnP ACPI: found 11 devices
Nov  4 13:44:52 localhost kernel: [4294668.559000] PnPBIOS: Disabled by ACPI PNP
Nov  4 13:44:52 localhost kernel: [4294668.559000] PCI: Using ACPI for IRQ routing
Nov  4 13:44:52 localhost kernel: [4294668.559000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Nov  4 13:44:52 localhost kernel: [4294668.615000] pnp: 00:00: ioport range 0x4000-0x407f could not be reserved
Nov  4 13:44:52 localhost kernel: [4294668.615000] pnp: 00:00: ioport range 0x4080-0x40ff has been reserved
Nov  4 13:44:52 localhost kernel: [4294668.615000] pnp: 00:00: ioport range 0x4400-0x447f has been reserved
Nov  4 13:44:52 localhost kernel: [4294668.615000] pnp: 00:00: ioport range 0x4480-0x44ff could not be reserved
Nov  4 13:44:52 localhost kernel: [4294668.615000] pnp: 00:00: ioport range 0x4800-0x487f has been reserved
Nov  4 13:44:52 localhost kernel: [4294668.615000] pnp: 00:00: ioport range 0x4880-0x48ff has been reserved
Nov  4 13:44:52 localhost kernel: [4294668.615000] audit: initializing netlink socket (disabled)
Nov  4 13:44:52 localhost kernel: [4294668.615000] audit: initialized
Nov  4 13:44:52 localhost kernel: [4294668.615000] highmem bounce pool size: 64 pages
Nov  4 13:44:52 localhost kernel: [4294668.615000] VFS: Disk quotas dquot_6.5.1
Nov  4 13:44:52 localhost kernel: [4294668.615000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Nov  4 13:44:52 localhost kernel: [4294668.615000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
Nov  4 13:44:52 localhost kernel: [4294668.615000] devfs: boot_options: 0x0
Nov  4 13:44:52 localhost kernel: [4294668.615000] Initializing Cryptographic API
Nov  4 13:44:52 localhost kernel: [4294668.615000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
Nov  4 13:44:53 localhost kernel: [4294668.615000] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
Nov  4 13:44:53 localhost kernel: [4294668.615000] assign_interrupt_mode Found MSI capability
Nov  4 13:44:53 localhost kernel: [4294668.615000] Allocate Port Service[pcie00]
Nov  4 13:44:53 localhost kernel: [4294668.615000] PCI: Setting latency timer of device 0000:00:0c.0 to 64
Nov  4 13:44:53 localhost kernel: [4294668.615000] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
Nov  4 13:44:53 localhost kernel: [4294668.615000] assign_interrupt_mode Found MSI capability
Nov  4 13:44:53 localhost kernel: [4294668.615000] Allocate Port Service[pcie00]
Nov  4 13:44:53 localhost kernel: [4294668.615000] PCI: Setting latency timer of device 0000:00:0d.0 to 64
Nov  4 13:44:53 localhost kernel: [4294668.615000] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
Nov  4 13:44:53 localhost kernel: [4294668.615000] assign_interrupt_mode Found MSI capability
Nov  4 13:44:53 localhost kernel: [4294668.615000] Allocate Port Service[pcie00]
Nov  4 13:44:53 localhost kernel: [4294668.615000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
Nov  4 13:44:53 localhost kernel: [4294668.615000] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
Nov  4 13:44:53 localhost kernel: [4294668.615000] assign_interrupt_mode Found MSI capability
Nov  4 13:44:53 localhost kernel: [4294668.615000] Allocate Port Service[pcie00]
Nov  4 13:44:53 localhost kernel: [4294668.615000] isapnp: Scanning for PnP cards...
Nov  4 13:44:53 localhost kernel: [4294668.967000] isapnp: No Plug & Play device found
Nov  4 13:44:53 localhost kernel: [4294668.980000] PNP: No PS/2 controller found. Probing ports directly.
Nov  4 13:44:53 localhost kernel: [4294668.991000] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov  4 13:44:53 localhost kernel: [4294668.991000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
Nov  4 13:44:53 localhost kernel: [4294668.991000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Nov  4 13:44:53 localhost kernel: [4294668.993000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Nov  4 13:44:53 localhost kernel: [4294668.993000] io scheduler noop registered
Nov  4 13:44:53 localhost kernel: [4294668.993000] io scheduler anticipatory registered
Nov  4 13:44:53 localhost kernel: [4294668.993000] io scheduler deadline registered
Nov  4 13:44:53 localhost kernel: [4294668.993000] io scheduler cfq registered
Nov  4 13:44:53 localhost kernel: [4294668.993000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Nov  4 13:44:53 localhost kernel: [4294668.993000] EISA: Probing bus 0 at eisa.0
Nov  4 13:44:53 localhost kernel: [4294668.993000] Cannot allocate resource for EISA slot 4
Nov  4 13:44:53 localhost kernel: [4294668.993000] Cannot allocate resource for EISA slot 6
Nov  4 13:44:53 localhost kernel: [4294668.993000] Cannot allocate resource for EISA slot 7
Nov  4 13:44:53 localhost kernel: [4294668.993000] Cannot allocate resource for EISA slot 8
Nov  4 13:44:53 localhost kernel: [4294668.993000] EISA: Detected 0 cards.
Nov  4 13:44:53 localhost kernel: [4294668.993000] NET: Registered protocol family 2
Nov  4 13:44:53 localhost kernel: [4294669.126000] IP: routing cache hash table of 8192 buckets, 64Kbytes
Nov  4 13:44:53 localhost kernel: [4294669.126000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Nov  4 13:44:53 localhost kernel: [4294669.127000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
Nov  4 13:44:53 localhost kernel: [4294669.127000] TCP: Hash tables configured (established 131072 bind 65536)
Nov  4 13:44:53 localhost kernel: [4294669.127000] NET: Registered protocol family 8
Nov  4 13:44:53 localhost kernel: [4294669.127000] NET: Registered protocol family 20
Nov  4 13:44:53 localhost kernel: [4294669.127000] ACPI wakeup devices: 
Nov  4 13:44:53 localhost kernel: [4294669.127000] HUB0 XVR0 XVR1 XVR2 XVR3 USB0 USB2 MMAC MMCI UAR1 
Nov  4 13:44:53 localhost kernel: [4294669.127000] ACPI: (supports S0 S3 S4 S5)
Nov  4 13:44:53 localhost kernel: [4294669.127000] Freeing unused kernel memory: 224k freed
Nov  4 13:44:53 localhost kernel: [4294669.639000] input: AT Translated Set 2 keyboard on isa0060/serio0
Nov  4 13:44:53 localhost kernel: [4294669.641000] vga16fb: initializing
Nov  4 13:44:53 localhost kernel: [4294669.641000] vga16fb: mapped to 0xc00a0000
Nov  4 13:44:53 localhost kernel: [4294669.754000] Console: switching to colour frame buffer device 80x30
Nov  4 13:44:53 localhost kernel: [4294669.754000] fb0: VGA16 VGA frame buffer device
Nov  4 13:44:53 localhost kernel: [4294670.982000] Capability LSM initialized
Nov  4 13:44:53 localhost kernel: [4294670.990000] NET: Registered protocol family 1
Nov  4 13:44:53 localhost kernel: [4294670.999000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Nov  4 13:44:53 localhost kernel: [4294670.999000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Nov  4 13:44:53 localhost kernel: [4294670.999000] ACPI: bus type ide registered
Nov  4 13:44:53 localhost kernel: [4294671.001000] SCSI subsystem initialized
Nov  4 13:44:53 localhost kernel: [4294671.001000] libata version 1.11 loaded.
Nov  4 13:44:53 localhost kernel: [4294671.002000] sata_nv version 0.6
Nov  4 13:44:53 localhost kernel: [4294671.002000] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
Nov  4 13:44:53 localhost kernel: [4294671.002000] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APSI] -> GSI 23 (level, low) -> IRQ 23
Nov  4 13:44:53 localhost kernel: [4294671.002000] PCI: Setting latency timer of device 0000:00:07.0 to 64
Nov  4 13:44:53 localhost kernel: [4294671.002000] ata1: SATA max UDMA/133 cmd 0x9F0 ctl 0xBF2 bmdma 0xCC00 irq 23
Nov  4 13:44:53 localhost kernel: [4294671.002000] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xB72 bmdma 0xCC08 irq 23
Nov  4 13:44:53 localhost kernel: [4294671.357000] ata1: dev 0 cfg 49:2f00 82:7c6b 83:7f09 84:4673 85:7c69 86:3e01 87:4663 88:407f
Nov  4 13:44:53 localhost kernel: [4294671.357000] ata1: dev 0 ATA, max UDMA/133, 398297088 sectors: lba48
Nov  4 13:44:53 localhost kernel: [4294671.358000] nv_sata: Primary device added
Nov  4 13:44:53 localhost kernel: [4294671.358000] nv_sata: Primary device removed
Nov  4 13:44:53 localhost kernel: [4294671.358000] nv_sata: Secondary device added
Nov  4 13:44:53 localhost kernel: [4294671.358000] nv_sata: Secondary device removed
Nov  4 13:44:53 localhost kernel: [4294671.358000] ata1: dev 0 configured for UDMA/133
Nov  4 13:44:53 localhost kernel: [4294671.358000] scsi0 : sata_nv
Nov  4 13:44:53 localhost kernel: [4294671.559000] ata2: no device found (phy stat 00000000)
Nov  4 13:44:53 localhost kernel: [4294671.559000] scsi1 : sata_nv
Nov  4 13:44:53 localhost kernel: [4294671.559000]   Vendor: ATA       Model: Maxtor 6L200S0    Rev: BANC
Nov  4 13:44:53 localhost kernel: [4294671.559000]   Type:   Direct-Access                      ANSI SCSI revision: 05
Nov  4 13:44:53 localhost kernel: [4294671.559000] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22
Nov  4 13:44:53 localhost kernel: [4294671.559000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSJ] -> GSI 22 (level, low) -> IRQ 22
Nov  4 13:44:53 localhost kernel: [4294671.559000] PCI: Setting latency timer of device 0000:00:08.0 to 64
Nov  4 13:44:53 localhost kernel: [4294671.560000] ata3: SATA max UDMA/133 cmd 0x9E0 ctl 0xBE2 bmdma 0xB800 irq 22
Nov  4 13:44:53 localhost kernel: [4294671.560000] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xB62 bmdma 0xB808 irq 22
Nov  4 13:44:53 localhost kernel: [4294671.761000] ata3: no device found (phy stat 00000000)
Nov  4 13:44:53 localhost kernel: [4294671.761000] scsi2 : sata_nv
Nov  4 13:44:53 localhost kernel: [4294671.962000] ata4: no device found (phy stat 00000000)
Nov  4 13:44:53 localhost kernel: [4294671.962000] scsi3 : sata_nv
Nov  4 13:44:53 localhost kernel: [4294671.981000] NFORCE-CK804: IDE controller at PCI slot 0000:00:06.0
Nov  4 13:44:53 localhost kernel: [4294671.981000] NFORCE-CK804: chipset revision 162
Nov  4 13:44:53 localhost kernel: [4294671.981000] NFORCE-CK804: not 100%% native mode: will probe irqs later
Nov  4 13:44:53 localhost kernel: [4294671.981000] NFORCE-CK804: 0000:00:06.0 (rev a2) UDMA133 controller
Nov  4 13:44:53 localhost kernel: [4294671.981000]     ide0: BM-DMA at 0xe000-0xe007, BIOS settings: hda:DMA, hdb:DMA
Nov  4 13:44:53 localhost kernel: [4294671.981000]     ide1: BM-DMA at 0xe008-0xe00f, BIOS settings: hdc:DMA, hdd:DMA
Nov  4 13:44:53 localhost kernel: [4294671.981000] Probing IDE interface ide0...
Nov  4 13:44:53 localhost kernel: [4294672.653000] hda: LITE-ON DVDRW SOHW-1673S, ATAPI CD/DVD-ROM drive
Nov  4 13:44:53 localhost kernel: [4294673.265000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Nov  4 13:44:53 localhost kernel: [4294673.265000] Probing IDE interface ide1...
Nov  4 13:44:53 localhost kernel: [4294673.784000] Probing IDE interface ide1...
Nov  4 13:44:53 localhost kernel: [4294674.302000] Probing IDE interface ide2...
Nov  4 13:44:53 localhost kernel: [4294674.814000] Probing IDE interface ide3...
Nov  4 13:44:53 localhost kernel: [4294675.326000] Probing IDE interface ide4...
Nov  4 13:44:53 localhost kernel: [4294675.838000] Probing IDE interface ide5...
Nov  4 13:44:53 localhost kernel: [4294676.354000] hda: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
Nov  4 13:44:53 localhost kernel: [4294676.354000] Uniform CD-ROM driver Revision: 3.20
Nov  4 13:44:53 localhost kernel: [4294676.358000] SCSI device sda: 398297088 512-byte hdwr sectors (203928 MB)
Nov  4 13:44:53 localhost kernel: [4294676.358000] SCSI device sda: drive cache: write back
Nov  4 13:44:53 localhost kernel: [4294676.358000] SCSI device sda: 398297088 512-byte hdwr sectors (203928 MB)
Nov  4 13:44:53 localhost kernel: [4294676.358000] SCSI device sda: drive cache: write back
Nov  4 13:44:53 localhost kernel: [4294676.358000]  /dev/scsi/host0/bus0/target0/lun0: p1 p2 p3 < p5 p6 p7 p8 >
Nov  4 13:44:53 localhost kernel: [4294676.434000] Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
Nov  4 13:44:53 localhost kernel: [4294676.632000] Attempting manual resume
Nov  4 13:44:53 localhost kernel: [4294676.633000] swsusp: Suspend partition has wrong signature?
Nov  4 13:44:53 localhost kernel: [4294676.654000] usbcore: registered new driver usbfs
Nov  4 13:44:53 localhost kernel: [4294676.654000] usbcore: registered new driver hub
Nov  4 13:44:53 localhost kernel: [4294676.654000] ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
Nov  4 13:44:53 localhost kernel: [4294676.655000] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
Nov  4 13:44:53 localhost kernel: [4294676.655000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 21 (level, low) -> IRQ 21
Nov  4 13:44:53 localhost kernel: [4294676.655000] PCI: Setting latency timer of device 0000:00:02.0 to 64
Nov  4 13:44:53 localhost kernel: [4294676.655000] ohci_hcd 0000:00:02.0: nVidia Corporation CK804 USB Controller
Nov  4 13:44:53 localhost kernel: [4294676.667000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
Nov  4 13:44:53 localhost kernel: [4294676.667000] ohci_hcd 0000:00:02.0: irq 21, io mem 0xfebff000
Nov  4 13:44:53 localhost kernel: [4294676.720000] hub 1-0:1.0: USB hub found
Nov  4 13:44:53 localhost kernel: [4294676.720000] hub 1-0:1.0: 10 ports detected
Nov  4 13:44:53 localhost kernel: [4294676.729000] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
Nov  4 13:44:53 localhost kernel: [4294676.729000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 20 (level, low) -> IRQ 20
Nov  4 13:44:53 localhost kernel: [4294676.729000] PCI: Setting latency timer of device 0000:00:02.1 to 64
Nov  4 13:44:53 localhost kernel: [4294676.729000] ehci_hcd 0000:00:02.1: nVidia Corporation CK804 USB Controller
Nov  4 13:44:53 localhost kernel: [4294676.729000] ehci_hcd 0000:00:02.1: debug port 1
Nov  4 13:44:53 localhost kernel: [4294676.729000] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
Nov  4 13:44:53 localhost kernel: [4294676.729000] ehci_hcd 0000:00:02.1: irq 20, io mem 0xfebfe000
Nov  4 13:44:53 localhost kernel: [4294676.729000] PCI: cache line size of 64 is not supported by device 0000:00:02.1
Nov  4 13:44:53 localhost kernel: [4294676.729000] ehci_hcd 0000:00:02.1: park 0
Nov  4 13:44:53 localhost kernel: [4294676.729000] ehci_hcd 0000:00:02.1: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
Nov  4 13:44:53 localhost kernel: [4294676.729000] hub 2-0:1.0: USB hub found
Nov  4 13:44:53 localhost kernel: [4294676.729000] hub 2-0:1.0: 10 ports detected
Nov  4 13:44:53 localhost kernel: [4294676.783000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.41.
Nov  4 13:44:53 localhost kernel: [4294676.784000] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
Nov  4 13:44:53 localhost kernel: [4294676.784000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APCH] -> GSI 23 (level, low) -> IRQ 23
Nov  4 13:44:53 localhost kernel: [4294676.784000] PCI: Setting latency timer of device 0000:00:0a.0 to 64
Nov  4 13:44:53 localhost kernel: [4294677.061000] ohci_hcd 0000:00:02.0: wakeup
Nov  4 13:44:53 localhost kernel: [4294677.296000] eth0: forcedeth.c: subsystem: 01019:1b51 bound to 0000:00:0a.0
Nov  4 13:44:53 localhost kernel: [4294677.444000] usb 1-3: new low speed USB device using ohci_hcd and address 2
Nov  4 13:44:53 localhost kernel: [4294677.728000] usb 1-4: new full speed USB device using ohci_hcd and address 3
Nov  4 13:44:53 localhost kernel: [4294677.838000] hub 1-4:1.0: USB hub found
Nov  4 13:44:53 localhost kernel: [4294677.841000] hub 1-4:1.0: 3 ports detected
Nov  4 13:44:53 localhost kernel: [4294678.046000] usb 1-4.1: new full speed USB device using ohci_hcd and address 4
Nov  4 13:44:53 localhost kernel: [4294679.363000] usbcore: registered new driver hiddev
Nov  4 13:44:53 localhost kernel: [4294679.372000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:02.0-3
Nov  4 13:44:53 localhost kernel: [4294679.379000] input: USB HID v1.00 Keyboard [NMB Dell USB 7HK Keyboard] on usb-0000:00:02.0-4.1
Nov  4 13:44:53 localhost kernel: [4294679.388000] input,hiddev96: USB HID v1.00 Device [NMB Dell USB 7HK Keyboard] on usb-0000:00:02.0-4.1
Nov  4 13:44:53 localhost kernel: [4294679.388000] usbcore: registered new driver usbhid
Nov  4 13:44:53 localhost kernel: [4294679.388000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
Nov  4 13:44:53 localhost kernel: [4294679.805000] ACPI: Fan [FAN] (on)
Nov  4 13:44:53 localhost kernel: [4294679.807000] ACPI: CPU0 (power states: C1[C1])
Nov  4 13:44:53 localhost kernel: [4294679.807000] ACPI: Processor [CPU0] (supports 8 throttling states)
Nov  4 13:44:53 localhost kernel: [4294679.810000] ACPI: Thermal Zone [THRM] (34 C)
Nov  4 13:44:53 localhost kernel: [4294680.017000] Attempting manual resume
Nov  4 13:44:53 localhost kernel: [4294680.017000] swsusp: Suspend partition has wrong signature?
Nov  4 13:44:53 localhost kernel: [4294680.029000] kjournald starting.  Commit interval 5 seconds
Nov  4 13:44:53 localhost kernel: [4294680.029000] EXT3-fs: mounted filesystem with ordered data mode.
Nov  4 13:44:53 localhost kernel: [4294680.702000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
Nov  4 13:44:53 localhost kernel: [4294683.124000] Adding 1951856k swap on /dev/sda8.  Priority:-1 extents:1
Nov  4 13:44:53 localhost kernel: [4294683.343000] EXT3 FS on sda5, internal journal
Nov  4 13:44:53 localhost kernel: [4294687.506000] parport: PnPBIOS parport detected.
Nov  4 13:44:53 localhost kernel: [4294687.506000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Nov  4 13:44:53 localhost kernel: [4294687.590000] lp0: using parport0 (interrupt-driven).
Nov  4 13:44:53 localhost kernel: [4294687.616000] mice: PS/2 mouse device common for all mice
Nov  4 13:44:53 localhost kernel: [4294690.017000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
Nov  4 13:44:53 localhost kernel: [4294690.715000] cdrom: open failed.
Nov  4 13:44:53 localhost kernel: [4294691.300000] kjournald starting.  Commit interval 5 seconds
Nov  4 13:44:53 localhost kernel: [4294691.300000] EXT3 FS on sda7, internal journal
Nov  4 13:44:53 localhost kernel: [4294691.300000] EXT3-fs: mounted filesystem with ordered data mode.
Nov  4 13:44:53 localhost kernel: [4294691.306000] NTFS driver 2.1.22 [Flags: R/O MODULE].
Nov  4 13:44:53 localhost kernel: [4294691.357000] NTFS volume version 3.1.
Nov  4 13:44:53 localhost kernel: [4294691.384000] NTFS volume version 3.1.
Nov  4 13:44:53 localhost kernel: [4294691.419000] NTFS volume version 3.1.
Nov  4 13:44:53 localhost kernel: [4294692.567000] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x4c00
Nov  4 13:44:53 localhost kernel: [4294692.577000] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x4c40
Nov  4 13:44:53 localhost kernel: [4294692.775000] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
Nov  4 13:44:53 localhost kernel: [4294692.775000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCJ] -> GSI 22 (level, low) -> IRQ 22
Nov  4 13:44:53 localhost kernel: [4294692.775000] PCI: Setting latency timer of device 0000:00:04.0 to 64
Nov  4 13:44:53 localhost kernel: [4294693.085000] intel8x0_measure_ac97_clock: measured 49711 usecs
Nov  4 13:44:53 localhost kernel: [4294693.085000] intel8x0: clocking to 46787
Nov  4 13:44:53 localhost kernel: [4294693.653000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov  4 13:44:53 localhost kernel: [4294693.660000] shpchp: Address64 -------- Resource unparsed
Nov  4 13:44:53 localhost last message repeated 2 times
Nov  4 13:44:53 localhost kernel: [4294693.666000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Nov  4 13:44:53 localhost kernel: [4294693.922000] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
Nov  4 13:44:53 localhost kernel: [4294693.922000] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
Nov  4 13:44:53 localhost kernel: [4294693.922000] Model 1006 Rev 00000000 Serial 10061102
Nov  4 13:44:53 localhost kernel: [4294695.735000] Real Time Clock Driver v1.12
Nov  4 13:44:53 localhost kernel: [4294695.776000] input: PC Speaker
Nov  4 13:44:53 localhost kernel: [4294695.870000] FDC 0 is a post-1991 82077
Nov  4 13:44:53 localhost kernel: [4294696.045000] ts: Compaq touchscreen protocol output

---

### Post by Micro Rotors on 2005-11-04
second half:

Nov  4 13:44:53 localhost kernel: [4294697.385000] NET: Registered protocol family 17
Nov  4 13:44:53 localhost kernel: [4294702.261000] NET: Registered protocol family 10
Nov  4 13:44:53 localhost kernel: [4294702.261000] Disabled Privacy Extensions on device c02eb280(lo)
Nov  4 13:44:53 localhost kernel: [4294702.261000] IPv6 over IPv4 tunneling driver
Nov  4 13:44:53 localhost kernel: [4294703.791000] ACPI: Power Button (FF) [PWRF]
Nov  4 13:44:53 localhost kernel: [4294703.791000] ACPI: Power Button (CM) [PWRB]
Nov  4 13:44:53 localhost kernel: [4294703.862000] ibm_acpi: ec object not found
Nov  4 13:44:55 localhost hpiod: 0.9.5 accepting connections at 32769... 
Nov  4 13:44:55 localhost hp: unable to open /var/run/hplip/hpssd.port: No such file or directory: prnt/hpijs/hplip_api.c 84 
Nov  4 13:44:55 localhost hpiod: invalid message: 
Nov  4 13:44:55 localhost hp: unable to connect hpssd socket 50002: Connection refused: prnt/hpijs/hplip_api.c 710 
Nov  4 13:44:55 localhost hpiod: unable to ParDevice::Open hp:/par/ANY?device=/dev/parport0: No such file or directory: io/hpiod/ppdevice.cpp 827 
Nov  4 13:44:55 localhost hpiod: unable to ParDevice::Open hp:/par/ANY?device=/dev/parport1: No such file or directory: io/hpiod/ppdevice.cpp 827 
Nov  4 13:44:55 localhost hpiod: unable to ParDevice::Open hp:/par/ANY?device=/dev/parport2: No such file or directory: io/hpiod/ppdevice.cpp 827 
Nov  4 13:44:55 localhost hpiod: unable to ParDevice::Open hp:/par/ANY?device=/dev/parport3: No such file or directory: io/hpiod/ppdevice.cpp 827 
Nov  4 13:44:57 localhost kernel: [4294708.990000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Nov  4 13:44:57 localhost kernel: [4294708.990000] apm: overridden by ACPI.
Nov  4 13:44:57 localhost kernel: [4294709.056000] ip_tables: (C) 2000-2002 Netfilter core team
Nov  4 13:44:57 localhost kernel: [4294709.080000] ip_conntrack version 2.1 (8183 buckets, 65464 max) - 248 bytes per conntrack
Nov  4 13:44:58 localhost kernel: [4294709.642000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.40.4)
Nov  4 13:44:58 localhost kernel: [4294709.646000] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
Nov  4 13:44:58 localhost hcid[8786]: Bluetooth HCI daemon
Nov  4 13:44:58 localhost kernel: [4294709.732000] Bluetooth: Core ver 2.7
Nov  4 13:44:58 localhost kernel: [4294709.732000] NET: Registered protocol family 31
Nov  4 13:44:58 localhost kernel: [4294709.732000] Bluetooth: HCI device and connection manager initialized
Nov  4 13:44:58 localhost kernel: [4294709.732000] Bluetooth: HCI socket layer initialized
Nov  4 13:44:58 localhost kernel: [4294709.754000] Bluetooth: L2CAP ver 2.7
Nov  4 13:44:58 localhost kernel: [4294709.754000] Bluetooth: L2CAP socket layer initialized
Nov  4 13:44:58 localhost sdpd[8792]: Bluetooth SDP daemon 
Nov  4 13:44:58 localhost kernel: [4294709.775000] Bluetooth: RFCOMM ver 1.5
Nov  4 13:44:58 localhost kernel: [4294709.775000] Bluetooth: RFCOMM socket layer initialized
Nov  4 13:44:58 localhost kernel: [4294709.775000] Bluetooth: RFCOMM TTY layer initialized
Nov  4 13:44:58 localhost anacron[8821]: Anacron 2.3 started on 2005-11-04
Nov  4 13:44:58 localhost anacron[8821]: Normal exit (0 jobs run)
Nov  4 13:44:58 localhost /usr/sbin/cron[8846]: (CRON) INFO (pidfile fd = 3)
Nov  4 13:44:58 localhost /usr/sbin/cron[8847]: (CRON) STARTUP (fork ok)
Nov  4 13:44:58 localhost /usr/sbin/cron[8847]: (CRON) INFO (Running @reboot jobs)
Nov  4 13:45:01 localhost kernel: [4294713.014000] eth0: no IPv6 routers present
Nov  4 13:45:16 localhost gconfd (bill-8979): starting (version 2.12.0), pid 8979 user 'bill'
Nov  4 13:45:16 localhost gconfd (bill-8979): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Nov  4 13:45:16 localhost gconfd (bill-8979): Resolved address "xml:readonly:/usr/share/gconf/local.mandatory" to a read-only configuration source at position 1
Nov  4 13:45:16 localhost gconfd (bill-8979): Resolved address "xml:readwrite:/home/bill/.gconf" to a writable configuration source at position 2
Nov  4 13:45:16 localhost gconfd (bill-8979): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 3
Nov  4 13:45:16 localhost gconfd (bill-8979): Resolved address "xml:readonly:/usr/share/gconf/local.defaults" to a read-only configuration source at position 4
Nov  4 13:45:16 localhost gconfd (bill-8979): Resolved address "xml:readonly:/usr/share/gconf/cdd.defaults" to a read-only configuration source at position 5
Nov  4 13:45:16 localhost gconfd (bill-8979): Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at position 6
Nov  4 13:45:16 localhost gconfd (bill-8979): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7
Nov  4 13:45:23 localhost gconfd (bill-8979): Resolved address "xml:readwrite:/home/bill/.gconf" to a writable configuration source at position 0
Nov  4 13:50:04 localhost gconfd (root-9190): starting (version 2.12.0), pid 9190 user 'root'
Nov  4 13:50:04 localhost gconfd (root-9190): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Nov  4 13:50:04 localhost gconfd (root-9190): Resolved address "xml:readonly:/usr/share/gconf/local.mandatory" to a read-only configuration source at position 1
Nov  4 13:50:04 localhost gconfd (root-9190): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 2
Nov  4 13:50:04 localhost gconfd (root-9190): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 3
Nov  4 13:50:04 localhost gconfd (root-9190): Resolved address "xml:readonly:/usr/share/gconf/local.defaults" to a read-only configuration source at position 4
Nov  4 13:50:04 localhost gconfd (root-9190): Resolved address "xml:readonly:/usr/share/gconf/cdd.defaults" to a read-only configuration source at position 5
Nov  4 13:50:04 localhost gconfd (root-9190): Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at position 6
Nov  4 13:50:04 localhost gconfd (root-9190): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7
Nov  4 13:50:34 localhost gconfd (root-9190): GConf server is not in use, shutting down.
Nov  4 13:50:34 localhost gconfd (root-9190): Exiting

---

### Post by majikstreet on 2005-11-04
I have the same mounting local file systems fail error.

---

### Post by vegetto on 2005-11-04
mount -l gives this:-

/dev/hda3 on / type ext3 (rw)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-9-386/volatile type tmpfs (rw,mode=0755)
/dev/hda5 on /media/hda5 type vfat (rw,noexec,nosuid,nodev,fmask=0111,dmask=0000) [NEW VOLUME]
/dev/hda1 on /media/hda1 type ntfs (ro,noexec,nosuid,nodev,fmask=0111,dmask=0000)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

---

### Post by vegetto on 2005-11-04
I just found out by dmseg in console that i get this error every time:-
4294701.434000] cdrom: open failed.
[4294705.840000] cdrom: open failed.

I commented  out the cdrom and other partitions from fstab but still both error messages continue to appear. Just before the error appears the cdrom drive hisses for a while. any help?

---

### Post by phanboy_iv on 2005-11-07
[QUOTE=vegetto]I just found out by dmseg in console that i get this error every time:-
4294701.434000] cdrom: open failed.
[4294705.840000] cdrom: open failed.

I commented  out the cdrom and other partitions from fstab but still both error messages continue to appear. Just before the error appears the cdrom drive hisses for a while. any help?[/QUOTE]

My fstab has this entry for cdrom
> /dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
Maybe edit your cdrom entry to match this? You could try it.
Always be sure to make backups of important files before editing(that's saved my hide more than once!).

Micro Rotors, if you type > dmesg

in a terminal, do you get the same error as veggeto did here> I just found out by dmseg in console that i get this error every time:-
4294701.434000] cdrom: open failed.
[4294705.840000] cdrom: open failed.

in the output somewhere?

---

### Post by Micro Rotors on 2005-11-07
I guess the tree of us are on our own.:(

---

### Post by ola on 2005-11-19
Im having the same problem with mounting local filesystem. The closest I am for the problem was that I pushed F2 during startup & saw something with problem mounting tmpfs (mount point does not exist).

Any solutions found?

---

### Post by ranf on 2005-11-20
[QUOTE=ola]Im having the same problem with mounting local filesystem. The closest I am for the problem was that I pushed F2 during startup & saw something with problem mounting tmpfs (mount point does not exist).
[/QUOTE]
For me this thread helped:
[http://lists.debian.org/debian-laptop/2005/10/msg00257.html](http://lists.debian.org/debian-laptop/2005/10/msg00257.html)

---

### Post by ola on 2005-11-20
Thanks for the reply! Unfortunatley that was not the sollution to my problem.

My /etc/fstab looks like this:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /boot           ext3    defaults        0       2
/dev/hda2       none            swap    sw              0       0
/dev/hda5       /home           ext3    defaults        0       0
#/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
#/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/tmpfs          tmpfs           defaults                0       0


```

& this is what gets mounted at boot (which seems correct):
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3             9.2G  3.5G  5.4G  40% /
tmpfs                 189M  4.0K  189M   1% /dev/shm
/dev/hda1              59M   13M   44M  22% /boot
/dev/hda5             101G   87G   14G  87% /home

```

---

### Post by ranf on 2005-11-20
[QUOTE=ola]Thanks for the reply! Unfortunatley that was not the sollution to my problem.
[/QUOTE]
For me the problem was solved by commenting out /proc. Like that one guy said (I think in the very last message) /etc/init.d/mountvirtfs already mounts /proc explicitly.

---

### Post by able on 2006-01-23
Somebody found a solution to this?

---

### Post by ola on 2006-01-23
No. The only info I found was that it had somenthing to do with mounting the tempfs filesystem.. But my computer seems to work..

---

