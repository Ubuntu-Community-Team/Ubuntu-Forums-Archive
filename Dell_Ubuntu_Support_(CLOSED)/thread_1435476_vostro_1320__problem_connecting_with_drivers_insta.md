---
title: "vostro 1320 : problem connecting with drivers installed"
date: 2010-03-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by wilfredt on 2010-03-21
Hi ,
      I have installed ubuntu 9.10 recently , by default installation I cudnt find my device drivers , I then have installed the drivers now . but still I dont seem to be able to connect to wireless . although I am able to do so with LAN (ethernet) .
again I installed wifi radar which shows my wireless , but when I am connecting 
I get a indefinite wait while resolving DHCP .

---

### Post by coffeeaddict22 on 2010-03-26
Hi, 
There's a page on wireless in the wiki [here that should help.]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")
As a start, open a terminal and type in 
```
nm-tool
```
Post back the output if you need more help.

---

### Post by wilfredt on 2010-03-30
Hi ,
       thanks for the reply , I went through the documentation , somewhere down the document i found for rfkill list 
the following out put comes 
/////
root@wilfred-laptop:~# rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
///////// 
This command shows a hardware block yes when the wifi is on ..

also I am giving the nm -tool output 
NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unmanaged
  Default:           no
  HW Address:        00:24:E8:9B:AD:ED

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        00:24:2C:63:B5:5F

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points

---

### Post by coffeeaddict22 on 2010-03-31
You'll have a switch.  Sometimes its a function-key combination, sometimes a separate switch.  Almost universally it seems that if there's a light associated with it, it won't work in Linux.  Try changing it's state.

The output of ```
lshw-C network
``` would also help.

---

### Post by wilfredt on 2010-04-25
Thanks for helping out , the wifi seems to be working now , although I had changed my ISP , for some other reasons , now the wireless is auto detected

---

### Post by amorphousvn on 2010-07-19
My vostro 1320 has the same problem, but the solution above doesn't work. Is there anybody help me? 

Thank you in advance!

~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:24:E8:CE:D5:5F

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             8.8.8.8
    DNS:             8.8.4.4


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             unavailable
  Default:           no
  HW Address:        00:26:5E:3A:8E:D7

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 



~$ sudo lshw -C network
 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 03
       serial: 00:24:e8:ce:d5:5f
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:30 ioport:3000(size=256) memory:f6004000-f6004fff(prefetchable) memory:f6000000-f6003fff(prefetchable) memory:f6020000-f603ffff(prefetchable)
  *-network
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:fa000000-fa003fff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:26:5e:3a:8e:d7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by wildmanne39 on 2012-07-07
Old thread closed.

---

