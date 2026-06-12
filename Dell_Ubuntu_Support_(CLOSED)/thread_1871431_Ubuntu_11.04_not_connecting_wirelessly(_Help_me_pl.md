---
title: "Ubuntu 11.04 not connecting wirelessly:( Help me please!"
date: 2011-10-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by LinuxTrix on 2011-10-28
Hi.
I have a Dell XPS M1530 and Ubuntu 11.04 Natty Narwhal. For some reason, when I was surfing the web, the connection to the internet quit(wireless). I can only access the internet through Ethernet, but I am unable to connect wirelessly. When you click the network icon in the top menu all that shows up is:
Wireless Networks
Device not ready firmware missing
Enable Networking
Enable Wireless

I really need help and Id love if someone could help me on this.
Thanks!
-sean

---

### Post by hansdown on 2011-10-28
Hi, LinuxTrix.

Have you installed,The correct drivers?

If it is a broadcom,

Try these, from the software center, or synaptic package manager.

Welcome to the forum, by the by.

---

### Post by LinuxTrix on 2011-10-28
Hi Hansdown, and thanks. 
I had all of those packages downloaded except the Broadcom 802.11. However, when i installed, it said: Package operation failed:The installation or removal of a software package failed.:confused:
I have no idea what this means, and i still cant connect wi-fi:(

---

### Post by hansdown on 2011-10-28
Can you open a terminal, and enter;

```
ifconfg
```

Thanks.

---

### Post by LinuxTrix on 2011-10-28
eth0      Link encap:Ethernet  HWaddr 00:23:ae:0f:ae:bb  
          inet addr:192.168.15.3  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::223:aeff:fe0f:aebb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21283 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18573 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24803449 (24.8 MB)  TX bytes:3050372 (3.0 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4904 (4.9 KB)  TX bytes:4904 (4.9 KB)

---

### Post by hansdown on 2011-10-29
I need to apologize, LinuxTrix.

Could you post the output of,

```
lspci
```

from the terminal?

---

### Post by LinuxTrix on 2011-10-29
er #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600M GT] (rev a1)
03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

---

### Post by hansdown on 2011-10-29
Please try this;

```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source  

```
Please don't shoot me, if this doesn't work.

You may need to reboot.

---

### Post by LinuxTrix on 2011-10-29
YAY! YOUR A GENIUS! ITS WoRKING!! THANK U SOOO MUCH!!!:D

---

### Post by hansdown on 2011-10-29
> **LinuxTrix said:**
> YAY! YOUR A GENIUS! ITS WoRKING!! THANK U SOOO MUCH!!!:D

Wow!

I was starting to sweat blood.

Glad you fixed it, LinuxTrix.

Good work.

---

