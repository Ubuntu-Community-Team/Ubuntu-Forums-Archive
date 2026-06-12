---
title: "Secondary display doesn't work"
date: 2019-12-03
forum: Desktop Environments
---

### Post by namjjd on 2019-12-03
I have been trying to get my secondary monitor (View Sonic VG2755-2K) connected and detected. I'm using a ubuntu 18 set up, and i3.

Things I tried:
- Installing lightdm
- Purging and reinstalling nvidia drivers
- Deleting xorg.conf

After trying those things, my computer is now unable to detect the secondary monitor. Any advice is welcome! Thank you![B] 


uname -a
[/B]
```
Linux man 5.0.0-36-generic #39~18.04.1-Ubuntu SMP Tue Nov 12 11:09:50 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
```

**lspci -v**

```
00:00.0 Host bridge: Intel Corporation 8th Gen Core Processor Host Bridge/DRAM Registers (rev 07)
    Subsystem: Device 1d05:105f
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: skl_uncore

00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16) (rev 07) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 122
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00006000-00006fff
    Memory behind bridge: a5000000-a60fffff
    Prefetchable memory behind bridge: 0000000090000000-00000000a20fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:02.0 VGA compatible controller: Intel Corporation Device 3e9b (prog-if 00 [VGA controller])
    Subsystem: Device 1d05:105f
    Flags: bus master, fast devsel, latency 0, IRQ 156
    Memory at a4000000 (64-bit, non-prefetchable) [size=16M]
    Memory at 80000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 7000 [size=64]
    [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:12.0 Signal processing controller: Intel Corporation Cannon Lake PCH Thermal Controller (rev 10)
    Subsystem: Device 1d05:105f
    Flags: fast devsel, IRQ 16
    Memory at a7723000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: intel_pch_thermal
    Kernel modules: intel_pch_thermal

00:14.0 USB controller: Intel Corporation Cannon Lake PCH USB 3.1 xHCI Host Controller (rev 10) (prog-if 30 [XHCI])
    Subsystem: Device 1d05:105f
    Flags: bus master, medium devsel, latency 0, IRQ 126
    Memory at a7700000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

00:14.2 RAM memory: Intel Corporation Cannon Lake PCH Shared SRAM (rev 10)
    Subsystem: Device 1d05:105f
    Flags: fast devsel
    Memory at a771a000 (64-bit, non-prefetchable) [disabled] [size=8K]
    Memory at a7722000 (64-bit, non-prefetchable) [disabled] [size=4K]
    Capabilities: <access denied>

00:14.3 Network controller: Intel Corporation Wireless-AC 9560 [Jefferson Peak] (rev 10)
    Subsystem: Intel Corporation Device 0034
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at a7714000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi

00:15.0 Serial bus controller [0c80]: Intel Corporation Device a368 (rev 10)
    Subsystem: Device 1d05:105f
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at a2100000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: intel-lpss
    Kernel modules: intel_lpss_pci

00:16.0 Communication controller: Intel Corporation Cannon Lake PCH HECI Controller (rev 10)
    Subsystem: Device 1d05:105f
    Flags: bus master, fast devsel, latency 0, IRQ 130
    Memory at a7720000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: mei_me
    Kernel modules: mei_me

00:17.0 SATA controller: Intel Corporation Device a353 (rev 10) (prog-if 01 [AHCI 1.0])
    Subsystem: Device 1d05:105f
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 129
    Memory at a7718000 (32-bit, non-prefetchable) [size=8K]
    Memory at a771f000 (32-bit, non-prefetchable) [size=256]
    I/O ports at 7090 [size=8]
    I/O ports at 7080 [size=4]
    I/O ports at 7060 [size=32]
    Memory at a771e000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1b.0 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port 21 (rev f0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 123
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: a6c00000-a75fffff
    Prefetchable memory behind bridge: 00000000a2c00000-00000000a35fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1d.0 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port 9 (rev f0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 124
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: a6200000-a6bfffff
    Prefetchable memory behind bridge: 00000000a2200000-00000000a2bfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1d.5 PCI bridge: Intel Corporation Device a335 (rev f0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 125
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: a7600000-a76fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1e.0 Communication controller: Intel Corporation Device a328 (rev 10)
    Subsystem: Device 1d05:105f
    Flags: bus master, fast devsel, latency 0, IRQ 20
    Memory at a2101000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: intel-lpss
    Kernel modules: intel_lpss_pci

00:1f.0 ISA bridge: Intel Corporation Device a30d (rev 10)
    Subsystem: Device 1d05:105f
    Flags: bus master, medium devsel, latency 0

00:1f.3 Audio device: Intel Corporation Cannon Lake PCH cAVS (rev 10)
    Subsystem: Device 1d05:105f
    Flags: bus master, fast devsel, latency 32, IRQ 157
    Memory at a7710000 (64-bit, non-prefetchable) [size=16K]
    Memory at a6100000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel, snd_soc_skl

00:1f.4 SMBus: Intel Corporation Cannon Lake PCH SMBus Controller (rev 10)
    Subsystem: Device 1d05:105f
    Flags: medium devsel, IRQ 255
    Memory at a771c000 (64-bit, non-prefetchable) [size=256]
    I/O ports at efa0 [size=32]
    Kernel modules: i2c_i801

00:1f.5 Serial bus controller [0c80]: Intel Corporation Cannon Lake PCH SPI Controller (rev 10)
    Subsystem: Device 1d05:105f
    Flags: fast devsel
    Memory at fe010000 (32-bit, non-prefetchable) [size=4K]

01:00.0 VGA compatible controller: NVIDIA Corporation Device 1f11 (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Device 1d05:105f
    Flags: fast devsel, IRQ 255
    Memory at a5000000 (32-bit, non-prefetchable) [disabled] [size=16M]
    Memory at 90000000 (64-bit, prefetchable) [disabled] [size=256M]
    Memory at a0000000 (64-bit, prefetchable) [disabled] [size=32M]
    I/O ports at 6000 [disabled] [size=128]
    Expansion ROM at a6000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel modules: nvidiafb, nouveau

01:00.1 Audio device: NVIDIA Corporation Device 10f9 (rev a1)
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at a6080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

01:00.2 USB controller: NVIDIA Corporation Device 1ada (rev a1) (prog-if 30 [XHCI])
    Flags: bus master, fast devsel, latency 0, IRQ 132
    Memory at a2000000 (64-bit, prefetchable) [size=256K]
    Memory at a2040000 (64-bit, prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

01:00.3 Serial bus controller [0c80]: NVIDIA Corporation Device 1adb (rev a1)
    Flags: bus master, fast devsel, latency 0, IRQ 128
    Memory at a6084000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia-gpu
    Kernel modules: i2c_nvidia_gpu

02:00.0 Non-Volatile memory controller: Device 1987:5012 (rev 01) (prog-if 02 [NVM Express])
    Subsystem: Device 1987:5012
    Physical Slot: 24
    Flags: bus master, fast devsel, latency 0, IRQ 16, NUMA node 0
    Memory at a6c00000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: nvme
    Kernel modules: nvme

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
    Subsystem: Device 1d05:105f
    Flags: bus master, fast devsel, latency 0, IRQ 17
    I/O ports at 3000 [size=256]
    Memory at a7604000 (64-bit, non-prefetchable) [size=4K]
    Memory at a7600000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169
```

**/usr/share/X11/xorg.conf.d/10-nvidia.conf**

```
Section "OutputClass"
    Identifier "nvidia"
    MatchDriver "nvidia-drm"
    Driver "nvidia"
    Option "AllowEmptyInitialConfiguration"
    ModulePath "/usr/lib/x86_64-linux-gnu/nvidia/xorg"
EndSection

```



[B]/usr/share/X11/xorg.conf.d/11-nvidia-prime.conf
[/B]
```
Section "OutputClass"
    Identifier "Nvidia Prime"
    MatchDriver "nvidia-drm"
    Driver "nvidia"
    Option "AllowEmptyInitialConfiguration"
    Option "IgnoreDisplayDevices" "CRT"
    Option "PrimaryGPU" "Yes"
    ModulePath "/x86_64-linux-gnu/nvidia/xorg"
EndSection
```

[B]cvt 1440 900
[/B]
```
# 1440x900 59.89 Hz (CVT 1.30MA) hsync: 55.93 kHz; pclk: 106.50 MHz
Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
```

**xrandr**

```
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
eDP-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1920x1080    144.00*+  60.01    59.97    59.96    60.00    59.93  
   1680x1050     84.94    74.89    69.88    59.95    59.88  
   1600x1024     60.17  
   1400x1050     85.00    74.76    70.00    59.98  
   1600x900      59.99    59.94    59.95    59.82  
   1280x1024     85.02    75.02    60.02  
   1440x900      59.89  
   1400x900      59.96    59.88  
   1280x960      85.00    60.00  
   1440x810      60.00    59.97  
   1368x768      59.88    59.85  
   1360x768      59.80    59.96  
   1280x800      59.99    59.97    59.81    59.91  
   1152x864     100.00    85.06    85.00    75.00    75.00    70.00    60.00  
   1280x720      60.00    59.99    59.86    59.74  
   1024x768      85.00    75.05    60.04    85.00    75.03    70.07    60.00  
   1024x768i     86.96  
   960x720       85.00    75.00    60.00  
   928x696       75.00    60.05  
   896x672       75.05    60.01  
   1024x576      59.95    59.96    59.90    59.82  
   960x600       59.93    60.00  
   832x624       74.55  
   960x540       59.96    59.99    59.63    59.82  
   800x600       85.00    75.00    70.00    65.00    60.00    85.14    72.19    75.00    60.32    56.25  
   840x525       85.02    74.96    69.88    60.01    59.88  
   864x486       59.92    59.57  
   800x512       60.17  
   700x525       85.08    74.76    70.06    59.98  
   800x450       59.95    59.82  
   640x512       85.02    75.02    60.02  
   720x450       59.89  
   700x450       59.96    59.88  
   640x480       85.09    60.00    85.01    72.81    75.00    59.94  
   720x405       59.51    58.99  
   720x400       85.04  
   684x384       59.88    59.85  
   680x384       59.80    59.96  
   640x400       59.88    59.98    85.08  
   576x432      100.11    85.15    85.09    75.00    75.00    70.00    60.06  
   640x360       59.86    59.83    59.84    59.32  
   640x350       85.08  
   512x384       85.00    75.03    70.07    60.00  
   512x384i      87.06  
   512x288       60.00    59.92  
   416x312       74.66  
   480x270       59.63    59.82  
   400x300       85.27    72.19    75.12    60.32    56.34  
   432x243       59.92    59.57  
   320x240       85.18    72.81    75.00    60.05  
   360x202       59.51    59.13  
   360x200       85.04  
   320x200       85.27  
   320x180       59.84    59.32  
   320x175       85.27  

```


**sudo lshw -c video**
```

  *-display UNCLAIMED       
       description: VGA compatible controller
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller cap_list
       configuration: latency=0
       resources: memory:a5000000-a5ffffff memory:90000000-9fffffff memory:a0000000-a1ffffff ioport:6000(size=128) memory:a6000000-a607ffff
  *-display
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:156 memory:a4000000-a4ffffff memory:80000000-8fffffff ioport:7000(size=64) memory:c0000-dffff
```

---

### Post by wildmanne39 on 2019-12-03
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end, if you are editing a post to add code tags click the edit button then click the go advanced button, highlight the code then select the # symbol from the tool bar.

---

