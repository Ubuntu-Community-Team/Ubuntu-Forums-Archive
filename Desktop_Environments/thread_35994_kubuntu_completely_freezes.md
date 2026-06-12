---
title: "kubuntu completely freezes"
date: 2005-05-21
forum: Desktop Environments
---

### Post by Redsun on 2005-05-21
Hi. Got a big problem here.

I installed kubuntu today. From what I've seen, I kinda like it. But then it has begun to systematically and completely freeze. After I log in, sooner or later, sometimes two minutes thereafter, sometimes up to ten, the system gets utterly frozen. No mouse nor keyboard response. Ctrl-alt-del or ctrl-alt-F1 won't change a thing, and the only option is to hit the reset button.

The problem got worse in time, and I think it has aroused after I completely upgraded all the packages via kynaptic. Could be the problem was there even before.

Btw, at first I had display problems (the background and at times even the content of windows was all messy), solved installing the nvidia drivers.

I'm writing this in text mode, so I have plenty of time, then I will start kde, and copy&paste it: I've already tried once to write this post but the system froze before I could post.

Now, I'm not a complete newbie, but almost, so treat me like one:

First of all, knowing the problem could be anything, what I ask for is please tell me how can I diagnose the problem here? If some of you could kindly help me, just ask what I should provide in order to make out this situation.

Just in case it could be useful, I post the kilometric results of ps axu and dmesg. I have noted that there's a process, "gpg-agent etc..", that strangely lingers and sits there indefinitely even after I log out (I've seen it logging in as root after ctrl-alt-F1 and monitoring from there my graphical login as jinko). However prematurely killing that process didn't prevent the system from freezing, but I'm telling you just in case.

```
jinko@reborn:~$ ps axu
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   2656   548 ?        S    16:24   0:00 init [2]
root         2  0.0  0.0      0     0 ?        SN   16:24   0:00 [ksoftirqd/0]
root         3  0.0  0.0      0     0 ?        S<   16:24   0:00 [events/0]
root         4  0.0  0.0      0     0 ?        S<   16:24   0:00 [khelper]
root        16  0.0  0.0      0     0 ?        S<   16:24   0:00 [kacpid]
root       138  0.0  0.0      0     0 ?        S<   16:24   0:00 [kblockd/0]
root       146  0.0  0.0      0     0 ?        S    16:24   0:00 [khubd]
root       187  0.0  0.0      0     0 ?        S    16:24   0:00 [pdflush]
root       188  0.0  0.0      0     0 ?        S    16:24   0:00 [pdflush]
root       190  0.0  0.0      0     0 ?        S<   16:24   0:00 [aio/0]
root       189  0.0  0.0      0     0 ?        S    16:24   0:00 [kswapd0]
root       777  0.0  0.0      0     0 ?        S    16:24   0:00 [kseriod]
root      1143  0.0  0.0      0     0 ?        S    16:24   0:00 [kjournald]
root      1168  0.0  0.0   2628   496 ?        S<s  16:24   0:00 udevd
root      2333  0.0  0.0      0     0 ?        S    16:24   0:00 [khpsbpkt]
root      2635  0.0  0.0      0     0 ?        S    16:24   0:00 [kjournald]
root      3162  0.0  0.0      0     0 ?        S    16:24   0:00 [shpchpd_event]
root      3538  0.0  0.0      0     0 ?        S    16:24   0:00 [knodemgrd_0]
root      3621  0.0  0.0      0     0 ?        S<   16:24   0:00 [ata/0]
root      3625  0.0  0.0      0     0 ?        S    16:24   0:00 [scsi_eh_0]
root      3626  0.0  0.0      0     0 ?        S    16:24   0:00 [scsi_eh_1]
root      5349  0.0  0.0      0     0 ?        S    16:24   0:00 [eth0]
root      6565  0.0  0.1   4548  1260 ?        S<s  16:24   0:00 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/run/dhcli
syslog    6907  0.0  0.0   6952   804 ?        Ss   16:24   0:00 /sbin/syslogd -u syslog
root      6922  0.0  0.0   2652   412 ?        Ss   16:24   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      6924  0.0  0.1   4032  1972 ?        Ss   16:24   0:00 /sbin/klogd -P /var/run/klogd/kmsg
cupsys    6951  0.0  0.3  25284  3284 ?        Ss   16:24   0:00 /usr/sbin/cupsd -F
root      7276  0.0  0.0   2908   948 ?        Ss   16:24   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socke
102       7288  0.0  0.1   8404  1084 ?        Ss   16:24   0:00 /usr/bin/dbus-daemon-1 --system
hal       7300  0.1  0.8  22844  8572 ?        Ss   16:24   0:00 /usr/sbin/hald --drop-privileges
root      7313  0.0  0.0   2644   448 ?        Ss   16:24   0:00 /usr/sbin/inetd
root      7528  0.0  0.1  15480  1360 ?        Ss   16:24   0:00 /usr/lib/postfix/master
postfix   7543  0.0  0.1  16508  1272 ?        S    16:24   0:00 pickup -l -t fifo -u -c
postfix   7544  0.0  0.1  16548  1316 ?        S    16:24   0:00 qmgr -l -t fifo -u -c
root      7709  0.0  0.0   2636   516 ?        SNs  16:24   0:00 /usr/sbin/powernowd -q
root      7722  0.0  0.0  11004   864 ?        Ss   16:24   0:00 /usr/bin/kdm
root      7735  0.9  1.8  36460 18812 ?        SL   16:24   0:04 /usr/X11R6/bin/X -nolisten tcp :0 vt7 -auth /var/run/xauth/
root      7737  0.0  0.1  23920  1508 ?        S    16:24   0:00 -:0
daemon    7749  0.0  0.0   6936   700 ?        Ss   16:24   0:00 /usr/sbin/atd
root      7764  0.0  0.0   9052   908 ?        Ss   16:24   0:00 /usr/sbin/cron
root      7820  0.0  0.0   2652   504 tty2     Ss+  16:25   0:00 /sbin/getty 38400 tty2
root      7821  0.0  0.0   2652   504 tty3     Ss+  16:25   0:00 /sbin/getty 38400 tty3
root      7822  0.0  0.0   2652   504 tty4     Ss+  16:25   0:00 /sbin/getty 38400 tty4
root      7823  0.0  0.0   2652   504 tty5     Ss+  16:25   0:00 /sbin/getty 38400 tty5
root      7824  0.0  0.0   2652   504 tty6     Ss+  16:25   0:00 /sbin/getty 38400 tty6
root      7970  0.0  0.0   2652   504 tty1     Ss+  16:31   0:00 /sbin/getty 38400 tty1
jinko     8026  0.1  0.1   7212  1500 ?        Ss   16:31   0:00 /bin/sh /usr/bin/x-session-manager
jinko     8068  0.0  0.0  10864   876 ?        Ss   16:31   0:00 gpg-agent --daemon
jinko     8071  0.0  0.1  11604  1184 ?        Ss   16:31   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session
jinko     8074  0.0  0.0   8900   836 ?        S    16:31   0:00 /usr/bin/dbus-launch --exit-with-session x-session-manager
jinko     8075  0.0  0.0   5220   780 ?        Ss   16:31   0:00 dbus-daemon-1 --fork --print-pid 8 --print-address 6 --sess
jinko     8098  0.2  1.3  67932 14300 ?        Ss   16:31   0:00 kdeinit Running...
jinko     8101  0.0  1.2  66456 12452 ?        S    16:31   0:00 dcopserver [kdeinit] dcopserver --nosid
jinko     8103  0.0  1.3  68792 13664 ?        S    16:31   0:00 klauncher [kdeinit] klauncher
jinko     8106  0.6  1.9 103420 19748 ?        S    16:31   0:00 kded [kdeinit] kded
jinko     8108  0.0  0.1   9324  1948 ?        S    16:31   0:00 /usr/lib/gamin/gam_server
jinko     8114  0.2  1.6  74128 17108 ?        S    16:31   0:00 kaccess [kdeinit] kaccess
jinko     8118  1.0  1.0  64624 10924 ?        S    16:31   0:00 /usr/bin/artsd -F 10 -S 4096 -s 60 -m artsmessage -c drkonq
jinko     8119  0.0  0.0   2632   372 ?        S    16:31   0:00 kwrapper ksmserver
jinko     8121  0.2  1.6  77444 17400 ?        S    16:31   0:00 ksmserver [kdeinit] ksmserver
jinko     8122  0.5  1.9  88004 19752 ?        S    16:31   0:00 kwin [kdeinit] kwin -session 10e4d3626f00011166750230000022
jinko     8124  0.6  2.1  89656 21872 ?        S    16:31   0:00 kdesktop [kdeinit] kdesktop
jinko     8126  0.8  2.3 101296 23920 ?        S    16:31   0:00 kicker [kdeinit] kicker
jinko     8128  0.5  1.8  84716 18596 ?        S    16:31   0:00 klipper [kdeinit] klipper
jinko     8130  0.0  1.4  74696 15088 ?        S    16:31   0:00 kio_file [kdeinit] kio_file file /tmp/ksocket-jinko/klaunch
jinko     8132  0.4  2.1  90224 22324 ?        S    16:31   0:00 kmix [kdeinit] kmix -session 10d8cecf9600011106545810000006
jinko     8135  0.3  2.2 105148 23188 ?        S    16:31   0:00 knotify [kdeinit] knotify
jinko     8136  0.3  1.9  86144 19840 ?        S    16:31   0:00 kio_uiserver [kdeinit] kio_uiserver
jinko     8137  0.0  1.5  75552 15580 ?        S    16:31   0:00 kio_trash [kdeinit] kio_trash trash /tmp/ksocket-jinko/klau
jinko     8139  0.9  2.0  91116 21360 ?        S    16:31   0:00 konsole [kdeinit] konsole
jinko     8140  0.0  0.1  11700  2024 pts/1    Ss   16:31   0:00 /bin/bash
jinko     8149  2.0  2.9 225476 30592 ?        Sl   16:31   0:00 /usr/lib/mozilla-firefox/firefox-bin -a firefox
jinko     8169  0.0  0.2  25500  2788 ?        S    16:31   0:00 /usr/lib/gconf2/gconfd-2 9
jinko     8178  0.0  0.1  10236  1160 pts/1    R+   16:31   0:00 ps axu

```

```
jinko@reborn:~$ dmesg
0 - 000000003fef0000 (ACPI data)
 BIOS-e820: 000000003fef0000 - 000000003ff00000 (reserved)
 BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
 BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
 BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
 BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
No mptable found.
On node 0 totalpages: 261856
  DMA zone: 4096 pages, LIFO batch:1
  Normal zone: 257760 pages, LIFO batch:16
  HighMem zone: 0 pages, LIFO batch:1
ACPI: RSDP (v000 K8T890                                ) @ 0x00000000000f7b90
ACPI: RSDT (v001 K8T890 AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003fee3040
ACPI: FADT (v001 K8T890 AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003fee30c0
ACPI: MCFG (v001 K8T890 AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003feea840
ACPI: MADT (v001 K8T890 AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003feea780
ACPI: DSDT (v001 K8T890 AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x0000000000000000
ACPI: Local APIC address 0xfee00000
ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Processor #0 15:15 APIC version 16
ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
ACPI: IOAPIC (id[0x03] address[0xfecc0000] gsi_base[24])
IOAPIC[1]: apic_id 3, version 3, address 0xfecc0000, GSI 24-47
ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
ACPI: IRQ0 used by override.
ACPI: IRQ2 used by override.
ACPI: IRQ9 used by override.
Setting APIC routing to flat
Using ACPI (MADT) for SMP configuration information
Checking aperture...
CPU 0: aperture @ fec0000000 size 128 MB
Aperture from northbridge cpu 0 beyond 4GB. Ignoring.
AGP bridge at 00:00:00
Aperture from AGP @ c0000000 size 128 MB (APSIZE f20)
Built 1 zonelists
Kernel command line: root=/dev/hda6 ro console=tty0 quiet splash
Initializing CPU#0
PID hash table entries: 4096 (order: 12, 131072 bytes)
time.c: Using 1.193182 MHz PIT timer.
time.c: Detected 2000.126 MHz processor.
Console: colour VGA+ 80x25
Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
Memory: 1023568k/1047424k available (1585k kernel code, 23132k reserved, 1008k data, 132k init)
Calibrating delay loop... 3915.77 BogoMIPS (lpj=1957888)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 256 (order: 0, 4096 bytes)
CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
CPU: L2 Cache: 512K (64 bytes/line)
CPU: AMD Athlon(tm) 64 Processor 3200+ stepping 00
ACPI: Looking for DSDT in initrd... not found!
Using local APIC NMI watchdog using perfctr0
Using local APIC timer interrupts.
Detected 12.500 MHz APIC timer.
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
NET: Registered protocol family 16
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter enabled
ACPI: Using IOAPIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
PCI: Via IRQ fixup
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEXG._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 10 *11 12)
ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 11 12) *5
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 *11 12)
ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *0, disabled.
ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
ACPI: PCI Interrupt Link [LNK1] (IRQs *3 4 6 7 10 11 12)
ACPI: PCI Interrupt Link [ALKA] (IRQs *20)
ACPI: PCI Interrupt Link [ALKB] (IRQs *21)
ACPI: PCI Interrupt Link [ALKC] (IRQs *22)
ACPI: PCI Interrupt Link [ALKD] (IRQs *23), disabled.
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 16 devices
usbcore: registered new driver usbfs
usbcore: registered new driver hub
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to bjorn.helgaas@hp.com
** so I can fix the driver.
agpgart: Detected AGP bridge 0
agpgart: Maximum main memory to use for agp memory: 940M
agpgart: AGP aperture is 128M @ 0xc0000000
PCI-DMA: Disabling IOMMU.
pnp: 00:00: ioport range 0x4000-0x407f could not be reserved
pnp: 00:00: ioport range 0x5000-0x500f has been reserved
IA32 emulation $Id: sys_ia32.c,v 1.32 2002/03/24 13:02:28 ak Exp $
audit: initializing netlink socket (disabled)
audit(1116692671.219:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
Linux agpgart interface v0.100 (c) Dave Jones
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
NET: Registered protocol family 2
IP: routing cache hash table of 8192 buckets, 64Kbytes
TCP: Hash tables configured (established 262144 bind 65536)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, khubd not stopped
 Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices:
PCI0 USB0 USB1 USB2 USB3 USB4 USB5 USB6 AC97 PEXG PEX0 PEX1 PEX2 PEX3 UAR1
ACPI: (supports S0 S1 S3 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 3988KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 132k freed
ACPI: Fan [FAN] (on)
ACPI: Thermal Zone [THRM] (35 C)
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
VP_IDE: IDE controller at PCI slot 0000:00:0f.1
ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
ACPI: PCI interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 20
VP_IDE: chipset revision 6
VP_IDE: not 100% native mode: will probe irqs later
VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
    ide0: BM-DMA at 0xcc00-0xcc07, BIOS settings: hda:DMA, hdb:pio
    ide1: BM-DMA at 0xcc08-0xcc0f, BIOS settings: hdc:DMA, hdd:DMA
Probing IDE interface ide0...
hda: Maxtor 6Y200P0, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 1024KiB
hda: 398297088 sectors (203928 MB) w/7936KiB Cache, CHS=24792/255/63, UDMA(133)
hda: cache flushes supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 p6 p7 p8 >
Probing IDE interface ide1...
hdc: PIONEER DVD-RW DVR-109, ATAPI CD/DVD-ROM drive
hdd: PLEXTOR CD-R PX-W1210A, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ===|
Freeing memory... done (515 pages freed)
Restarting tasks... done
EXT3-fs: INFO: recovery required on readonly filesystem.
EXT3-fs: write access will be enabled during recovery.
kjournald starting.  Commit interval 5 seconds
EXT3-fs: recovery complete.
EXT3-fs: mounted filesystem with ordered data mode.
Adding 1028120k swap on /dev/hda8.  Priority:-1 extents:1
EXT3 FS on hda6, internal journal
hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2000kB Cache
Uniform CD-ROM driver Revision: 3.20
hdd: ATAPI 32X CD-ROM CD-R/RW drive, 2048kB Cache
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
input: ImPS/2 Logitech Wheel Mouse on isa0060/serio1
Real Time Clock Driver v1.12
ieee1394: Initialized config rom entry `ip1394'
SCSI subsystem initialized
sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
ts: Compaq touchscreen protocol output
nvidia: module license 'NVIDIA' taints kernel.
ACPI: PCI interrupt 0000:02:00.0[A] -> GSI 24 (level, low) -> IRQ 24
PCI: Setting latency timer of device 0000:02:00.0 to 64
NVRM: loading NVIDIA Linux x86_64 NVIDIA Kernel Module  1.0-7174  Tue Mar 22 06:45:40 PST 2005
NVRM: WARNING: Your Linux kernel has problems in its implementation of
NVRM: the change_page_attr kernel interface.  The NVIDIA kernel
NVRM: module will attempt to work around these problems, but
NVRM: system stability may be affected.  It is recommended that
NVRM: you update to a 2.6.11 or newer kernel.

Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: dm-devel@redhat.com
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hda7, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
input: PC Speaker
inserting floppy driver for 2.6.10-5-amd64-generic
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
ACPI: PCI interrupt 0000:00:08.0[A] -> GSI 16 (level, low) -> IRQ 16
ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[d8024000-d80247ff]  Max Packet=[2048]
8139too Fast Ethernet driver 0.9.27
ACPI: PCI interrupt 0000:00:0c.0[A] -> GSI 17 (level, low) -> IRQ 17
8139too: 0000:00:0c.0: unknown chip version, assuming RTL-8139
8139too: 0000:00:0c.0: TxConfig = 0x0
eth0: RealTek RTL8129 at 0xffffff0000158000, 00:a0:d2:04:1a:17, IRQ 17
eth0:  Identified 8139 chip type 'RTL-8139'
eth0: MII transceiver 1 status 0x7829 advertising 01e1.
libata version 1.10 loaded.
sata_via version 1.1
ACPI: PCI interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 20
sata_via(0000:00:0f.0): routed to hard irq line 4
ata1: SATA max UDMA/133 cmd 0xB400 ctl 0xB802 bmdma 0xC400 irq 20
ata2: SATA max UDMA/133 cmd 0xBC00 ctl 0xC002 bmdma 0xC408 irq 20
ata1: no device found (phy stat 00000000)
scsi0 : sata_via
ata2: no device found (phy stat 00000000)
scsi1 : sata_via
USB Universal Host Controller Interface driver v2.2
ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
ACPI: PCI interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.0: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
uhci_hcd 0000:00:10.0: irq 21, io base 0xd000
uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.1: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
uhci_hcd 0000:00:10.1: irq 21, io base 0xd400
uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
uhci_hcd 0000:00:10.2: irq 21, io base 0xd800
uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.3: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#4)
uhci_hcd 0000:00:10.3: irq 21, io base 0xdc00
uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 21
ehci_hcd 0000:00:10.4: VIA Technologies, Inc. USB 2.0
ehci_hcd 0000:00:10.4: irq 21, pci mem 0xd8026000
ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
ehci_hcd 0000:00:10.4: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 5-0:1.0: USB hub found
hub 5-0:1.0: 8 ports detected
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d8000014c250]
via82xx: Assuming DXS channels with 48k fixed sample rate.
         Please try dxs_support=1 or dxs_support=4 option
         and report if it works on your machine.
ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
ACPI: PCI interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 22
PCI: Setting latency timer of device 0000:00:11.5 to 64
eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
NET: Registered protocol family 17
NET: Registered protocol family 10
Disabled Privacy Extensions on device ffffffff80350ec0(lo)
IPv6 over IPv4 tunneling driver
ACPI: Power Button (FF) [PWRF]
ibm_acpi: ec object not found
powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.00.09e)
powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x6 (1400 mV)
powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x8 (1350 mV)
powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12 (1100 mV)
cpu_init done, current fid 0xc, vid 0x6
eth0: no IPv6 routers present

```

Many many heartfelt thanks to any of you who will help me out. I'll check this thread out tomorrow.

Cheers from Rome!!

---

### Post by GeneralZod on 2005-05-21
> **Redsun]Hi. Got a big problem here.

I installed kubuntu today. From what I've seen, I kinda like it. But then it has begun to systematically and completely freeze. After I log in, sooner or later, sometimes two minutes thereafter, sometimes up to ten, the system gets utterly frozen. No mouse nor keyboard response. Ctrl-alt-del or ctrl-alt-F1 won't change a thing, and the only option is to hit the reset button.
[/QUOTE]

Ouch - that's a nasty one :( It's extremely rare for Linux to lock-up completely, and when it does it is usually either the Kernel (very rare) or X (rare, but not as rare as with the Kernel).  Annoyingly, X also controls the keyboard so if X locks up, the only way to restart is to reset *or* log in from another PC using ssh.  If you are able to do this, then it is probably X at fault rather than the kernel.

> 
The problem got worse in time, and I think it has aroused after I completely upgraded all the packages via kynaptic. Could be the problem was there even before.


I'm willing to bet that this wasn't the problem said:**
> 
Btw, at first I had display problems (the background and at times even the content of windows was all messy), solved installing the nvidia drivers.


Alarm bells ringing! ;) Sounds like it's probably X.  Do you have Windows installed on this computer, and if so, does it crash or perhaps blank the screen every so often? If so, it's almost certainly your graphics card; if not - I'm not sure :(
> 
```

I'm writing this in text mode, so I have plenty of time, then I will start kde, and copy&paste it: I've already tried once to write this post but the system froze before I could post.

```


You might want to try out the "links/elinks" browsers, so you can post to the ubuntuforums entirely from text mode :)  sudo apt-get install links

> 
Now, I'm not a complete newbie, but almost, so treat me like one:

First of all, knowing the problem could be anything, what I ask for is please tell me how can I diagnose the problem here? If some of you could kindly help me, just ask what I should provide in order to make out this situation.

Just in case it could be useful, I post the kilometric results of ps axu and dmesg. I have noted that there's a process, "gpg-agent etc..", that strangely lingers and sits there indefinitely even after I log out (I've seen it logging in as root after ctrl-alt-F1 and monitoring from there my graphical login as jinko). However prematurely killing that process didn't prevent the system from freezing, but I'm telling you just in case.


gpg-agent is a key-handler for gpg, the encryption/ signing utility.  I'm 99.9% sure that's not your problem.

> 
<snipped> :logs


I'm not knowledgeable enough to try and debug the logs, alas, but I notice that there is an nVidia-related warning which you might want to look into.  You might want to post your X log, also.

---

### Post by vanaedium on 2005-05-21
the only reason is the X server:
if you have installed the nvidia drivers is a good thing to disable render acceleration 3d
Go to /etc/X11/xorg.conf with root permissions
and go to the line
RenderAccel=true 
and change with false
If you are a game player you have to use gnome because there the 3d acceleration works fine but in Kubuntu is already unsolved.
I think is a problem with kde 3.4, we all are waiting a new release like 3.4.1   :roll:

---

### Post by Redsun on 2005-05-22
Here I am. Really really thanks for the replies.

So, now I'm posting with links, that's cool. Unfortunately I didn't find the acceleration option. I'd post the xorg.conf, but don't now how to do it with links :)

A little update: I was fiddling in text mode, however leaving the login screen (and so kdm) open. The system froze, but the last desperate message he gave was a lot of messy commands enclosed in brackets and a last message that was something like "kernel panic: Aiee! closing interrupt handler".

Now, while writing I'm running apt-get install gnome (god bless broad band), I'll see if there's no problem with that one. However I must admit I prefer kde. How could I disable hardware acceleration in kde? Maybe disabling loading of glx module?

One other thing. The warning in dmesg says I should upgrade to a new version of the kernell... I think I would be ale to do it, I've done kernel compiling with FC3 a couple of times. Should I do it just to try?

Thanks again for your help, it was greatly appreciated!

---

### Post by GeneralZod on 2005-05-22
[QUOTE=Redsun]Here I am. Really really thanks for the replies.


Now, while writing I'm running apt-get install gnome (god bless broad band), I'll see if there's no problem with that one. However I must admit I prefer kde. How could I disable hardware acceleration in kde? Maybe disabling loading of glx module?
[/QUOTE]

Sounds like you've narrowed it down a bit :) If your xorg.conf contains any references to enabling Composite or switching on RenderAccel, I'd remove them, although RenderAccel has never caused me any problems with my nvidia card.  Make a backup before you experiment, though ;) Other things that you might want to tweak are "dri", "glx" and "GLcore", but I'm really pushing the limits of my knowledge here ;)  That's the best advice I can give you, I'm afraid, so I'll leave it to others mor qualified to guide you :)

Edit:

About the kernel - there's a 2.6.11 (?) version in one of the repositories, but I'm not sure which one.  This will enable you to install it with a couple of mouse-clicks, which is handy.  I tried it myself, but apparently the Synaptic touch-pad driver for my laptop is broken in that kernel version, so I ended up reverting.

Edit2:

Oh, silly me - try setting the driver back from "nvidia" to just "nv", as well!

---

### Post by aramazan on 2005-05-22
[QUOTE=Redsun]But then it has begun to systematically and completely freeze. After I log in, sooner or later, sometimes two minutes thereafter, sometimes up to ten, the system gets utterly frozen. No mouse nor keyboard response. Ctrl-alt-del or ctrl-alt-F1 won't change a thing, and the only option is to hit the reset button.[/QUOTE]Though you're apparently running amd64-generic kernel, this looks similar to: [https://bugzilla.ubuntu.com/show_bug.cgi?id=10668](https://bugzilla.ubuntu.com/show_bug.cgi?id=10668)
So could you install ksensors (universe) and kicker-applets packages ans run ksensors in a small sticky window showing CPU frequency, and run the KDE panel applet "System Monitor" with 100 ms refresh periods?
Perhaps you're freezing while powernowd is switching CPU freq, like me. If so, just do "sudo chmod -x /etc/init.d/powernowd" and reboot. (Also report this in the bug report page above, please, so that it gets better attention :)

HTH & best regards

---

### Post by Redsun on 2005-05-22
Okay, here I am again. Gnome gives the same problem. First I thought it was beacause it was still wrapped in kdm, so I apt-got gdm, and tried both kde wrapped in gdm and gnome-gdm, but the system keeps freezing.

Answering to a point I forgot before: yes, I also have windows xp installed, no problems yet, I'm posting from it now, so the video card should be allright.

@aramazen: I'm going to try what you say now. However the timings of our problems are quite different. My system doesn't last more than 5-10 minutes... :( I'll see what I get. Relating to it, a thought passing through my mind: could it be that the AMD-cool&quiet option being enabled in BIOS is involved? I'll try that option too...

If fiddling with powernowd will give no results I'll try upgrading the kernel. If still unsuccessful, I'll try tweaking nvidia drivers....

---

### Post by Redsun on 2005-05-22
Dear aramazan, I'm thinking you hit the spot. I did chmod -x /etc/init.d/powernowd and system seems stable. Well, heck, considering it always took at most ten minutes for the kernel to panick, I'd say I'm quite sure now the system is stable now.

I'm going to update your bug report.

Btw, what are the consequences of this solution? If I understood correctly, now my AMD 64 3200+ will run constantly at 2000 mhz, instead of keeping quiet at 1000 and jump up at 2000 when needed,,, is this it? If this is the case, is it harmful in any way? (btw in this session at startup I got a "sensors failed to initialize", and ksensors will exit immediately)

---

### Post by aramazan on 2005-05-22
[QUOTE=Redsun]I'm going to update your bug report.[/QUOTE]I'm glad that your problem is solved. Well, partly... :)
> 
Btw, what are the consequences of this solution? If I understood correctly, now my AMD 64 3200+ will run constantly at 2000 mhz, instead of keeping quiet at 1000 and jump up at 2000 when needed,,, is this it? If this is the case, is it harmful in any way? (btw in this session at startup I got a "sensors failed to initialize", and ksensors will exit immediately)I think so, too. But the processor is designed to run at full speed continuously, and PowerNow! is a bonus. However this may not be the case for laptops. They usually take this "bonus" as a design parameter, so a full-throttle CPU may cause over-spec heating on laptops. (I gather that your machine doesn't look like a laptop.)

As stated in the bug report, I experience freeze only on amd64-k8 kernel and powernowd pair. Problem goes away if I stop powernowd or use amd64-generic kernel (which I do). As this is such a marginal bug, I suspect trying different kernels / powernowd versions might solve your problem too.

BTW I have a VIA K8M800 and you have a VIA K8T890 chipset. Same family. Could be a chipset specific bug?

As for ksensors, I don't know. It works without problems here.

Best regards,

---

### Post by speedsix on 2005-05-31
I have the exact same problem, A64 3000+ with default Kubuntu kernel.

Have just done the chmod powersaved and not a single lockup yet, would usually go with 10mins or so. Ubuntu would crash alot more frequently than Kubuntu mind, wierd.

Can someone tell me how I add comments to bugzilla?

Thanks alot!

---

### Post by speedsix on 2005-05-31
Kubuntu seemed to run fine for quite a while so I decided to try Ubuntu again, I did the chmod on powersave but it still locks up frequently. Most of the time it's cligging dragging the mouse, last crash I was resizing a column.

Tbh just about to give up with K/Ubuntu. :(

Dom

---

### Post by speedsix on 2005-05-31
I can replicate the freeze everytime now;

Go into Synaptic package manager
Move mouse over one of the column's edges until the double arrow appears
Resize it back and forth, several seconds later it will freeze.

---

### Post by simianMiscreant on 2005-06-04
I have this exact same problem. 

[http://ubuntuforums.org/showthread.php?t=39158&](http://ubuntuforums.org/showthread.php?t=39158&)

---

### Post by simianMiscreant on 2005-06-06
My fix is here:

[http://ubuntuforums.org/showthread.php?p=201964](http://ubuntuforums.org/showthread.php?p=201964)

---

### Post by tommyhot on 2007-04-20
I have exactly the same problem on Kubuntu as well as on Ubuntu both versions 6.06, 6.10 and 7.04. I have Athlon 3000+ and 1.5GB RAM (512 + 1024). If i leave only 512MB RAM in my pc, it works, but if there is more than 512MB it just freezes. Of course where there's not the powenowd running, or any other daemon that scales cpu frequency it goes well. It seems to me that it freezes on every distro (not just debian based) that has daemons to scale the cpu frequency.

---

