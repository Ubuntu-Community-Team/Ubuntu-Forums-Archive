---
title: "networking again"
date: 2006-01-02
forum: Desktop Environments
---

### Post by alterstill on 2006-01-02
Hi all,

I've spent few days to solve the network problem on my Acer Travelmate 4001 laptop. After installing Breezy I had no internet att all, although I could access my wireless AP (DLink DSL G-604T). Hunting for solution on this forum has allowed me to make Firefox working (about:config and disabling ipv6 support).
Then I followed the steps found on this forum and I have disabled ipv6 for all system. Unfortunately Firefox is the only application that can work online, still cannot use evolution, gaim, upt-get etc.
ping, nslookup, host [www.google.com](www.google.com) seem to work fine.

I've already tried both dhcp and static settings.
Any ideas? What else should I do? Upgrading firmware of router sounds risky to me. Thanks in advance and sorry for my English ;) .
Here are some infos about my system:

```
bag@alterstill:~$ sudo lspci
0000:02:04.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)
```

```

bag@alterstill:~$ sudo lshw -C network
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@02:04.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:77:59:61
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.0.6 firmware=ABG:9.0.1.5 (Oct 15 2004) ip=192.168.1.3 link=yes multicast=yes wireless=IEEE 802.11g resources: iomemory:d0208000-d0208fff irq:10
```

```
bag@alterstill:~$ ping -c 4 www.google.com
PING www.google.com (216.239.59.103) 56(84) bytes of data.
64 bytes from www.google.com (216.239.59.103): icmp_seq=1 ttl=248 time=44.3 ms
64 bytes from www.google.com (216.239.59.103): icmp_seq=2 ttl=248 time=42.6 ms
64 bytes from www.google.com (216.239.59.103): icmp_seq=3 ttl=248 time=41.9 ms
64 bytes from www.google.com (216.239.59.103): icmp_seq=4 ttl=248 time=42.0 ms

```

```
bag@alterstill:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"alternet"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:3D:B0:B2:B4
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=97/100  Signal level=-28 dBm  Noise level=-86 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
```

bag@alterstill:~$ dmesg | grep ipw
[4294704.729000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
[4294704.729000] ipw2200: Copyright(c) 2003-2004 Intel Corporation
[4294704.731000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[4295151.438000] ipw2200: Firmware error detected.  Restarting.
[4295551.882000] ipw2200: Firmware error detected.  Restarting.
[4296173.223000] ipw2200: Firmware error detected.  Restarting.
[4297476.490000] ipw2200: Firmware error detected.  Restarting.
```

---

