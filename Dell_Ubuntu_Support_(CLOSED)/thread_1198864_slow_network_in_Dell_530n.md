---
title: "slow network in Dell 530n"
date: 2009-06-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by askapartov on 2009-06-28
Hello 

I have just got my new Dell Inspiron 530n quad core. with ubuntu pre-installed. Everything seems fine except the network, it is very slow

I have found several info in internet but still no success:
1) I have updated the headers (linux-headers-2.6.24-24-generic) and also the backports (linux-backports-modules-2.6.24-24-generic) 
2) I have uninstalled network-manager (and installed wicd instead)
3) I have played with the /etc/network/interfaces

up to now, the network is still slow

It is curious because the network in my laptop (with the same version of ubuntu: Hardy 8.04) works perfectly....

This is what I get from dmesg
[   34.727883] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   34.873559] Bluetooth: Core ver 2.11
[   34.873727] NET: Registered protocol family 31
[   34.873732] Bluetooth: HCI device and connection manager initialized
[   34.873737] Bluetooth: HCI socket layer initialized
[   34.906071] Bluetooth: L2CAP ver 2.9
[   34.906076] Bluetooth: L2CAP socket layer initialized
[   34.962734] Bluetooth: RFCOMM socket layer initialized
[   34.962745] Bluetooth: RFCOMM TTY layer initialized
[   34.962747] Bluetooth: RFCOMM ver 1.8
[   36.110577] eth0: Link is Up 100 Mbps Full Duplex, Flow Control: None
[   36.110583] eth0: 10/100 speed: disabling TSO
[   36.112470] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   37.620772] [drm] Initialized drm 1.1.0 20060810
[   37.622767] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   37.622776] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   37.622827] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   37.642791] mtrr: no more MTRRs available
[   38.099254] set status page addr 0x00033000
[   46.550434] eth0: no IPv6 routers present


I have no idea about what else I can try, please, help!

btw, I tried to contact Dell support and they do not seem to know too much about ubuntu... I think it is not good publicity if they sell a computer with ubuntu pre-installed and not to be able to provide a minimum assistance. Anyway, it is just an opinion.

thanks

---

### Post by coffeeaddict22 on 2009-06-28
Hi,
Welcome to Ubuntu!
Don't mind the Dell Service people.  They were employed for their ability to reinstall another OS off the CD.
Your problem at present is that Linux wireless got better by far over the last 12 months.  I'd strongly recommend you upgrade to 8.10 at least, as you may find this fixes all your problems.  My own experience with a Dell is that ndiswrapper was necessary until 8.10, and I'd guess that's why your previous install works.  Ndiswrapper is a bit of an ugly hack though- it simply wraps Windows drivers, and since 8.10 most of the drivers have been native Linux drivers and are part of the kernel, so a lot of the hassle has gone out of wireless.

Anyway, troubleshooting networks.
Open a terminal, type in the following 2 commands```
lspci -v
lshw -C network
``` and post the output back.  
Can you give us a few more details?
1) what version of Ubuntu?  I'm assuming you're in Gnome, ie not running Ku/Xu/ or edu/ buntu.
2) Wired or wireless?
3) builtin card or plugin?
4) From what you've said, I'm guessing you do(?did) have network accessibility, it's just slow.  Is that right?

---

### Post by RedRat on 2009-06-28
When contacting Dell about Linux machine make sure that you call the Linux support telephone number. Here in the U.S., the last number I had was 1-866-622-1947. Calling the regular Dell support will put you in contact with Windows people and they have not got a clue about Linux.

---

### Post by askapartov on 2009-06-29
First of all, thanks a lot for your help

This is what I get from ls lspci -v

```
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
    Subsystem: Dell Unknown device 020d
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information

00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fde00000-fdefffff
    Prefetchable memory behind bridge: 00000000fda00000-00000000fdafffff
    Capabilities: [88] Subsystem: Dell Unknown device 020d
    Capabilities: [80] Power Management version 3
    Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [a0] Express Root Port (Slot+) IRQ 0

00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
    Subsystem: Dell Unknown device 020d
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fdf00000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at ff00 [size=8]
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    Memory at fdb00000 (32-bit, non-prefetchable) [size=1M]
    Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Capabilities: [d0] Power Management version 2

00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
    Subsystem: Dell Unknown device 020d
    Flags: bus master, fast devsel, latency 0, IRQ 222
    Memory at fdfc0000 (32-bit, non-prefetchable) [size=128K]
    Memory at fdfff000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at fe00 [size=32]
    Capabilities: [c8] Power Management version 2
    Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
    Capabilities: [e0] Vendor Specific Information

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Unknown device 020d
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at fd00 [size=32]
    Capabilities: [50] Vendor Specific Information

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Unknown device 020d
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at fc00 [size=32]
    Capabilities: [50] Vendor Specific Information

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Unknown device 020d
    Flags: bus master, medium devsel, latency 0, IRQ 20
    I/O ports at fb00 [size=32]
    Capabilities: [50] Vendor Specific Information

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
    Subsystem: Dell Unknown device 020d
    Flags: bus master, medium devsel, latency 0, IRQ 17
    Memory at fdffe000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port
    Capabilities: [98] Vendor Specific Information

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
    Subsystem: Dell Unknown device 020d
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at fdff4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [70] Express Unknown type IRQ 0

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Unknown device 020d
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at fa00 [size=32]
    Capabilities: [50] Vendor Specific Information

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Unknown device 020d
    Flags: bus master, medium devsel, latency 0, IRQ 20
    I/O ports at f900 [size=32]
    Capabilities: [50] Vendor Specific Information

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Unknown device 020d
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at f800 [size=32]
    Capabilities: [50] Vendor Specific Information

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
    Subsystem: Dell Unknown device 020d
    Flags: bus master, medium devsel, latency 0, IRQ 18
    Memory at fdffd000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port
    Capabilities: [98] Vendor Specific Information

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fdd00000-fddfffff
    Prefetchable memory behind bridge: 00000000fdc00000-00000000fdcfffff
    Capabilities: [50] Subsystem: Dell Unknown device 020d

00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
    Subsystem: Dell Unknown device 020d
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information

00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Dell Unknown device 020d
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
    I/O ports at f700 [size=8]
    I/O ports at f600 [size=4]
    I/O ports at f500 [size=8]
    I/O ports at f400 [size=4]
    I/O ports at f300 [size=16]
    I/O ports at f200 [size=16]
    Capabilities: [70] Power Management version 3
    Capabilities: [b0] Vendor Specific Information

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
    Subsystem: Dell Unknown device 020d
    Flags: medium devsel, IRQ 11
    Memory at fdffc000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 0500 [size=32]

00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02) (prog-if 85 [Master SecO PriO])
    Subsystem: Dell Unknown device 020d
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
    I/O ports at f000 [size=8]
    I/O ports at ef00 [size=4]
    I/O ports at ee00 [size=8]
    I/O ports at ed00 [size=4]
    I/O ports at ec00 [size=16]
    I/O ports at eb00 [size=16]
    Capabilities: [70] Power Management version 3
    Capabilities: [b0] Vendor Specific Information
```
and from  lshw -C network
  ```
*-network               
       description: Ethernet interface
       product: 82562V-2 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:21:9b:12:41:66
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k2 duplex=full firmware=1.1-2 ip=131.215.127.240 latency=0 link=yes module=e1000e multicast=yes port=twisted pair speed=100MB/s
```>Can you give us a few more details?
1) what version of Ubuntu?  I'm assuming you're in Gnome, ie not running Ku/Xu/ or edu/ buntu.

Yes, I am in gnome. Ubuntu 8.04

2) Wired or wireless?

wired

3) builtin card or plugin?

builtin card

4) From what you've said, I'm guessing you do(?did) have network accessibility, it's just slow.  Is that right?

Yes, that's it

Just one remark. I have downloaded ubuntu 9.04 and the network is also slow when I use the live CD. I could invest one or two days installing it but I am not sure it is worthy to do that.


thanks again for your help
Daniel

---

### Post by coffeeaddict22 on 2009-06-29
OK, you've got a driver installed, and it's behaving by all appearances.
What are you comparing it to?  Have you used the same network before?  It looks like the network is running standard (100MB/s) and not Gigabit ethernet.  Can you download some network monitoring tools and look at the upload/download function?  There's a wide selection on [this internet site]("http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-ubuntu-users.html"); any one would do.

---

### Post by askapartov on 2009-06-29
The network seems to work fine as it works fine in my laptop using the same cable.

I do not know if I did a mistake but trying to look for a solution I moved to Ubuntu 9.04. Now I have completely lost my internet connection...

This is what I get from dmesg
```

&#65279;[   12.294557] Bridge firewalling registered  
[   13.262321] ppdev: user-space parallel port driver  
[   13.904227] [drm] Initialized drm 1.1.0 20060810  
[   13.929138] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16  
[   13.929142] pci 0000:00:02.0: setting latency timer to 64  
[   13.929211] pci 0000:00:02.0: irq 2301 for MSI/MSI-X  
[   13.929283] [drm] Initialized i915 1.6.0 20080730 on minor 0  
[   13.930816] [drm:i915_setparam] *ERROR* unknown parameter 4  
[   13.930836] [drm:i915_getparam] *ERROR* Unknown parameter 6  
[   14.415047] [drm:i915_getparam] *ERROR* Unknown parameter 6  
[   24.333893] [drm:i915_getparam] *ERROR* Unknown parameter 6
```

(I have been reading that this error is harmless).

I get this from lspci -v 

[HTML]00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02) 
    Subsystem: Dell Device 020d 
    Flags: bus master, fast devsel, latency 0 
    Capabilities: [e0] Vendor Specific Information <?> 
    Kernel driver in use: agpgart-intel 
    Kernel modules: intel-agp 
 
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02) 
    Flags: bus master, fast devsel, latency 0 
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0 
    I/O behind bridge: 0000c000-0000cfff 
    Memory behind bridge: fde00000-fdefffff 
    Prefetchable memory behind bridge: 00000000fda00000-00000000fdafffff 
    Capabilities: [88] Subsystem: Dell Device 020d 
    Capabilities: [80] Power Management version 3 
    Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+ 
    Capabilities: [a0] Express Root Port (Slot+), MSI 00 
    Capabilities: [100] Virtual Channel <?> 
    Capabilities: [140] Root Complex Link <?> 
    Kernel driver in use: pcieport-driver 
    Kernel modules: shpchp 
 
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02) 
    Subsystem: Dell Device 020d 
    Flags: bus master, fast devsel, latency 0, IRQ 2301 
    Memory at fdf00000 (32-bit, non-prefetchable) [size=512K] 
    I/O ports at ff00 [size=8] 
    Memory at d0000000 (32-bit, prefetchable) [size=256M] 
    Memory at fdb00000 (32-bit, non-prefetchable) [size=1M] 
    Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+ 
    Capabilities: [d0] Power Management version 2 
 
00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02) 
    Subsystem: Dell Device 020d 
    Flags: bus master, fast devsel, latency 0, IRQ 2302 
    Memory at fdfc0000 (32-bit, non-prefetchable) [size=128K] 
    Memory at fdfff000 (32-bit, non-prefetchable) [size=4K] 
    I/O ports at fe00 [size=32] 
    Capabilities: [c8] Power Management version 2 
    Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+ 
    Capabilities: [e0] Vendor Specific Information <?> 
    Kernel driver in use: e1000e 
    Kernel modules: e1000e 
 
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02) 
    Subsystem: Dell Device 020d 
    Flags: bus master, medium devsel, latency 0, IRQ 16 
    I/O ports at fd00 [size=32] 
    Capabilities: [50] Vendor Specific Information <?> 
    Kernel driver in use: uhci_hcd 
 
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02) 
    Subsystem: Dell Device 020d 
    Flags: bus master, medium devsel, latency 0, IRQ 21 
    I/O ports at fc00 [size=32] 
    Capabilities: [50] Vendor Specific Information <?> 
    Kernel driver in use: uhci_hcd 
 
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02) 
    Subsystem: Dell Device 020d 
    Flags: bus master, medium devsel, latency 0, IRQ 19 
    I/O ports at fb00 [size=32] 
    Capabilities: [50] Vendor Specific Information <?> 
    Kernel driver in use: uhci_hcd 
 
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20) 
    Subsystem: Dell Device 020d 
    Flags: bus master, medium devsel, latency 0, IRQ 18 
    Memory at fdffe000 (32-bit, non-prefetchable) [size=1K] 
    Capabilities: [50] Power Management version 2 
    Capabilities: [58] Debug port: BAR=1 offset=00a0 
    Capabilities: [98] Vendor Specific Information <?> 
    Kernel driver in use: ehci_hcd 
 
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02) 
    Subsystem: Dell Device 020d 
    Flags: bus master, fast devsel, latency 0, IRQ 22 
    Memory at fdff4000 (64-bit, non-prefetchable) [size=16K] 
    Capabilities: [50] Power Management version 2 
    Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable- 
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00 
    Capabilities: [100] Virtual Channel <?> 
    Capabilities: [130] Root Complex Link <?> 
    Kernel driver in use: HDA Intel 
    Kernel modules: snd-hda-intel 
 
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02) 
    Subsystem: Dell Device 020d 
    Flags: bus master, medium devsel, latency 0, IRQ 23 
    I/O ports at fa00 [size=32] 
    Capabilities: [50] Vendor Specific Information <?> 
    Kernel driver in use: uhci_hcd 
 
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02) 
    Subsystem: Dell Device 020d 
    Flags: bus master, medium devsel, latency 0, IRQ 19 
    I/O ports at f900 [size=32] 
    Capabilities: [50] Vendor Specific Information <?> 
    Kernel driver in use: uhci_hcd 
 
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02) 
    Subsystem: Dell Device 020d 
    Flags: bus master, medium devsel, latency 0, IRQ 18 
    I/O ports at f800 [size=32] 
    Capabilities: [50] Vendor Specific Information <?> 
    Kernel driver in use: uhci_hcd 
 
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20) 
    Subsystem: Dell Device 020d 
    Flags: bus master, medium devsel, latency 0, IRQ 23 
    Memory at fdffd000 (32-bit, non-prefetchable) [size=1K] 
    Capabilities: [50] Power Management version 2 
    Capabilities: [58] Debug port: BAR=1 offset=00a0 
    Capabilities: [98] Vendor Specific Information <?> 
    Kernel driver in use: ehci_hcd 
 
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92) (prog-if 01) 
    Flags: bus master, fast devsel, latency 0 
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=32 
    I/O behind bridge: 0000d000-0000dfff 
    Memory behind bridge: fdd00000-fddfffff 
    Prefetchable memory behind bridge: 00000000fdc00000-00000000fdcfffff 
    Capabilities: [50] Subsystem: Dell Device 020d 
 
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02) 
    Subsystem: Dell Device 020d 
    Flags: bus master, medium devsel, latency 0 
    Capabilities: [e0] Vendor Specific Information <?> 
    Kernel modules: iTCO_wdt 
 
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO]) 
    Subsystem: Dell Device 020d 
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19 
    I/O ports at f700 [size=8] 
    I/O ports at f600 [size=4] 
    I/O ports at f500 [size=8] 
    I/O ports at f400 [size=4] 
    I/O ports at f300 [size=16] 
    I/O ports at f200 [size=16] 
    Capabilities: [70] Power Management version 3 
    Capabilities: [b0] Vendor Specific Information <?> 
    Kernel driver in use: ata_piix 
 
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02) 
    Subsystem: Dell Device 020d 
    Flags: medium devsel, IRQ 11 
    Memory at fdffc000 (64-bit, non-prefetchable) [size=256] 
    I/O ports at 0500 [size=32] 
    Kernel modules: i2c-i801 
 
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02) (prog-if 85 [Master SecO PriO]) 
    Subsystem: Dell Device 020d 
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19 
    I/O ports at f000 [size=8] 
    I/O ports at ef00 [size=4] 
    I/O ports at ee00 [size=8] 
    I/O ports at ed00 [size=4] 
    I/O ports at ec00 [size=16] 
    I/O ports at eb00 [size=16] 
    Capabilities: [70] Power Management version 3 
    Capabilities: [b0] Vendor Specific Information <?> 
    Kernel driver in use: ata_piix
[/HTML]

and finally this from 
lshw -C network [HTML]
  *-network                 
       description: Ethernet interface  
       product: 82562V-2 10/100 Network Connection  
       vendor: Intel Corporation  
       physical id: 19  
       bus info: pci@0000:00:19.0  
       logical name: eth0  
       version: 02  
       serial: 00:21:9b:12:41:66  
       capacity: 100MB/s  
       width: 32 bits  
       clock: 33MHz  
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation  
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=1.1-2 ip=131.215.127.240 latency=0 link=no module=e1000e multicast=yes port=twisted pair  
  *-network DISABLED  
       description: Ethernet interface  
       physical id: 1  
       logical name: pan0  
       serial: ce:ee:2b:b6:68:68  
       capabilities: ethernet physical  
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes[/HTML]

It is good to know that the card is correctly configured (I hope also in 9.04). At least I would like to know from where the problem is coming from.

---

### Post by coffeeaddict22 on 2009-06-29
Looks like you've got a firewall installed on that dmesg post.  
What's the output of ```
ifconfig -a
``` and ```
route -n
```?

---

### Post by askapartov on 2009-06-29
root@pluton:/etc# ifconfig -a eth0      Link encap:Ethernet  HWaddr 00:21:9b:12:41:66             inet addr:131.215.127.240  Bcast:131.215.127.255  Mask:255.255.255.0           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1           RX packets:0 errors:0 dropped:0 overruns:0 frame:0           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0           collisions:0 txqueuelen:1000            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)           Memory:fdfc0000-fdfe0000   lo        Link encap:Local Loopback             inet addr:127.0.0.1  Mask:255.0.0.0           inet6 addr: ::1/128 Scope:Host           UP LOOPBACK RUNNING  MTU:16436  Metric:1           RX packets:410 errors:0 dropped:0 overruns:0 frame:0           TX packets:410 errors:0 dropped:0 overruns:0 carrier:0           collisions:0 txqueuelen:0            RX bytes:38025 (38.0 KB)  TX bytes:38025 (38.0 KB)  pan0      Link encap:Ethernet  HWaddr ce:ee:2b:b6:68:68             BROADCAST MULTICAST  MTU:1500  Metric:1           RX packets:0 errors:0 dropped:0 overruns:0 frame:0           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0           collisions:0 txqueuelen:0            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  root@pluton:/etc# route -n Kernel IP routing table Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 131.215.127.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0 169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0 0.0.0.0         131.215.127.1   0.0.0.0         UG    100    0        0 eth0

---

### Post by askapartov on 2009-06-29
sorry


root@pluton:/etc# ifconfig -a 
```
eth0      Link encap:Ethernet  HWaddr 00:21:9b:12:41:66  
          inet addr:131.215.127.240  Bcast:131.215.127.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fdfc0000-fdfe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:410 errors:0 dropped:0 overruns:0 frame:0
          TX packets:410 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:38025 (38.0 KB)  TX bytes:38025 (38.0 KB)

pan0      Link encap:Ethernet  HWaddr ce:ee:2b:b6:68:68  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
root@pluton:/etc# route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
131.215.127.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         131.215.127.1   0.0.0.0         UG    100    0        0 eth0
```

---

### Post by askapartov on 2009-06-30
Hello

I have found very strange solution to my problem. I have installed Windows Vista first and then Ubuntu 9.04. Now everything works fine. Indeed, my network was working perfectly even with the CD live of Ubuntu 9.04 (was not the case before)

I cannot understand but anyway, my problem is solved. Thanks for your help

---

### Post by coffeeaddict22 on 2009-07-01
Congrats, and enjoy.  The solution tends to suggest it was something in hardware or BIOS, so I'm quite happy to not have to go there!

---

