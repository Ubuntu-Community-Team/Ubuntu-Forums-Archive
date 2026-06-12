---
title: "Dell Latitude D600 Wireless Issue"
date: 2009-07-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by unAWARE 777 on 2009-07-17
My dad is currently running a Dell Latitude D600 with Jaunty Jackalope, and an Intel Centrino processor. The hardware driver ubuntu suggested (the Broadcom B43legacy driver) works..kind of. The computer finds and connects to the router, but with a signal strength of 0%, virtually meaning the card really isn't connecting. Mind you this is while the computer is practically next to the router. We tried this on a laptop that was supposedly identical to this one, and the driver worked great. I'm suspecting that internally, the cards may be different. Any advice?

---

### Post by coffeeaddict22 on 2009-07-18
Hi,
Try a few terminal commands.  Open a terminal (Applications/Accessories/Terminal, then type in```
nm-tool
lshw -C network
ifconfig
```
should give you enough to start; post back here if you want more help.  If you want more info on any of the commands, type in the terminal ```
man xxxxx
``` where xxxxx is the command and you'll get a page or two back.

---

### Post by ajonesse on 2009-10-29
I am having the same problem (sorry for the necropost) and I ran your commands and got this.
> 
NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        00:0F:1F:D1:F9:AE

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0  [Wireless] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            NULL(info.linux.driver)
  State:             connected
  Default:           no
  HW Address:        00:11:F5:1B:E2:49

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *Wireless:       Ad-Hoc, F2:7E:D7:0E:40:9A, Freq 2412 MHz, Rate 0 Mb/s, Strength 0 WPA

  IPv4 Settings:
    Address:         10.42.43.1
    Prefix:          24 (255.255.255.0)
    Gateway:         0.0.0.0



sebastian@sebastian-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:d1:f9:ae
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5705-v3.16 latency=32 mingnt=64 module=tg3 multicast=yes
  *-network:1
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:11:f5:1b:e2:49
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=10.42.43.1 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 66:06:5e:16:32:68
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
sebastian@sebastian-laptop:~$ lshw -C network
I can get a connection but no signal strength, I am about three feet from the router and it works fine in my windows partition.  I have the same model of laptop and wireless card, I followed the instructions on the linuxwireless site and it worked perfectly. 

Any ideas?

---

