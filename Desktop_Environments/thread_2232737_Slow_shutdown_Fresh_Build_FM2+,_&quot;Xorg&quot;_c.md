---
title: "Slow shutdown: Fresh Build FM2+, &quot;Xorg&quot; cpu usage holds at 27%"
date: 2014-07-03
forum: Desktop Environments
---

### Post by presence2 on 2014-07-03
The issues I'm having:

[B]When I click on "shutdown" icon on the panel, it takes [COLOR=#800080]~45 seconds to bring up the shutdown menu[/COLOR]:

[/B]  I can click shutdown on this NEW machine, then go from machine to machine shutting down my old machines (and getting them completely dark) before the menu even pops up on this machine.  Then once the menu does pop up, I confirm the shutdown and the machine is dark in 2 seconds.   At idle, CPU usage is less than 2%. 

[I][B]While waitng for shutdown menu, [SIZE=5]Xorg[/SIZE] CPU usage holds at 27%:

[/B][/I][IMG]http://i.imgur.com/2NexqKK.png[/IMG]

[B]


One other odd thing that sometimes takes FOREVER on this machine is "shutter screen capture". 
[/B]
The program is usually opening normally. I click to take a screen shot and it can take 20-30 seconds or more, regardless of "selection" "repeat" or "full desktop" mode.   Capture delay and pre capture delay are both minimized; 1 sec and 0 sec respectively.   On my older machines, screen capture happens instantly/or within 1 second.  While I'm waiting CPU usage holds at 27% exactly like when I'm waiting for shutdown menu. 

[IMG]http://fsdportal.com/wp-content/uploads/2012/12/Shutter-icon-150x150.png[/IMG]

This is happening when waiting for screen capture to appear, but **NOT DURING SHUTDOWN:**

[IMG]http://i.imgur.com/3CA1C3F.png[/IMG]


As seen above... it is[COLOR=#800080]** "NOT shutter screen capture" using my CPU cycles it is [SIZE=5]Xorg[/SIZE]**[/COLOR]


**Everything else (so far) seems peachy and FAST:**

All other programs work fine: Firefox, open in 1 second, and closes instantly.  GIMP fires up in about 6 seconds; closes instantly. 

[B]Other side issues I'm noticing:
[/B]
I haven't got sound configured yet... but I suspect that's another issue.   I installed psensor and its not detecting any sensors on this new motherboard.

[B]I have 4 total machines running Lubuntu 14, recent updates:

[/B]The machine with issues is: 

[B]*NEW BUILD*
[COLOR=#000000]ASUS A88XM-A 
[/COLOR][COLOR=#ff0000]AMD A10-7700K
8G RAM[/COLOR]
 250G SATA 7200 (the drive is 2 years old); only 3% disc space is used; SMART says "disk ok"[/B]

Clearly the superior machine relative to my older lubuntu machines without such issues:

lga775 motherboards, 1 gig RAM, 2 GHz or less, 7200 platters, drives are pretty full and stupid old. 

**On my older machines running lubuntu 14, SHUTDOWN menu opens instantly.**

presence

---

### Post by presence2 on 2014-07-03
I've been meaning to do a full diagnostic on this new build... so here we go:

```


TABLE OF CONTENTS:
-----------------------------------------------

1) sudo uname -a
2) sudo hddtemp /dev/sda
3) sensors
4) sudo fdisk -l
5) free -m
6) grep MemTotal /proc/meminfo
7) cat /proc/meminfo
8) cat /proc/cpuinfo | grep "MHz"
9) sudo dmidecode -t processor | grep Speed
[FONT=Verdana]10) [/FONT]cat /var/log/kern.log | grep "MHz processor"
11) cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_max_freq 
12) acpi -V
13) df -h
14) ./speedtest-cli [redacted]
15) mount
16) lspci -v
17) sudo lshw


FULL DIAGNOSTICS REPORT:
-----------------------------------------------
(per subsections above, let me know if you need anything else):

11111111111111111111
sudo uname -a
-----------------------------------------------
Linux oracle-System-Product-Name 3.13.0-30-generic #54-Ubuntu SMP Mon Jun 9 22:47:59 UTC 2014 i686 athlon i686 GNU/Linux

22222222222222222222
sudo hddtemp /dev/sda
-----------------------------------------------

/dev/sda: ST3250318AS: 36°C

3333333333333333333
sensors
-----------------------------------------------

radeon-pci-0008
Adapter: PCI adapter
temp1: +0.0°C 

k10temp-pci-00c3
Adapter: PCI adapter
temp1: +4.1°C (high = +70.0°C)
(crit = +70.0°C, hyst = +69.0°C)

444444444444444444444444
sudo fdisk -l
-----------------------------------------------

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006c53a

Device Boot Start End Blocks Id System
/dev/sda1 * 2048 473839615 236918784 83 Linux
/dev/sda2 473841662 488396799 7277569 5 Extended
/dev/sda5 473841664 488396799 7277568 82 Linux swap / Solaris

555555555555555555555
free -m
---------------------------------------------

total used free shared buffers cached
Mem: 7011 1440 5571 32 48 589
-/+ buffers/cache: 802 6209
Swap: 7106 0 7106

666666666666666666666
grep MemTotal /proc/meminfo
-----------------------------------------------------

MemTotal: 7179828 kB


777777777777777777777
cat /proc/meminfo
---------------------------------------------------

MemTotal: 7179828 kB
MemFree: 5726920 kB
Buffers: 49600 kB
Cached: 607208 kB
SwapCached: 0 kB
Active: 955736 kB
Inactive: 405400 kB
Active(anon): 705260 kB
Inactive(anon): 36204 kB
Active(file): 250476 kB
Inactive(file): 369196 kB
Unevictable: 0 kB
Mlocked: 0 kB
HighTotal: 6365804 kB
HighFree: 5079712 kB
LowTotal: 814024 kB
LowFree: 647208 kB
SwapTotal: 7277564 kB
SwapFree: 7277564 kB
Dirty: 64 kB
Writeback: 0 kB
AnonPages: 704324 kB
Mapped: 148396 kB
Shmem: 37140 kB
Slab: 41708 kB
SReclaimable: 25924 kB
SUnreclaim: 15784 kB
KernelStack: 3000 kB
PageTables: 9288 kB
NFS_Unstable: 0 kB
Bounce: 0 kB
WritebackTmp: 0 kB
CommitLimit: 10867476 kB
Committed_AS: 2432408 kB
VmallocTotal: 122880 kB
VmallocUsed: 41812 kB
VmallocChunk: 75360 kB
HardwareCorrupted: 0 kB
AnonHugePages: 206848 kB
HugePages_Total: 0
HugePages_Free: 0
HugePages_Rsvd: 0
HugePages_Surp: 0
Hugepagesize: 2048 kB
DirectMap4k: 30712 kB
DirectMap2M: 882688 kB

88888888888888888888888888
cat /proc/cpuinfo | grep "MHz"
-------------------------------------------------------

cpu MHz : 2000.000
cpu MHz : 2000.000
cpu MHz : 2000.000
cpu MHz : 3400.000

99999999999999999999999999
sudo dmidecode -t processor | grep Speed
----------------------------------------------------------------

Max Speed: 3400 MHz
Current Speed: 3400 MHz

101010101010101010
cat /var/log/kern.log | grep "MHz processor"
--------------------------------------------------------------------

Jun 30 23:22:55 oracle-System-Product-Name kernel: [ 0.004000] tsc: Detected 3417.106 MHz processor
Jun 30 23:39:32 oracle-System-Product-Name kernel: [ 0.004000] tsc: Detected 3416.755 MHz processor
Jul 1 07:38:10 oracle-System-Product-Name kernel: [ 0.004000] tsc: Detected 3416.970 MHz processor
Jul 1 07:42:58 oracle-System-Product-Name kernel: [ 0.004000] tsc: Detected 3417.178 MHz processor
Jul 1 07:48:36 oracle-System-Product-Name kernel: [ 0.004000] tsc: Detected 3417.030 MHz processor
Jul 2 06:27:43 oracle-System-Product-Name kernel: [ 0.004000] tsc: Detected 3416.825 MHz processor
Jul 2 13:08:37 oracle-System-Product-Name kernel: [ 0.004000] tsc: Detected 3417.164 MHz processor
Jul 2 13:11:41 oracle-System-Product-Name kernel: [ 0.004000] tsc: Detected 3417.006 MHz processor
Jul 3 10:51:20 oracle-System-Product-Name kernel: [ 0.012000] tsc: Detected 3416.960 MHz processor
Jul 3 19:15:48 oracle-System-Product-Name kernel: [ 0.004000] tsc: Detected 3416.754 MHz processor
Jul 3 21:29:08 oracle-System-Product-Name kernel: [ 0.004000] tsc: Detected 3417.043 MHz processor


1111111111111111111111111111111
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_max_freq 
------------------------------------------------------

3400000
3400000
3400000
3400000

1212121212121212121212
acpi -V
-----------------------------------------------------

No support for device type: power_supply
No support for device type: power_supply
Cooling 0: Processor 0 of 10
Cooling 1: Processor 0 of 10
Cooling 2: Processor 0 of 10
Cooling 3: Processor 0 of 10

131313131313131313
df -h
----------------------------------------------------

Filesystem Size Used Avail Use% Mounted on
/dev/sda1 223G 3.8G 208G 2% /
none 4.0K 0 4.0K 0% /sys/fs/cgroup
udev 3.5G 4.0K 3.5G 1% /dev
tmpfs 702M 1.1M 701M 1% /run
none 5.0M 0 5.0M 0% /run/lock
none 3.5G 30M 3.4G 1% /run/shm
none 100M 20K 100M 1% /run/user


1414141414141414
./speedtest-cli
----------------------------------------------------------


Retrieving speedtest.net configuration...
Retrieving speedtest.net server list...
Testing from XXX (X.X.X.X)...
Selecting best server based on ping...
Hosted by XXX (XXX, XX) [100.85 km]: 18.597 ms
Testing download speed........................................
Download: 3.25 Mbits/s
Testing upload speed..................................................
Upload: 0.43 Mbits/s

151515151515151515
mount
------------------------------------------------

/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=xxxx)

16161616161616
lspci -v
---------------------------------------------------------


00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1422
Subsystem: ASUSTeK Computer Inc. Device 85cb
Flags: bus master, fast devsel, latency 0


00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Kaveri [Radeon R7 200 Series] (prog-if 00 [VGA controller])
Subsystem: ASUSTeK Computer Inc. Device 85cb
Flags: bus master, fast devsel, latency 0, IRQ 84
Memory at e0000000 (64-bit, prefetchable) 
Memory at f0000000 (64-bit, prefetchable) 
I/O ports at f000 
Memory at feb00000 (32-bit, non-prefetchable) 
Expansion ROM at feb40000 [disabled] 
Capabilities: <access denied>
Kernel driver in use: radeon


00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device 1308
Subsystem: ASUSTeK Computer Inc. Device 85cb
Flags: bus master, fast devsel, latency 0, IRQ 85
Memory at feb64000 (64-bit, non-prefetchable) 
Capabilities: <access denied>
Kernel driver in use: snd_hda_intel


00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1424
Flags: fast devsel


00:03.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1424
Flags: fast devsel


00:04.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1424
Flags: fast devsel


00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 09) (prog-if 30 [XHCI])
Subsystem: ASUSTeK Computer Inc. Device 85ca
Flags: bus master, fast devsel, latency 0, IRQ 18
Memory at feb6a000 (64-bit, non-prefetchable) 
Capabilities: <access denied>
Kernel driver in use: xhci_hcd


00:10.1 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 09) (prog-if 30 [XHCI])
Subsystem: ASUSTeK Computer Inc. Device 85ca
Flags: bus master, fast devsel, latency 0, IRQ 17
Memory at feb68000 (64-bit, non-prefetchable) 
Capabilities: <access denied>
Kernel driver in use: xhci_hcd


00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 40) (prog-if 01 [AHCI 1.0])
Subsystem: ASUSTeK Computer Inc. Device 85ca
Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 82
I/O ports at f140 
I/O ports at f130 [size=4]
I/O ports at f120 [size=8]
I/O ports at f110 [size=4]
I/O ports at f100 [size=16]
Memory at feb70000 (32-bit, non-prefetchable) [size=2K]
Capabilities: <access denied>
Kernel driver in use: ahci


00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11) (prog-if 10 [OHCI])
Subsystem: ASUSTeK Computer Inc. Device 85ca
Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
Memory at feb6f000 (32-bit, non-prefetchable) [size=4K]
Kernel driver in use: ohci-pci


00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11) (prog-if 20 [EHCI])
Subsystem: ASUSTeK Computer Inc. Device 85ca
Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
Memory at feb6e000 (32-bit, non-prefetchable) [size=256]
Capabilities: <access denied>
Kernel driver in use: ehci-pci


00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11) (prog-if 10 [OHCI])
Subsystem: ASUSTeK Computer Inc. Device 85ca
Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
Memory at feb6d000 (32-bit, non-prefetchable) [size=4K]
Kernel driver in use: ohci-pci


00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11) (prog-if 20 [EHCI])
Subsystem: ASUSTeK Computer Inc. Device 85ca
Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
Memory at feb6c000 (32-bit, non-prefetchable) [size=256]
Capabilities: <access denied>
Kernel driver in use: ehci-pci


00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 16)
Subsystem: ASUSTeK Computer Inc. Device 85ca
Flags: 66MHz, medium devsel
Kernel driver in use: piix4_smbus


00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01)
Subsystem: ASUSTeK Computer Inc. Device 8576
Flags: bus master, slow devsel, latency 32, IRQ 16
Memory at feb60000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: snd_hda_intel


00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
Subsystem: ASUSTeK Computer Inc. Device 85ca
Flags: bus master, 66MHz, medium devsel, latency 0


00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
Bus: primary=00, secondary=01, subordinate=01, sec-latency=64


00:15.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 0) (prog-if 00 [Normal decode])
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
Capabilities: <access denied>
Kernel driver in use: pcieport


00:15.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 2) (prog-if 00 [Normal decode])
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
I/O behind bridge: 0000e000-0000efff
Memory behind bridge: fea00000-feafffff
Prefetchable memory behind bridge: 00000000f0800000-00000000f08fffff
Capabilities: <access denied>
Kernel driver in use: pcieport


00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 141a
Flags: fast devsel


00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 141b
Flags: fast devsel


00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 141c
Flags: fast devsel


00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 141d
Flags: fast devsel
Capabilities: <access denied>
Kernel driver in use: k10temp


00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 141e
Flags: fast devsel


00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 141f
Flags: fast devsel


03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
Subsystem: ASUSTeK Computer Inc. Device 8554
Flags: bus master, fast devsel, latency 0, IRQ 83
I/O ports at e000 [size=256]
Memory at fea00000 (64-bit, non-prefetchable) [size=4K]
Memory at f0800000 (64-bit, prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: r8169

171717171717
sudo lshw
-------------------------------------------------


oracle-system-product-name
description: Desktop Computer
product: System Product Name (SKU)
vendor: System manufacturer
version: System Version
serial: System Serial Number
width: 32 bits
capabilities: smbios-2.7 dmi-2.7 smp-1.4 smp
configuration: boot=normal chassis=desktop cpus=4 family=To be filled by O.E.M. sku=SKU uuid=0E68279D-786E-F300-62AB-D850E63F1882
*-core
[SIZE=5]description: Motherboard
product: A88XM-A
[SIZE=5]vendor: ASUSTeK COMPUTER INC.
physical id: 0
version: Rev X.0x
serial: 130916103401299
slot: To be filled by O.E.M.
*-firmware
description: BIOS
vendor: American Megatrends Inc.
physical id: 0
version: 0603
date: 10/16/2013
size: 64KiB
capacity: 8128KiB
capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
*-memory
description: System Memory
physical id: 24
slot: System board or motherboard
[SIZE=5]size: 8GiB
*-bank:0
[SIZE=5]description: DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
product: Array1_PartNumber1
vendor: A1_Manufacturer1
physical id: 0
serial: A1_SerNum1
slot: DIMM_A1
size: 4GiB
width: 64 bits
clock: 1600MHz (0.6ns)
*-bank:1
description: [empty]
product: Array1_PartNumber0
vendor: A1_Manufacturer0
physical id: 1
serial: A1_SerNum0
slot: DIMM_A2
*-bank:2
description: DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
product: BLS4G3D1609DS1S00.
vendor: Undefined
physical id: 2
serial: AD0195EA
slot: DIMM_B1
size: 4GiB
width: 64 bits
clock: 1600MHz (0.6ns)
*-bank:3
description: [empty]
product: Array1_PartNumber3
vendor: A1_Manufacturer3
physical id: 3
serial: A1_SerNum3
slot: DIMM_B2
*-cache:0
description: L1 cache
physical id: 32
slot: L1 CACHE
size: 256KiB
capacity: 256KiB
clock: 1GHz (1.0ns)
capabilities: pipeline-burst internal write-back unified
*-cache:1
description: L2 cache
physical id: 33
slot: L2 CACHE
size: 4MiB
capacity: 4MiB
clock: 1GHz (1.0ns)
capabilities: pipeline-burst internal write-back unified
*-cpu:0
[SIZE=5]description: CPU
product: AMD A10-7700K APU with Radeon(TM) R7 Graphics
vendor: Advanced Micro Devices [AMD]
physical id: 3c
bus info: cpu@0
version: 15.0.1
slot: FM2+
size: 2GHz
capacity: 3400MHz
width: 64 bits
clock: 100MHz
capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp constant_tsc nonstop_tsc extd_apicid aperfmperf eagerfpu pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb arat cpb xsaveopt hw_pstate npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold fsgsbase bmi1 cpufreq
configuration: cores=4 enabledcores=4 threads=4
*-cpu:1
physical id: 1
bus info: cpu@1
version: 15.0.1
size: 2GHz
capacity: 2GHz
capabilities: cpufreq
*-cpu:2
physical id: 2
bus info: cpu@2
version: 15.0.1
size: 2GHz
capacity: 2GHz
capabilities: cpufreq
*-cpu:3
physical id: 3
bus info: cpu@3
version: 15.0.1
size: 2GHz
capacity: 2GHz
capabilities: cpufreq
*-pci:0
description: Host bridge
product: Advanced Micro Devices, Inc. [AMD]
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 100
bus info: pci@0000:00:00.0
version: 00
width: 32 bits
clock: 33MHz
*-display
description: VGA compatible controller
product: Kaveri [Radeon R7 200 Series]
vendor: Advanced Micro Devices, Inc. [AMD/ATI]
physical id: 1
bus info: pci@0000:00:01.0
version: 00
width: 64 bits
clock: 33MHz
capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
configuration: driver=radeon latency=0
resources: irq:84 memory:e0000000-efffffff memory:f0000000-f07fffff ioport:f000(size=256) memory:feb00000-feb3ffff memory:feb40000-feb5ffff
*-multimedia:0
description: Audio device
product: Advanced Micro Devices, Inc. [AMD/ATI]
vendor: Advanced Micro Devices, Inc. [AMD/ATI]
physical id: 1.1
bus info: pci@0000:00:01.1
version: 00
width: 64 bits
clock: 33MHz
capabilities: pm pciexpress msi bus_master cap_list
configuration: driver=snd_hda_intel latency=0
resources: irq:85 memory:feb64000-feb67fff
*-usb:0
description: USB controller
product: FCH USB XHCI Controller
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 10
bus info: pci@0000:00:10.0
version: 09
width: 64 bits
clock: 33MHz
capabilities: pm msi msix pciexpress xhci bus_master cap_list
configuration: driver=xhci_hcd latency=0
resources: irq:18 memory:feb6a000-feb6bfff
*-usb:1
description: USB controller
product: FCH USB XHCI Controller
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 10.1
bus info: pci@0000:00:10.1
version: 09
width: 64 bits
clock: 33MHz
capabilities: pm msi msix pciexpress xhci bus_master cap_list
configuration: driver=xhci_hcd latency=0
resources: irq:17 memory:feb68000-feb69fff
*-storage
description: SATA controller
product: FCH SATA Controller [AHCI mode]
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 11
bus info: pci@0000:00:11.0
version: 40
width: 32 bits
clock: 66MHz
capabilities: storage msi ahci_1.0 bus_master cap_list
configuration: driver=ahci latency=32
resources: irq:82 ioport:f140(size=8) ioport:f130(size=4) ioport:f120(size=8) ioport:f110(size=4) ioport:f100(size=16) memory:feb70000-feb707ff
*-usb:2
description: USB controller
product: FCH USB OHCI Controller
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 12
bus info: pci@0000:00:12.0
version: 11
width: 32 bits
clock: 66MHz
capabilities: ohci bus_master
configuration: driver=ohci-pci latency=32
resources: irq:18 memory:feb6f000-feb6ffff
*-usb:3
description: USB controller
product: FCH USB EHCI Controller
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 12.2
bus info: pci@0000:00:12.2
version: 11
width: 32 bits
clock: 66MHz
capabilities: pm debug ehci bus_master cap_list
configuration: driver=ehci-pci latency=32
resources: irq:17 memory:feb6e000-feb6e0ff
*-usb:4
description: USB controller
product: FCH USB OHCI Controller
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 13
bus info: pci@0000:00:13.0
version: 11
width: 32 bits
clock: 66MHz
capabilities: ohci bus_master
configuration: driver=ohci-pci latency=32
resources: irq:18 memory:feb6d000-feb6dfff
*-usb:5
description: USB controller
product: FCH USB EHCI Controller
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 13.2
bus info: pci@0000:00:13.2
version: 11
width: 32 bits
clock: 66MHz
capabilities: pm debug ehci bus_master cap_list
configuration: driver=ehci-pci latency=32
resources: irq:17 memory:feb6c000-feb6c0ff
*-serial
description: SMBus
product: FCH SMBus Controller
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 14
bus info: pci@0000:00:14.0
version: 16
width: 32 bits
clock: 66MHz
configuration: driver=piix4_smbus latency=0
resources: irq:0
*-multimedia:1
description: Audio device
product: FCH Azalia Controller
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 14.2
bus info: pci@0000:00:14.2
version: 01
width: 64 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: driver=snd_hda_intel latency=32
resources: irq:16 memory:feb60000-feb63fff
*-isa
description: ISA bridge
product: FCH LPC Bridge
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 14.3
bus info: pci@0000:00:14.3
version: 11
width: 32 bits
clock: 66MHz
capabilities: isa bus_master
configuration: latency=0
*-pci:0
description: PCI bridge
product: FCH PCI Bridge
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 14.4
bus info: pci@0000:00:14.4
version: 40
width: 32 bits
clock: 66MHz
capabilities: pci subtractive_decode bus_master vga_palette
*-pci:1
description: PCI bridge
product: Hudson PCI to PCI bridge (PCIE port 0)
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 15
bus info: pci@0000:00:15.0
version: 00
width: 32 bits
clock: 33MHz
capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
configuration: driver=pcieport
resources: irq:17
*-pci:2
description: PCI bridge
product: Hudson PCI to PCI bridge (PCIE port 2)
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 15.2
bus info: pci@0000:00:15.2
version: 00
width: 32 bits
clock: 33MHz
capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
configuration: driver=pcieport
resources: irq:17 ioport:e000(size=4096) memory:fea00000-feafffff ioport:f0800000(size=1048576)
*-network
description: Ethernet interface
product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:03:00.0
logical name: eth0
version: 0c
serial: d8:50:e6:3f:18:82
size: 100Mbit/s
capacity: 1Gbit/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=192.168.2.150 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
resources: irq:83 ioport:e000(size=256) memory:fea00000-fea00fff memory:f0800000-f0803fff
*-pci:1
description: Host bridge
product: Advanced Micro Devices, Inc. [AMD]
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 101
bus info: pci@0000:00:02.0
version: 00
width: 32 bits
clock: 33MHz
*-pci:2
description: Host bridge
product: Advanced Micro Devices, Inc. [AMD]
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 102
bus info: pci@0000:00:03.0
version: 00
width: 32 bits
clock: 33MHz
*-pci:3
description: Host bridge
product: Advanced Micro Devices, Inc. [AMD]
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 103
bus info: pci@0000:00:04.0
version: 00
width: 32 bits
clock: 33MHz
*-pci:4
description: Host bridge
product: Advanced Micro Devices, Inc. [AMD]
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 104
bus info: pci@0000:00:18.0
version: 00
width: 32 bits
clock: 33MHz
*-pci:5
description: Host bridge
product: Advanced Micro Devices, Inc. [AMD]
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 105
bus info: pci@0000:00:18.1
version: 00
width: 32 bits
clock: 33MHz
*-pci:6
description: Host bridge
product: Advanced Micro Devices, Inc. [AMD]
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 106
bus info: pci@0000:00:18.2
version: 00
width: 32 bits
clock: 33MHz
*-pci:7
description: Host bridge
product: Advanced Micro Devices, Inc. [AMD]
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 107
bus info: pci@0000:00:18.3
version: 00
width: 32 bits
clock: 33MHz
configuration: driver=k10temp
resources: irq:0
*-pci:8
description: Host bridge
product: Advanced Micro Devices, Inc. [AMD]
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 108
bus info: pci@0000:00:18.4
version: 00
width: 32 bits
clock: 33MHz
*-pci:9
description: Host bridge
product: Advanced Micro Devices, Inc. [AMD]
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 109
bus info: pci@0000:00:18.5
version: 00
width: 32 bits
clock: 33MHz
*-scsi:0
physical id: 4
logical name: scsi0
capabilities: emulated
*-disk
description: ATA Disk
[SIZE=5]product: ST3250318AS
vendor: Seagate
physical id: 0.0.0
bus info: scsi@0:0.0.0
logical name: /dev/sda
version: CC66
serial: 6VY6F8Q4
[SIZE=5]size: 232GiB (250GB)
capabilities: partitioned partitioned:dos
configuration: ansiversion=5 sectorsize=512 signature=0006c53a
*-volume:0
description: EXT4 volume
vendor: Linux
physical id: 1
bus info: scsi@0:0.0.0,1
logical name: /dev/sda1
logical name: /
version: 1.0
serial: 83b7608a-c08e-4492-90de-46ea3a1b92ac
size: 225GiB
capacity: 225GiB
capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
configuration: created=2014-06-30 23:14:08 filesystem=ext4 lastmountpoint=/ modified=2014-07-03 19:15:47 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-07-03 19:15:47 state=mounted
*-volume:1
description: Extended partition
physical id: 2
bus info: scsi@0:0.0.0,2
[SIZE=5]logical name: /dev/sda2
capacity: 7107MiB
size: 7107MiB
capabilities: primary extended partitioned partitioned:extended
*-logicalvolume
description: Linux swap / Solaris partition
physical id: 5
logical name: /dev/sda5
capacity: 7107MiB
capabilities: nofs
*-scsi:1
physical id: 5
logical name: scsi1
capabilities: emulated
*-cdrom
description: DVD-RAM writer
product: DVDRAM GH24NSB0
vendor: HL-DT-ST
physical id: 0.0.0
bus info: scsi@1:0.0.0
logical name: /dev/cdrom
logical name: /dev/sr0
version: LN00
capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
configuration: ansiversion=5 status=nodisc

sudo sensors-detect 
--------------------------------------------

# sensors-detect revision 6170 (2013-05-20 21:25:22 +0200)
# Board: ASUSTeK COMPUTER INC. A88XM-A


This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.


Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): y
Silicon Integrated Systems SIS5595... No
VIA VT82C686 Integrated Sensors... No
VIA VT8231 Integrated Sensors... No
AMD K8 thermal sensors... No
AMD Family 10h thermal sensors... No
AMD Family 11h thermal sensors... No
AMD Family 12h and 14h thermal sensors... No
AMD Family 15h thermal sensors... No
AMD Family 15h power sensors... No
AMD Family 16h power sensors... No
Intel digital thermal sensor... No
Intel AMB FB-DIMM thermal sensor... No
VIA C7 thermal sensor... No
VIA Nano thermal sensor... No


Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor/ITE'... No
Trying family `SMSC'... No
Trying family `VIA/Winbond/Nuvoton/Fintek'... No
Trying family `ITE'... Yes
Found unknown chip with ID 0x8603
(logical device 4 has address 0x290, could be sensors)
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor/ITE'... No
Trying family `SMSC'... No
Trying family `VIA/Winbond/Nuvoton/Fintek'... No
Trying family `ITE'... No


Some systems (mainly servers) implement IPMI, a set of common interfaces
through which system health data may be retrieved, amongst other things.
We first try to get the information from SMBIOS. If we don't find it
there, we have to read from arbitrary I/O ports to probe for such
interfaces. This is normally safe. Do you want to scan for IPMI
interfaces? (YES/no): y
Probing for `IPMI BMC KCS' at 0xca0... No
Probing for `IPMI BMC SMIC' at 0xca8... No


Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): y
Probing for `National Semiconductor LM78' at 0x290... No
Probing for `National Semiconductor LM79' at 0x290... No
Probing for `Winbond W83781D' at 0x290... No
Probing for `Winbond W83782D' at 0x290... No


Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): y
Using driver `i2c-piix4' for device 0000:00:14.0: AMD Hudson-2 SMBus


Next adapter: Radeon i2c bit bus 0x90 (i2c-0)
Do you want to scan it? (yes/NO/selectively): y


Next adapter: Radeon i2c bit bus 0x91 (i2c-1)
Do you want to scan it? (yes/NO/selectively): y


Next adapter: Radeon i2c bit bus 0x92 (i2c-2)
Do you want to scan it? (yes/NO/selectively): y


Next adapter: Radeon i2c bit bus 0x93 (i2c-3)
Do you want to scan it? (yes/NO/selectively): y


Next adapter: Radeon i2c bit bus 0x94 (i2c-4)
Do you want to scan it? (yes/NO/selectively): y


Next adapter: Radeon i2c bit bus 0x95 (i2c-5)
Do you want to scan it? (yes/NO/selectively): y


Next adapter: Radeon aux bus DP-auxch (i2c-6)
Do you want to scan it? (yes/NO/selectively): y


Next adapter: SMBus PIIX4 adapter at 0b00 (i2c-7)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x50
Probing for `Analog Devices ADM1033'... No
Probing for `Analog Devices ADM1034'... No
Probing for `SPD EEPROM'... Yes
(confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'... No
Client found at address 0x51
Probing for `Analog Devices ADM1033'... No
Probing for `Analog Devices ADM1034'... No
Probing for `SPD EEPROM'... Yes
(confidence 8, not a hardware monitoring chip)


Next adapter: SMBus PIIX4 adapter at 0b20 (i2c-8)
Do you want to scan it? (YES/no/selectively): y


Sorry, no sensors were detected.
Either your system has no sensors, or they are not supported, or
they are connected to an I2C or SMBus adapter that is not
supported. If you find out what chips are on your board, check
[http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for driver status.
```

---

### Post by mörgæs on 2014-07-04
Please edit your post above and add CODE tags about relevant sections.

---

### Post by presence2 on 2014-07-05
> **mörgæs said:**
> Please edit your post above and add CODE tags about relevant sections.


I'm not really sure what is relevant.    Is it a RAM issue?  A Motherboard issue?  A hard drive issue? 

**I added a table of contents (and code tags) to my diagnostic report.**

(Thanks for the addition of code tags [bapoumba]("http://ubuntuforums.org/posthistory.php?p=13065006") I just now figured out how to do that :))
[SIZE=5]
[/SIZE]I know how to generate these reports... but have little understanding of what any of it means.  Anything you need should be there and easily referenced with the table of contents.


Primary Issue:
[SIZE=5]**Shutdown Takes Forever**[/SIZE]

Secondary Issue:
[B]Screen Capture Takes Forever
[/B]
other side issues:
[B]Sensor Detect Doesn't Work
[/B]

---

### Post by presence2 on 2014-07-08
Ok... scrubbed my hard drive... Brand New freshy install, new ISO, new download... 64 bit this time.   (was 32 bit last time as that was what I had laying around for my older machines.)

SAME ISSUES.

Shutter Screenshot and Shutdown Menu are both 30  to 45 seconds delayed.


from terminal:

```

sudo shutdown -P now

```

shuts down my machine almost instantly

---

### Post by glicci on 2014-09-03
Hi Presence2, 
i'm having the very same problem as your, shutdown menu takes a lot of seconds/minutes to appear; I've also checked and Xorg process goes above 60-80% cpu while waiting for shutting down menu to appear.
I've installed Lubuntu 14.04 LTS on a MSI All-In-One AE200 PC.
All other programs are working fine with no delay.
Did you managed to solve this issue ? 
Someone can help about this ? 

Thank You
Regards,
Giacomo

---

### Post by stef_va_uijtregt on 2014-11-09
Hi, 

I have had the same problem with Lubuntu 14 on an acer laptop: aspire v5-123 (AMD E1). 

I tried installing the proprietary video drivers which sovled the problem for me.

---

### Post by jds2 on 2014-12-15
I have the same problem on Xubuntu 14.04. Screenshots and shutting down are slow with Xorg using a lot of CPU. You can get the machine 'unstuck' by doing Ctrl-Alt-F1 and then then Ctrl-Alt-F7 to switch out and back into the Xorg session. I'm using a Thinkpad X140e netbook which has an AMD A4-5000 APU in it. This is not a fresh install, but the problem was present immediately after installing.

lspci and Xorg log are included below. I'll be happy to provide any other information desired or test any suggestions.

```

> $ lspci -v                                                                   
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Root Complex
    Subsystem: Lenovo Device 2219
    Flags: bus master, fast devsel, latency 0

00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Kabini [Radeon HD 8330] (prog-if 00 [VGA controller])
    Subsystem: Lenovo Device 2219
    Flags: bus master, fast devsel, latency 0, IRQ 80
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f0000000 (64-bit, prefetchable) [size=8M]
    I/O ports at 4000 [size=256]
    Memory at f1500000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at f1560000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon

00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device 9840
    Subsystem: Lenovo Device 2219
    Flags: bus master, fast devsel, latency 0, IRQ 81
    Memory at f1540000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 0
    Flags: fast devsel

00:02.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1 (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=02, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: f1300000-f14fffff
    Prefetchable memory behind bridge: 00000000f0800000-00000000f08fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:02.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1 (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: f0b00000-f12fffff
    Prefetchable memory behind bridge: 00000000f0900000-00000000f09fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:02.5 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1 (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    Memory behind bridge: f0a00000-f0afffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 01) (prog-if 30 [XHCI])
    Subsystem: Lenovo Device 2219
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at f1548000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (prog-if 01 [AHCI 1.0])
    Subsystem: Lenovo Device 2219
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 79
    I/O ports at 4118 [size=8]
    I/O ports at 4124 [size=4]
    I/O ports at 4110 [size=8]
    I/O ports at 4120 [size=4]
    I/O ports at 4100 [size=16]
    Memory at f154c000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 39) (prog-if 10 [OHCI])
    Subsystem: Lenovo Device 2219
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at f154b000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci

00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39) (prog-if 20 [EHCI])
    Subsystem: Lenovo Device 2219
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at f154c500 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 39) (prog-if 10 [OHCI])
    Subsystem: Lenovo Device 2219
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at f154a000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci

00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39) (prog-if 20 [EHCI])
    Subsystem: Lenovo Device 2219
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at f154c400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 3a)
    Subsystem: Lenovo Device 2219
    Flags: 66MHz, medium devsel

00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 02)
    Subsystem: Lenovo Device 2219
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at f1544000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
    Subsystem: Lenovo Device 2219
    Flags: bus master, 66MHz, medium devsel, latency 0

00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 0
    Flags: fast devsel

00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 1
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 2
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 3
    Flags: fast devsel
    Capabilities: <access denied>
    Kernel driver in use: k10temp

00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 4
    Flags: fast devsel
    Kernel driver in use: fam15h_power

00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 5
    Flags: fast devsel

01:00.0 Network controller: Broadcom Corporation BCM43228 802.11a/b/g/n
    Subsystem: Broadcom Corporation Device 0607
    Flags: bus master, fast devsel, latency 0, IRQ 28
    Memory at f1300000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: wl

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 07)
    Subsystem: Lenovo Device 2219
    Flags: bus master, fast devsel, latency 0, IRQ 78
    I/O ports at 2000 [size=256]
    Memory at f0904000 (64-bit, prefetchable) [size=4K]
    Memory at f0900000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169

04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
    Subsystem: Lenovo Device 2219
    Flags: bus master, fast devsel, latency 0, IRQ 77
    Memory at f0a00000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: rtsx_pci

> $ cat /var/log/Xorg.0.log                                                    
[    73.646] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    73.646] X Protocol Version 11, Revision 0
[    73.646] Build Operating System: Linux 3.2.0-61-generic x86_64 Ubuntu
[    73.647] Current Operating System: Linux red 3.13.0-43-generic #72-Ubuntu SMP Mon Dec 8 19:35:06 UTC 2014 x86_64
[    73.647] Kernel command line: BOOT_IMAGE=/vmlinuz-3.13.0-43-generic root=/dev/mapper/xubuntu--vg-root ro quiet acpi_backlight=vendor thinkpad-acpi.brightness_enable=1
[    73.647] Build Date: 09 December 2014  11:14:53PM
[    73.647] xorg-server 2:1.15.1-0ubuntu2.5 (For technical support please see http://www.ubuntu.com/support) 
[    73.647] Current version of pixman: 0.30.2
[    73.647]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    73.647] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    73.647] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Dec 15 13:29:04 2014
[    73.694] (==) Using config file: "/etc/X11/xorg.conf"
[    73.694] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    73.887] (==) ServerLayout "aticonfig Layout"
[    73.887] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    73.887] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    73.889] (**) |   |-->Device "aticonfig-Device[0]-0"
[    73.889] (==) Automatically adding devices
[    73.889] (==) Automatically enabling devices
[    73.889] (==) Automatically adding GPU devices
[    73.965] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    73.965]     Entry deleted from font path.
[    74.147] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    74.147]     Entry deleted from font path.
[    74.147] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    74.147]     Entry deleted from font path.
[    74.147] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    built-ins
[    74.147] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    74.147] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    74.148] (II) Loader magic: 0x7f19646a5d40
[    74.148] (II) Module ABI versions:
[    74.148]     X.Org ANSI C Emulation: 0.4
[    74.148]     X.Org Video Driver: 15.0
[    74.148]     X.Org XInput driver : 20.0
[    74.148]     X.Org Server Extension : 8.0
[    74.148] (II) xfree86: Adding drm device (/dev/dri/card0)
[    74.151] (--) PCI:*(0:0:1:0) 1002:9832:17aa:2219 rev 0, Mem @ 0xe0000000/268435456, 0xf0000000/8388608, 0xf1500000/262144, I/O @ 0x00004000/256, BIOS @ 0x????????/131072
[    74.176] Initializing built-in extension Generic Event Extension
[    74.177] Initializing built-in extension SHAPE
[    74.177] Initializing built-in extension MIT-SHM
[    74.177] Initializing built-in extension XInputExtension
[    74.177] Initializing built-in extension XTEST
[    74.177] Initializing built-in extension BIG-REQUESTS
[    74.177] Initializing built-in extension SYNC
[    74.177] Initializing built-in extension XKEYBOARD
[    74.177] Initializing built-in extension XC-MISC
[    74.177] Initializing built-in extension SECURITY
[    74.177] Initializing built-in extension XINERAMA
[    74.177] Initializing built-in extension XFIXES
[    74.177] Initializing built-in extension RENDER
[    74.177] Initializing built-in extension RANDR
[    74.177] Initializing built-in extension COMPOSITE
[    74.177] Initializing built-in extension DAMAGE
[    74.177] Initializing built-in extension MIT-SCREEN-SAVER
[    74.177] Initializing built-in extension DOUBLE-BUFFER
[    74.177] Initializing built-in extension RECORD
[    74.177] Initializing built-in extension DPMS
[    74.177] Initializing built-in extension Present
[    74.177] Initializing built-in extension DRI3
[    74.177] Initializing built-in extension X-Resource
[    74.177] Initializing built-in extension XVideo
[    74.177] Initializing built-in extension XVideo-MotionCompensation
[    74.177] Initializing built-in extension SELinux
[    74.177] Initializing built-in extension XFree86-VidModeExtension
[    74.177] Initializing built-in extension XFree86-DGA
[    74.177] Initializing built-in extension XFree86-DRI
[    74.177] Initializing built-in extension DRI2
[    74.177] (II) "glx" will be loaded by default.
[    74.177] (WW) "xmir" is not to be loaded by default. Skipping.
[    74.177] (II) LoadModule: "glx"
[    74.535] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    75.249] (II) Module glx: vendor="X.Org Foundation"
[    75.249]     compiled for 1.15.1, module version = 1.0.0
[    75.249]     ABI class: X.Org Server Extension, version 8.0
[    75.249] (==) AIGLX enabled
[    75.249] Loading extension GLX
[    75.249] (II) LoadModule: "fglrx"
[    75.250] (WW) Warning, couldn't open module fglrx
[    75.250] (II) UnloadModule: "fglrx"
[    75.250] (II) Unloading fglrx
[    75.250] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    75.250] (==) Matched fglrx as autoconfigured driver 0
[    75.250] (==) Matched ati as autoconfigured driver 1
[    75.250] (==) Matched fglrx as autoconfigured driver 2
[    75.250] (==) Matched ati as autoconfigured driver 3
[    75.250] (==) Matched modesetting as autoconfigured driver 4
[    75.250] (==) Matched fbdev as autoconfigured driver 5
[    75.250] (==) Matched vesa as autoconfigured driver 6
[    75.250] (==) Assigned the driver to the xf86ConfigLayout
[    75.250] (II) LoadModule: "fglrx"
[    75.251] (WW) Warning, couldn't open module fglrx
[    75.251] (II) UnloadModule: "fglrx"
[    75.251] (II) Unloading fglrx
[    75.251] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    75.251] (II) LoadModule: "ati"
[    75.251] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    75.276] (II) Module ati: vendor="X.Org Foundation"
[    75.276]     compiled for 1.15.1, module version = 7.3.0
[    75.276]     Module class: X.Org Video Driver
[    75.276]     ABI class: X.Org Video Driver, version 15.0
[    75.276] (II) LoadModule: "radeon"
[    75.277] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    75.479] (II) Module radeon: vendor="X.Org Foundation"
[    75.479]     compiled for 1.15.1, module version = 7.3.0
[    75.479]     Module class: X.Org Video Driver
[    75.479]     ABI class: X.Org Video Driver, version 15.0
[    75.479] (II) LoadModule: "modesetting"
[    75.479] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    75.505] (II) Module modesetting: vendor="X.Org Foundation"
[    75.505]     compiled for 1.15.0, module version = 0.8.1
[    75.505]     Module class: X.Org Video Driver
[    75.505]     ABI class: X.Org Video Driver, version 15.0
[    75.505] (II) LoadModule: "fbdev"
[    75.505] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    75.547] (II) Module fbdev: vendor="X.Org Foundation"
[    75.547]     compiled for 1.15.0, module version = 0.4.4
[    75.547]     Module class: X.Org Video Driver
[    75.547]     ABI class: X.Org Video Driver, version 15.0
[    75.547] (II) LoadModule: "vesa"
[    75.548] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    75.580] (II) Module vesa: vendor="X.Org Foundation"
[    75.580]     compiled for 1.15.0, module version = 2.3.3
[    75.580]     Module class: X.Org Video Driver
[    75.580]     ABI class: X.Org Video Driver, version 15.0
[    75.580] (II) RADEON: Driver for ATI Radeon chipsets:
    ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
    ATI Radeon Mobility X300 (M24) 3152 (PCIE),
    ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
    ATI Radeon X600 (RV380) 3E50 (PCIE),
    ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
    ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
    ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
    ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
    ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
    ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
    ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
    ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
    ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
    ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
    ATI Radeon IGP330M/340M/350M (U2) 4337,
    ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
    ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
    ATI Radeon X800PRO (R420) JI (AGP),
    ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
    ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
    ATI Radeon Mobility 9800 (M18) JN (AGP),
    ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
    ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
    ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
    ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
    ATI Radeon Mobility M7 LW (AGP),
    ATI Mobility FireGL 7800 M7 LX (AGP),
    ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
    ATI FireGL Mobility 9000 (M9) Ld (AGP),
    ATI Radeon Mobility 9000 (M9) Lf (AGP),
    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
    ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
    ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
    ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
    ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
    ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
    ATI Radeon Mobility 9600 (M10) NQ (AGP),
    ATI Radeon Mobility 9600 (M11) NR (AGP),
    ATI Radeon Mobility 9600 (M10) NS (AGP),
    ATI FireGL Mobility T2 (M10) NT (AGP),
    ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
    ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
    ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
    ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
    ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
    ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
    ATI Radeon Mobility X300 (M22) 5460 (PCIE),
    ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
    ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
    ATI Radeon X800PRO (R423) UI (PCIE),
    ATI Radeon X800LE (R423) UJ (PCIE),
    ATI Radeon X800SE (R423) UK (PCIE),
    ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
    ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
    ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
    ATI FireGL unknown (R423) UR (PCIE),
    ATI FireGL unknown (R423) UT (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility Radeon X700 XL (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
    ATI Radeon Mobility 9100 IGP (U3) 5835,
    ATI Radeon XPRESS 200 5954 (PCIE),
    ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
    ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
    ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
    ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
    ATI Radeon XPRESS 200M 5975 (PCIE),
    ATI Radeon XPRESS 200 5A41 (PCIE),
    ATI Radeon XPRESS 200M 5A42 (PCIE),
    ATI Radeon XPRESS 200 5A61 (PCIE),
    ATI Radeon XPRESS 200M 5A62 (PCIE),
    ATI Radeon X300 (RV370) 5B60 (PCIE),
    ATI Radeon X600 (RV370) 5B62 (PCIE),
    ATI Radeon X550 (RV370) 5B63 (PCIE),
    ATI FireGL V3100 (RV370) 5B64 (PCIE),
    ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
    ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
    ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
    ATI Mobility Radeon X800 XT (M28) (PCIE),
    ATI Mobility FireGL V5100 (M28) (PCIE),
    ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
    ATI Radeon X850 XT PE (R480) (PCIE),
    ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
    ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
    ATI Radeon X850 XT (R480) (PCIE),
    ATI Radeon X800XT (R423) 5D57 (PCIE),
    ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
    ATI Radeon X700 PRO (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
    ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
    ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
    ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
    ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
    ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
    ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
    ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
    ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
    ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
    ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
    ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
    ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
    ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
    ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
    ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
    ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
    ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
    ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
    ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
    ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
    ATI Mobility Radeon X1700, ATI Radeon X2300HD,
    ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
    ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
    ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
    ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
    ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
    ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
    ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
    ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
    ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
    ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
    ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
    ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
    ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
    ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
    ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
    ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
    AMD FireStream 9250, ATI FirePro V8700 (FireGL),
    ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
    ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
    ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
    ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
    ATI Mobility Radeon HD 4670, ATI FirePro M5750,
    ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
    ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
    ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
    ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
    ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
    ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
    ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
    ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
    ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
    ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
    ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
    ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
    ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
    ATI Mobility Radeon HD 3850 X2, ATI RV670,
    ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
    ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
    ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
    ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
    ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
    ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
    ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI Radeon HD 2600 LE,
    ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
    ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
    ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
    ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
    ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
    ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
    ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
    ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
    ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
    ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
    SUMO, SUMO, SUMO2, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
    ATI Radeon 4100, ATI Mobility Radeon HD 4200,
    ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
    AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
    AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
    AMD Radeon HD 6300 Series Graphics,
    AMD Radeon HD 6200 Series Graphics, PALM, PALM, PALM, CYPRESS,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
    AMD Firestream 9350, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
    ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
    ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
    ATI Mobility Radeon Graphics, CEDAR,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
    ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
    CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
    BARTS, BARTS, Mobility Radeon HD 6000 Series,
    Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
    AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
    AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, TAHITI, TAHITI, TAHITI, TAHITI,
    TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI,
    TAHITI, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
    PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
    VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
    VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
    VERDE, VERDE, VERDE, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND,
    OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, HAINAN, HAINAN, HAINAN,
    HAINAN, HAINAN, HAINAN, BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE,
    BONAIRE, BONAIRE, BONAIRE, KABINI, KABINI, KABINI, KABINI, KABINI,
    KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI,
    KABINI, KABINI, KABINI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII,
    HAWAII, HAWAII, HAWAII, HAWAII
[    75.596] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    75.597] (II) FBDEV: driver for framebuffer: fbdev
[    75.597] (II) VESA: driver for VESA chipsets: vesa
[    75.597] (++) using VT number 7

[    75.630] (II) [KMS] Kernel modesetting enabled.
[    75.630] (WW) Falling back to old probe method for modesetting
[    75.630] (WW) Falling back to old probe method for fbdev
[    75.630] (II) Loading sub module "fbdevhw"
[    75.630] (II) LoadModule: "fbdevhw"
[    75.631] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    75.642] (II) Module fbdevhw: vendor="X.Org Foundation"
[    75.642]     compiled for 1.15.1, module version = 0.0.2
[    75.642]     ABI class: X.Org Video Driver, version 15.0
[    75.642] (WW) Falling back to old probe method for vesa
[    75.642] (**) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    75.642] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    75.642] (==) RADEON(0): Default visual is TrueColor
[    75.642] (==) RADEON(0): RGB weight 888
[    75.642] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    75.642] (--) RADEON(0): Chipset: "KABINI" (ChipID = 0x9832)
[    75.643] (II) Loading sub module "dri2"
[    75.643] (II) LoadModule: "dri2"
[    75.643] (II) Module "dri2" already built-in
[    75.643] (II) Loading sub module "glamoregl"
[    75.643] (II) LoadModule: "glamoregl"
[    75.643] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    75.742] (II) Module glamoregl: vendor="X.Org Foundation"
[    75.742]     compiled for 1.15.0, module version = 0.6.0
[    75.742]     ABI class: X.Org ANSI C Emulation, version 0.4
[    75.742] (II) glamor: OpenGL accelerated X.org driver based.
[    76.971] (II) glamor: EGL version 1.4 (DRI2):
[    77.066] (II) RADEON(0): glamor detected, initialising EGL layer.
[    77.066] (II) RADEON(0): KMS Color Tiling: disabled
[    77.066] (II) RADEON(0): KMS Color Tiling 2D: disabled
[    77.066] (II) RADEON(0): KMS Pageflipping: enabled
[    77.066] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    77.066] (II) RADEON(0): Output LVDS using monitor section aticonfig-Monitor[0]-0
[    77.069] (II) RADEON(0): Output HDMI-0 has no monitor section
[    77.092] (II) RADEON(0): Output VGA-0 has no monitor section
[    77.092] (II) RADEON(0): EDID for output LVDS
[    77.092] (II) RADEON(0): Manufacturer: IVO  Model: 489  Serial#: 0
[    77.092] (II) RADEON(0): Year: 2011  Week: 28
[    77.092] (II) RADEON(0): EDID Version: 1.3
[    77.092] (II) RADEON(0): Digital Display Input
[    77.092] (II) RADEON(0): Max Image Size [cm]: horiz.: 26  vert.: 14
[    77.092] (II) RADEON(0): Gamma: 2.20
[    77.092] (II) RADEON(0): No DPMS capabilities specified
[    77.093] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    77.093] (II) RADEON(0): First detailed timing is preferred mode
[    77.093] (II) RADEON(0): redX: 0.566 redY: 0.337   greenX: 0.324 greenY: 0.572
[    77.093] (II) RADEON(0): blueX: 0.156 blueY: 0.120   whiteX: 0.312 whiteY: 0.328
[    77.093] (II) RADEON(0): Manufacturer's mask: 0
[    77.093] (II) RADEON(0): Supported detailed timing:
[    77.093] (II) RADEON(0): clock: 69.7 MHz   Image Size:  256 x 144 mm
[    77.093] (II) RADEON(0): h_active: 1366  h_sync: 1386  h_sync_end 1406 h_blank_end 1478 h_border: 0
[    77.093] (II) RADEON(0): v_active: 768  v_sync: 770  v_sync_end 774 v_blanking: 786 v_border: 0
[    77.093] (II) RADEON(0):  InfoVision
[    77.093] (II) RADEON(0):  M116NWR1 R3
[    77.093] (II) RADEON(0): EDID (in hex):
[    77.093] (II) RADEON(0):     00ffffffffffff0026cf890400000000
[    77.093] (II) RADEON(0):     1c150103801a0e780a12309156539228
[    77.093] (II) RADEON(0):     1e505400000001010101010101010101
[    77.093] (II) RADEON(0):     0101010101013a1b5670500012301414
[    77.093] (II) RADEON(0):     24000090100000190000000000000000
[    77.093] (II) RADEON(0):     00000000000000000000000000fe0049
[    77.093] (II) RADEON(0):     6e666f566973696f6e0a2020000000fe
[    77.093] (II) RADEON(0):     004d3131364e575231205233200a0045
[    77.093] (II) RADEON(0): Printing probed modes for output LVDS
[    77.093] (II) RADEON(0): Modeline "1366x768"x60.0   69.70  1366 1386 1406 1478  768 770 774 786 -hsync -vsync (47.2 kHz eP)
[    77.093] (II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
[    77.093] (II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
[    77.093] (II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[    77.093] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    77.093] (II) RADEON(0): Modeline "848x480"x59.7   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync (29.8 kHz)
[    77.093] (II) RADEON(0): Modeline "720x480"x59.7   26.75  720 744 808 896  480 483 493 500 -hsync +vsync (29.9 kHz)
[    77.093] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    77.096] (II) RADEON(0): EDID for output HDMI-0
[    77.120] (II) RADEON(0): EDID for output VGA-0
[    77.120] (II) RADEON(0): Output LVDS connected
[    77.120] (II) RADEON(0): Output HDMI-0 disconnected
[    77.120] (II) RADEON(0): Output VGA-0 disconnected
[    77.120] (II) RADEON(0): Using exact sizes for initial modes
[    77.120] (II) RADEON(0): Output LVDS using initial mode 1366x768
[    77.120] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    77.120] (II) RADEON(0): mem size init: gart size :3fb7e000 vram size: s:20000000 visible:1fba0000
[    77.120] (==) RADEON(0): DPI set to (96, 96)
[    77.120] (II) Loading sub module "fb"
[    77.120] (II) LoadModule: "fb"
[    77.121] (II) Loading /usr/lib/xorg/modules/libfb.so
[    77.137] (II) Module fb: vendor="X.Org Foundation"
[    77.137]     compiled for 1.15.1, module version = 1.0.0
[    77.137]     ABI class: X.Org ANSI C Emulation, version 0.4
[    77.137] (II) Loading sub module "ramdac"
[    77.137] (II) LoadModule: "ramdac"
[    77.137] (II) Module "ramdac" already built-in
[    77.138] (II) UnloadModule: "modesetting"
[    77.138] (II) Unloading modesetting
[    77.138] (II) UnloadModule: "fbdev"
[    77.138] (II) Unloading fbdev
[    77.138] (II) UnloadSubModule: "fbdevhw"
[    77.138] (II) Unloading fbdevhw
[    77.138] (II) UnloadModule: "vesa"
[    77.138] (II) Unloading vesa
[    77.138] (--) Depth 24 pixmap format is 32 bpp
[    77.147] (II) RADEON(0): [DRI2] Setup complete
[    77.147] (II) RADEON(0): [DRI2]   DRI driver: radeonsi
[    77.148] (II) RADEON(0): [DRI2]   VDPAU driver: radeonsi
[    77.148] (II) RADEON(0): Front buffer size: 4224K
[    77.148] (II) RADEON(0): VRAM usage limit set to 463996K
[    77.149] (==) RADEON(0): Backing store enabled
[    77.149] (II) RADEON(0): Direct rendering enabled
[    77.474] (II) RADEON(0): Use GLAMOR acceleration.
[    77.474] (II) RADEON(0): Acceleration enabled
[    77.474] (**) RADEON(0): DPMS enabled
[    77.474] (==) RADEON(0): Silken mouse enabled
[    77.474] (II) RADEON(0): Set up textured video (glamor)
[    77.475] (II) RADEON(0): [XvMC] Associated with GLAMOR Textured Video.
[    77.475] (II) RADEON(0): [XvMC] Extension initialized.
[    77.475] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    77.475] (WW) RADEON(0): Option "RegistryDwords" is not used
[    77.475] (WW) RADEON(0): Option "VendorName" is not used
[    77.475] (WW) RADEON(0): Option "ModelName" is not used
[    77.475] (--) RandR disabled
[    77.488] (II) SELinux: Disabled on system
[    77.491] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    77.491] (II) AIGLX: enabled GLX_ARB_create_context
[    77.491] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    77.491] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    77.491] (II) AIGLX: enabled GLX_INTEL_swap_event
[    77.491] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    77.491] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    77.491] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    77.491] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    77.493] (II) AIGLX: Loaded and initialized radeonsi
[    77.493] (II) GLX: Initialized DRI2 GL provider for screen 0
[    77.542] (II) RADEON(0): Setting screen physical size to 361 x 203
[    77.643] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    77.669] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    77.669] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    77.669] (II) LoadModule: "evdev"
[    77.670] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    77.723] (II) Module evdev: vendor="X.Org Foundation"
[    77.723]     compiled for 1.15.0, module version = 2.8.2
[    77.723]     Module class: X.Org XInput Driver
[    77.723]     ABI class: X.Org XInput driver, version 20.0
[    77.723] (II) Using input driver 'evdev' for 'Power Button'
[    77.723] (**) Power Button: always reports core events
[    77.723] (**) evdev: Power Button: Device: "/dev/input/event3"
[    77.723] (--) evdev: Power Button: Vendor 0 Product 0x1
[    77.723] (--) evdev: Power Button: Found keys
[    77.723] (II) evdev: Power Button: Configuring as keyboard
[    77.723] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    77.723] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    77.723] (**) Option "xkb_rules" "evdev"
[    77.723] (**) Option "xkb_model" "pc105"
[    77.723] (**) Option "xkb_layout" "us"
[    77.725] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    77.725] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    77.725] (II) Using input driver 'evdev' for 'Video Bus'
[    77.725] (**) Video Bus: always reports core events
[    77.725] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    77.725] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    77.725] (--) evdev: Video Bus: Found keys
[    77.725] (II) evdev: Video Bus: Configuring as keyboard
[    77.725] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input7/event5"
[    77.725] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    77.725] (**) Option "xkb_rules" "evdev"
[    77.725] (**) Option "xkb_model" "pc105"
[    77.725] (**) Option "xkb_layout" "us"
[    77.726] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    77.726] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    77.726] (II) Using input driver 'evdev' for 'Power Button'
[    77.726] (**) Power Button: always reports core events
[    77.726] (**) evdev: Power Button: Device: "/dev/input/event0"
[    77.726] (--) evdev: Power Button: Vendor 0 Product 0x1
[    77.726] (--) evdev: Power Button: Found keys
[    77.726] (II) evdev: Power Button: Configuring as keyboard
[    77.726] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    77.726] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    77.726] (**) Option "xkb_rules" "evdev"
[    77.726] (**) Option "xkb_model" "pc105"
[    77.726] (**) Option "xkb_layout" "us"
[    77.728] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[    77.728] (II) No input driver specified, ignoring this device.
[    77.728] (II) This device may have been added with another device file.
[    77.728] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    77.728] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    77.728] (II) Using input driver 'evdev' for 'Sleep Button'
[    77.728] (**) Sleep Button: always reports core events
[    77.728] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    77.728] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    77.728] (--) evdev: Sleep Button: Found keys
[    77.728] (II) evdev: Sleep Button: Configuring as keyboard
[    77.728] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[    77.729] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    77.729] (**) Option "xkb_rules" "evdev"
[    77.729] (**) Option "xkb_model" "pc105"
[    77.729] (**) Option "xkb_layout" "us"
[    77.729] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:01.0/drm/card0
[    77.729] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    77.730] (II) config/udev: Adding input device HD-Audio Generic HDMI/DP,pcm=3 (/dev/input/event10)
[    77.730] (II) No input driver specified, ignoring this device.
[    77.730] (II) This device may have been added with another device file.
[    77.731] (II) config/udev: Adding input device HD-Audio Generic HDMI/DP,pcm=7 (/dev/input/event9)
[    77.731] (II) No input driver specified, ignoring this device.
[    77.731] (II) This device may have been added with another device file.
[    77.731] (II) config/udev: Adding input device Integrated Camera (/dev/input/event13)
[    77.731] (**) Integrated Camera: Applying InputClass "evdev keyboard catchall"
[    77.731] (II) Using input driver 'evdev' for 'Integrated Camera'
[    77.732] (**) Integrated Camera: always reports core events
[    77.732] (**) evdev: Integrated Camera: Device: "/dev/input/event13"
[    77.732] (--) evdev: Integrated Camera: Vendor 0x5986 Product 0x299
[    77.732] (--) evdev: Integrated Camera: Found keys
[    77.732] (II) evdev: Integrated Camera: Configuring as keyboard
[    77.732] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.2/usb2/2-1/2-1:1.0/input/input20/event13"
[    77.732] (II) XINPUT: Adding extended input device "Integrated Camera" (type: KEYBOARD, id 10)
[    77.732] (**) Option "xkb_rules" "evdev"
[    77.732] (**) Option "xkb_model" "pc105"
[    77.732] (**) Option "xkb_layout" "us"
[    77.733] (II) config/udev: Adding input device HD-Audio Generic Mic (/dev/input/event12)
[    77.733] (II) No input driver specified, ignoring this device.
[    77.733] (II) This device may have been added with another device file.
[    77.734] (II) config/udev: Adding input device HD-Audio Generic Headphone (/dev/input/event11)
[    77.734] (II) No input driver specified, ignoring this device.
[    77.734] (II) This device may have been added with another device file.
[    77.734] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    77.734] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    77.734] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    77.734] (**) AT Translated Set 2 keyboard: always reports core events
[    77.734] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    77.734] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    77.734] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    77.734] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    77.734] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    77.735] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[    77.735] (**) Option "xkb_rules" "evdev"
[    77.735] (**) Option "xkb_model" "pc105"
[    77.735] (**) Option "xkb_layout" "us"
[    77.736] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
[    77.736] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    77.736] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    77.736] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    77.736] (II) LoadModule: "synaptics"
[    77.736] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    77.747] (II) Module synaptics: vendor="X.Org Foundation"
[    77.747]     compiled for 1.15.0, module version = 1.7.4
[    77.747]     Module class: X.Org XInput Driver
[    77.747]     ABI class: X.Org XInput driver, version 20.0
[    77.747] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    77.748] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    77.748] (**) Option "Device" "/dev/input/event6"
[    77.764] (II) synaptics: SynPS/2 Synaptics TouchPad: found clickpad property
[    77.764] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5766 (res 65)
[    77.764] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 5260 (res 180)
[    77.764] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    77.764] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    77.764] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left double triple
[    77.764] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    77.764] (**) Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
[    77.764] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    77.764] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    77.780] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input13/event6"
[    77.780] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 12)
[    77.780] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    77.780] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    77.780] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.035
[    77.781] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    77.781] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    77.781] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    77.781] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    77.781] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    77.782] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    77.782] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    77.782] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/event7)
[    77.782] (**) TPPS/2 IBM TrackPoint: Applying InputClass "evdev pointer catchall"
[    77.782] (**) TPPS/2 IBM TrackPoint: Applying InputClass "trackpoint catchall"
[    77.782] (II) Using input driver 'evdev' for 'TPPS/2 IBM TrackPoint'
[    77.782] (**) TPPS/2 IBM TrackPoint: always reports core events
[    77.782] (**) evdev: TPPS/2 IBM TrackPoint: Device: "/dev/input/event7"
[    77.782] (--) evdev: TPPS/2 IBM TrackPoint: Vendor 0x2 Product 0xa
[    77.783] (--) evdev: TPPS/2 IBM TrackPoint: Found 3 mouse buttons
[    77.783] (--) evdev: TPPS/2 IBM TrackPoint: Found relative axes
[    77.783] (--) evdev: TPPS/2 IBM TrackPoint: Found x and y relative axes
[    77.783] (II) evdev: TPPS/2 IBM TrackPoint: Configuring as mouse
[    77.783] (**) Option "Emulate3Buttons" "true"
[    77.783] (**) Option "EmulateWheel" "true"
[    77.783] (**) Option "EmulateWheelButton" "2"
[    77.783] (**) Option "YAxisMapping" "4 5"
[    77.783] (**) evdev: TPPS/2 IBM TrackPoint: YAxisMapping: buttons 4 and 5
[    77.783] (**) Option "XAxisMapping" "6 7"
[    77.783] (**) evdev: TPPS/2 IBM TrackPoint: XAxisMapping: buttons 6 and 7
[    77.783] (**) evdev: TPPS/2 IBM TrackPoint: EmulateWheelButton: 2, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    77.783] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/serio5/input/input14/event7"
[    77.783] (II) XINPUT: Adding extended input device "TPPS/2 IBM TrackPoint" (type: MOUSE, id 13)
[    77.783] (II) evdev: TPPS/2 IBM TrackPoint: initialized for relative axes.
[    77.784] (**) TPPS/2 IBM TrackPoint: (accel) keeping acceleration scheme 1
[    77.784] (**) TPPS/2 IBM TrackPoint: (accel) acceleration profile 0
[    77.784] (**) TPPS/2 IBM TrackPoint: (accel) acceleration factor: 2.000
[    77.784] (**) TPPS/2 IBM TrackPoint: (accel) acceleration threshold: 4
[    77.784] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/mouse1)
[    77.784] (II) No input driver specified, ignoring this device.
[    77.784] (II) This device may have been added with another device file.
[    77.789] (II) config/udev: Adding input device ThinkPad Extra Buttons (/dev/input/event8)
[    77.789] (**) ThinkPad Extra Buttons: Applying InputClass "evdev keyboard catchall"
[    77.789] (II) Using input driver 'evdev' for 'ThinkPad Extra Buttons'
[    77.789] (**) ThinkPad Extra Buttons: always reports core events
[    77.789] (**) evdev: ThinkPad Extra Buttons: Device: "/dev/input/event8"
[    77.789] (--) evdev: ThinkPad Extra Buttons: Vendor 0x17aa Product 0x5054
[    77.789] (--) evdev: ThinkPad Extra Buttons: Found keys
[    77.789] (II) evdev: ThinkPad Extra Buttons: Configuring as keyboard
[    77.789] (**) Option "config_info" "udev:/sys/devices/platform/thinkpad_acpi/input/input15/event8"
[    77.789] (II) XINPUT: Adding extended input device "ThinkPad Extra Buttons" (type: KEYBOARD, id 14)
[    77.789] (**) Option "xkb_rules" "evdev"
[    77.789] (**) Option "xkb_model" "pc105"
[    77.789] (**) Option "xkb_layout" "us"
[   103.467] (II) RADEON(0): EDID vendor "IVO", prod id 1161
[   103.467] (II) RADEON(0): Printing DDC gathered Modelines:
[   103.467] (II) RADEON(0): Modeline "1366x768"x0.0   69.70  1366 1386 1406 1478  768 770 774 786 -hsync -vsync (47.2 kHz eP)
[   103.513] (II) RADEON(0): EDID vendor "IVO", prod id 1161
[   103.513] (II) RADEON(0): Printing DDC gathered Modelines:
[   103.513] (II) RADEON(0): Modeline "1366x768"x0.0   69.70  1366 1386 1406 1478  768 770 774 786 -hsync -vsync (47.2 kHz eP)



```

---

### Post by presence2 on 2014-12-19
I'm sorry I can't help I still have this issue.

I've been using

```

sudo shutdown -P now

```

I take far less screen shots than I used to because of it (screenshot is the only other thing effected), which impairs my ability to do business.

---

### Post by callnow8448138225 on 2014-12-20
Also i have the same problem, if anyone know the solution please reply me.

---

### Post by jds2 on 2014-12-22
For the other people having this problem: what happens when you select a range of cells in gnumeric and copy it? It should draw a little animated border around the range you copied. When this border is visible, Xorg pushes one of the CPU cores to 100% (so 25% CPU usage as noted above) and gnumeric becomes sluggish. I'm interested in knowing if anyone else is getting this problem.

---

### Post by presence2 on 2014-12-28
> **jds2 said:**
>  You can get the machine 'unstuck' by doing Ctrl-Alt-F1 and then then Ctrl-Alt-F7 to switch out and back into the Xorg session.


Works great for shutdown... probably my fastest shutdown solution.   

Not so good for screenshot; it leaves the screen distorted/tiled for the screenshot.

---

