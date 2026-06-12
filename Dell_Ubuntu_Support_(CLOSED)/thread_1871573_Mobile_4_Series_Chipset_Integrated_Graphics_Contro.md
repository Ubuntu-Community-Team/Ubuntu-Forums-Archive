---
title: "Mobile 4 Series Chipset Integrated Graphics Controller?"
date: 2011-10-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Aireyura on 2011-10-29
I have recently installed Ubuntu 11.10 on my Dell Inspiron 1545. Everything seems to have installed correctly, save my graphics driver. Though when running lspci, it accurately lists the devices that should be in use (Mobile 4 Series Chipset Integrated Graphics Controller). However when checking the 'System Info' my graphics displays as "Unknown". 

Any help with this situation would be greatly appreciated. If anymore information is needed for a solution, I would be gladly be willing to give it a post right on these here forums.

Thanks.

---

### Post by Aireyura on 2011-10-29
So, I'm assuming this is either a very common and solved issue, and I just fail at searching the forums/google. Though, I'm going to post up my lspci.

> 

[LIST]
[*]00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
 00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4  Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
  00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series  Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
 00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
 00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
 00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
 00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
 00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
 00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
 00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
 00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
 00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
 00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
 00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
 00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
 00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
 00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
 00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
 00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
 00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
 09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13)
 0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
[/LIST]
  Any other information that could be relevant? I have seen this issue a lot on the internet, and I have not found a single solution that works for me.

---

### Post by Tishers on 2012-03-17
-Bump-

I too have the same problem with the Intel Graphics 4 not doing any better than default resolution;

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    Subsystem: Dell Device 024f
    Flags: bus master, fast devsel, latency 0
    Memory at f6b00000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: [d0] Power Management version 3

It also shows as unknown, I am running .10 as well

---

### Post by jervin2 on 2012-05-03
affects my brand newly refurbished Dell Latitude e6400 too.

lspci | grep Graphics
jervin@Laptop:~$ lspci | grep Graphics
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

sudo lshw -C display
[sudo] password for jervin: 
  *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:47 memory:f6c00000-f6ffffff memory:e0000000-efffffff ioport:ef98(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f6b00000-f6bfffff

---

### Post by jii on 2012-06-02
I have the same exact problem with my gazelle laptop purchased from System76 who said it was "guaranteed to work with Ubuntu". I have the same exact graphics card info being reported. I can 2D mode okay in 12.04, but not the regular Ubuntu mode. 

In regular mode, there is no top bar, the launcher thing doesn't appear, and shortcuts like alt+F2 do not work. It's just an empty desktop with my icons and I can't do anything.

I first had this problem after updating from 11.04. Then I wiped my root and did a fresh install, but the problem is the same. This problem is all over the Internet with no solutions. Can anybody answer this? 

I used to show off Ubuntu 5 years ago when it had cool effects, but now my system looks worse than my phone :P

---

