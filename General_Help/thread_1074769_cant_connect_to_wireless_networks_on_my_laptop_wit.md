---
title: "cant connect to wireless networks on my laptop with ubuntu"
date: 2009-02-19
forum: General Help
---

### Post by darthfodder on 2009-02-19
Hi, I'm new to these forums, ubuntu, and Linux in general. I finally got fed up with Vista(and Windows in general) and decided to make the jump to Linux. 

I installed ubuntu via wubi (I'll probably use a CD to make a seperate partition at some point, but for right now I just want to try it out) on my laptop, it installed/booted up fine, and even detected wireless networks. But it won't connect. The light that comes on when my laptop's wireless switch is on doesn't come on in ubuntu and  when I try to connect to a wireless network it tries to connect but fails, or else instantly disconnects, its impossible to say. It shouldn't be a low signal problem because when I'm on Windows with the same computer in the same exact place it gets full bars and connects just fine. I did a little bit of prowling around the forum to see if I could find an answer without asking, but to no avail. Heres my basic network info from the terminal; I have no idea whether this is too much or too little info:


  *-network               
       description: Wireless interface 
       product: AR928X Wireless Network Adapter (PCI-Express) 
       vendor: Atheros Communications Inc. 
       physical id: 0 
       bus info: pci@0000:06:00.0 
       logical name: wmaster0 
       version: 01 
       serial: 00:1f:e1:aa:96:d0 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless 
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn 
  *-network 
       description: Ethernet interface 
       product: 88E8055 PCI-E Gigabit Ethernet Controller 
       vendor: Marvell Technology Group Ltd. 
       physical id: 0 
       bus info: pci@0000:08:00.0 
       logical name: eth0 
       version: 13 
       serial: 00:1d:ba:19:1f:d2 
       capacity: 1GB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 1 
       logical name: pan0 
       serial: 86:0d:b9:d1:07:dc 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by mttman on 2009-02-19
post results from opening a terminal and typing ```
ifconfig
```
and
```
iwlist ath0 scan
```

ps - you can put information in the code tags by hitting the # button at the top of the reply dialoge or putting it inside [ CODE ] and [ /CODE ] tags (no spaces)

---

### Post by darthfodder on 2009-02-19
```
 fconfig 
eth0      Link encap:Ethernet  HWaddr 00:1d:ba:19:1f:d2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:486 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:486 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:30448 (30.4 KB)  TX bytes:30448 (30.4 KB) 

wlan0     Link encap:Ethernet  HWaddr 00:1f:e1:aa:96:d0  
          inet6 addr: fe80::21f:e1ff:feaa:96d0/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:655 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:87727 (87.7 KB)  TX bytes:4176 (4.1 KB) 

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-E1-AA-96-D0-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

shawn@ubuntu:~$ iwlist ath0 scan 
ath0      Interface doesn't support scanning. 

```

Also, I don't know if the following is useful or not:

```
shawn@ubuntu:~$ iwlist scan 
lo        Interface doesn't support scanning. 

eth0      Interface doesn't support scanning. 

wmaster0  Interface doesn't support scanning. 
 
wlan0     Scan completed : 
          Cell 01 - Address: 00:0B:86:4C:96:A1 
                    ESSID:"Butte_College" 
                    Mode:Master 
                    Channel:6 
                    Frequency:2.437 GHz (Channel 6) 
                    Quality=65/100  Signal level:-53 dBm  Noise level=-95 dBm 
                    Encryption key:off 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
                              48 Mb/s; 54 Mb/s 
                    Extra:tsf=000000538880d515 
                    Extra: Last beacon: 100ms ago 

pan0      Interface doesn't support scanning. 

```

---

### Post by mttman on 2009-02-19
if you really do have an atheros card then you have the wrong driver installed for it, which would explain the problems.

run ```
lsmod |grep ath
``` and post the output. it should look something like this ```
$ lsmod |grep ath
ath_rate_sample        19968  1 
ath_pci                99096  0 
wlan                  211952  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               198864  3 ath_rate_sample,ath_pci

```

---

