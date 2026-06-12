---
title: "Dell Mini 10 - connected to wireless network but cant access firefox"
date: 2010-08-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by buddhasurf on 2010-08-04
Hi, 
I just installed UNR on my dell mini. I connected to internet  via wire and downloaded the updates. Installed Broadcom driver and  wireless says it is connected. 

I cannot open any websites using  firefox and when I try to download programs using ubuntu software centre  - it says in progress and then "failed to download. check your internet  connection". 

The status bar says it is connected and has a  strong signal. I deleted the driver and reinstalled it. I deleted the  wireless connection and re-entered it. Now, I am not sure what to do. 

Any suggestions? 

Thanks.

---

### Post by ugm6hr on 2010-08-05
Run the following commands when "connected" by wifi (and disconnected by ethernet).
```
lshw -class network
ifconfig
iwconfig
route -n
ping -c 3 208.67.219.101
ping -c 3 www.opendns.com
```
Then copy / paste the results back here.

---

### Post by buddhasurf on 2010-08-05
> **ugm6hr said:**
> Run the following commands when "connected" by wifi (and disconnected by ethernet).
```
lshw -class network
ifconfig
iwconfig
route -n
ping -c 3 208.67.219.101
ping -c 3 www.opendns.com
```Then copy / paste the results back here.

Hi [[COLOR=#d40000]**ugm6hr**[/COLOR]]("http://ubuntuforums.org/member.php?u=103883"), 

Thanks for replying to my query! Here is the info that you asked for. 

             [FONT=Courier New][SIZE=2][FONT=&quot]chris@Chris:~$ lshw -class network [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]WARNING: you should run this program as super-user. [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]  *-network               [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]       description: Wireless interface [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]       product: BCM4312 802.11b/g [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]       vendor: Broadcom Corporation [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]       physical id: 0 [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]       bus info: pci@0000:03:00.0 [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]       logical name: eth1 [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]       version: 01 [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]       serial: 00:25:56:10:f1:f1 [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]       width: 64 bits [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]       clock: 33MHz [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]       capabilities: bus_master cap_list ethernet physical wireless [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=10.42.43.1 latency=0 multicast=yes wireless=IEEE 802.11 [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]       resources: irq:17 memory:f0100000-f0103fff [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]  *-network [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]       description: Ethernet interface [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]       vendor: Realtek Semiconductor Co., Ltd. [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]       physical id: 0 [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]       bus info: pci@0000:04:00.0 [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]       logical name: eth0 [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]       version: 02 [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]       serial: 00:24:e8:a5:32:c6 [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]       width: 64 bits [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]       clock: 33MHz [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]       capabilities: bus_master cap_list rom ethernet physical [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]       resources: irq:27 ioport:2000(size=256) memory:f0510000-f0510fff(prefetchable) memory:f0500000-f050ffff(prefetchable) memory:f0520000-f053ffff(prefetchable) [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]chris@Chris:~$ ifconfig [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]eth0      Link encap:Ethernet  HWaddr 00:24:e8:a5:32:c6  [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]          UP BROADCAST MULTICAST  MTU:1500  Metric:1 [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]          collisions:0 txqueuelen:1000 [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]          Interrupt:27 Base address:0xe000 [/FONT][/SIZE][/FONT]
  
  [FONT=Courier New][SIZE=2][FONT=&quot]eth1      Link encap:Ethernet  HWaddr 00:25:56:10:f1:f1  [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0 [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]          inet6 addr: fe80::225:56ff:fe10:f1f1/64 Scope:Link [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]          RX packets:0 errors:0 dropped:0 overruns:0 frame:5571 [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]          TX packets:21 errors:11 dropped:0 overruns:0 carrier:0 [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]          collisions:0 txqueuelen:1000 [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]          RX bytes:0 (0.0 B)  TX bytes:4467 (4.4 KB) [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]          Interrupt:17 [/FONT][/SIZE][/FONT]
  
  [FONT=Courier New][SIZE=2][FONT=&quot]lo        Link encap:Local Loopback  [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]          inet addr:127.0.0.1  Mask:255.0.0.0 [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]          inet6 addr: ::1/128 Scope:Host [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]          UP LOOPBACK RUNNING  MTU:16436  Metric:1 [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]          RX packets:845 errors:0 dropped:0 overruns:0 frame:0 [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]          TX packets:845 errors:0 dropped:0 overruns:0 carrier:0 [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]          collisions:0 txqueuelen:0 [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]          RX bytes:133812 (133.8 KB)  TX bytes:133812 (133.8 KB) [/FONT][/SIZE][/FONT]
  
  [FONT=Courier New][SIZE=2][FONT=&quot]chris@Chris:~$ iwconfig [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]lo        no wireless extensions. [/FONT][/SIZE][/FONT]
  
  [FONT=Courier New][SIZE=2][FONT=&quot]eth0      no wireless extensions. [/FONT][/SIZE][/FONT]
  
  [FONT=Courier New][SIZE=2][FONT=&quot]eth1      IEEE 802.11  Access Point: Not-Associated   [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]          Link Quality:5  Signal level:199  Noise level:170 [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]          Rx invalid nwid:0  invalid crypt:0  invalid misc:0 [/FONT][/SIZE][/FONT]
  
  [FONT=Courier New][SIZE=2][FONT=&quot]pan0      no wireless extensions. [/FONT][/SIZE][/FONT]
  
  [FONT=Courier New][SIZE=2][FONT=&quot]chris@Chris:~$ route -n [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]Kernel IP routing table [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]Destination     Gateway         Genmask         Flags Metric Ref    Use Iface [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]10.42.43.0      0.0.0.0         255.255.255.0   U     2      0        0 eth1 [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1 [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]chris@Chris:~$ ping -c 208.67.219.101 [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]Usage: ping [-LRUbdfnqrvVaA] [-c count] [-i interval] [-w deadline] [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]            [-p pattern] [-s packetsize] [-t ttl] [-I interface or address] [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]            [-M mtu discovery hint] [-S sndbuf] [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]            [ -T timestamp option ] [ -Q tos ] [hop1 ...] destination [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]chris@Chris:~$ ping -c [www.opendns.com]("http://www.opendns.com") [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]ping: bad number of packets to transmit. [/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]chris@Chris:~$ ^C [/FONT][/SIZE][/FONT]
  [FONT=&quot][FONT=Courier New][SIZE=2]chris@Chris:~$[/SIZE][/FONT] [/FONT]

---

### Post by Iowan on 2010-08-05
Hmmm... You need to include a count with the **ping** command (ping -c [COLOR="Red"]3[/COLOR] 208.67.219.101)
Curious that no default gateway shows up under **route -n**...

---

### Post by buddhasurf on 2010-08-05
> **Iowan said:**
> Hmmm... You need to include a count with the **ping** command (ping -c [COLOR=Red]3[/COLOR] 208.67.219.101)
Curious that no default gateway shows up under **route -n**...

My apologies....
[FONT=Courier New][SIZE=2]
[/SIZE][/FONT]              [FONT=Courier New][SIZE=2][FONT=&quot]chris@Chris:~$ ping -c 3 208.67.219.101[/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot][/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]connect: Network is unreachable[/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot][/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]chris@Chris:~$ ping -c 3 [www.opendns.com](www.opendns.com)[/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot][/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot]ping: unknown host [www.opendns.com](www.opendns.com)[/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=2][FONT=&quot][/FONT][/SIZE][/FONT]
  [FONT=&quot][FONT=Courier New][SIZE=2]chris@Chris:~$ [/SIZE][/FONT][/FONT]
  [FONT=&quot][/FONT]

---

### Post by buddhasurf on 2010-08-05
Can anybody help? Please!!

---

### Post by ugm6hr on 2010-08-06
> **Iowan said:**
> Curious that no default gateway shows up under **route -n**...

This is weird...

You have an IP address 10.42.43.1
But no gateway...

This means your router is not assigning IP addresses correctly.

Can you connect to the same router by wire and run the command and post here again:
```
ifconfig
```

Or from any Windows computer connected:
```
ipconfig
```

---

### Post by bergfly on 2010-08-07
Looking into this I suspect the issue may not be the laptop, it might be the network. When you say you are using wireless, is it at home or work? Can you get onto it fine with a windows machine? Do you access to the wireless router. I have a mini 10 with a boardcom wireless nic and have never had any issues, and it is well travelled. 

If you can post some more details of the network, we can maybe troubleshoot from that side. As Iowan pointed out, you really should have got a gateway address. 

Can you also try the following

```
ping -c5 127.0.0.1
```

and then

```
ping -c5 10.42.43.1
```assuming your address has not changed

cheers

---

