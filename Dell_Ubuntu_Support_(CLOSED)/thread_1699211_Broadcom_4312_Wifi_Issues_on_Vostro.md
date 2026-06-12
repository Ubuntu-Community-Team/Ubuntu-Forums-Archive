---
title: "Broadcom 4312 Wifi Issues on Vostro"
date: 2011-03-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Zahne on 2011-03-03
I have a Dell Vostro 1520 with Ubuntu 10.10. I'm working out various kinks but one I can't seem to get passed is the wireless. There was an available driver which was installed and activated for but when it was activated I found that it said that it was active and currently not in use. 

I did a google search and found that someone had a work around. I followed the steps and the status was elevated to active and currently in use. I unplugged the ethernet cable, restarted the Vostro and when it turned back on wireless still said that it wasn't enabled. I'm stuck and this work around solved the issue for everyone else so no one, that I've found has experienced this continuing issue. 

The wireless switch is on and the wireless was working when I had XP installed. I'd really appreciate some feedback on this. Thanks!

---

### Post by nm_geo on 2011-03-03
I have the same chipset on my multi-boot D620 laptop and on Maverick 10.10 I used the Broadcom STA driver. On other versions on the same laptop the b43-fwcutter seems to find a good driver. Run this in terminal and let's see your results.
 
```
sudo lshw -C network
```
 
I am not on my Ubuntu Box right now so some of my terminology might be little off as I can't check the codes myself.
 
Also 
```
rfkill list
```

---

### Post by Zahne on 2011-03-03
Results:

 *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 03
       serial: 00:24:e8:aa:9d:24
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=10.0.0.11 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:47 ioport:4000(size=256) memory:fe004000-fe004fff memory:fe000000-fe003fff memory:fe020000-fe03ffff
  *-network DISABLED
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth1
       version: 01
       serial: 00:25:56:3e:8b:f7
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:f6000000-f6003fff


for killlist:

0: dell-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes

---

### Post by nm_geo on 2011-03-03
Here is the problem.. or at least part of it.
 
```
0: dell-wifi: Wireless LAN
Soft blocked: yes
Hard blocked: yes
```
 
Are you sure your wifi switch is enabled?  
 
Try 
 
```
rfkill unblock all
```
 
Again I am not on my Ubuntu Box so don't have all my cheat sheets

---

### Post by nm_geo on 2011-03-03
Your driver is installed 
 
*-network DISABLED
description: Wireless interface
product: BCM4312 802.11b/g LP-PHY
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:0e:00.0
logical name: eth1
version: 01
serial: 00:25:56:3e:8b:f7
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes [COLOR=red]**driver=wl0 driverversion**[/COLOR]=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg
resources: irq:18 memory:f6000000-f6003fff
 
[COLOR=black]Right click on the Network Manager icon the radar looking icon should be in the top right (make sure wireless is enabled) too.[/COLOR]

---

### Post by Zahne on 2011-03-03
That's just it. When I click on the wireless icon it says that wireless is disabled but it doesn't allow me an option enable it. Then when I right click the only two options are enable networking and enable notifications. Both of which are enabled. I know it's not the hardware because I did a systems check and the wireless works in XP.

---

### Post by nm_geo on 2011-03-03
> **Zahne said:**
> That's just it. When I click on the wireless icon it says that wireless is disabled but it doesn't allow me an option enable it. Then when I right click the only two options are enable networking and enable notifications. Both of which are enabled. I know it's not the hardware because I did a systems check and the wireless works in XP.

Did you try the rfkill unblock all ?  We can try a number of things if you want. Even installing another driver if you like..

---

### Post by Zahne on 2011-03-03
> **nm_geo said:**
> Did you try the rfkill unblock all ?  We can try a number of things if you want. Even installing another driver if you like..

Yep I tried unblock. It didn't work. Another alternative would be great, I appreciate the help.

---

### Post by nm_geo on 2011-03-03
> **Zahne said:**
> Yep I tried unblock. It didn't work. Another alternative would be great, I appreciate the help.

No problem I have ran around that 4312 driver myself a few times... OK go to synaptic and remove the bcmwl-kernel-source
that is the STA Broadcom driver.  Then we will install b43-fwcutter it may require a firmware we will see.

After you install try a reboot with the ethernet cable disconnected.  Then we might have to reconnect and run more wireless commands.

---

### Post by Zahne on 2011-03-03
Okay, so I've installed, restarted with ethernet disconnected. All set for the next step.

---

### Post by nm_geo on 2011-03-03
I take it you did not see a wifi light.. 


Ok let do this long line of commands.

```
sudo apt-get update; sudo apt-get install hwinfo grep; sudo lshw -C network; rfkill list; sudo iwlist scanning; cat /etc/network/interfaces; cat /etc/lsb-release; lspci -nn; lsusb; sudo lshw -short; unamea -a; dmesg | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|ound|p54|prism|rtl|rt2|rt3|rt6|rt7|usb|witch|wl';  iwconfig; cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|witch|wl'; sudo hwinfo --netcard ; cat /var/lib/NetworkManager/NetworkManager.state; sudo lsmod
```Just copy and then paste results from the terminal in the code boxes here.  It will take me some time to go through them.

---

### Post by nm_geo on 2011-03-03
Check for this package in Synaptic too.

firmware-b43-lpphy-installer

Remove the B43-fwcutter > Install the firmware from above reinstall the b43-fwcutter > then reboot

---

### Post by Zahne on 2011-03-04
For sudo apt-get update:

I updated all that it asked to do and restarted. There was no change with the wireless.

For sudo apt-get install hwinfogrep:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
grep is already the newest version.
The following extra packages will be installed:
  libhal1 libhd16
The following NEW packages will be installed:
  hwinfo libhal1 libhd16
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 860kB of archives.
After this operation, 2,339kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ maverick/main libhal1 amd64 0.5.14-0ubuntu6 [110kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ maverick/universe libhd16 amd64 16.0-2 [703kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ maverick/universe hwinfo amd64 16.0-2 [46.9kB]
Fetched 860kB in 1s (582kB/s)  
Selecting previously deselected package libhal1.
(Reading database ... 146268 files and directories currently installed.)
Unpacking libhal1 (from .../libhal1_0.5.14-0ubuntu6_amd64.deb) ...
Selecting previously deselected package libhd16.
Unpacking libhd16 (from .../libhd16_16.0-2_amd64.deb) ...
Selecting previously deselected package hwinfo.
Unpacking hwinfo (from .../hwinfo_16.0-2_amd64.deb) ...
Processing triggers for man-db ...
Setting up firmware-b43-installer (4.150.10.5-4) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up libhal1 (0.5.14-0ubuntu6) ...
Setting up libhd16 (16.0-2) ...
Setting up hwinfo (16.0-2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 firmware-b43-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

For sudo lshw -C network:

```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 03
       serial: 00:24:e8:aa:9d:24
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=10.0.0.11 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:48 ioport:4000(size=256) memory:fe004000-fe004fff memory:fe000000-fe003fff memory:fe020000-fe03ffff
  *-network
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:f6000000-f6003fff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:25:56:3e:8b:f7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-27-generic firmware=N/A link=yes multicast=yes wireless=IEEE 802.11bg

```

For rfkill list:

```
0: dell-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

```

For cat /etc/network/interfaces:

```
auto lo
iface lo inet loopback

```

For cat /etc/lsb-release:

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

```

For lspci -nn:

```
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
01:00.0 VGA compatible controller [0300]: nVidia Corporation G98 [GeForce 9300M GS] [10de:06e9] (rev a1)
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
0e:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
1a:00.0 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. Device [1217:10f7] (rev 01)
1a:00.1 SD Host controller [0805]: O2 Micro, Inc. Device [1217:8120] (rev 01)
1a:00.2 Mass storage controller [0180]: O2 Micro, Inc. Device [1217:8130] (rev 01)

```

For lsusb:

```
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0c45:63e0 Microdia Sonix Integrated Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

For sudo lshw -short:

```
H/W path           Device      Class       Description
======================================================
                               system      Vostro 1520
/0                             bus         0T808J
/0/1                           memory      118KiB BIOS
/0/5                           processor   Intel(R) Core(TM)2 Duo CPU     P8700  @ 2.53GHz
/0/5/6                         memory      64KiB L1 cache
/0/5/7                         memory      3MiB L2 cache
/0/11                          memory      4GiB System Memory
/0/11/0                        memory      2GiB SODIMM DDR2 Synchronous 800 MHz (1.2 ns)
/0/11/1                        memory      2GiB SODIMM DDR2 Synchronous 800 MHz (1.2 ns)
/0/100                         bridge      Mobile 4 Series Chipset Memory Controller Hub
/0/100/1                       bridge      Mobile 4 Series Chipset PCI Express Graphics Port
/0/100/1/0                     display     G98 [GeForce 9300M GS]
/0/100/1a                      bus         82801I (ICH9 Family) USB UHCI Controller #4
/0/100/1a.1                    bus         82801I (ICH9 Family) USB UHCI Controller #5
/0/100/1a.2                    bus         82801I (ICH9 Family) USB UHCI Controller #6
/0/100/1a.7                    bus         82801I (ICH9 Family) USB2 EHCI Controller #2
/0/100/1b                      multimedia  82801I (ICH9 Family) HD Audio Controller
/0/100/1c                      bridge      82801I (ICH9 Family) PCI Express Port 1
/0/100/1c.1                    bridge      82801I (ICH9 Family) PCI Express Port 2
/0/100/1c.1/0      eth0        network     RTL8111/8168B PCI Express Gigabit Ethernet controller
/0/100/1c.2                    bridge      82801I (ICH9 Family) PCI Express Port 3
/0/100/1c.2/0                  network     BCM4312 802.11b/g LP-PHY
/0/100/1c.3                    bridge      82801I (ICH9 Family) PCI Express Port 4
/0/100/1c.4                    bridge      82801I (ICH9 Family) PCI Express Port 5
/0/100/1c.4/0                  bus         O2 Micro, Inc.
/0/100/1c.4/0.1                generic     O2 Micro, Inc.
/0/100/1c.4/0.2                storage     O2 Micro, Inc.
/0/100/1c.5                    bridge      82801I (ICH9 Family) PCI Express Port 6
/0/100/1d                      bus         82801I (ICH9 Family) USB UHCI Controller #1
/0/100/1d.1                    bus         82801I (ICH9 Family) USB UHCI Controller #2
/0/100/1d.2                    bus         82801I (ICH9 Family) USB UHCI Controller #3
/0/100/1d.7                    bus         82801I (ICH9 Family) USB2 EHCI Controller #1
/0/100/1e                      bridge      82801 Mobile PCI Bridge
/0/100/1f                      bridge      ICH9M LPC Interface Controller
/0/100/1f.2        scsi0       storage     ICH9M/M-E SATA AHCI Controller
/0/100/1f.2/0      /dev/sda    disk        250GB WDC WD2500BJKT-7
/0/100/1f.2/0/1    /dev/sda1   volume      223GiB EXT4 volume
/0/100/1f.2/0/2    /dev/sda2   volume      9704MiB Extended partition
/0/100/1f.2/0/2/5  /dev/sda5   volume      9704MiB Linux swap / Solaris partition
/0/100/1f.2/1      /dev/cdrom  disk        DVDRWBD CT10N
/0/100/1f.3                    bus         82801I (ICH9 Family) SMBus Controller
/1                             power       SANYO     06/01/01
/2                 wlan0       network     Wireless interface

```

For unamea which I think you meant uname -a:

```
Linux ernie-Vostro-1520 2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:46 UTC 2011 x86_64 GNU/Linux

```

For dmesg | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|ound|p54|prism|rtl|rt2|rt3|rt6|rt7|usb|witch|wl':

```
[    0.000000] No AGP bridge found
[    0.000000] found SMP MP-table at [ffff8800000f6b20] f6b20
[    0.000000] No NUMA configuration found
[    0.000000] No AGP bridge found
[    0.561245] ACPI: No dock devices found.
[    0.595318] HEST: Table is not found!
[    0.595557] usbcore: registered new interface driver usbfs
[    0.595557] usbcore: registered new interface driver hub
[    0.595557] usbcore: registered new device driver usb
[    0.595557] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.600016] Switching to clocksource tsc
[    0.671031] pnp: PnP ACPI: found 10 devices
[    0.760082] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.760124] ACPI: Lid Switch [LID0]
[    0.765064] Switching to clocksource hpet
[    0.833719] ERST: Table is not found!
[    0.860104] hub 1-0:1.0: USB hub found
[    0.880090] hub 2-0:1.0: USB hub found
[    0.880360] hub 3-0:1.0: USB hub found
[    0.880575] hub 4-0:1.0: USB hub found
[    0.880777] hub 5-0:1.0: USB hub found
[    0.880977] hub 6-0:1.0: USB hub found
[    0.881182] hub 7-0:1.0: USB hub found
[    0.881402] hub 8-0:1.0: USB hub found
[    0.923781] device-mapper: multipath: version 1.1.1 loaded
[    0.923783] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.933268] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.014974] r8169 0000:08:00.0: eth0: RTL8168d/8111d at 0xffffc9001109e000, 00:24:e8:aa:9d:24, XID 081000c0 IRQ 48
[    1.038439] b43-pci-bridge 0000:0e:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.038453] b43-pci-bridge 0000:0e:00.0: setting latency timer to 64
[    1.072824] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x16, vendor 0x4243)
[    1.072842] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0F, vendor 0x4243)
[    1.072859] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x0A, vendor 0x4243)
[    1.072875] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x09, vendor 0x4243)
[    1.162825] ssb: Sonics Silicon Backplane found on PCI device 0000:0e:00.0
[    1.190203] sdhci-pci 0000:1a:00.1: SDHCI controller found [1217:8120] (rev 1)
[    1.210106] usb 2-2: new high speed USB device using ehci_hcd and address 2
[    9.681613] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[    9.698087] uvcvideo: Found UVC 1.00 device Integrated Webcam (0c45:63e0)
[    9.714354] input: Integrated Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2:1.0/input/input6
[    9.714409] usbcore: registered new interface driver uvcvideo
[    9.843943] lp: driver loaded but no devices found
[   10.005920] dell-wmi-aio: No known WMI GUID found
[   10.468473] Registered led device: b43-phy0::tx
[   10.468487] Registered led device: b43-phy0::rx
[   10.468502] Registered led device: b43-phy0::radio
[   10.468562] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[   11.543013] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   11.543170] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   14.827367] r8169 0000:08:00.0: eth0: link up
[   14.827377] r8169 0000:08:00.0: eth0: link up
[   25.590051] eth0: no IPv6 routers present

```


Will post more shortly...

---

### Post by nm_geo on 2011-03-04
I am traveling today and tomorrow but will check when I can.
By-the -way I download 10.10 again just for this testing. Oh well, I had a partition that needed something.
Yes you got it "uname -a"  
and the blacklist stuff from (/etc/modprobe.d/blacklist.cong)  could be important.

**Try this first;**

Remove b43-fwcutter with synaptic
Remove firmware-b43-installer also.

Install  firmware-b43-lpphy-installer with Synaptic.
Re-Install b43-fwcutter again ..

Reboot and let's see what happens

You probably need the BCM4312 low power firmware my fault I should have seen it sooner your chipset is 
Low power chip.  
**[COLOR=Red]product: BCM4312 802.11b/g LP-PHY[/COLOR]**
 and we had an error in the firmware install. 
[COLOR=Red][B]Setting up firmware-b43-installer (4.150.10.5-4) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.


[/B][/COLOR]

---

