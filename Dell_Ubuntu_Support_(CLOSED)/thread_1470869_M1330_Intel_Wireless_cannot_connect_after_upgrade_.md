---
title: "M1330 Intel Wireless cannot connect after upgrade to 10.04"
date: 2010-05-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Ryback on 2010-05-03
Hello all,

A couple of days ago I upgraded to 10.04 from 9.10 on my XPS M1330, and now the wireless cannot connect to any networks.  I have only tried with WPA encryption.  It can detect the networks, but gets stuck at the point of aquiring a network address, and eventually times out.  I'm new to wireless issues, could someone give me a hand diagnosing?  It's an intel card so I believe should work fine using the driver in the kernel.  Everything was working fine in 9.10 prior to the upgrade.  

Many thanks if anyone can help!  Below are various outputs to confirm the hardware, driver etc.  Perhaps the next thing would be to obtain logging information from the connection attempts, but I'm not sure how...

lspci -nn
```

00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 02)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
03:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)

```

iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"f2\x0D\xB71X\xA3Z%]\x05\x17X\xE9^\xD4\xAB\xB2\xCD\xC6\x9B\xB4T\x11\x0E\x82tA!=\xDC\x87"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
pan0      no wireless extensions.

```

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:1d:09:40:5c:42  
          inet6 addr: fe80::21d:9ff:fe40:5c42/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4555 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3984 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4654516 (4.6 MB)  TX bytes:729988 (729.9 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:4e:29:ea  
          inet6 addr: fe80::21f:3cff:fe4e:29ea/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1224 (1.2 KB)  TX bytes:9433 (9.4 KB)

```

nm-tool
```

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             disconnected
  Default:           no
  HW Address:        00:1F:3C:4E:29:EA

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Tiscali11DACD:   Infra, 00:21:04:11:DA:CD, Freq 2417 MHz, Rate 54 Mb/s, Strength 81 WPA WPA2
    BTHomeHub2-4HM2: Infra, 00:24:17:C7:02:6F, Freq 2452 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        00:1D:09:40:5C:42

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off

```

---

### Post by Ryback on 2010-05-03
Bizarrely, after about the 10th boot of the machine since the upgrade, it suddenly started working.  No further upgrades have been applied, so I'm at a loss to explain it.  I'll update back one way or the other.

---

### Post by mihai.ile on 2010-05-06
Strange, I have an nvidia powered m1330 but also with intel wifi and never had problems (oh I also never do distro updates, I do a clean install every time)

---

### Post by Ryback on 2010-05-07
It seems to have fixed itself now.  I'm not sure what the issue could have been as it was occurring with both networks that I was trying to connect to.

I do notice that it takes longer to connect to a network under 10.04 generally though.

Just to clarify though, the "Intel" in the post subject was referring to my wireless card, not video card (as some machines have Broadcom wireless which use different drivers).

---

### Post by keithb685 on 2010-05-07
I've the same problem with a Dell 1525, spend hours setting up 10.04 thinking it would solve this wireless issue I also had on Karmic but no joy. Will try the "10 reboots" to see if it fixes it.

Loaded 10.04 onto a Dell tower machine and it ran no problem, picked up wireless perfectly as it did with karmic - seems to be laptops :(

---

### Post by Ryback on 2010-05-10
Have you tried using a usb/boot from live cd and seeing if the wireless works ok there?  There shouldn't be anything extra to install so it should work straight out of the box.  That was my next move before mine started working.

---

