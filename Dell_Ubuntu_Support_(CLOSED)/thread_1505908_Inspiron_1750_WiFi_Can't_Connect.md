---
title: "Inspiron 1750 WiFi Can't Connect"
date: 2010-06-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Freik_1 on 2010-06-09
Update: I was able to get the B43 driver option back. I just had to disable the STA driver and then restart. However, I still wasn't able to connect to my wireless network. After switching back to the B43 driver, my system would sometimes still hang for about 3-5 seconds. I decided to try switching back to the STA driver, but when I hit activate on STA (without removing B43), my system hung for >30 seconds and I had to hard restart it. Upon restart it was still on the B43 driver and it finally connected to my wireless network, and as of yet my system hasn't hung. I will now attempt to restart and boot into Windows and see if it works there, too.

Update 2: Restarted, but it took rediculously long for Ubuntu to shut down, almost 45 seconds. Couldn't get the wireless connection to work in Windows, came back to Ubuntu, and the wireless wouldn't work either. Also, the annoying system hangs where back. Tried going back to the STA driver, but it's currently stuck at "Downloading and Installing Driver" with the orange bar bouncing back and forth. I think I'm going to try a hard reset again.

Update 3: It appears that the hard reset has worked! The Broadcom STA driver is the active driver and my wireless is now working in both Ubuntu and Windows 7! I have no idea what would cause the adapter to not work properly in both OS's, but I'll leave that question to the smart people ^_^

--------------

Just installed Ubuntu 10.04 as a second OS yesterday, everything seemed to be going fine, got the system updated and running smooth. In Hardware Drivers I had the option of the B43xx driver or the Broadcom STA driver. Since I was familiar with the B43xx I went ahead and used that. However, today my wireless connection was acting funny (kept dropping out and sometimes the system would temporarily hang when online) so I switched to the Broadcom STA driver.

Now I can not connect to any wireless networks in Ubuntu **or Windows 7**! Also, in Hardware Drivers I no longer have the B43xx driver as an option, even though it is still installed. I attempted the steps in the second post of [this thread]("http://ubuntuforums.org/showthread.php?t=1049761"), but it still won't work. Pushing the Wifi button on the keyboard didn't do anything either, nor did reinstalling the card in Windows 7.

Specs:
Dell Inspiron 1750
Core 2 Duo
4GB Memory
BCM4312
Ubuntu 10.04 LTS 64bit

Here's the output from some terminal commands.

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:25:64:63:b0:19  
          inet addr:192.168.16.64  Bcast:192.168.16.255  Mask:255.255.255.0
          inet6 addr: fe80::225:64ff:fe63:b019/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6081 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5552 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6114902 (6.1 MB)  TX bytes:836078 (836.0 KB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 70:1a:04:1b:e7:9d  
          inet6 addr: fe80::721a:4ff:fe1b:e79d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3646 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3646 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:502375 (502.3 KB)  TX bytes:502375 (502.3 KB)
```sudo lshw -C network
```
*-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 70:1a:04:1b:e7:9d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:25:64:63:b0:19
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A ip=192.168.16.64 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:28 memory:f68fc000-f68fffff ioport:de00(size=256)
```

---

