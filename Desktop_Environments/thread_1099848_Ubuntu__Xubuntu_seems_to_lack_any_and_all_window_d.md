---
title: "Ubuntu / Xubuntu seems to lack any and all window decorations"
date: 2009-03-18
forum: Desktop Environments
---

### Post by dented42 on 2009-03-18
I have an iMac g3 running Xubuntu/Ubuntu 8.10
Everything sems to be working fine, excepting the fact that all windows are borderless (actually for some of them I can see window decorations, but the disappear in under .4 seconds).  Also, Windows tend to maximize themselves by default.

I initially installed Xubuntu on the machine, and after some initial problems, everything seemed to work fine.  But when I connected to the internet, I did what I normally do, and go on a repository binge.  that is when the problems began.  I know for sure that I installed 'ubuntu-desktop' and many things related to 'ubuntu-mobile' and 'Sugar' because they seemed interesting.  I know I did more than that, but the details are a bit fuzzy.

Did I do a bad thing?  How can I fix it?

---

### Post by .:Justus:. on 2009-03-18
Press alt-f2 and type xfwm4 --replace.
This is only if you´re using xubuntu. Ubuntu uses a different window manager i think.

---

### Post by dented42 on 2009-03-18
> **.:Justus:. said:**
> Press alt-f2 and type xfwm4 --replace.
This is only if you´re using xubuntu. Ubuntu uses a different window manager i think.

I tried that, and the windows flickered hopefully, but I still have no window decorations, both in xfce and GNOME.  Just for kicks, I tried the same thing with metacity as well. But those were both while in xfce, I have yet to try either of those in GNOME.

---

### Post by dented42 on 2009-03-20
I've begun to go through my history in synaptic package manager, and have started undoing my changes, but I'm not sure if that will help.  will it?

---

### Post by dented42 on 2009-03-20
Here are some of the system logs that look like they might be related to the problem:

/var/log/user.log
```
Mar 20 11:30:53 sclinux pulseaudio[5142]: ltdl-bind-now.c: Failed to find original dlopen loader.
Mar 20 11:30:53 sclinux pulseaudio[5144]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Mar 20 11:30:53 sclinux pulseaudio[5144]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Mar 20 11:31:11 sclinux pulseaudio[5144]: module-x11-xsmp.c: X11 session manager not running.
Mar 20 11:31:11 sclinux pulseaudio[5144]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
```

/var/log/syslog
```
Mar 20 08:29:18 sclinux syslogd 1.5.0#2ubuntu6: restart.
Mar 20 08:29:18 sclinux anacron[7389]: Job `cron.daily' terminated
Mar 20 08:29:18 sclinux anacron[7389]: Normal exit (1 job run)
Mar 20 08:52:11 sclinux -- MARK --
Mar 20 09:12:11 sclinux -- MARK --
Mar 20 09:17:02 sclinux /USR/SBIN/CRON[7749]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 20 09:32:11 sclinux -- MARK --
Mar 20 09:52:11 sclinux -- MARK --
Mar 20 09:53:44 sclinux avahi-daemon[4125]: Invalid legacy unicast query packet.
Mar 20 09:53:45 sclinux last message repeated 2 times
Mar 20 09:53:45 sclinux avahi-daemon[4125]: Received response with invalid source port 49158 on interface 'eth0.0'
Mar 20 09:54:16 sclinux last message repeated 5 times
Mar 20 09:54:48 sclinux avahi-daemon[4125]: Received response with invalid source port 49158 on interface 'eth0.0'
Mar 20 10:05:34 sclinux avahi-daemon[4125]: Invalid legacy unicast query packet.
Mar 20 10:05:34 sclinux last message repeated 2 times
Mar 20 10:05:34 sclinux avahi-daemon[4125]: Received response with invalid source port 49291 on interface 'eth0.0'
Mar 20 10:05:41 sclinux last message repeated 3 times
Mar 20 10:05:46 sclinux avahi-daemon[4125]: Invalid legacy unicast query packet.
Mar 20 10:05:47 sclinux last message repeated 2 times
Mar 20 10:05:47 sclinux avahi-daemon[4125]: Received response with invalid source port 49156 on interface 'eth0.0'
Mar 20 10:05:48 sclinux avahi-daemon[4125]: Received response with invalid source port 49156 on interface 'eth0.0'
Mar 20 10:05:49 sclinux avahi-daemon[4125]: Received response with invalid source port 49291 on interface 'eth0.0'
Mar 20 10:05:50 sclinux avahi-daemon[4125]: Received response with invalid source port 49156 on interface 'eth0.0'
Mar 20 10:06:02 sclinux last message repeated 2 times
Mar 20 10:06:06 sclinux avahi-daemon[4125]: Received response with invalid source port 49291 on interface 'eth0.0'
Mar 20 10:06:18 sclinux avahi-daemon[4125]: Received response with invalid source port 49156 on interface 'eth0.0'
Mar 20 10:06:37 sclinux avahi-daemon[4125]: Received response with invalid source port 49291 on interface 'eth0.0'
Mar 20 10:06:50 sclinux avahi-daemon[4125]: Received response with invalid source port 49156 on interface 'eth0.0'
Mar 20 10:17:01 sclinux /USR/SBIN/CRON[7829]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 20 10:32:11 sclinux -- MARK --
Mar 20 10:39:40 sclinux avahi-daemon[4125]: Invalid legacy unicast query packet.
Mar 20 10:39:40 sclinux last message repeated 2 times
Mar 20 10:39:41 sclinux avahi-daemon[4125]: Received response with invalid source port 49206 on interface 'eth0.0'
Mar 20 10:39:56 sclinux last message repeated 4 times
Mar 20 10:40:44 sclinux last message repeated 2 times
Mar 20 10:52:11 sclinux -- MARK --
Mar 20 11:12:11 sclinux -- MARK --
Mar 20 11:17:01 sclinux /USR/SBIN/CRON[7927]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 20 11:18:52 sclinux NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Mar 20 11:25:28 sclinux console-kit-daemon[4619]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
Mar 20 11:25:28 sclinux console-kit-daemon[4619]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
Mar 20 11:25:29 sclinux init: tty4 main process (3900) killed by TERM signal
Mar 20 11:25:29 sclinux init: tty5 main process (3901) killed by TERM signal
Mar 20 11:25:29 sclinux init: tty2 main process (3908) killed by TERM signal
Mar 20 11:25:29 sclinux init: tty3 main process (3910) killed by TERM signal
Mar 20 11:25:29 sclinux init: tty6 main process (3913) killed by TERM signal
Mar 20 11:25:29 sclinux init: tty1 main process (5006) killed by TERM signal
Mar 20 11:25:42 sclinux mouseemu[4567]: mouseemu: cleaning... 
Mar 20 11:25:43 sclinux mouseemu[4566]: terminating, 0 
Mar 20 11:25:48 sclinux bluetoothd[4787]: bridge pan0 removed
Mar 20 11:25:48 sclinux bluetoothd[4787]: Stopping SDP server
Mar 20 11:25:48 sclinux bluetoothd[4787]: Exit
Mar 20 11:25:48 sclinux avahi-daemon[4125]: Got SIGTERM, quitting.
Mar 20 11:25:48 sclinux avahi-daemon[4125]: Leaving mDNS multicast group on interface eth0.IPv4 with address 205.124.38.86.
Mar 20 11:25:49 sclinux exiting on signal 15
Mar 20 11:29:57 sclinux syslogd 1.5.0#2ubuntu6: restart.
Mar 20 11:29:57 sclinux kernel: Inspecting /boot/System.map-2.6.25-2-powerpc
Mar 20 11:29:57 sclinux kernel: Loaded 25934 symbols from /boot/System.map-2.6.25-2-powerpc.
Mar 20 11:29:57 sclinux kernel: Symbols match kernel version 2.6.25.
Mar 20 11:29:58 sclinux kernel: Loaded 12151 symbols from 55 modules.
Mar 20 11:29:58 sclinux kernel: [    0.000000] Crash kernel location must be 0x2000000
Mar 20 11:29:58 sclinux kernel: [    0.000000] Reserving 0MB of memory at 32MB for crashkernel (System RAM: 320MB)
Mar 20 11:29:58 sclinux kernel: [    0.000000] Using PowerMac machine description
Mar 20 11:29:58 sclinux kernel: [    0.000000] Total memory = 320MB; using 1024kB for hash table (at cff00000)
Mar 20 11:29:58 sclinux kernel: [    0.000000] Linux version 2.6.25-2-powerpc (buildd@adare) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu8) ) #1 Tue Sep 30 14:49:00 UTC 2008
Mar 20 11:29:58 sclinux kernel: [    0.000000] Found initrd at 0xc1a00000:0xc22e7000
Mar 20 11:29:58 sclinux kernel: [    0.000000] Found UniNorth memory controller & host bridge @ 0xf8000000 revision: 0x08
Mar 20 11:29:58 sclinux kernel: [    0.000000] Mapped at 0xfdfc0000
Mar 20 11:29:58 sclinux kernel: [    0.000000] Found a Keylargo mac-io controller, rev: 3, mapped at 0xfdf40000
Mar 20 11:29:58 sclinux kernel: [    0.000000] Processor NAP mode on idle enabled.
Mar 20 11:29:58 sclinux kernel: [    0.000000] PowerMac motherboard: iMac FireWire
Mar 20 11:29:58 sclinux kernel: [    0.000000] console [udbg0] enabled
Mar 20 11:29:58 sclinux kernel: [    0.000000] Entering add_active_range(0, 0, 81920) 0 entries of 256 used
Mar 20 11:29:58 sclinux kernel: [    0.000000] Found UniNorth PCI host bridge at 0x00000000f0000000. Firmware bus number: 0->0
Mar 20 11:29:58 sclinux kernel: [    0.000000] PCI host bridge /pci@f0000000  ranges:
Mar 20 11:29:58 sclinux kernel: [    0.000000]  MEM 0x00000000f1000000..0x00000000f1ffffff -> 0x00000000f1000000 
Mar 20 11:29:58 sclinux kernel: [    0.000000]   IO 0x00000000f0000000..0x00000000f07fffff -> 0x0000000000000000
Mar 20 11:29:58 sclinux kernel: [    0.000000]  MEM 0x0000000090000000..0x000000009fffffff -> 0x0000000090000000 
Mar 20 11:29:58 sclinux kernel: [    0.000000] Found UniNorth PCI host bridge at 0x00000000f2000000. Firmware bus number: 0->0
Mar 20 11:29:58 sclinux kernel: [    0.000000] PCI host bridge /pci@f2000000 (primary) ranges:
Mar 20 11:29:58 sclinux kernel: [    0.000000]  MEM 0x00000000f3000000..0x00000000f3ffffff -> 0x00000000f3000000 
Mar 20 11:29:58 sclinux kernel: [    0.000000]   IO 0x00000000f2000000..0x00000000f27fffff -> 0x0000000000000000
Mar 20 11:29:58 sclinux kernel: [    0.000000]  MEM 0x0000000080000000..0x000000008fffffff -> 0x0000000080000000 
Mar 20 11:29:58 sclinux kernel: [    0.000000] Found UniNorth PCI host bridge at 0x00000000f4000000. Firmware bus number: 0->0
Mar 20 11:29:58 sclinux kernel: [    0.000000] PCI host bridge /pci@f4000000  ranges:
Mar 20 11:29:58 sclinux kernel: [    0.000000]  MEM 0x00000000f5000000..0x00000000f5ffffff -> 0x00000000f5000000 
Mar 20 11:29:58 sclinux kernel: [    0.000000]   IO 0x00000000f4000000..0x00000000f47fffff -> 0x0000000000000000
Mar 20 11:29:58 sclinux kernel: [    0.000000] via-pmu: Server Mode is disabled
Mar 20 11:29:58 sclinux kernel: [    0.000000] PMU driver v2 initialized for Core99, firmware: 0c
Mar 20 11:29:58 sclinux kernel: [    0.000000] nvram: Checking bank 0...
Mar 20 11:29:58 sclinux kernel: [    0.000000] nvram: gen0=1132, gen1=1131
Mar 20 11:29:58 sclinux kernel: [    0.000000] nvram: Active bank is: 0
Mar 20 11:29:58 sclinux kernel: [    0.000000] nvram: OF partition at 0x210
Mar 20 11:29:58 sclinux kernel: [    0.000000] nvram: XP partition at 0x1220
Mar 20 11:29:58 sclinux kernel: [    0.000000] nvram: NR partition at 0x1320
Mar 20 11:29:58 sclinux kernel: [    0.000000] Top of RAM: 0x14000000, Total RAM: 0x14000000
Mar 20 11:29:58 sclinux kernel: [    0.000000] Memory hole size: 0MB
Mar 20 11:29:58 sclinux kernel: [    0.000000] Zone PFN ranges:
Mar 20 11:29:58 sclinux kernel: [    0.000000]   DMA             0 ->    81920
Mar 20 11:29:58 sclinux kernel: [    0.000000]   Normal      81920 ->    81920
Mar 20 11:29:58 sclinux kernel: [    0.000000]   HighMem     81920 ->    81920
Mar 20 11:29:58 sclinux kernel: [    0.000000] Movable zone start PFN for each node
Mar 20 11:29:58 sclinux kernel: [    0.000000] early_node_map[1] active PFN ranges
Mar 20 11:29:58 sclinux kernel: [    0.000000]     0:        0 ->    81920
Mar 20 11:29:58 sclinux kernel: [    0.000000] On node 0 totalpages: 81920
Mar 20 11:29:58 sclinux kernel: [    0.000000]   DMA zone: 640 pages used for memmap
Mar 20 11:29:58 sclinux kernel: [    0.000000]   DMA zone: 0 pages reserved
Mar 20 11:29:58 sclinux kernel: [    0.000000]   DMA zone: 81280 pages, LIFO batch:15
Mar 20 11:29:58 sclinux kernel: [    0.000000]   Normal zone: 0 pages used for memmap
Mar 20 11:29:58 sclinux kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
Mar 20 11:29:58 sclinux kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Mar 20 11:29:58 sclinux kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 81280
Mar 20 11:29:58 sclinux kernel: [    0.000000] Kernel command line: root=/dev/hda3 ro quiet nosplash nofb 
Mar 20 11:29:58 sclinux kernel: [    0.000000] mpic: Setting up MPIC " MPIC 1   " version 1.2 at 80040000, max 4 CPUs
Mar 20 11:29:58 sclinux kernel: [    0.000000] mpic: ISU size: 64, shift: 6, mask: 3f
Mar 20 11:29:58 sclinux kernel: [    0.000000] mpic: Initializing for 64 sources
Mar 20 11:29:58 sclinux kernel: [    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
Mar 20 11:29:58 sclinux kernel: [    0.000000] GMT Delta read from XPRAM: 0 minutes, DST: off
Mar 20 11:29:58 sclinux kernel: [    0.000000] time_init: decrementer frequency = 24.967326 MHz
Mar 20 11:29:58 sclinux kernel: [    0.000000] time_init: processor frequency   = 450.000000 MHz
Mar 20 11:29:58 sclinux kernel: [    0.000013] clocksource: timebase mult[a0359a6] shift[22] registered
Mar 20 11:29:58 sclinux kernel: [    0.000028] clockevent: decrementer mult[664] shift[16] cpu[0]
Mar 20 11:29:58 sclinux kernel: [    0.000184] Console: colour dummy device 80x25
Mar 20 11:29:58 sclinux kernel: [    0.000199] console handover: boot [udbg0] -> real [tty0]
Mar 20 11:29:58 sclinux kernel: [    0.001970] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Mar 20 11:29:58 sclinux kernel: [    0.003631] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Mar 20 11:29:58 sclinux kernel: [    0.041669] High memory: 0k
Mar 20 11:29:58 sclinux kernel: [    0.041685] Memory: 309940k/327680k available (3688k kernel code, 17440k reserved, 132k data, 357k bss, 212k init)
Mar 20 11:29:58 sclinux kernel: [    0.041822] SLUB: Genslabs=12, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Mar 20 11:29:58 sclinux kernel: [    0.041833] Calibrating delay loop... 49.79 BogoMIPS (lpj=99584)
Mar 20 11:29:58 sclinux kernel: [    0.120110] Security Framework initialized
Mar 20 11:29:58 sclinux kernel: [    0.120151] SELinux:  Disabled at boot.
Mar 20 11:29:58 sclinux kernel: [    0.120170] Capability LSM initialized
Mar 20 11:29:58 sclinux kernel: [    0.120197] Mount-cache hash table entries: 512
Mar 20 11:29:58 sclinux kernel: [    0.120931] device-tree: Duplicate name in /cpus/PowerPC,750@0, renamed to "l2-cache#1"
Mar 20 11:29:58 sclinux kernel: [    0.123278] Initializing cgroup subsys ns
Mar 20 11:29:58 sclinux kernel: [    0.124424] net_namespace: 540 bytes
Mar 20 11:29:58 sclinux kernel: [    0.125206] NET: Registered protocol family 16
Mar 20 11:29:58 sclinux kernel: [    0.127048] KeyWest i2c @0xf8001003 irq 42 /uni-n@f8000000/i2c@f8001000
Mar 20 11:29:58 sclinux kernel: [    0.127068]  channel 0 bus <multibus>
Mar 20 11:29:58 sclinux kernel: [    0.127075]  channel 1 bus <multibus>
Mar 20 11:29:58 sclinux kernel: [    0.127117] KeyWest i2c @0x80018000 irq 26 /pci@f2000000/mac-io@17/i2c@18000
Mar 20 11:29:58 sclinux kernel: [    0.127127]  channel 0 bus <multibus>
Mar 20 11:29:58 sclinux kernel: [    0.127147] PMU i2c /pci@f2000000/mac-io@17/via-pmu@16000
Mar 20 11:29:58 sclinux kernel: [    0.127157]  channel 1 bus <multibus>
Mar 20 11:29:58 sclinux kernel: [    0.127165]  channel 2 bus <multibus>
Mar 20 11:29:58 sclinux kernel: [    0.127267] PCI: Probing PCI hardware
Mar 20 11:29:58 sclinux kernel: [    0.144221] NET: Registered protocol family 8
Mar 20 11:29:58 sclinux kernel: [    0.144238] NET: Registered protocol family 20
Mar 20 11:29:58 sclinux kernel: [    0.146371] NET: Registered protocol family 2
Mar 20 11:29:58 sclinux kernel: [    0.148038] Switched to high resolution mode on CPU 0
Mar 20 11:29:58 sclinux kernel: [    0.180198] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Mar 20 11:29:58 sclinux kernel: [    0.180852] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
Mar 20 11:29:58 sclinux kernel: [    0.181627] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
Mar 20 11:29:58 sclinux kernel: [    0.182018] TCP: Hash tables configured (established 16384 bind 16384)
Mar 20 11:29:58 sclinux kernel: [    0.182030] TCP reno registered
Mar 20 11:29:58 sclinux kernel: [    0.192614] checking if image is initramfs... it is
Mar 20 11:29:58 sclinux kernel: [    2.931546] Freeing initrd memory: 6144k freed
Mar 20 11:29:58 sclinux kernel: [    2.933166] Freeing initrd memory: 2968k freed
Mar 20 11:29:58 sclinux kernel: [    2.934005] Thermal assist unit using timers, shrink_timer: 500 jiffies
Mar 20 11:29:58 sclinux kernel: [    2.936084] audit: initializing netlink socket (disabled)
Mar 20 11:29:58 sclinux kernel: [    2.936156] type=2000 audit(1237569991.936:1): initialized
Mar 20 11:29:58 sclinux kernel: [    2.946203] VFS: Disk quotas dquot_6.5.1
Mar 20 11:29:58 sclinux kernel: [    2.946332] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Mar 20 11:29:58 sclinux kernel: [    2.947267] io scheduler noop registered
Mar 20 11:29:58 sclinux kernel: [    2.947279] io scheduler anticipatory registered
Mar 20 11:29:58 sclinux kernel: [    2.947287] io scheduler deadline registered
Mar 20 11:29:58 sclinux kernel: [    2.947354] io scheduler cfq registered (default)
Mar 20 11:29:58 sclinux kernel: [    2.949472] PCI: Enabling device 0000:00:10.0 (0086 -> 0087)
Mar 20 11:29:58 sclinux kernel: [    2.949873] aty128fb: Invalid ROM signature 8181 should  be 0xaa55
Mar 20 11:29:58 sclinux kernel: [    2.949898] aty128fb: BIOS not located, guessing timings.
Mar 20 11:29:58 sclinux kernel: [    2.949919] aty128fb: Rage128 PR PRO PCI [chip rev 0x1] 8M 64-bit SDR SGRAM (2:1)
Mar 20 11:29:58 sclinux kernel: [    2.967054] Console: switching to colour frame buffer device 128x48
Mar 20 11:29:58 sclinux kernel: [    2.982874] fb0: ATY Rage128 frame buffer device on Rage128 PR PRO PCI
Mar 20 11:29:58 sclinux kernel: [    3.126295] Generic RTC Driver v1.07
Mar 20 11:29:58 sclinux kernel: [    3.126517] Macintosh non-volatile memory driver v1.1
Mar 20 11:29:58 sclinux kernel: [    3.129795] brd: module loaded
Mar 20 11:29:58 sclinux kernel: [    3.129977] MacIO PCI driver attached to Keylargo chipset
Mar 20 11:29:58 sclinux kernel: [    3.134623] input: Macintosh mouse button emulation as /class/input/input0
Mar 20 11:29:58 sclinux kernel: [    3.135757] Uniform Multi-Platform E-IDE driver
Mar 20 11:29:58 sclinux kernel: [    3.135776] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Mar 20 11:29:58 sclinux kernel: [    3.136318] adb: starting probe task...
Mar 20 11:29:58 sclinux kernel: [    3.136344] adb: finished probe task...
Mar 20 11:29:58 sclinux kernel: [    3.176021] ide0: Found Apple KeyLargo ATA-4 controller, bus ID 2, irq 19
Mar 20 11:29:58 sclinux kernel: [    3.176080] Probing IDE interface ide0...
Mar 20 11:29:58 sclinux kernel: [    3.204323] hda: QUANTUM FIREBALLlct15 20, ATA DISK drive
Mar 20 11:29:58 sclinux kernel: [    3.244322] hdb: MATSHITADVD-ROM SR-8186, ATAPI CD/DVD-ROM drive
Mar 20 11:29:58 sclinux kernel: [    3.248000] hda: host max PIO4 wanted PIO255(auto-tune) selected PIO4
Mar 20 11:29:58 sclinux kernel: [    3.248000] hda: UDMA/33 mode selected
Mar 20 11:29:58 sclinux kernel: [    3.248000] hdb: host max PIO4 wanted PIO255(auto-tune) selected PIO4
Mar 20 11:29:58 sclinux kernel: [    3.248000] hdb: UDMA/33 mode selected
Mar 20 11:29:58 sclinux kernel: [    3.248000] ide0 at 0xd5014000-0xd5014007,0xd5014160 on irq 19
Mar 20 11:29:58 sclinux kernel: [    3.288021] ide1: Found Apple KeyLargo ATA-3 controller, bus ID 0, irq 20
Mar 20 11:29:58 sclinux kernel: [    3.288069] Probing IDE interface ide1...
Mar 20 11:29:58 sclinux kernel: [    3.368017] ide2: Found Apple KeyLargo ATA-3 controller, bus ID 1, irq 22
Mar 20 11:29:58 sclinux kernel: [    3.368061] Probing IDE interface ide2...
Mar 20 11:29:58 sclinux kernel: [    3.432361] mice: PS/2 mouse device common for all mice
Mar 20 11:29:58 sclinux kernel: [    3.432792] PowerMac i2c bus pmu 2 registered
Mar 20 11:29:58 sclinux kernel: [    3.432990] PowerMac i2c bus pmu 1 registered
Mar 20 11:29:58 sclinux kernel: [    3.433187] PowerMac i2c bus mac-io 0 registered
Mar 20 11:29:58 sclinux kernel: [    3.433384] PowerMac i2c bus uni-n 1 registered
Mar 20 11:29:58 sclinux kernel: [    3.433575] PowerMac i2c bus uni-n 0 registered
Mar 20 11:29:58 sclinux kernel: [    3.435397] NET: Registered protocol family 1
Mar 20 11:29:58 sclinux kernel: [    3.436155] registered taskstats version 1
Mar 20 11:29:58 sclinux kernel: [    3.436816] input: PMU as /class/input/input1
Mar 20 11:29:58 sclinux kernel: [    3.452059] Freeing unused kernel memory: 212k init
Mar 20 11:29:58 sclinux kernel: [    4.121792] fuse init (API version 7.9)
Mar 20 11:29:58 sclinux kernel: [    5.181788] device-mapper: uevent: version 1.0.3
Mar 20 11:29:58 sclinux kernel: [    5.182135] device-mapper: ioctl: 4.13.0-ioctl (2007-10-18) initialised: dm-devel@redhat.com
Mar 20 11:29:58 sclinux kernel: [    9.432540] sungem.c:v0.98 8/24/03 David S. Miller (davem@redhat.com)
Mar 20 11:29:58 sclinux kernel: [    9.484300] usbcore: registered new interface driver usbfs
Mar 20 11:29:58 sclinux kernel: [    9.484399] usbcore: registered new interface driver hub
Mar 20 11:29:58 sclinux kernel: [    9.500420] PHY ID: 406212, addr: 0
Mar 20 11:29:58 sclinux kernel: [    9.501676] eth0: Sun GEM (PCI) 10/100/1000BaseT Ethernet 00:30:65:6d:81:78
Mar 20 11:29:58 sclinux kernel: [    9.501688] eth0: Found BCM5201 PHY
Mar 20 11:29:58 sclinux kernel: [    9.520221] usbcore: registered new device driver usb
Mar 20 11:29:58 sclinux kernel: [    9.528543] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Mar 20 11:29:58 sclinux kernel: [    9.528744] PCI: Enabling device 0001:10:18.0 (0000 -> 0002)
Mar 20 11:29:58 sclinux kernel: [    9.528792] ohci_hcd 0001:10:18.0: OHCI Host Controller
Mar 20 11:29:58 sclinux kernel: [    9.529534] ohci_hcd 0001:10:18.0: new USB bus registered, assigned bus number 1
Mar 20 11:29:58 sclinux kernel: [    9.529627] ohci_hcd 0001:10:18.0: irq 27, io mem 0x80081000
Mar 20 11:29:58 sclinux kernel: [    9.604033] usb usb1: configuration #1 chosen from 1 choice
Mar 20 11:29:58 sclinux kernel: [    9.604152] hub 1-0:1.0: USB hub found
Mar 20 11:29:58 sclinux kernel: [    9.604229] hub 1-0:1.0: 2 ports detected
Mar 20 11:29:58 sclinux kernel: [    9.708596] PCI: Enabling device 0001:10:19.0 (0000 -> 0002)
Mar 20 11:29:58 sclinux kernel: [    9.708657] ohci_hcd 0001:10:19.0: OHCI Host Controller
Mar 20 11:29:58 sclinux kernel: [    9.708799] ohci_hcd 0001:10:19.0: new USB bus registered, assigned bus number 2
Mar 20 11:29:58 sclinux kernel: [    9.708886] ohci_hcd 0001:10:19.0: irq 28, io mem 0x80080000
Mar 20 11:29:58 sclinux kernel: [    9.783851] usb usb2: configuration #1 chosen from 1 choice
Mar 20 11:29:58 sclinux kernel: [    9.783965] hub 2-0:1.0: USB hub found
Mar 20 11:29:58 sclinux kernel: [    9.784030] hub 2-0:1.0: 2 ports detected
Mar 20 11:29:58 sclinux kernel: [    9.941142] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[40]  MMIO=[f5000000-f50007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Mar 20 11:29:58 sclinux kernel: [   10.056096] usb 1-1: new full speed USB device using ohci_hcd and address 2
Mar 20 11:29:58 sclinux kernel: [   10.264656] usb 1-1: configuration #1 chosen from 1 choice
Mar 20 11:29:58 sclinux kernel: [   10.265353] hub 1-1:1.0: USB hub found
Mar 20 11:29:58 sclinux kernel: [   10.267097] hub 1-1:1.0: 3 ports detected
Mar 20 11:29:58 sclinux kernel: [   10.367769] hda: max request size: 128KiB
Mar 20 11:29:58 sclinux kernel: [   10.383329] hda: 40011552 sectors (20485 MB) w/418KiB Cache, CHS=39694/16/63
Mar 20 11:29:58 sclinux kernel: [   10.383354] hda: cache flushes not supported
Mar 20 11:29:58 sclinux kernel: [   10.383563]  hda: [mac] hda1 hda2 hda3 hda4
Mar 20 11:29:58 sclinux kernel: [   10.585126] usb 1-1.1: new full speed USB device using ohci_hcd and address 3
Mar 20 11:29:58 sclinux kernel: [   10.618227] hdb: ATAPI 46X DVD-ROM drive, 512kB Cache
Mar 20 11:29:58 sclinux kernel: [   10.618258] Uniform CD-ROM driver Revision: 3.20
Mar 20 11:29:58 sclinux kernel: [   10.695519] usb 1-1.1: configuration #1 chosen from 1 choice
Mar 20 11:29:58 sclinux kernel: [   10.901156] usb 1-1.2: new low speed USB device using ohci_hcd and address 4
Mar 20 11:29:58 sclinux kernel: [   11.014579] usb 1-1.2: configuration #1 chosen from 1 choice
Mar 20 11:29:58 sclinux kernel: [   11.363247] ohci1394: fw-host0: SelfID received outside of bus reset sequence
Mar 20 11:29:58 sclinux kernel: [   11.541110] usbcore: registered new interface driver hiddev
Mar 20 11:29:58 sclinux kernel: [   11.546012] input: Mitsumi Electric Apple Extended USB Keyboard as /class/input/input2
Mar 20 11:29:58 sclinux kernel: [   11.556327] input,hidraw0: USB HID v1.10 Keyboard [Mitsumi Electric Apple Extended USB Keyboard] on usb-0001:10:18.0-1.1
Mar 20 11:29:58 sclinux kernel: [   11.564496] input: Mitsumi Electric Apple Extended USB Keyboard as /class/input/input3
Mar 20 11:29:58 sclinux kernel: [   11.580308] input,hidraw1: USB HID v1.10 Device [Mitsumi Electric Apple Extended USB Keyboard] on usb-0001:10:18.0-1.1
Mar 20 11:29:58 sclinux kernel: [   11.586849] input: Microsoft Basic Optical Mouse as /class/input/input4
Mar 20 11:29:58 sclinux kernel: [   11.596265] input,hidraw2: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0001:10:18.0-1.2
Mar 20 11:29:58 sclinux kernel: [   11.596352] usbcore: registered new interface driver usbhid
Mar 20 11:29:58 sclinux kernel: [   11.596370] /build/buildd/linux-ports-2.6.25/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Mar 20 11:29:58 sclinux kernel: [   11.636625] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[003065fffe6d8178]
Mar 20 11:29:58 sclinux kernel: [   11.896225] eth0: Link is up at 100 Mbps, full-duplex.
Mar 20 11:29:58 sclinux kernel: [   11.983567] PM: Starting manual resume from disk
Mar 20 11:29:58 sclinux kernel: [   12.097384] kjournald starting.  Commit interval 5 seconds
Mar 20 11:29:58 sclinux kernel: [   12.097444] EXT3-fs: mounted filesystem with ordered data mode.
Mar 20 11:29:58 sclinux kernel: [   19.221654] udevd version 124 started
Mar 20 11:29:58 sclinux kernel: [   20.799073] device-mapper: multipath: version 1.0.5 loaded
Mar 20 11:29:58 sclinux kernel: [   32.737803] Linux agpgart interface v0.103
Mar 20 11:29:58 sclinux kernel: [   32.793870] agpgart: Detected Apple UniNorth chipset
Mar 20 11:29:58 sclinux kernel: [   32.794329] agpgart: configuring for size idx: 8
Mar 20 11:29:58 sclinux kernel: [   32.813272] agpgart: AGP aperture is 32M @ 0x0
Mar 20 11:29:58 sclinux kernel: [   38.784185] pmac_zilog: 0.6 (Benjamin Herrenschmidt <benh@kernel.crashing.org>)
Mar 20 11:29:58 sclinux kernel: [   38.784321] pmac_zilog: i2c-modem detected, id: 1
Mar 20 11:29:58 sclinux kernel: [   38.784443] ttyPZ0 at MMIO 0x80013020 (irq = 29) is a Z85c30 ESCC - Internal modem
Mar 20 11:29:58 sclinux kernel: [   38.796063] ttyPZ1 at MMIO 0x80013000 (irq = 50) is a Z85c30 ESCC - Serial port
Mar 20 11:29:58 sclinux kernel: [   39.882772] apm_emu: PMU APM Emulation initialized.
Mar 20 11:29:58 sclinux kernel: [   39.973953] loop: module loaded
Mar 20 11:29:58 sclinux kernel: [   40.662456] SCSI subsystem initialized
Mar 20 11:29:58 sclinux kernel: [   42.228041] input: PowerMac Beep as /class/input/input5
Mar 20 11:29:58 sclinux kernel: [   43.519810] Adding 879756k swap on /dev/hda4.  Priority:-1 extents:1 across:879756k
Mar 20 11:29:58 sclinux kernel: [  106.632270] EXT3 FS on hda3, internal journal
Mar 20 11:29:58 sclinux kernel: [  109.015057] ip_tables: (C) 2000-2006 Netfilter Core Team
Mar 20 11:29:58 sclinux kernel: [  109.399836] eth0: Link is up at 100 Mbps, full-duplex.
Mar 20 11:29:58 sclinux kernel: [  109.399860] eth0: Pause is disabled
Mar 20 11:29:58 sclinux kernel: [  110.103113] NET: Registered protocol family 17
Mar 20 11:29:58 sclinux kernel: [  111.331794] NET: Registered protocol family 10
Mar 20 11:29:58 sclinux kernel: [  111.333353] lo: Disabled Privacy Extensions
Mar 20 11:29:59 sclinux pbbuttonsd: WARNING: No backlight driver available - check your Kernel configuration. 
Mar 20 11:29:59 sclinux pbbuttonsd: INFO: Soundsystem requested: ALSA and at least activated: ALSA. 
Mar 20 11:29:59 sclinux pbbuttonsd: INFO: saving of config enabled to /etc/pbbuttonsd.conf. 
Mar 20 11:29:59 sclinux pbbuttonsd: INFO: pbbuttonsd 0.7.9: Unknown PowerBook - PMU version: 12 
Mar 20 11:30:00 sclinux anacron[4122]: Anacron 2.3 started on 2009-03-20
Mar 20 11:30:00 sclinux anacron[4122]: Normal exit (0 jobs run)
Mar 20 11:30:00 sclinux kernel: [  117.937514] hda: host max PIO4 wanted PIO0 selected PIO0
Mar 20 11:30:00 sclinux kernel: [  118.108024] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
Mar 20 11:30:00 sclinux avahi-daemon[4132]: Found user 'avahi' (UID 105) and group 'avahi' (GID 113).
Mar 20 11:30:00 sclinux avahi-daemon[4132]: Successfully dropped root privileges.
Mar 20 11:30:00 sclinux avahi-daemon[4132]: avahi-daemon 0.6.23 starting up.
Mar 20 11:30:00 sclinux avahi-daemon[4132]: Successfully called chroot().
Mar 20 11:30:00 sclinux avahi-daemon[4132]: Successfully dropped remaining capabilities.
Mar 20 11:30:00 sclinux avahi-daemon[4132]: No service file found in /etc/avahi/services.
Mar 20 11:30:00 sclinux avahi-daemon[4132]: Joining mDNS multicast group on interface eth0.IPv4 with address 205.124.38.95.
Mar 20 11:30:00 sclinux avahi-daemon[4132]: New relevant interface eth0.IPv4 for mDNS.
Mar 20 11:30:00 sclinux avahi-daemon[4132]: Network interface enumeration completed.
Mar 20 11:30:00 sclinux avahi-daemon[4132]: Registering new address record for fe80::230:65ff:fe6d:8178 on eth0.*.
Mar 20 11:30:00 sclinux avahi-daemon[4132]: Registering new address record for 205.124.38.95 on eth0.IPv4.
Mar 20 11:30:00 sclinux avahi-daemon[4132]: Registering HINFO record with values 'PPC'/'LINUX'.
Mar 20 11:30:01 sclinux kernel: [  118.606152] hda: task_no_data_intr: status=0x51 { DriveReady SeekComplete Error }
Mar 20 11:30:01 sclinux kernel: [  118.606194] hda: task_no_data_intr: error=0x04 { DriveStatusError }
Mar 20 11:30:01 sclinux kernel: [  118.606208] ide: failed opcode was: 0xef
Mar 20 11:30:01 sclinux avahi-daemon[4132]: Server startup complete. Host name is sclinux.local. Local service cookie is 1461758892.
Mar 20 11:30:01 sclinux kernel: [  119.190602] lp: driver loaded but no devices found
Mar 20 11:30:02 sclinux pbbuttonsd: INFO: Script '/etc/power/pmcs-pbbuttonsd performance ac ' launched and exited normally 
Mar 20 11:30:02 sclinux kernel: [  119.558980] ppdev: user-space parallel port driver
Mar 20 11:30:02 sclinux ntpdate[3655]: no server suitable for synchronization found
Mar 20 11:30:04 sclinux kernel: [  120.688129] eth0: no IPv6 routers present
Mar 20 11:30:06 sclinux mouseemu[4570]: mouseemu 0.15 (C) Colin Leroy <colin@colino.net> 
Mar 20 11:30:06 sclinux mouseemu[4570]: using (0+87) as middle button, (0+88) as right button, (0) as scroll. 
Mar 20 11:30:07 sclinux mouseemu[4572]: Trying to open /dev/uinput...
Mar 20 11:30:07 sclinux mouseemu[4572]:  error. 
Mar 20 11:30:07 sclinux mouseemu[4572]: Trying to open /dev/uinput...
Mar 20 11:30:07 sclinux mouseemu[4572]:  error. 
Mar 20 11:30:07 sclinux mouseemu[4572]: Trying to open /dev/input/uinput...
Mar 20 11:30:07 sclinux mouseemu[4572]:  ok. 
Mar 20 11:30:07 sclinux kernel: [  123.456064] input: Mouseemu virtual keyboard as /class/input/input6
Mar 20 11:30:07 sclinux mouseemu[4572]: Trying to open /dev/uinput...
Mar 20 11:30:07 sclinux mouseemu[4572]:  error. 
Mar 20 11:30:07 sclinux mouseemu[4572]: Trying to open /dev/uinput...
Mar 20 11:30:07 sclinux mouseemu[4572]:  error. 
Mar 20 11:30:07 sclinux mouseemu[4572]: Trying to open /dev/input/uinput...
Mar 20 11:30:07 sclinux mouseemu[4572]:  ok. 
Mar 20 11:30:07 sclinux kernel: [  123.490402] input: Mouseemu virtual mouse as /class/input/input7
Mar 20 11:30:10 sclinux bluetoothd[4792]: Bluetooth daemon
Mar 20 11:30:10 sclinux kernel: [  126.336316] Bluetooth: Core ver 2.11
Mar 20 11:30:10 sclinux kernel: [  126.364347] NET: Registered protocol family 31
Mar 20 11:30:10 sclinux kernel: [  126.364378] Bluetooth: HCI device and connection manager initialized
Mar 20 11:30:10 sclinux kernel: [  126.364392] Bluetooth: HCI socket layer initialized
Mar 20 11:30:10 sclinux bluetoothd[4792]: Starting SDP server
Mar 20 11:30:10 sclinux kernel: [  126.753925] Bluetooth: L2CAP ver 2.9
Mar 20 11:30:10 sclinux kernel: [  126.753959] Bluetooth: L2CAP socket layer initialized
Mar 20 11:30:10 sclinux kernel: [  126.916219] Bluetooth: RFCOMM socket layer initialized
Mar 20 11:30:10 sclinux kernel: [  126.918215] Bluetooth: RFCOMM TTY layer initialized
Mar 20 11:30:10 sclinux kernel: [  126.918236] Bluetooth: RFCOMM ver 1.8
Mar 20 11:30:11 sclinux kernel: [  127.099143] Bluetooth: BNEP (Ethernet Emulation) ver 1.2
Mar 20 11:30:11 sclinux kernel: [  127.099179] Bluetooth: BNEP filters: protocol multicast
Mar 20 11:30:11 sclinux kernel: [  127.310497] Bridge firewalling registered
Mar 20 11:30:11 sclinux kernel: [  127.312861] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
Mar 20 11:30:11 sclinux bluetoothd[4792]: bridge pan0 created
Mar 20 11:30:11 sclinux bluetoothd[4792]: Starting experimental netlink support
Mar 20 11:30:11 sclinux bluetoothd[4792]: Failed to find Bluetooth netlink family
Mar 20 11:30:11 sclinux bluetoothd[4792]: Can't init plugin /usr/lib/bluetooth/plugins/netlink.so
Mar 20 11:30:11 sclinux NetworkManager: <info>  starting... 
Mar 20 11:30:11 sclinux kernel: [  127.710857] Bluetooth: SCO (Voice Link) ver 0.5
Mar 20 11:30:11 sclinux kernel: [  127.710891] Bluetooth: SCO socket layer initialized
Mar 20 11:30:11 sclinux NetworkManager: <info>  eth0: driver is 'gem'. 
Mar 20 11:30:12 sclinux NetworkManager: <info>  Found new Ethernet device 'eth0'. 
Mar 20 11:30:12 sclinux NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_30_65_6d_81_78 
Mar 20 11:30:12 sclinux NetworkManager: <info>  Trying to start the supplicant... 
Mar 20 11:30:12 sclinux NetworkManager: <info>  Trying to start the system settings daemon... 
Mar 20 11:30:12 sclinux NetworkManager: <info>  (eth0): carrier now ON (device state 1) 
Mar 20 11:30:12 sclinux nm-system-settings:    SCPlugin-Ifupdown: init!
Mar 20 11:30:12 sclinux nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
Mar 20 11:30:12 sclinux nm-system-settings:    SCPluginIfupdown: guessed connection type (eth0) = 802-3-ethernet
Mar 20 11:30:13 sclinux nm-system-settings:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:eth0, type:802-3-ethernet, autoconnect:0, id:Ifupdown (eth0), uuid: 681b428f-0000-0000-0000-000000000039
Mar 20 11:30:13 sclinux nm-system-settings:    SCPlugin-Ifupdown: autoconnect
Mar 20 11:30:13 sclinux nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
Mar 20 11:30:13 sclinux nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_30_65_6d_81_78, iface: eth0): well known
Mar 20 11:30:13 sclinux nm-system-settings:    Ifupdown: get unmanaged devices count: 1
Mar 20 11:30:13 sclinux nm-system-settings:    SCPlugin-Ifupdown: (268611816) ... get_connections.
Mar 20 11:30:13 sclinux nm-system-settings:    SCPlugin-Ifupdown: (268611816) ... get_connections (managed=false): return empty list.
Mar 20 11:30:13 sclinux nm-system-settings:    Ifupdown: get unmanaged devices count: 1
Mar 20 11:30:13 sclinux nm-system-settings:    SCPlugin-Ifupdown: end _init.
Mar 20 11:30:13 sclinux nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Mar 20 11:30:13 sclinux nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Mar 20 11:30:13 sclinux NetworkManager: <info>  (eth0): now unmanaged 
Mar 20 11:30:13 sclinux gdm[4865]: WARNING: Didn't understand `' (expected true or false) 
Mar 20 11:30:14 sclinux anacron[4906]: Anacron 2.3 started on 2009-03-20
Mar 20 11:30:14 sclinux anacron[4906]: Normal exit (0 jobs run)
Mar 20 11:30:15 sclinux /usr/sbin/cron[4950]: (CRON) INFO (pidfile fd = 3)
Mar 20 11:30:15 sclinux /usr/sbin/cron[4951]: (CRON) STARTUP (fork ok)
Mar 20 11:30:15 sclinux /usr/sbin/cron[4951]: (CRON) INFO (Running @reboot jobs)
Mar 20 11:30:26 sclinux gdmgreeter[5023]: Gtk-WARNING: Unable to locate theme engine in module_path: "ubuntulooks", 
Mar 20 11:30:39 sclinux gdm[4867]: WARNING: Couldn't authenticate user 
Mar 20 11:30:53 sclinux pulseaudio[5142]: ltdl-bind-now.c: Failed to find original dlopen loader.
Mar 20 11:30:53 sclinux pulseaudio[5144]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Mar 20 11:30:53 sclinux pulseaudio[5144]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Mar 20 11:31:10 sclinux gnome-session[5061]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout 
Mar 20 11:31:11 sclinux gnome-session[5061]: WARNING: Could not launch application 'tracker-applet.desktop': Unable to start application: Failed to execute child process "tracker-applet" (No such file or directory) 
Mar 20 11:31:11 sclinux pulseaudio[5144]: module-x11-xsmp.c: X11 session manager not running.
Mar 20 11:31:11 sclinux pulseaudio[5144]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Mar 20 11:31:12 sclinux gnome-session[5061]: WARNING: Could not launch application 'trackerd.desktop': Unable to start application: Failed to execute child process "trackerd" (No such file or directory) 
Mar 20 11:31:15 sclinux NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Mar 20 11:31:15 sclinux NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Mar 20 11:39:58 sclinux NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
```

/var/log/daemon.log
```
Mar 20 10:05:50 sclinux avahi-daemon[4125]: Received response with invalid source port 49156 on interface 'eth0.0'
Mar 20 10:06:02 sclinux last message repeated 2 times
Mar 20 10:06:06 sclinux avahi-daemon[4125]: Received response with invalid source port 49291 on interface 'eth0.0'
Mar 20 10:06:18 sclinux avahi-daemon[4125]: Received response with invalid source port 49156 on interface 'eth0.0'
Mar 20 10:06:37 sclinux avahi-daemon[4125]: Received response with invalid source port 49291 on interface 'eth0.0'
Mar 20 10:06:50 sclinux avahi-daemon[4125]: Received response with invalid source port 49156 on interface 'eth0.0'
Mar 20 10:39:40 sclinux avahi-daemon[4125]: Invalid legacy unicast query packet.
Mar 20 10:39:40 sclinux last message repeated 2 times
Mar 20 10:39:41 sclinux avahi-daemon[4125]: Received response with invalid source port 49206 on interface 'eth0.0'
Mar 20 10:39:56 sclinux last message repeated 4 times
Mar 20 10:40:44 sclinux last message repeated 2 times
Mar 20 11:18:52 sclinux NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Mar 20 11:25:28 sclinux console-kit-daemon[4619]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
Mar 20 11:25:28 sclinux console-kit-daemon[4619]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
Mar 20 11:25:29 sclinux init: tty4 main process (3900) killed by TERM signal
Mar 20 11:25:29 sclinux init: tty5 main process (3901) killed by TERM signal
Mar 20 11:25:29 sclinux init: tty2 main process (3908) killed by TERM signal
Mar 20 11:25:29 sclinux init: tty3 main process (3910) killed by TERM signal
Mar 20 11:25:29 sclinux init: tty6 main process (3913) killed by TERM signal
Mar 20 11:25:29 sclinux init: tty1 main process (5006) killed by TERM signal
Mar 20 11:25:42 sclinux mouseemu[4567]: mouseemu: cleaning... 
Mar 20 11:25:43 sclinux mouseemu[4566]: terminating, 0 
Mar 20 11:25:48 sclinux bluetoothd[4787]: bridge pan0 removed
Mar 20 11:25:48 sclinux bluetoothd[4787]: Stopping SDP server
Mar 20 11:25:48 sclinux bluetoothd[4787]: Exit
Mar 20 11:25:48 sclinux avahi-daemon[4125]: Got SIGTERM, quitting.
Mar 20 11:25:48 sclinux avahi-daemon[4125]: Leaving mDNS multicast group on interface eth0.IPv4 with address 205.124.38.86.
Mar 20 11:29:59 sclinux pbbuttonsd: WARNING: No backlight driver available - check your Kernel configuration. 
Mar 20 11:29:59 sclinux pbbuttonsd: INFO: Soundsystem requested: ALSA and at least activated: ALSA. 
Mar 20 11:29:59 sclinux pbbuttonsd: INFO: saving of config enabled to /etc/pbbuttonsd.conf. 
Mar 20 11:29:59 sclinux pbbuttonsd: INFO: pbbuttonsd 0.7.9: Unknown PowerBook - PMU version: 12 
Mar 20 11:30:00 sclinux avahi-daemon[4132]: Found user 'avahi' (UID 105) and group 'avahi' (GID 113).
Mar 20 11:30:00 sclinux avahi-daemon[4132]: Successfully dropped root privileges.
Mar 20 11:30:00 sclinux avahi-daemon[4132]: avahi-daemon 0.6.23 starting up.
Mar 20 11:30:00 sclinux avahi-daemon[4132]: Successfully called chroot().
Mar 20 11:30:00 sclinux avahi-daemon[4132]: Successfully dropped remaining capabilities.
Mar 20 11:30:00 sclinux avahi-daemon[4132]: No service file found in /etc/avahi/services.
Mar 20 11:30:00 sclinux avahi-daemon[4132]: Joining mDNS multicast group on interface eth0.IPv4 with address 205.124.38.95.
Mar 20 11:30:00 sclinux avahi-daemon[4132]: New relevant interface eth0.IPv4 for mDNS.
Mar 20 11:30:00 sclinux avahi-daemon[4132]: Network interface enumeration completed.
Mar 20 11:30:00 sclinux avahi-daemon[4132]: Registering new address record for fe80::230:65ff:fe6d:8178 on eth0.*.
Mar 20 11:30:00 sclinux avahi-daemon[4132]: Registering new address record for 205.124.38.95 on eth0.IPv4.
Mar 20 11:30:00 sclinux avahi-daemon[4132]: Registering HINFO record with values 'PPC'/'LINUX'.
Mar 20 11:30:01 sclinux avahi-daemon[4132]: Server startup complete. Host name is sclinux.local. Local service cookie is 1461758892.
Mar 20 11:30:02 sclinux pbbuttonsd: INFO: Script '/etc/power/pmcs-pbbuttonsd performance ac ' launched and exited normally 
Mar 20 11:30:02 sclinux ntpdate[3655]: no server suitable for synchronization found
Mar 20 11:30:06 sclinux mouseemu[4570]: mouseemu 0.15 (C) Colin Leroy <colin@colino.net> 
Mar 20 11:30:06 sclinux mouseemu[4570]: using (0+87) as middle button, (0+88) as right button, (0) as scroll. 
Mar 20 11:30:07 sclinux mouseemu[4572]: Trying to open /dev/uinput...
Mar 20 11:30:07 sclinux mouseemu[4572]:  error. 
Mar 20 11:30:07 sclinux mouseemu[4572]: Trying to open /dev/uinput...
Mar 20 11:30:07 sclinux mouseemu[4572]:  error. 
Mar 20 11:30:07 sclinux mouseemu[4572]: Trying to open /dev/input/uinput...
Mar 20 11:30:07 sclinux mouseemu[4572]:  ok. 
Mar 20 11:30:07 sclinux mouseemu[4572]: Trying to open /dev/uinput...
Mar 20 11:30:07 sclinux mouseemu[4572]:  error. 
Mar 20 11:30:07 sclinux mouseemu[4572]: Trying to open /dev/uinput...
Mar 20 11:30:07 sclinux mouseemu[4572]:  error. 
Mar 20 11:30:07 sclinux mouseemu[4572]: Trying to open /dev/input/uinput...
Mar 20 11:30:07 sclinux mouseemu[4572]:  ok. 
Mar 20 11:30:10 sclinux bluetoothd[4792]: Bluetooth daemon
Mar 20 11:30:10 sclinux bluetoothd[4792]: Starting SDP server
Mar 20 11:30:11 sclinux bluetoothd[4792]: bridge pan0 created
Mar 20 11:30:11 sclinux bluetoothd[4792]: Starting experimental netlink support
Mar 20 11:30:11 sclinux bluetoothd[4792]: Failed to find Bluetooth netlink family
Mar 20 11:30:11 sclinux bluetoothd[4792]: Can't init plugin /usr/lib/bluetooth/plugins/netlink.so
Mar 20 11:30:11 sclinux NetworkManager: <info>  starting... 
Mar 20 11:30:11 sclinux NetworkManager: <info>  eth0: driver is 'gem'. 
Mar 20 11:30:12 sclinux NetworkManager: <info>  Found new Ethernet device 'eth0'. 
Mar 20 11:30:12 sclinux NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_30_65_6d_81_78 
Mar 20 11:30:12 sclinux NetworkManager: <info>  Trying to start the supplicant... 
Mar 20 11:30:12 sclinux NetworkManager: <info>  Trying to start the system settings daemon... 
Mar 20 11:30:12 sclinux NetworkManager: <info>  (eth0): carrier now ON (device state 1) 
Mar 20 11:30:12 sclinux nm-system-settings:    SCPlugin-Ifupdown: init!
Mar 20 11:30:12 sclinux nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
Mar 20 11:30:12 sclinux nm-system-settings:    SCPluginIfupdown: guessed connection type (eth0) = 802-3-ethernet
Mar 20 11:30:13 sclinux nm-system-settings:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:eth0, type:802-3-ethernet, autoconnect:0, id:Ifupdown (eth0), uuid: 681b428f-0000-0000-0000-000000000039
Mar 20 11:30:13 sclinux nm-system-settings:    SCPlugin-Ifupdown: autoconnect
Mar 20 11:30:13 sclinux nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
Mar 20 11:30:13 sclinux nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_30_65_6d_81_78, iface: eth0): well known
Mar 20 11:30:13 sclinux nm-system-settings:    Ifupdown: get unmanaged devices count: 1
Mar 20 11:30:13 sclinux nm-system-settings:    SCPlugin-Ifupdown: (268611816) ... get_connections.
Mar 20 11:30:13 sclinux nm-system-settings:    SCPlugin-Ifupdown: (268611816) ... get_connections (managed=false): return empty list.
Mar 20 11:30:13 sclinux nm-system-settings:    Ifupdown: get unmanaged devices count: 1
Mar 20 11:30:13 sclinux nm-system-settings:    SCPlugin-Ifupdown: end _init.
Mar 20 11:30:13 sclinux nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Mar 20 11:30:13 sclinux nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Mar 20 11:30:13 sclinux NetworkManager: <info>  (eth0): now unmanaged 
Mar 20 11:30:13 sclinux gdm[4865]: WARNING: Didn't understand `' (expected true or false) 
Mar 20 11:30:26 sclinux gdmgreeter[5023]: Gtk-WARNING: Unable to locate theme engine in module_path: "ubuntulooks", 
Mar 20 11:30:39 sclinux gdm[4867]: WARNING: Couldn't authenticate user 
Mar 20 11:31:10 sclinux gnome-session[5061]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout 
Mar 20 11:31:11 sclinux gnome-session[5061]: WARNING: Could not launch application 'tracker-applet.desktop': Unable to start application: Failed to execute child process "tracker-applet" (No such file or directory) 
Mar 20 11:31:12 sclinux gnome-session[5061]: WARNING: Could not launch application 'trackerd.desktop': Unable to start application: Failed to execute child process "trackerd" (No such file or directory) 
Mar 20 11:31:15 sclinux NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Mar 20 11:31:15 sclinux NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Mar 20 11:39:58 sclinux NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
```

---

