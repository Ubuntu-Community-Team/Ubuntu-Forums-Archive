---
title: "Dell Inspiron 2200 wifi problem (Ubuntu 9.04)"
date: 2009-06-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Dafunkybhudda on 2009-06-07
Hi there i've got the same problem on a dell inspiron 2200. I am clued up on windows, but am struggling to find my way around on Linux. I have followed the instructions you posted and found them very informative. sorry to butt in on the post with my problem. but I got the following information.

lshw -c networlogical name: eth0
       version: 03
       serial: 00:12:3f:17:32:a5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI firmware=N/A ip=192.168.0.3 latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:04:b0:f7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: aa:3d:3c:a8:80:e2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

iwconfig:

pan0 no wireless extensions

nm-tool:

Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             disconnected
  Default:           no
  HW Address:        00:00:00:00:00:00

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


I've got faith in you guys, cos this linux aint for no mugs lol... eagerly await your reply

---

### Post by ugm6hr on 2009-06-07
Looks like you are using the b43 (broadcom) driver; confirm chipset with:
```
lspci
```

The wlan0 device is disabled; be certain that the wifi is enabled in BIOS.

If it is, plug into an ethernet connection and reboot (if it doesn't connect).

Then check System -> Admin -> Hardware Drivers
There should be an option to enable a Broadcom Firmware - this will install the driver firmware, which should get you online with wifi.

---

