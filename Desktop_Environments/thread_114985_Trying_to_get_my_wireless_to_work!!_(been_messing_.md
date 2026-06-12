---
title: "Trying to get my wireless to work!! (been messing with /etc/network/interfaces)"
date: 2006-01-09
forum: Desktop Environments
---

### Post by kundalinikat on 2006-01-09
I have a Linksys WMP54Gv4 with Ra2500 chipset.
My wireless router is encrypted with WPA.
I've been poking around the forums and the Wiki and trying iwconfig, iwlist, and I edited /etc/network/interfaces as someone suggested here...

*copious possibly redundant info follows*

This is what's in my '/etc/network/interfaces':

```
mapping hotplug
        script grep
        map eth0

auto ra0

iface ra0 inet dhcp
wireless-essid [[network]]
wireless-key [[key]]
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up ifconfig ra0 essid "[[network]]"
        pre-up ifconfig ra0 mode Managed
        pre-up iwpriv ra0 set AuthMode=WPAPSK
        pre-up iwpriv ra0 set EncrypType=TKIP
        pre-up iwpriv ra0 set WPAPSK="[[key]]"
        pre-up ifconfig ra0 up

auto ra0
```


This is what I get from typing 'iwconfig':

```
ra0       RT2500 Wireless  ESSID:"[[key]]"
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:11 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-120 dBm  Noise level:-195 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

from typing 'ifconfig':

```
ra0       Link encap:Ethernet  HWaddr 00:0C:41:6C:0E:0E
          inet6 addr: fe80::20c:41ff:fe6c:e0e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86907 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:4171536 (3.9 MiB)
          Interrupt:23 Base address:0x4000
```

from typing 'iwlist scan':

```
ra0       Scan completed :
          Cell 01 - Address: 00:0F:B5:EE:07:42
                    Mode:Managed
                    ESSID:"[[network]]"
                    Encryption key:on
                    Channel:11
                    Quality:0/100  Signal level:-41 dBm  Noise level:-195 dBm
```

The really weird thing is from typing 'iwconfig' I get a signal level of -120 dBm and from 'iwlist scan' I get a signal level of -41 dBm. What's going on??

(right now i'm connected via ethernet (after typing 'sudo dhclient') but wires are stretched through hallways, it's quite unworkable in the long term :( )

---

