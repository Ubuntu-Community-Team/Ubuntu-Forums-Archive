---
title: "HP Pro 3420 video problem"
date: 2020-08-12
forum: Desktop Environments
---

### Post by gorwell1984 on 2020-08-12
Hello.
I installed ubuntu 20 on my HP Pro 3420 All-in-One PC.
When using a graphics accelerator, the display constantly flashing in stripes. Like this:
[https://www.youtube.com/watch?v=0Cd-8VvTplU](https://www.youtube.com/watch?v=0Cd-8VvTplU)
[https://www.youtube.com/watch?v=aizzVMtmT_I](https://www.youtube.com/watch?v=aizzVMtmT_I)
If you enable nomodeset, then this problem disappears, but the resolution becomes 800 * 600. This solution is completely unacceptable for work.
Please help me solve the problem, I could not find a solution.


```
root@test:~# dmesg | grep -i intel
[    0.000000]   Intel GenuineIntel
[    0.028608] Reserving Intel graphics memory at [mem 0xbba00000-0xbf9fffff]
[    0.097619] smpboot: CPU0: Intel(R) Pentium(R) CPU G630 @ 2.70GHz (family: 0x6, model: 0x2a, stepping: 0x7)
[    0.097720] Performance Events: PEBS fmt1+, SandyBridge events, 16-deep LBR, full-width counters, Intel PMU driver.
[    0.548345] intel_idle: MWAIT substates: 0x1120
[    0.548346] intel_idle: v0.4.1 model 0x2A
[    0.548414] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.594083] intel_pstate: Intel P-state driver initializing
[   11.899061] fb0: switching to inteldrmfb from EFI VGA
[   12.839826] snd_hda_intel 0000:00:1b.0: enabling device (0100 -> 0102)
[   12.941378] intel_rapl_common: Found RAPL domain package
[   12.941380] intel_rapl_common: Found RAPL domain core
[   12.941381] intel_rapl_common: Found RAPL domain uncore
[   12.941386] intel_rapl_common: RAPL package-0 domain package locked by BIOS
[   14.253589] snd_hda_intel 0000:00:1b.0: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[   14.401477] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   14.402543] input: HDA Intel PCH Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   14.402647] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
root@test:~#

root@test:~# lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H61 Express Chipset LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port Desktop SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Network controller: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
root@test:~#

root@test:~# lspci -knn | grep -i '3d\|vga' -A3
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0102] (rev 09)
        DeviceName:  Onboard IGD
        Subsystem: Hewlett-Packard Company 2nd Generation Core Processor Family Integrated Graphics Controller [103c:2ac5]
        Kernel driver in use: i915


```

---

### Post by GhX6GZMB on 2020-08-12
As you seem to have Intel graphics, this might help:

In:
```
[COLOR=#000000]/usr/share/X11/xorg.conf.d/20-intel.conf[/COLOR]
```
Enter:
```
Section "OutputClass"
    Identifier "Intel"
    MatchDriver "intel"
    Driver "intel"
    [COLOR=#ff0000]Option "tearfree" "on"[/COLOR]
EndSection
```

But 'lshw' would provide more information.

---

### Post by gorwell1984 on 2020-08-13
Thanks for your reply.

```

root@uTest:~# ll /usr/share/X11/xorg.conf.d/
total 28
drwxr-xr-x 2 root root 4096 &#1072;&#1074;&#1075; 13 11:18 ./
drwxr-xr-x 5 root root 4096 &#1072;&#1087;&#1088; 23 10:37 ../
-rw-r--r-- 1 root root   92 &#1086;&#1082;&#1090; 22  2019 10-amdgpu.conf
-rw-r--r-- 1 root root 1350 &#1080;&#1102;&#1085; 24 09:00 10-quirks.conf
-rw-r--r-- 1 root root   92 &#1086;&#1082;&#1090; 22  2019 10-radeon.conf
-rw-r--r-- 1 root root 1429 &#1072;&#1074;&#1075; 13  2019 40-libinput.conf
-rw-r--r-- 1 root root 3458 &#1084;&#1072;&#1088; 11 11:56 70-wacom.conf

```

```
root@uTest:~# hwinfo --framebuffer
02: None 00.0: 11001 VESA Framebuffer
  [Created at bios.459]
  Unique ID: rdCR.QgFYtsmQZBC
  Hardware Class: framebuffer
  Model: "Intel(R) Sandybridge/Ivybridge Graphics Controller"
  Vendor: "Intel Corporation"
  Device: "Intel(R) Sandybridge/Ivybridge Graphics Controller"
  SubVendor: "Intel(R) Sandybridge/Ivybridge Graphics Chipset Accelerated VGA BIOS"
  SubDevice:
  Revision: "Hardware Version 0.0"
  Memory Size: 63 MB + 960 kB
  Memory Range: 0x00000000-0x03feffff (rw)
  Mode 0x0360: 1600x900 (+1600), 8 bits
  Mode 0x0361: 1600x900 (+3200), 16 bits
  Mode 0x0362: 1600x900 (+6400), 24 bits
  Mode 0x033c: 1920x1440 (+1920), 8 bits
  Mode 0x034d: 1920x1440 (+3840), 16 bits
  Mode 0x035c: 1920x1440 (+7680), 24 bits
  Mode 0x033a: 1600x1200 (+1600), 8 bits
  Mode 0x034b: 1600x1200 (+3200), 16 bits
  Mode 0x035a: 1600x1200 (+6400), 24 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+832), 8 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x037d: 0x0 (+0), 8 bits
  Mode 0x037e: 0x0 (+0), 16 bits
  Mode 0x037f: 0x0 (+0), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

```
root@uTest:~# hwinfo --short
cpu:
                       Intel(R) Pentium(R) CPU G630 @ 2.70GHz, 2142 MHz
                       Intel(R) Pentium(R) CPU G630 @ 2.70GHz, 2240 MHz
keyboard:
  /dev/input/event4    Colorado HP PR1101U / Primax PMX-KPR1101U Keyboard
  /dev/input/event2    AT Translated Set 2 keyboard
mouse:
  /dev/input/mice      Colorado HP Optical Mouse
monitor:
                       HP Omni / Pro
graphics card:
                       Intel 2nd Generation Core Processor Family Integrated Graphics Controller
sound:
                       Intel 6 Series/C200 Series Chipset Family High Definition Audio Controller
storage:
                       Floppy disk controller
                       Intel 6 Series/C200 Series Chipset Family 6 port Desktop SATA AHCI Controller
network:
  enp3s0               Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
  wlp2s0               Ralink RT5390 Wireless 802.11n 1T/1R PCIe
network interface:
  lo                   Loopback network interface
  enp3s0               Ethernet network interface
  wlp2s0               Ethernet network interface
disk:
  /dev/sda             Hitachi HDS72105
partition:
  /dev/sda1            Partition
  /dev/sda2            Partition
cdrom:
  /dev/sr0             hp DVD A  DS8A5SH
usb controller:
                       Intel 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
                       Intel 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
bios:
                       BIOS
bridge:
                       Intel 6 Series/C200 Series Chipset Family PCI Express Root Port 1
                       Intel H61 Express Chipset LPC Controller
                       Intel 6 Series/C200 Series Chipset Family PCI Express Root Port 6
                       Intel 6 Series/C200 Series Chipset Family PCI Express Root Port 4
                       Intel 2nd Generation Core Processor Family DRAM Controller
                       Intel 6 Series/C200 Series Chipset Family PCI Express Root Port 3
hub:
                       Intel Integrated Rate Matching Hub
                       Linux Foundation 2.0 root hub
                       Intel Integrated Rate Matching Hub
                       Linux Foundation 2.0 root hub
memory:
                       Main Memory
unknown:
                       FPU
                       DMA controller
                       PIC
                       Keyboard controller
                       PS/2 Controller
                       Intel 6 Series/C200 Series Chipset Family MEI Controller #1
                       Intel 6 Series/C200 Series Chipset Family SMBus Controller
                       Realtek RTS5209 PCI Express Card Reader
                       Chicony Electronics HP 0.3MP Webcam
  /dev/input/event5    Colorado HP PR1101U / Primax PMX-KPR1101U Keyboard

```

```
root@uTest:~# lshw -class video
  *-display
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:32 memory:fe000000-fe3fffff memory:c0000000-cfffffff ioport:f000(size=64) memory:c0000-dffff


```

---

### Post by GhX6GZMB on 2020-08-13
You may have to create the file
[COLOR=#000000]/usr/share/X11/xorg.conf.d/20-intel.conf[/COLOR]

---

### Post by gorwell1984 on 2020-08-14
It's doesnt work.

---

### Post by CelticWarrior on 2020-08-14
> **gorwell1984 said:**
> It's doesnt work.

What exactly?

---

### Post by GhX6GZMB on 2020-08-14
> **CelticWarrior said:**
> What exactly?

Indeed.

There was an error in my earlier post. The file:
```
/usr/share/X11/xorg.conf.d/20-intel.conf
```

should contain:
```
Section "OutputClass"
    Identifier "Intel Graphics"
    MatchDriver "intel"
    Driver "intel"
    [COLOR=#ff0000]Option "tearfree" "on"[/COLOR]
EndSection
```

with access rights 644 root:root

Like I said, you probably need to create it.

More info: [https://wiki.archlinux.org/index.php/intel_graphics](https://wiki.archlinux.org/index.php/intel_graphics)

---

