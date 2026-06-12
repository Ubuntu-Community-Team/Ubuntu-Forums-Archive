---
title: "WLAN not reciveing any IP"
date: 2005-10-13
forum: Desktop Environments
---

### Post by hamil on 2005-10-13
Hello!

I had a similar problem in Hoary, but it dissapered when I installed Breezy Colony 4. 
2 days ago, when i did an upgrade, I got disconnected from the net on my Ubuntu machine. I thought it may be a minor bug, that would be fixed, whith the final release of Breezy. 
I did a fresh install today, looking forward to surf with my Netgear WLAN adapter card again... But no..

During the installation process, my card is detected, and I entered the correct ESSID, and key. It also downloaded some languagefiles from the net during the installation, so it should work in X also??
After logging in, i tried to open firefox and surf, but network server is not found.
I opened the network administration, and could see that the ESSID was correct, and that the password was corect. I tried to disable, and enable a couple of times, but no help doing that.
A friend of me recommended the Netapplet, so I installed that one. But the netapplet can not see any of the available networks. I have 4 diffrent ones, which I can see in Network admin, 3 of those which I have the key for.
I have set it to DHCP, and not Static IP, since I do not know any other information but the DNS..

Any ideas to what I can do to get connected on my Ubuntu machine again? Or what kind of other information I have to post?

Any help is greatly appreciated!
Thnx in advance!

Lasse

---

### Post by dbott67 on 2005-10-13
From a terminal prompt, what do you get when you type **iwlist wlan0 scanning**:
```
dbott@breezy:~$ iwlist wlan0 scanning

wlan0     Scan completed :

Cell 01 - Address: 00:40:05:B2:AF:45
              ESSID:"bott"
              Mode:Master
              Frequency:2.437 GHz (Channel 6)
              Quality=34/100  Signal level=39/100  Noise level=11/100
              Encryption key:on
              Bit Rate:22 Mb/s

Cell 02 - Address: 00:05:5D:FA:B2:FA
              ESSID:"soni"
              Mode:Master
              Frequency:2.437 GHz (Channel 6)
              Quality=24/100  Signal level=27/100  Noise level=12/100
              Encryption key:on
              Bit Rate:54 Mb/s
```

There are a couple of other commands you can try from the terminal as well to get more information:
```
iwgetid
iwevent
ifconfig

```

If you can see the ESSID of your WLAN, you can enter it in the iwconfig command:
```
iwconfig wlan0 essid "YourESSID"
```

These 3 commands will allow you to bring down, bring up & obtain an IP address from the command line:
```
sudo ifdown wlan0
sudo ifup wlan0
sudo dhclient wlan0
```

This command will restart the networking services:
```
sudo /etc/init.d/networking restart
```

-Dave

---

### Post by hamil on 2005-10-14
Hello sirs,

Thank you for the respones. I have done all those diffrent commands, and this is the results I get:

sudo iwlist scan gives, amongst other results, this result:
```

wlan0     Scan completed :
          Cell 02 - Address: 00:0F:3D:DF:EB:89
                    ESSID:"Etasje 3"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 6)
                    Quality=39/100  Signal level=15/100  Noise level=0/100
                    Encryption key:on
                    Bit Rate:54 Mb/s

```
Which is the network I am supposed to connect to. (And which I gave the ESSID, and key to during the installlation process.)

sudo iwgetid, gives no respone at all in the terminal.

sudo iwevent, gives this output:
```

Waiting for Wireless Events from interfaces...
06:40:24.463747   wlan0    New Access Point/Cell address:00:00:00:00:00:00

```
sudo ifconfig has this output:
```

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1538 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1538 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:134881 (131.7 KiB)  TX bytes:134881 (131.7 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:0F:B5:80:B6:D9
          inet6 addr: fe80::20f:b5ff:fe80:b6d9/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0xe000

```

When i ran the sudo ifdown wlan0 command, I got an errormessage? It outputed like this:
```

There is already a pid file /var/run/dhclient.wlan0.pid with pid 9168
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:0f:b5:80:b6:d9
Sending on   LPF/wlan0/00:0f:b5:80:b6:d9
Sending on   Socket/fallback

```

While the command sudo ifup wlan0 has this output:
```

There is already a pid file /var/run/dhclient.wlan0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:0f:b5:80:b6:d9
Sending on   LPF/wlan0/00:0f:b5:80:b6:d9
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

I also tried to manually configure with the commands:
sudo iwconfig wlan0 ESSID "Etasje 3"
sudo iwconfig wlan0 key open nnnnnnnnnn
sudo iwconfig up
sudo /etc/init.d/networking restart
But none of the above got me any closer to get online...

Hope that this could could help me further?

Brgds 
Lasse

---

### Post by hamil on 2005-10-14
Hmmm...
Seems like this is the wrong fora to post in... I did a repost of this in the correct fora. 
Is it possible for an admin to lock, or remove this?

Thnx in advance
Lasse

---

