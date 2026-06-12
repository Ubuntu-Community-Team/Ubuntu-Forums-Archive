---
title: "1420 &amp; kernel 2.6.28-13 doesnt detect my wireless driver"
date: 2009-07-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by aznkiller on 2009-07-01
on the newest kernel that i jus barely updated today didnt detect my wireless, the lite indicator didnt even light up when the wireless was on. when i went back to 2.6.28-11 the light lit up. so any help?

---

### Post by coffeeaddict22 on 2009-07-01
Hi,
The kernel has most wireless drivers built in these days, so it's not so much a matter of it detecting your driver as picking and working with the right one.
Could be due to a lot of things.  Assuming you're using a standard Ubuntu setup, can you type ```
nm-tool
``` in both kernels and post back the output?  If you're not, can you use the following two commands instead: ```
lshw -C network
sudo iwconfig
```
Feel free to hide the network addresses before posting if you're happy to confirm they're real.

---

### Post by Gladk on 2009-07-05
I'm not a topicstarter, but I have exactly the same problem on Dell Inspiron 1501. Actually, Ethernet also does not work, not only WIFI.


2.6.28.11, nm-tool:
```

NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            NULL(info.linux.driver)
  State:             unavailable
  Default:           no
  HW Address:        00:19:B9:60:69:1B

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: eth1  [Auto Lessingstr46] --------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        00:19:7E:53:C7:6C

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    FRITZ!Box Fon WLAN 7170: Infra, 00:1F:3F:10:CA:4A, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    default:         Infra, 00:15:E9:0A:ED:92, Freq 2437 MHz, Rate 0 Mb/s, Strength 60 WEP
    *Lessingstr46:   Infra, 00:1C:F0:FB:2A:5E, Freq 2412 MHz, Rate 54 Mb/s, Strength 60 WEP

  IPv4 Settings:
    Address:         192.168.0.198
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

```


2.6.28.11, lshw -C network:
```

*-network
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 01
       serial: 00:19:7e:53:c7:6c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 ip=192.168.0.198 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:60:69:1b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 56:95:50:f6:1a:c0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```


2.6.28.13, nm-tool:
```

NetworkManager Tool

State: disconnected

```

2.6.28.13, lshw -C network:
```

  *-network UNCLAIMED
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network UNCLAIMED
       description: Ethernet controller
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 16:a2:90:e4:74:1a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

Thank you for help.

---

### Post by Gladk on 2009-07-05
[http://georgia.ubuntuforums.org/showpost.php?p=7506946&postcount=18](http://georgia.ubuntuforums.org/showpost.php?p=7506946&postcount=18)
Post #18 solved my problem

```

sudo /sbin/lrm-manager
sudo modprobe wl

```

Thank you all!

---

