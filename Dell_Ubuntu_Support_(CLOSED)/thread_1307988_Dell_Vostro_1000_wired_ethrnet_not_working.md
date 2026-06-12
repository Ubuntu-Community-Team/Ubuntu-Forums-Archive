---
title: "Dell Vostro 1000 wired ethrnet not working"
date: 2009-10-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vimalgs on 2009-10-31
Hi,
I just installed ubuntu 8.04..3 LTS for amd 64 bit.on my dell vostro 1000 
I even made my wireless work by installing the proprietary firmware.

inputting lspci on the terminal gives me this:

Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

The problem now is that my wired lan is not working.
any help in this matter would be appreciated.

I am guessing that there must be a driver download for BCM4401-B0 100 Base -Tx.
I am not able to find it after wading through lots of forums.

---

### Post by vimalgs on 2009-10-31
I am writing on this through the wireless.an if config gave me this



vimal@vimal-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:23:ae:fa:5e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:992 errors:0 dropped:0 overruns:0 frame:0
          TX packets:95 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:97900 (95.6 KB)  TX bytes:16556 (16.1 KB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:189 errors:0 dropped:0 overruns:0 frame:0
          TX packets:189 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10653 (10.4 KB)  TX bytes:10653 (10.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:4c:13:91:6c  
          inet addr:10.25.32.237  Bcast:10.25.255.255  Mask:255.255.0.0
          inet6 addr: fe80::21e:4cff:fe13:916c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:175280 errors:0 dropped:0 overruns:0 frame:0
          TX packets:94268 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:230696896 (220.0 MB)  TX bytes:9621622 (9.1 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1E-4C-13-91-6C-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


I have tried disconnecting my wireless and then connecting to wired ethernet.It shows wired connection.But i am unable to surf the net with known proxies and ip settings.
I am also not able to get PING reply from network computers via the wired connection.

---

### Post by cfreak2399 on 2009-11-05
I have a similar problem with 9.10.  I don't have any configuration at all for eth0 in the network manager or in ifconfig. I don't see the device listed anywhere.

It works fine in windows. And the cable and port I use work fine for my desktop machine.

The weird thing is that it was detected with the LiveCD.

Sadly I can't get the wireless to work either (no connection to download the appropriate driver and apparently no way to get it off the CD even though it worked in Live as well!) so I'm pretty much stuck with a useless ubuntu on the laptop until I can find the answer.

---

### Post by vimalgs on 2009-11-06
Hi Cfreak,
I too initially faced a same problem with 9.10.I guess this is some driver issue or proprietary firmware which is not yet available for 9.10.

What I can suggest is go back to 8.04..3 LTS(long term support).All drivers and firmware exist for this version.I was having intial hiccups(I hadn't upadtes some packages) but now my wired ethernet works like a breeze(i am writing this through a wired ethernet.

---

### Post by Rede on 2009-11-19
I have the same problem - worked in previous releases, and one in three times I boot it is detected and works.

I found this in syslog:


...
Nov 19 08:50:02 localhost kernel: [   14.897045] eth1: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:15:c5:7b:83:06             
Nov 19 08:50:02 localhost udevd-work[606]: error changing netif name eth0 to eth1: Device or resource busy                   
Nov 19 08:50:02 localhost NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/net/eth0, iface: eth0)                                                                                                
Nov 19 08:50:02 localhost NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/net/eth0, iface: eth0): no ifupdown configuration found.                                                               
Nov 19 08:50:02 localhost NetworkManager: <info>  Found radio killswitch rfkill0 (at /sys/devices/virtual/rfkill/rfkill0) (driver <unknown>)                                                                                                                 
...

---

### Post by Rede on 2009-11-19
I'm using an Inspiron 640m, with a similar network card.

Doing the following fixed my issue:

```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```


The file was regenerated on reboot and I had my NIC's back.

Previously, wired was eth0 and after doing so it became eth1, with wlan being eth0.

---

