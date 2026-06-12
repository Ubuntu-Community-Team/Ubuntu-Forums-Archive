---
title: "How do I remove a hard drive?"
date: 2010-04-19
forum: Desktop Environments
---

### Post by jiex on 2010-04-19
Hello
I'm new to Linux / UBUNTU. I built a machine to use as a torrent box, installed Karmic on a 1 GB SATA HDD. I later added another 1 GB SATA HDD for nothing other than storage. Karmic is installed in ext4 (about 50 GB); while the data area of the HDD is NTFS (about 930 GB). The second drive is NTFS all the way.
I have been trying to remove the second HDD that has nothing other than data on it.
My question is this: How do I do that?
If I disconnect the second drive, the system will not boot. I end up with a message something like: /dev/sdb1 does not exist.
If I reverse the connections of the drives on the MB, the system will not boot - and this problem persists even if I go into the BIOS and change the boot order.
I have also tried using the BIOS to detect only the single drive, which it does OK, but when I exist the bios, it hangs.
the other odd thing is that when I first added the second drive, the boot up went straight to log in. A few days ago, before I tried removing the second drive, GRUB loaded and I had the usual options of booting to recovery  and so on.
On one occasion, the options included XP, which is not installed on this box.
I have searched high and low for a solution, and i suspect it may have something to do with GRUB2 and the MBR, but cannot find out what I need to do. 
Most obliged for any assistance. I must say that every time I have had other queries, I've found the answers, but this one eludes me.
Thanks again for your help.
Jim.

---

### Post by micio on 2010-04-19
Take a look to /etc/fstab and comment the line with /dev/sdb1 (or that you need to disable)

for some reference take a look [here]("http://en.wikipedia.org/wiki/Fstab")

---

### Post by Vishal Agarwal on 2010-04-19
send me the output of your mount command
> root# mount

---

### Post by jiex on 2010-04-19
> **Vishal Agarwal said:**
> send me the output of your mount command

Thank you Micio and Vishal. Being new to this I'm learning how to do things so I hope I have the right information for you. This is what I found with the fdisk -ls command:
james@Ubuntu:~$ sudo fdisk -ls

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7573c67c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6079    48829536    7  HPFS/NTFS
/dev/sda2            6080      121601   927930465    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000afffd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6079    48829536   83  Linux
/dev/sdb2            6080        7295     9767520    5  Extended
/dev/sdb3            7296      121601   918162945    7  HPFS/NTFS
/dev/sdb5            6080        7295     9767488+  82  Linux swap / Solaris


Not sure whether this is what you were looking for. Thanks again to you both for taking the trouble to help me.
Jim

---

### Post by bolucpap on 2010-04-19
It seems that your Linux installation is on the second hard drive (/dev/sdb). This creates a problem when you remove the first drive, because the Linux drive now becomes the first drive (ie. /dev/sda), but the mount filesystem table (the /etc/fstab file) references your drives by paths like /dev/sdb1 instead of UUID's, which is a more robust way of specifying mount points. If you could post the output of ```
cat /etc/fstab 
``` and ```
ls -l /dev/disk/by-uuid/
``` We could be able to convert your fstab mounts to UUID based ones. That would also make your system much more robust towards any future hardware changes.

---

### Post by Vishal Agarwal on 2010-04-19
> **jiex said:**
> Thank you Micio and Vishal. Being new to this I'm learning how to do things so I hope I have the right information for you. This is what I found with the fdisk -ls command:
james@Ubuntu:~$ sudo fdisk -ls

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7573c67c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6079    48829536    7  HPFS/NTFS
/dev/sda2            6080      121601   927930465    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000afffd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6079    48829536   83  Linux
/dev/sdb2            6080        7295     9767520    5  Extended
/dev/sdb3            7296      121601   918162945    7  HPFS/NTFS
/dev/sdb5            6080        7295     9767488+  82  Linux swap / Solaris


Not sure whether this is what you were looking for. Thanks again to you both for taking the trouble to help me.
Jim

just use the mount command, to see the details of disk mounting. and also post it here. fdisk is a disk details util not the linux partitioning display util

---

### Post by micio on 2010-04-19
> **jiex said:**
> Thank you Micio and Vishal. Being new to this I'm learning how to do things so I hope I have the right information for you. This is what I found with the fdisk -ls command:



pls post /etc/fstab file.

Thanks

---

### Post by jiex on 2010-04-19
> **bolucpap said:**
> It seems that your Linux installation is on the second hard drive (/dev/sdb). This creates a problem when you remove the first drive, because the Linux drive now becomes the first drive (ie. /dev/sda), but the mount filesystem table (the /etc/fstab file) references your drives by paths like /dev/sdb1 instead of UUID's, which is a more robust way of specifying mount points. If you could post the output of ```
cat /etc/fstab 
``` and ```
ls -l /dev/disk/by-uuid/
``` We could be able to convert your fstab mounts to UUID based ones. That would also make your system much more robust towards any future hardware changes.

Thank you bolucpap. I appreciate the help you and everyone is giving me. I am only just learning to use the terminal. I hope this is what you were after:

Micio - is the following information what you wanted etc/fstab - I did not know how to bring that up on the terminal

james@Ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=c18b6409-d129-4363-b616-bb56638f571c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3dfc1e22-d576-49c1-8ebd-079a29ce50f7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
james@Ubuntu:~$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2010-04-19 16:59 3dfc1e22-d576-49c1-8ebd-079a29ce50f7 -> ../../sdb5
lrwxrwxrwx 1 root root 10 2010-04-19 16:59 5a807c7b-92d8-4dab-87f2-d3f6f6b46762 -> ../../sda1
lrwxrwxrwx 1 root root 10 2010-04-19 16:59 B8200862200829C8 -> ../../sdb3
lrwxrwxrwx 1 root root 10 2010-04-19 16:59 c18b6409-d129-4363-b616-bb56638f571c -> ../../sdb1

---

### Post by jiex on 2010-04-19
> **Vishal Agarwal said:**
> just use the mount command, to see the details of disk mounting. and also post it here. fdisk is a disk details util not the linux partitioning display util

Hello Vishal Thank you for taking the time to help me. This is what I got when I typed mount at the prompt in the terminal:
/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/james/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=james)

Thanks again.

---

### Post by micio on 2010-04-19
please add dmesg output :P

just a question, have you disconnected both sata cable and power cable from hdd?

---

### Post by jiex on 2010-04-19
> **micio said:**
> please add dmesg output :P

just a question, have you disconnected both sata cable and power cable from hdd?

Hello Micio.
Thanks again for all the help.

When I tried to disconnect, yes, I disconnected power and the SATA cable. I'm using the UBUNTU machine at the moment to make these posts.

I ran dmesg, and the following came up:

[    0.176850] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.176925] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
[    0.176966] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.192039] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.192107] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.192174] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.192239] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.192304] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.192370] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.192436] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.192507] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.192620] SCSI subsystem initialized
[    0.192651] libata version 3.00 loaded.
[    0.192651] usbcore: registered new interface driver usbfs
[    0.192651] usbcore: registered new interface driver hub
[    0.192651] usbcore: registered new device driver usb
[    0.192651] ACPI: WMI: Mapper loaded
[    0.192651] PCI: Using ACPI for IRQ routing
[    0.192651] pci 0000:00:00.0: BAR 3: address space collision on of device [0xe0000000-0xffffffff]
[    0.192651] pci 0000:00:00.0: BAR 3: can't allocate resource
[    0.204020] Bluetooth: Core ver 2.15
[    0.204053] NET: Registered protocol family 31
[    0.204053] Bluetooth: HCI device and connection manager initialized
[    0.204053] Bluetooth: HCI socket layer initialized
[    0.204053] NetLabel: Initializing
[    0.204053] NetLabel:  domain hash size = 128
[    0.204053] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.204053] NetLabel:  unlabeled traffic allowed by default
[    0.204070] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 24, 0
[    0.204074] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.208037] hpet: hpet2 irq 24 for MSI
[    0.220024] pnp: PnP ACPI init
[    0.220038] ACPI: bus type pnp registered
[    0.221959] pnp 00:0b: mem resource (0xcec00-0xcffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.221962] pnp 00:0b: mem resource (0xf0000-0xf7fff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.221964] pnp 00:0b: mem resource (0xf8000-0xfbfff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.221967] pnp 00:0b: mem resource (0xfc000-0xfffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.221969] pnp 00:0b: mem resource (0x0-0x9ffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.221972] pnp 00:0b: mem resource (0x100000-0xafedffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.222027] pnp: PnP ACPI: found 12 devices
[    0.222028] ACPI: ACPI bus type pnp unregistered
[    0.222031] PnPBIOS: Disabled by ACPI PNP
[    0.222038] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.222040] system 00:01: ioport range 0x220-0x225 has been reserved
[    0.222042] system 00:01: ioport range 0x290-0x294 has been reserved
[    0.222046] system 00:02: ioport range 0x4100-0x411f has been reserved
[    0.222048] system 00:02: ioport range 0x228-0x22f has been reserved
[    0.222050] system 00:02: ioport range 0x40b-0x40b has been reserved
[    0.222052] system 00:02: ioport range 0x4d6-0x4d6 has been reserved
[    0.222053] system 00:02: ioport range 0xc00-0xc01 has been reserved
[    0.222055] system 00:02: ioport range 0xc14-0xc14 has been reserved
[    0.222057] system 00:02: ioport range 0xc50-0xc52 has been reserved
[    0.222059] system 00:02: ioport range 0xc6c-0xc6d has been reserved
[    0.222061] system 00:02: ioport range 0xc6f-0xc6f has been reserved
[    0.222063] system 00:02: ioport range 0xcd0-0xcd1 has been reserved
[    0.222065] system 00:02: ioport range 0xcd2-0xcd3 has been reserved
[    0.222067] system 00:02: ioport range 0xcd4-0xcdf has been reserved
[    0.222068] system 00:02: ioport range 0x4000-0x40fe has been reserved
[    0.222070] system 00:02: ioport range 0x4210-0x4217 has been reserved
[    0.222072] system 00:02: ioport range 0xb00-0xb0f has been reserved
[    0.222074] system 00:02: ioport range 0xb10-0xb1f has been reserved
[    0.222076] system 00:02: ioport range 0xb20-0xb3f has been reserved
[    0.222081] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
[    0.222085] system 00:0b: iomem range 0xafee0000-0xafefffff could not be reserved
[    0.222087] system 00:0b: iomem range 0xffff0000-0xffffffff has been reserved
[    0.222089] system 00:0b: iomem range 0xafff0000-0xcffeffff could not be reserved
[    0.222092] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.222094] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.222096] system 00:0b: iomem range 0xfff80000-0xfffeffff has been reserved
[    0.256705] AppArmor: AppArmor Filesystem Enabled
[    0.256725] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.256727] pci 0000:00:01.0:   IO window: 0xe000-0xefff
[    0.256730] pci 0000:00:01.0:   MEM window: 0xfde00000-0xfdffffff
[    0.256733] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.256738] pci 0000:00:0a.0: PCI bridge, secondary bus 0000:02
[    0.256740] pci 0000:00:0a.0:   IO window: 0xd000-0xdfff
[    0.256742] pci 0000:00:0a.0:   MEM window: 0xfdd00000-0xfddfffff
[    0.256745] pci 0000:00:0a.0:   PREFETCH window: 0x000000fda00000-0x000000fdafffff
[    0.256748] pci 0000:00:14.4: PCI bridge, secondary bus 0000:03
[    0.256751] pci 0000:00:14.4:   IO window: 0xc000-0xcfff
[    0.256755] pci 0000:00:14.4:   MEM window: 0xfdc00000-0xfdcfffff
[    0.256759] pci 0000:00:14.4:   PREFETCH window: 0xfdb00000-0xfdbfffff
[    0.256770]   alloc irq_desc for 18 on node -1
[    0.256772]   alloc kstat_irqs on node -1
[    0.256779] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.256781] pci 0000:00:0a.0: setting latency timer to 64
[    0.256788] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.256790] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.256792] pci_bus 0000:01: resource 0 io:  [0xe000-0xefff]
[    0.256794] pci_bus 0000:01: resource 1 mem: [0xfde00000-0xfdffffff]
[    0.256796] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.256798] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
[    0.256799] pci_bus 0000:02: resource 1 mem: [0xfdd00000-0xfddfffff]
[    0.256801] pci_bus 0000:02: resource 2 pref mem [0xfda00000-0xfdafffff]
[    0.256803] pci_bus 0000:03: resource 0 io:  [0xc000-0xcfff]
[    0.256805] pci_bus 0000:03: resource 1 mem: [0xfdc00000-0xfdcfffff]
[    0.256807] pci_bus 0000:03: resource 2 pref mem [0xfdb00000-0xfdbfffff]
[    0.256809] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.256811] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.256835] NET: Registered protocol family 2
[    0.256898] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.257094] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.257460] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.257654] TCP: Hash tables configured (established 131072 bind 65536)
[    0.257655] TCP reno registered
[    0.257718] NET: Registered protocol family 1
[    0.257760] Trying to unpack rootfs image as initramfs...
[    0.395619] Freeing initrd memory: 7488k freed
[    0.397833] cpufreq-nforce2: No nForce2 chipset.
[    0.397849] Scanning for low memory corruption every 60 seconds
[    0.397912] audit: initializing netlink socket (disabled)
[    0.397922] type=2000 audit(1271660358.396:1): initialized
[    0.403852] highmem bounce pool size: 64 pages
[    0.403855] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.404683] VFS: Disk quotas dquot_6.5.2
[    0.404720] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.405080] fuse init (API version 7.12)
[    0.405127] msgmni has been set to 1638
[    0.405283] alg: No test for stdrng (krng)
[    0.405299] io scheduler noop registered
[    0.405300] io scheduler anticipatory registered
[    0.405301] io scheduler deadline registered
[    0.405328] io scheduler cfq registered (default)
[    0.540438] Switched to high resolution mode on CPU 1
[    0.544032] Switched to high resolution mode on CPU 0
[    0.544058] pci 0000:01:05.0: Boot video device
[    0.544151]   alloc irq_desc for 25 on node -1
[    0.544153]   alloc kstat_irqs on node -1
[    0.544158] pcieport-driver 0000:00:0a.0: irq 25 for MSI/MSI-X
[    0.544163] pcieport-driver 0000:00:0a.0: setting latency timer to 64
[    0.544209] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.544223] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.544302] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.544304] ACPI: Power Button [PWRF]
[    0.544335] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.544337] ACPI: Power Button [PWRB]
[    0.544561] processor LNXCPU:00: registered as cooling_device0
[    0.544589] processor LNXCPU:01: registered as cooling_device1
[    0.545966] isapnp: Scanning for PnP cards...
[    0.899527] isapnp: No Plug & Play device found
[    0.900210] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.900313] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.900548] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.901099] brd: module loaded
[    0.901346] loop: module loaded
[    0.901389] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.901427] ahci 0000:00:11.0: version 3.0
[    0.901438]   alloc irq_desc for 22 on node -1
[    0.901439]   alloc kstat_irqs on node -1
[    0.901446] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    0.901528] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    0.901530] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    0.901774] scsi0 : ahci
[    0.901852] scsi1 : ahci
[    0.901895] scsi2 : ahci
[    0.901935] scsi3 : ahci
[    0.901996] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 22
[    0.901999] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 22
[    0.902002] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 22
[    0.902004] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 22
[    0.902164]   alloc irq_desc for 16 on node -1
[    0.902165]   alloc kstat_irqs on node -1
[    0.902171] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.902250] scsi4 : pata_atiixp
[    0.902291] scsi5 : pata_atiixp
[    0.902980] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
[    0.902982] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
[    0.903373] Fixed MDIO Bus: probed
[    0.903394] PPP generic driver version 2.4.2
[    0.903457] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.903469]   alloc irq_desc for 17 on node -1
[    0.903470]   alloc kstat_irqs on node -1
[    0.903476] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.903489] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    0.903509] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    0.903535] ehci_hcd 0000:00:12.2: debug port 1
[    0.903555] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe02c000
[    0.912045] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    0.912120] usb usb1: configuration #1 chosen from 1 choice
[    0.912142] hub 1-0:1.0: USB hub found
[    0.912148] hub 1-0:1.0: 6 ports detected
[    0.912197]   alloc irq_desc for 19 on node -1
[    0.912199]   alloc kstat_irqs on node -1
[    0.912206] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.912222] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    0.912247] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    0.912274] ehci_hcd 0000:00:13.2: debug port 1
[    0.912296] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe029000
[    0.924044] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.924112] usb usb2: configuration #1 chosen from 1 choice
[    0.924129] hub 2-0:1.0: USB hub found
[    0.924135] hub 2-0:1.0: 6 ports detected
[    0.924181] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.924200] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.924216] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    0.924239] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    0.924268] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe02e000
[    0.984095] usb usb3: configuration #1 chosen from 1 choice
[    0.984115] hub 3-0:1.0: USB hub found
[    0.984123] hub 3-0:1.0: 3 ports detected
[    0.984164] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.984178] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    0.984209] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    0.984226] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe02d000
[    1.044087] usb usb4: configuration #1 chosen from 1 choice
[    1.044108] hub 4-0:1.0: USB hub found
[    1.044117] hub 4-0:1.0: 3 ports detected
[    1.044158] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.044174] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.044198] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.044227] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe02b000
[    1.064527] ata5.00: ATAPI: PIONEER DVD-RW  DVR-109, 1.17, max UDMA/66
[    1.080475] ata5.00: configured for UDMA/66
[    1.104091] usb usb5: configuration #1 chosen from 1 choice
[    1.104109] hub 5-0:1.0: USB hub found
[    1.104117] hub 5-0:1.0: 3 ports detected
[    1.104158] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.104173] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.104197] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.104214] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe02a000
[    1.164097] usb usb6: configuration #1 chosen from 1 choice
[    1.164116] hub 6-0:1.0: USB hub found
[    1.164124] hub 6-0:1.0: 3 ports detected
[    1.164165] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.164181] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.164206] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    1.164222] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe028000
[    1.220113] ata4: SATA link down (SStatus 0 SControl 300)
[    1.220141] ata3: SATA link down (SStatus 0 SControl 300)
[    1.224100] usb usb7: configuration #1 chosen from 1 choice
[    1.224118] hub 7-0:1.0: USB hub found
[    1.224126] hub 7-0:1.0: 2 ports detected
[    1.224164] uhci_hcd: USB Universal Host Controller Interface driver
[    1.224224] PNP: No PS/2 controller found. Probing ports directly.
[    1.257840] Failed to disable AUX port, but continuing anyway... Is this a SiS?
[    1.257842] If AUX port is really absent please use the 'i8042.noaux' option.
[    1.408043] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.408067] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.408730] ata1.00: ATA-8: WDC WD1001FALS-00J7B1, 05.00K05, max UDMA/133
[    1.408733] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.409541] ata1.00: configured for UDMA/133
[    1.423702] ata2.00: ATA-8: WDC WD10EARS-00Y5B1, 80.00A80, max UDMA/133
[    1.423705] ata2.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.424611] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1001FALS-0 05.0 PQ: 0 ANSI: 5
[    1.424709] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.424734] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.424757] sd 0:0:0:0: [sda] Write Protect is off
[    1.424759] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.424771] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.424846]  sda:
[    1.425863] ata2.00: configured for UDMA/133
[    1.435156]  sda1 sda2
[    1.435335] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.440601] scsi 1:0:0:0: Direct-Access     ATA      WDC WD10EARS-00Y 80.0 PQ: 0 ANSI: 5
[    1.440694] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.440719] sd 1:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.440742] sd 1:0:0:0: [sdb] Write Protect is off
[    1.440743] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.440755] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.440827]  sdb: sdb1 sdb2 <
[    1.447130] scsi 4:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-109  1.17 PQ: 0 ANSI: 5
[    1.452042] usb 3-1: new low speed USB device using ohci_hcd and address 2
[    1.453593]  sdb5 > sdb3
[    1.453803] sd 1:0:0:0: [sdb] Attached SCSI disk
[    1.465664] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    1.465668] Uniform CD-ROM driver Revision: 3.20
[    1.465739] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    1.465778] sr 4:0:0:0: Attached scsi generic sg2 type 5
[    1.508131] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.508210] mice: PS/2 mouse device common for all mice
[    1.508276] rtc_cmos 00:05: RTC can wake from S4
[    1.508300] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.508329] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.508403] device-mapper: uevent: version 1.0.3
[    1.508466] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    1.508507] device-mapper: multipath: version 1.1.0 loaded
[    1.508509] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.508585] EISA: Probing bus 0 at eisa.0
[    1.508601] Cannot allocate resource for EISA slot 4
[    1.508617] EISA: Detected 0 cards.
[    1.508661] cpuidle: using governor ladder
[    1.508663] cpuidle: using governor menu
[    1.508975] TCP cubic registered
[    1.509065] NET: Registered protocol family 10
[    1.509351] lo: Disabled Privacy Extensions
[    1.509556] NET: Registered protocol family 17
[    1.509569] Bluetooth: L2CAP ver 2.13
[    1.509570] Bluetooth: L2CAP socket layer initialized
[    1.509572] Bluetooth: SCO (Voice Link) ver 0.6
[    1.509573] Bluetooth: SCO socket layer initialized
[    1.509586] Bluetooth: RFCOMM TTY layer initialized
[    1.509588] Bluetooth: RFCOMM socket layer initialized
[    1.509589] Bluetooth: RFCOMM ver 1.11
[    1.509608] powernow-k8: Found 1 AMD Athlon(tm) II X2 245 Processor processors (2 cpu cores) (version 2.20.00)
[    1.509640] powernow-k8:    0 : pstate 0 (2900 MHz)
[    1.509641] powernow-k8:    1 : pstate 1 (2200 MHz)
[    1.509643] powernow-k8:    2 : pstate 2 (1700 MHz)
[    1.509644] powernow-k8:    3 : pstate 3 (800 MHz)
[    1.509732] Using IPI No-Shortcut mode
[    1.509811] PM: Resume from disk failed.
[    1.509820] registered taskstats version 1
[    1.509910]   Magic number: 6:491:974
[    1.509994] rtc_cmos 00:05: setting system clock to 2010-04-19 06:59:19 UTC (1271660359)
[    1.509997] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.509998] EDD information not available.
[    1.620233] usb 3-1: configuration #1 chosen from 1 choice
[    1.631143] Freeing unused kernel memory: 544k freed
[    1.631342] Write protecting the kernel text: 4604k
[    1.631394] Write protecting the kernel read-only data: 1840k
[    1.706149] Linux agpgart interface v0.103
[    1.750554] [drm] Initialized drm 1.1.0 20060810
[    1.767945] [drm] radeon default to kernel modesetting DISABLED.
[    1.768462] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.768465] pci 0000:01:05.0: setting latency timer to 64
[    1.768548] [drm] Initialized radeon 1.31.0 20080528 for 0000:01:05.0 on minor 0
[    1.770906] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.770918] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.770942] r8169 0000:02:00.0: setting latency timer to 64
[    1.770973]   alloc irq_desc for 26 on node -1
[    1.770974]   alloc kstat_irqs on node -1
[    1.770984] r8169 0000:02:00.0: irq 26 for MSI/MSI-X
[    1.771392] eth0: RTL8168c/8111c at 0xf849e000, 6c:f0:49:0a:cd:4a, XID 3c4000c0 IRQ 26
[    1.782196] ohci1394 0000:03:0e.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.785582] usbcore: registered new interface driver hiddev
[    1.785635] usbcore: registered new interface driver usbhid
[    1.785637] usbhid: v2.6:USB HID core driver
[    1.792359] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.0/input/input3
[    1.792408] logitech 0003:046D:C517.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:12.0-1/input0
[    1.800338] logitech 0003:046D:C517.0002: fixing up Logitech keyboard report descriptor
[    1.800785] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.1/input/input4
[    1.800871] logitech 0003:046D:C517.0002: input,hiddev96,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:12.0-1/input1
[    1.836563] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[fdcff000-fdcff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.589777] PM: Starting manual resume from disk
[    2.589781] PM: Resume from partition 8:21
[    2.589782] PM: Checking hibernation image.
[    2.589938] PM: Resume from disk failed.
[    2.607293] EXT4-fs (sdb1): barriers enabled
[    2.619861] kjournald2 starting: pid 447, dev sdb1:8, commit interval 5 seconds
[    2.619905] EXT4-fs (sdb1): delayed allocation enabled
[    2.619907] EXT4-fs: file extents enabled
[    2.624324] EXT4-fs: mballoc enabled
[    2.624334] EXT4-fs (sdb1): mounted filesystem with ordered data mode
[    3.108614] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00323b94006cf049]
[    3.187766] type=1505 audit(1271660361.174:2): operation="profile_load" pid=472 name=/usr/share/gdm/guest-session/Xsession
[    3.189947] type=1505 audit(1271660361.178:3): operation="profile_load" pid=473 name=/sbin/dhclient3
[    3.190147] type=1505 audit(1271660361.178:4): operation="profile_load" pid=473 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.190259] type=1505 audit(1271660361.178:5): operation="profile_load" pid=473 name=/usr/lib/connman/scripts/dhclient-script
[    3.267492] type=1505 audit(1271660361.254:6): operation="profile_load" pid=474 name=/usr/bin/evince
[    3.270719] type=1505 audit(1271660361.258:7): operation="profile_load" pid=474 name=/usr/bin/evince-previewer
[    3.272634] type=1505 audit(1271660361.262:8): operation="profile_load" pid=474 name=/usr/bin/evince-thumbnailer
[    3.284425] type=1505 audit(1271660361.270:9): operation="profile_load" pid=476 name=/usr/lib/cups/backend/cups-pdf
[    3.284673] type=1505 audit(1271660361.274:10): operation="profile_load" pid=476 name=/usr/sbin/cupsd
[    8.315049] udev: starting version 147
[    8.325007] Adding 9767480k swap on /dev/sdb5.  Priority:-1 extents:1 across:9767480k 
[    8.340993] shpchp 0000:00:01.0: HPC vendor_id 1022 device_id 9602 ss_vid 0 ss_did 0
[    8.340997] shpchp 0000:00:01.0: Cannot reserve MMIO region
[    8.341015] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    8.385931] ACPI: I/O resource piix4_smbus [0xb00-0xb07] conflicts with ACPI region SOR1 [0xb00-0xb0f]
[    8.385935] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.424209] parport_pc 00:09: reported by Plug and Play ACPI
[    8.424274] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    8.427786] ppdev: user-space parallel port driver
[    8.448377] EXT4-fs (sdb1): internal journal on sdb1:8
[    8.449576] lp: driver loaded but no devices found
[    8.469872] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.476085] ip_tables: (C) 2000-2006 Netfilter Core Team
[    8.512157] lp0: using parport0 (interrupt-driven).
[    8.538035] hda_codec: Unknown model for ALC889A, trying auto-probe from BIOS...
[    8.538234] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input5
[    8.541708] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    8.541724] HDA Intel 0000:01:05.1: setting latency timer to 64
[    9.593008] __ratelimit: 3 callbacks suppressed
[    9.593010] type=1505 audit(1271660367.582:12): operation="profile_replace" pid=993 name=/usr/share/gdm/guest-session/Xsession
[    9.593943] type=1505 audit(1271660367.582:13): operation="profile_replace" pid=994 name=/sbin/dhclient3
[    9.594142] type=1505 audit(1271660367.582:14): operation="profile_replace" pid=994 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    9.594252] type=1505 audit(1271660367.582:15): operation="profile_replace" pid=994 name=/usr/lib/connman/scripts/dhclient-script
[    9.596421] type=1505 audit(1271660367.582:16): operation="profile_replace" pid=995 name=/usr/bin/evince
[    9.599657] type=1505 audit(1271660367.586:17): operation="profile_replace" pid=995 name=/usr/bin/evince-previewer
[    9.601609] type=1505 audit(1271660367.590:18): operation="profile_replace" pid=995 name=/usr/bin/evince-thumbnailer
[    9.605575] type=1505 audit(1271660367.594:19): operation="profile_replace" pid=997 name=/usr/lib/cups/backend/cups-pdf
[    9.605815] type=1505 audit(1271660367.594:20): operation="profile_replace" pid=997 name=/usr/sbin/cupsd
[    9.606931] type=1505 audit(1271660367.594:21): operation="profile_replace" pid=998 name=/usr/sbin/tcpdump
[   10.105903] r8169: eth0: link up
[   10.105914] r8169: eth0: link up
[   16.081556] CPU0 attaching NULL sched-domain.
[   16.081561] CPU1 attaching NULL sched-domain.
[   16.100073] CPU0 attaching sched-domain:
[   16.100076]  domain 0: span 0-1 level MC
[   16.100078]   groups: 0 1
[   16.100081]   domain 1: span 0-1 level CPU
[   16.100083]    groups: 0-1 (__cpu_power = 2048)
[   16.100087] CPU1 attaching sched-domain:
[   16.100089]  domain 0: span 0-1 level MC
[   16.100090]   groups: 1 0
[   16.100092]   domain 1: span 0-1 level CPU
[   16.100094]    groups: 0-1 (__cpu_power = 2048)
[   18.246306] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   18.246310] Disabling lock debugging due to kernel taint
[   18.262370] [fglrx] Maximum main memory to use for locked dma buffers: 3358 MBytes.
[   18.262393] [fglrx]   vendor: 1002 device: 9710 count: 1
[   18.262618] [fglrx] ioport: bar 1, base 0xee00, size: 0x100
[   18.262623] pci 0000:01:05.0: setting latency timer to 64
[   18.262867] [fglrx] Kernel PAT support is enabled
[   18.262885] [fglrx] module loaded - fglrx 8.69.4 [Dec 11 2009] with 1 minors
[   18.925755] [fglrx] GART Table is not in FRAME_BUFFER range 
[   18.925916]   alloc irq_desc for 27 on node -1
[   18.925919]   alloc kstat_irqs on node -1
[   18.925926] fglrx_pci 0000:01:05.0: irq 27 for MSI/MSI-X
[   18.926343] [fglrx] Firegl kernel thread PID: 1655
[   19.324282] [fglrx] Gart USWC size:1096 M.
[   19.324285] [fglrx] Gart cacheable size:435 M.
[   19.324290] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   19.324292] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000 
[   20.300017] eth0: no IPv6 routers present
[   20.573817] CPU0 attaching NULL sched-domain.
[   20.573821] CPU1 attaching NULL sched-domain.
[   20.588571] CPU0 attaching sched-domain:
[   20.588575]  domain 0: span 0-1 level MC
[   20.588577]   groups: 0 1
[   20.588581] CPU1 attaching sched-domain:
[   20.588583]  domain 0: span 0-1 level MC
[   20.588584]   groups: 1 0
[   22.524510] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
james@Ubuntu:~$

---

### Post by micio on 2010-04-19
Please we have to make the point of situation...

from this piece of log

```
[ 1.408043] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 1.408067] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 1.408730] ata1.00: ATA-8: WDC WD1001FALS-00J7B1, 05.00K05, max UDMA/133
[ 1.408733] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[ 1.409541] ata1.00: configured for UDMA/133
[ 1.423702] ata2.00: ATA-8: WDC WD10EARS-00Y5B1, 80.00A80, max UDMA/133
[ 1.423705] ata2.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
```

both sata disk are recognized and no errors are reported...
So it seems that you have both connected...

now.. your problem is that when you disconnect the second disk the system remain on ubuntu logo for a lot of time? (as it would mount a disk that really is not there)

I'm just loosing :P

---

### Post by mick222 on 2010-04-19
When you reboot with only 1 drive if you get to grub try editing the grub entry select it then press e. Where it says set root=(hdd1,1)or similar change the firs number to 0 then press  ctrl x to boot. If that works update grub in the terminal
[PHP]sudo update-grub2[/PHP]
that should sort it.
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
This might help as well.

---

### Post by jiex on 2010-04-19
> **mick222 said:**
> When you reboot with only 1 drive if you get to grub try editing the grub entry select it then press e. Where it says set root=(hdd1,1)or similar change the firs number to 0 then press  ctrl x to boot. If that works update grub in the terminal
[PHP]sudo update-grub2[/PHP]
that should sort it.
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
This might help as well.

Success!
First of all, thank you to everyone who helped me here: Micio, Vishal, bolucpap, and Mick222. I have learnt so much today and lost, a little, my fear of the terminal!
Also, UBUNTU was recommended to me because the help forums were friendly and tolerant of a computing cretin like me. And you were. Many thanks.
The initial diagnosis by bolucpap as quite right. I do not know how I managed to muck up the installation.
This is what I did - following Mick222's advice:
1. I powered down and disconnected the drive I want to remove.
2. I powered up and GRUM appeared. I hit "e" and entered the editing mode.
3. As per Mick222's advice I changed the first number. This sis not work. So then I changed the letter from "b" to "a". 
4. Pressed ctrl-x and booted up.
5. I then entered terminal and entered "sudo update-grub2", as per Mick222's advice. 
6. I then went into terminal again and did "sudo fdisk -ls" and saw a single HDD and this was listed:
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000afffd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6079    48829536   83  Linux
/dev/sda2            6080        7295     9767520    5  Extended
/dev/sda3            7296      121601   918162945    7  HPFS/NTFS
/dev/sda5            6080        7295     9767488+  82  Linux swap / Solaris

Thank you to everyone who helped me out in this. Much appreciated. You have all been so patient and I really appreciate it.
Warm regards
Jim

---

### Post by mick222 on 2010-04-19
See the link i gave you it tells you how to mount the partition by uuid which should save trouble if you swap drives again. I havn't tried this myself by the way . I just usually edit grub if i swap hard drives.

---

