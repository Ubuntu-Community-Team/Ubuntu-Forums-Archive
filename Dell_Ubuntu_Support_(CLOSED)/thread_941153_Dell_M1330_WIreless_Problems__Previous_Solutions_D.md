---
title: "Dell M1330 WIreless Problems:  Previous Solutions Don't Work..."
date: 2008-10-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vanishikawa on 2008-10-07
I'm brand new to linux and am currently dual-booting Vista and Ubuntu on a Dell XPS M1330.  Like many who I've seen have had same problem, the wireless card for my laptop is not being read by Ubuntu and drivers do not claim it.  I've gone through several searches on the forums and tried every method suggested, but nothing seems to help.  Any assistance would be greatly appreciated!

Here's some information that I've seen often asked for:


```
domenic@domenic-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:5e:36:f8
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 ip=199.111.237.55 latency=0 module=tg3 multicast=yes
domenic@domenic-laptop:~$ ndiswrapper -lbcmwl5 : driver installed
	device (14E4:4328) present
bcmwl6 : driver installed
	device (14E4:4328) present
domenic@domenic-laptop:~$ lspci -n | grep '14e4:43'0c:00.0 0280: 14e4:4328 (rev 03)
domenic@domenic-laptop:~$ lspci -n
00:00.0 0600: 8086:2a00 (rev 0c)
00:01.0 0604: 8086:2a01 (rev 0c)
00:1a.0 0c03: 8086:2834 (rev 02)
00:1a.1 0c03: 8086:2835 (rev 02)
00:1a.7 0c03: 8086:283a (rev 02)
00:1b.0 0403: 8086:284b (rev 02)
00:1c.0 0604: 8086:283f (rev 02)
00:1c.1 0604: 8086:2841 (rev 02)
00:1c.3 0604: 8086:2845 (rev 02)
00:1c.5 0604: 8086:2849 (rev 02)
00:1d.0 0c03: 8086:2830 (rev 02)
00:1d.1 0c03: 8086:2831 (rev 02)
00:1d.2 0c03: 8086:2832 (rev 02)
00:1d.7 0c03: 8086:2836 (rev 02)
00:1e.0 0604: 8086:2448 (rev f2)
00:1f.0 0601: 8086:2815 (rev 02)
00:1f.1 0101: 8086:2850 (rev 02)
00:1f.2 0106: 8086:2829 (rev 02)
00:1f.3 0c05: 8086:283e (rev 02)
01:00.0 0300: 10de:0427 (rev a1)
03:01.0 0c00: 1180:0832 (rev 05)
03:01.1 0805: 1180:0822 (rev 22)
03:01.2 0880: 1180:0843 (rev 12)
03:01.3 0880: 1180:0592 (rev 12)
03:01.4 0880: 1180:0852 (rev ff)
09:00.0 0200: 14e4:1713 (rev 02)
0c:00.0 0280: 14e4:4328 (rev 03)
```


Thanks again for helping!

---

### Post by doronz on 2008-11-03
Same problem here...

---

