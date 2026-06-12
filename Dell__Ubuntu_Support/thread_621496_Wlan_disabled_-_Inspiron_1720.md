---
title: "Wlan disabled - Inspiron 1720"
date: 2007-11-23
forum: Dell  Ubuntu Support
---

### Post by vuroth on 2007-11-23
Installed 7.10.  Wireless network shows up in system->administration->network, but enable fails.

lshw yields the following:

           *-network DISABLED
                description: Wireless interface
                product: BCM94311MCG wlan mini-PCI
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: eth1
                version: 01
                serial: 00:1d:60:a9:68:0c
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22

Having read some of the troubleshooting stuff, I'm unclear as to whether I have to manually enable the wireless card, or if something else is amiss.

fwiw, iwconfig gives the following:

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Any insights into why I'm seeing DISABLED, and on how to fix it?

Thanks.

V

---

### Post by vuroth on 2007-11-23
Figures, nothing leads you to finding the answer yourself like asking someone else. :)

The answer was system->administration->restricted drivers manager.

I may be having more problems, though....

---

