---
title: "Wireless issues, i217-V."
date: 2017-01-26
forum: Debian
---

### Post by kolkolkol on 2017-01-26
Hi all, first post here. Im Ivan, its nice to meet.  :D 

So i finally came to install Debian Jessie stable, and it's good to be back.
My installation is brand new and i have not a wired connection avalaible, so ill have to make things works nowired.

As the title say, my card is an _Intel i217-V_, which in the beginning was not recognized at all by the OS. 
That was normal and expected, because in the installation phase Debian told that i was missing firmware files *named rtlwifi/rtl8821aefw.bin*. 
After a few search i came to download from windows (im in a dual boot system) the following packages: _firmware-iwlwifi_0.43_all.deb_ and _firmware-realtek_0.43_all.deb_. 
I also installed this driver, that seems to fit in for my net card: [https://downloadcenter.intel.com/download/15817/Intel-Network-Adapter-Driver-for-PCI-E-Gigabit-Network-Connections-under-Linux-](https://downloadcenter.intel.com/download/15817/Intel-Network-Adapter-Driver-for-PCI-E-Gigabit-Network-Connections-under-Linux-)
That made my OS _"graphically"_recognize the net card and made me able to see avalaible connections trough it. And that, for instance, it is not completely true because at the present day connections appear just for a while, like 3 or 4 minutes after the boot, then totally disappear and i have to reboot to see them again.
I'm able to see my home wifi connection among others, but can't connect to it.

Heres my **ifconfig **
```
root@kkk:/home/kolkolkol# ifconfig
eth0      Link encap:Ethernet  HWaddr 1c:87:2c:cc:97:f7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f7200000-f7220000 

eth0:avahi Link encap:Ethernet  HWaddr 1c:87:2c:cc:97:f7  
          inet addr:169.254.11.115  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:20 Memory:f7200000-f7220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:31 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3317 (3.2 KiB)  TX bytes:3317 (3.2 KiB)

wlan0     Link encap:Ethernet  HWaddr dc:85:de:ef:dd:31  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

**iwconfig**
```
root@kkk:/home/kolkolkol# sudo iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          
eth0      no wireless extensions.
```
As i understood there isnt any statement on this about my netcard. Like eth1, 2, etcetera. Am i right?

**interfaces**
```
/etc/network/interfaces/
/etc/network/interfaces/
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
allow-hotplug eth0
iface eth0 inet dhcp

```

and **lspci -v**
```
00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device 8534
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel driver in use: hsw_uncore

00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: f6000000-f70fffff
    Prefetchable memory behind bridge: 00000000e8000000-00000000f1ffffff
    Capabilities: [88] Subsystem: ASUSTeK Computer Inc. Device 8534
    Capabilities: [80] Power Management version 3
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [a0] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [140] Root Complex Link
    Kernel driver in use: pcieport

00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05) (prog-if 30 [XHCI])
    Subsystem: ASUSTeK Computer Inc. Device 8534
    Flags: bus master, medium devsel, latency 0, IRQ 42
    Memory at f7220000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [70] Power Management version 2
    Capabilities: [80] MSI: Enable+ Count=1/8 Maskable- 64bit+
    Kernel driver in use: xhci_hcd

00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 8534
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at f723b000 (64-bit, non-prefetchable) [size=16]
    Capabilities: [50] Power Management version 3
    Capabilities: [8c] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Kernel driver in use: mei_me

00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I217-V (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device 859f
    Flags: bus master, fast devsel, latency 0, IRQ 41
    Memory at f7200000 (32-bit, non-prefetchable) [size=128K]
    Memory at f7239000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at f040 [size=32]
    Capabilities: [c8] Power Management version 2
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [e0] PCI Advanced Features
    Kernel driver in use: e1000e

00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 8534
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at f7238000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci-pci

00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device 8692
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at f7230000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Kernel driver in use: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: e0000000-e01fffff
    Prefetchable memory behind bridge: 00000000e0200000-00000000e03fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 8534
    Capabilities: [a0] Power Management version 3
    Kernel driver in use: pcieport

00:1c.1 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #2 (rev d5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: f7100000-f71fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 8534
    Capabilities: [a0] Power Management version 3
    Kernel driver in use: pcieport

00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 8534
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f7237000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci-pci

00:1f.0 ISA bridge: Intel Corporation C220 Series Chipset Family H81 Express LPC Controller (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device 8534
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel driver in use: lpc_ich

00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05) (prog-if 01 [AHCI 1.0])
    Subsystem: ASUSTeK Computer Inc. Device 8534
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 43
    I/O ports at f090 [size=8]
    I/O ports at f080 [size=4]
    I/O ports at f070 [size=8]
    I/O ports at f060 [size=4]
    I/O ports at f020 [size=32]
    Memory at f7236000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Power Management version 3
    Capabilities: [a8] SATA HBA v1.0
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device 8534
    Flags: medium devsel, IRQ 18
    Memory at f7235000 (64-bit, non-prefetchable) [size=256]
    I/O ports at f000 [size=32]

01:00.0 VGA compatible controller: NVIDIA Corporation Device 1289 (rev a1) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 866f
    Flags: fast devsel, IRQ 16
    Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e8000000 (64-bit, prefetchable) [size=128M]
    Memory at f0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    Expansion ROM at f7000000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>

01:00.1 Audio device: NVIDIA Corporation Device 0e0f (rev a1)
    Subsystem: ASUSTeK Computer Inc. Device 866f
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f7080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Kernel driver in use: snd_hda_intel

03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter
    Subsystem: AzureWave Device 2161
    Flags: bus master, fast devsel, latency 0, IRQ 17
    I/O ports at d000 [size=256]
    Memory at f7100000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 00-e0-4c-ff-fe-87-2b-01
    Capabilities: [150] Latency Tolerance Reporting
    Capabilities: [158] L1 PM Substates
    Kernel driver in use: rtl8821ae

```

Im going now to download and install wpasupplicant, but i think problem should be something else, that i can't get (for now); hope to solve this alone and to post the solution soon, but... 
with a little help from my friends could go faster! 

Thank you for your support and your commitment here,
Ivan

---

### Post by issh on 2017-02-20
> **kolkolkol said:**
> Hi all, first post here. Im Ivan, its nice to meet. :D 

So i finally came to install Debian Jessie stable, and it's good to be back.
My installation is brand new and i have not a wired connection avalaible, so ill have to make things works nowired.

As the title say, my card is an _Intel i217-V_, which in the beginning was not recognized at all by the OS. 
That was normal and expected, because in the installation phase Debian told that i was missing firmware files *named rtlwifi/rtl8821aefw.bin*. 
After a few search i came to download from windows (im in a dual boot system) the following packages: _firmware-iwlwifi_0.43_all.deb_ and _firmware-realtek_0.43_all.deb_. 
I also installed this driver, that seems to fit in for my net card: [https://downloadcenter.intel.com/download/15817/Intel-Network-Adapter-Driver-for-PCI-E-Gigabit-Network-Connections-under-Linux-](https://downloadcenter.intel.com/download/15817/Intel-Network-Adapter-Driver-for-PCI-E-Gigabit-Network-Connections-under-Linux-)
That made my OS _"graphically"_recognize the net card and made me able to see avalaible connections trough it. And that, for instance, it is not completely true because at the present day connections appear just for a while, like 3 or 4 minutes after the boot, then totally disappear and i have to reboot to see them again.
I'm able to see my home wifi connection among others, but can't connect to it.

Heres my **ifconfig **
```
root@kkk:/home/kolkolkol# ifconfig
eth0      Link encap:Ethernet  HWaddr 1c:87:2c:cc:97:f7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f7200000-f7220000 

eth0:avahi Link encap:Ethernet  HWaddr 1c:87:2c:cc:97:f7  
          inet addr:169.254.11.115  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:20 Memory:f7200000-f7220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:31 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3317 (3.2 KiB)  TX bytes:3317 (3.2 KiB)

wlan0     Link encap:Ethernet  HWaddr dc:85:de:ef:dd:31  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

**iwconfig**
```
root@kkk:/home/kolkolkol# sudo iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          
eth0      no wireless extensions.
```
As i understood there isnt any statement on this about my netcard. Like eth1, 2, etcetera. Am i right?

**interfaces**
```
/etc/network/interfaces/
/etc/network/interfaces/
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
allow-hotplug eth0
iface eth0 inet dhcp

```

and **lspci -v**
```
00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device 8534
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel driver in use: hsw_uncore

00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: f6000000-f70fffff
    Prefetchable memory behind bridge: 00000000e8000000-00000000f1ffffff
    Capabilities: [88] Subsystem: ASUSTeK Computer Inc. Device 8534
    Capabilities: [80] Power Management version 3
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [a0] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [140] Root Complex Link
    Kernel driver in use: pcieport

00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05) (prog-if 30 [XHCI])
    Subsystem: ASUSTeK Computer Inc. Device 8534
    Flags: bus master, medium devsel, latency 0, IRQ 42
    Memory at f7220000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [70] Power Management version 2
    Capabilities: [80] MSI: Enable+ Count=1/8 Maskable- 64bit+
    Kernel driver in use: xhci_hcd

00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 8534
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at f723b000 (64-bit, non-prefetchable) [size=16]
    Capabilities: [50] Power Management version 3
    Capabilities: [8c] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Kernel driver in use: mei_me

00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I217-V (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device 859f
    Flags: bus master, fast devsel, latency 0, IRQ 41
    Memory at f7200000 (32-bit, non-prefetchable) [size=128K]
    Memory at f7239000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at f040 [size=32]
    Capabilities: [c8] Power Management version 2
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [e0] PCI Advanced Features
    Kernel driver in use: e1000e

00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 8534
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at f7238000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci-pci

00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device 8692
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at f7230000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Kernel driver in use: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: e0000000-e01fffff
    Prefetchable memory behind bridge: 00000000e0200000-00000000e03fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 8534
    Capabilities: [a0] Power Management version 3
    Kernel driver in use: pcieport

00:1c.1 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #2 (rev d5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: f7100000-f71fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 8534
    Capabilities: [a0] Power Management version 3
    Kernel driver in use: pcieport

00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 8534
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f7237000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci-pci

00:1f.0 ISA bridge: Intel Corporation C220 Series Chipset Family H81 Express LPC Controller (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device 8534
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel driver in use: lpc_ich

00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05) (prog-if 01 [AHCI 1.0])
    Subsystem: ASUSTeK Computer Inc. Device 8534
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 43
    I/O ports at f090 [size=8]
    I/O ports at f080 [size=4]
    I/O ports at f070 [size=8]
    I/O ports at f060 [size=4]
    I/O ports at f020 [size=32]
    Memory at f7236000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Power Management version 3
    Capabilities: [a8] SATA HBA v1.0
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device 8534
    Flags: medium devsel, IRQ 18
    Memory at f7235000 (64-bit, non-prefetchable) [size=256]
    I/O ports at f000 [size=32]

01:00.0 VGA compatible controller: NVIDIA Corporation Device 1289 (rev a1) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 866f
    Flags: fast devsel, IRQ 16
    Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e8000000 (64-bit, prefetchable) [size=128M]
    Memory at f0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    Expansion ROM at f7000000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>

01:00.1 Audio device: NVIDIA Corporation Device 0e0f (rev a1)
    Subsystem: ASUSTeK Computer Inc. Device 866f
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f7080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Kernel driver in use: snd_hda_intel

03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter
    Subsystem: AzureWave Device 2161
    Flags: bus master, fast devsel, latency 0, IRQ 17
    I/O ports at d000 [size=256]
    Memory at f7100000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 00-e0-4c-ff-fe-87-2b-01
    Capabilities: [150] Latency Tolerance Reporting
    Capabilities: [158] L1 PM Substates
    Kernel driver in use: rtl8821ae

```

Im going now to download and install wpasupplicant, but i think problem should be something else, that i can't get (for now); hope to solve this alone and to post the solution soon, but... 
with a little help from my friends could go faster! 

Thank you for your support and your commitment here,
Ivan

Hello Ivan, 

I would suggest you download the third-party .iso image that contains non-free firmware repos in the installer. 

Here are some links for you. Please choose according to your architecture. 

[IMG]http://i.imgur.com/IN3x7gx.png[/IMG]

[http://cdimage.debian.org/cdimage/unofficial/non-free/cd-including-firmware/8.7.1+nonfree/amd64/iso-cd/firmware-8.7.1-amd64-netinst.iso](http://cdimage.debian.org/cdimage/unofficial/non-free/cd-including-firmware/8.7.1+nonfree/amd64/iso-cd/firmware-8.7.1-amd64-netinst.iso)  <----- AMD64 net installer with non-free firmwares
[http://cdimage.debian.org/cdimage/unofficial/non-free/cd-including-firmware/8.7.1+nonfree/i386/iso-cd/firmware-8.7.1-i386-netinst.iso](http://cdimage.debian.org/cdimage/unofficial/non-free/cd-including-firmware/8.7.1+nonfree/i386/iso-cd/firmware-8.7.1-i386-netinst.iso)  <----- i386 net installer with non-free firmwares

Source: [https://www.debian.org/releases/stable/debian-installer/](https://www.debian.org/releases/stable/debian-installer/)

---

