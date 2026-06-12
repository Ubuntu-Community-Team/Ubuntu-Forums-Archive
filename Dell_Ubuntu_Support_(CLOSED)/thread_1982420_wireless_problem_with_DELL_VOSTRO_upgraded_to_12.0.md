---
title: "wireless problem with DELL VOSTRO upgraded to 12.04"
date: 2012-05-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by olinart on 2012-05-18
The wireless worked fine on 10.04, but fails to connect with the new LTS system (32 bit).
The failure is:
[ 3262.329542] wlan0: authenticate with 00:26:88:e6:db:34 (try 1)
[ 3262.331556] wlan0: authenticated
[ 3262.361303] wlan0: associate with 00:26:88:e6:db:34 (try 1)
[ 3262.365295] wlan0: RX AssocResp from 00:26:88:e6:db:34 (capab=0x411 status=12 aid=0)
[ 3262.365301] wlan0: 00:26:88:e6:db:34 denied association (code=12)
[ 3262.385620] wlan0: deauthenticating from 00:26:88:e6:db:34 by local choice (reason=3)

It occurs only when I connect to a router set to WPA TKIP. Works fine with WPA AES.
I looked for additional drivers with the Wireless connections app and, at the suggestion of a forum posting, installed ndiswrapper-1.58rc1 from sourceforge with no effect. Is there a new driver needed? More generally, are there proprietary Dell drivers tested on 12.04 that I should download?
I noticed that the driver is 64 bit - would upgrading to the 64bit system help?

Present driver info:
description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:12:00.0
       logical name: wlan0
       version: 01
       serial: ec:55:f9:42:85:eb
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k  driverversion=3.2.0-24-generic-pae firmware=N/A latency=0 link=no  multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fe400000-fe40ffff

/sbin/iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:"Blacknight"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:26:88:E6:DB:34   
          Bit Rate=1 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=70/70  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3  Invalid misc:30   Missed beacon:0

---

### Post by olinart on 2012-06-25
I also tried WICD instead of networkManager.  WICD reports wrong password for the connection (that's the password that is correct for Netwrork manager using AES encryption. The message is likely  from the association failure, hence the same error. Anyone trying to fix the driver? This orked fine in 10.04.

---

