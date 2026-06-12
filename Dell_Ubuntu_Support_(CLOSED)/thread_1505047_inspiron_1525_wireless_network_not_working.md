---
title: "inspiron 1525 wireless network not working"
date: 2010-06-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by raac on 2010-06-08
My wireless is not working, I'm new with linux so I don't know too much about it, I looked online to check what kind of wireless chipset i have and I found this command "sudo lshw". and I found this

*-network
                description: Wireless interface
                product: BCM4312 802.11b/g
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:0b:00.0
                logical name: eth1
                version: 01
                serial: 00:23:4e:1a:db:31
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=192.168.1.66 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg

---------------------------------------------------------------------------------------------------------------------------

What do I need to do to make it work??????

As I said my laptop is an inspiron 1525, 32 bits. I have the linux 10.04

---

### Post by Ichido on 2010-06-08
This issue caused me many headaches for some time, but I've got the "Bugs" worked out.

Let me start here to help you. 

1st...Check in your BIOS Settings that your Wireless is ON.
2nd...Check to make sure that your Wireless Switch is in the ON Position. this switch is on the Right Side, near to the Front Edge. This 3 Position Switch is OFF/ON/Test for Wireless Signal.

Go to:
[http://support.dell.com/support/edocs/systems/ins1525/en/index.htm](http://support.dell.com/support/edocs/systems/ins1525/en/index.htm)

Dell™ Inspiron™ 1525/1526

and download the "Set up Guide" PDF 1.14MB. (Y465HA01MR.PDF)

Look at Section 2, Page 6.

Let me know how it's going.

---

### Post by raac on 2010-06-08
First of all thanks for taking the time in helping me. 
 
I tried what you said, and I have that set up right. What else could it be???

---

### Post by Ichido on 2010-06-08
Try theses in the Terminal window:

ifconfig - lists IP address (similar to ipconfig in Windows)
iwconfig -  Get wireless info
iwlist scan - shows wireless networks that are available in the area along with basic encryption information
lshw -C network - Shows interface and driver associated with each networking device
lspci -nn - Shows hardware connected to the pci bus

---

### Post by raac on 2010-06-09
sorry for saying this too explicit, but like I said before I'm new at this so, you guys might see something that is important to my problem.

with the ifconfig command, I got this

eth0      Link encap:Ethernet  HWaddr 00:23:ae:09:9b:10  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3072 (3.0 KB)  TX bytes:3072 (3.0 KB)

-----------------------------------------------------------------

with the command iwconfig i got this

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

-----------------------------------------------------------------

iwlist scan command

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

-----------------------------------------------------------------
lshw -C network command

  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:23:ae:09:9b:10
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 multicast=yes
       resources: irq:27 memory:fe8fc000-fe8fffff ioport:de00(size=256)
  *-network
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:fe7fc000-fe7fffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:23:4e:1a:db:31
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

-----------------------------------------------------------------

lspci command


00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
02:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
02:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
02:09.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
02:09.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
02:09.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 12)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
-----------------------------------------------------------------

What can I do based on this output???

---

### Post by Ichido on 2010-06-09
Thanks for posting the Terminal Output!

I see Problems;

1) "ifconfig" Shows: lo and eth0, but _*no "wlan0"*_.

2) "iwconfig" Shows:

wlan0 IEEE 802.11bg ESSID_*off*_/any
Mode:Managed Access Point: Not-Associated _*Tx-Power=0 dBm*_ 

3) "iwlist" Shows: wlan0 Failed to read scan data : _*Network is down*_

4) "lshw -C network" Shows: 

*-network
description: Network controller
_product: BCM4312 802.11b/g_
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:0b:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: driver=b43-pci-bridge latency=0
resources: irq:17 memory:fe7fc000-fe7fffff
_**-network DISABLED*_
description: Wireless interface
physical id: 2
logical name: wlan0
serial: 00:23:4e:1a:db:31
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

"lspci"

[U]0b:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
[/U]

It seems as though you have a Wireless Device which is "Disabled"?

How old is this Laptop and did you purchase this new?
Have you checked with the Dell Forum "http://en.community.dell.com/" for help?

Keep checking back to your Post because someone else, with more or better help, may jump-in here.
If not, I will do what I can to help.

---

### Post by raac on 2010-06-09
IT WORKS NOW!!!

this is what I did....

I plugged in the ethernet cable directly, then I went to "System" -> "Administration" -> "Hardware Drivers"

And it finds it by itself and you just need to activate it......You DO need internet access

Thanks for all your help.

---

### Post by Ichido on 2010-06-11
Mark you post as SOLVED.

---

