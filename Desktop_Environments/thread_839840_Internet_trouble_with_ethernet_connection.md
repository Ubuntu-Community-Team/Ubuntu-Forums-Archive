---
title: "Internet trouble with ethernet connection"
date: 2008-06-24
forum: Desktop Environments
---

### Post by peeskey on 2008-06-24
I first installed 8.04 about 3 months ago and everything went fine including the internet connection.  I have moved and thus received a different modem from Time Warner (Toshiba PCX 2200)when they came to install internet.  The internet works fine on my laptop running Windows XP.  BUT, for my desktop, running Ubuntu 8.04, it does not work using Mozilla.  The ubuntu help section says that ethernet connections should be no problem.  I dont know if this modem is compatible with ubuntu or any linux but I would assume that it is.  Any help greatly appreciated.

---

### Post by pytheas22 on 2008-06-24
How are you plugged into the modem (ethernet cable or USB)?  And there's nothing between your computer and the modem, right?

Also, it could be a DNS issue.  What happens if you open Firefox and put just 64.233.167.99 in the address bar?

---

### Post by peeskey on 2008-06-25
thanks for response.  I am using ethernet cable and it goes straight to computer.  No routers or anything.  When typed into the address bar, it said that site seems valid but there is no connection.

---

### Post by John.Klockenkemper on 2008-06-25
We will need more information from you regarding your network configuration to diagnose your problem correctly.

If you could:

1. run ifconfig and paste the output here.

and

2. paste the contents of your /etc/network/interfaces 

Thanks,
John

---

### Post by peeskey on 2008-06-26
Here is the ifconfig:


eth0      Link encap:Ethernet  HWaddr 00:11:09:94:89:33  
          inet6 addr: fe80::211:9ff:fe94:8933/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:64388 errors:0 dropped:0 overruns:0 frame:0
          TX packets:773 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4178198 (3.9 MB)  TX bytes:59406 (58.0 KB)
          Interrupt:16 Base address:0xd400 

eth0:avahi Link encap:Ethernet  HWaddr 00:11:09:94:89:33  
          inet addr:169.254.5.3  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1671 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1671 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:108150 (105.6 KB)  TX bytes:108150 (105.6 KB)


Sorry, but i am not sure what you wanted in the step 2.

---

### Post by pytheas22 on 2008-06-26
I guess it's not DNS.

Please post the output of these things:
```

sudo dhclient eth0
cat /etc/network/interfaces
cat /etc/resolv.conf
```

It would also be helpful to find out where the packets are going.  Open a terminal and type:
```

sudo tcpdump -i eth0
```

and try visiting google.com in Firefox.  After you get the error message, go back to the terminal and press control-C to kill tcpdump.  Then please copy the output of tcpdump there.  This will tell us what's happening to the traffic as it tries to reach the Internet (it would be easier to do this with Wireshark, but that would be hard to install since you have no connection right now).

---

### Post by krodiak on 2008-06-26
If theres an DNS problem, ubuntu should recognize the new DNS servers, but apparently to me ur eth0 ip doesn't match any of LAN ips.

First:
```
cat /etc/resolv.conf
```

And paste it here

Then try using an static LAN IP
```

sudo cp /etc/network/interfaces /etc/network/interfaces.bak
sudo nano /etc/network/interfaces
```

Delete the line:
```

iface eth0 inet dhcp

```
Then use:
```

iface eth0 inet static
address your.lan.numbers.X
netmask 255.255.255.0
gateway your.default.gate.way

```

Usually gateway is the .254 ( not always ) of your LAN, using a lan 192.168.1.X ur gateway should be 192.168.1.254 ( your DSL modem ip )


Hope I helped u

---

### Post by peeskey on 2008-06-27
Here are the 4 commands that were requested in order.


adamo@Home:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:11:09:94:89:33
Sending on   LPF/eth0/00:11:09:94:89:33
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


adamo@Home:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback




iface eth0 inet dhcp

auto eth0

adamo@Home:~$ cat /etc/resolv.conf
search austin.rr.com
nameserver 24.93.41.127
nameserver 24.93.41.128

adamo@Home:~$ sudo tcpdump -i eth0
tcpdump: WARNING: eth0: no IPv4 address assigned
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
11:50:35.375685 arp who-has 70.112.4.58 tell 70.112.0.1
11:50:35.413023 arp who-has 63.246.169.61 tell 63.246.169.1
11:50:35.690600 arp who-has 70.112.77.24 tell 70.112.72.1
11:50:35.714812 arp who-has 70.112.72.55 tell 70.112.72.1

4 packets captured
5787 packets received by filter
5420 packets dropped by kernel

---

### Post by pytheas22 on 2008-06-27
I don't really see any place where the problem would lie, but I can think of a few more suggestions that may help.

1. after booting to Ubuntu, unplug your modem, wait a few seconds and plug it back in.

2. clean up /etc/network/interfaces.  Type in a terminal:

```

sudo gedit /etc/network/interfaces
```

and remove from that file everything *except* the lines:
```

auto lo
iface lo inet loopback
```

Then save the file.  The other stuff should not be necessary and may be causing some problem.

3. Clean up /etc/resolv.conf.  Type:
```

sudo gedit /etc/resolv.conf
```

and delete the first line, "search austin.rr.com"  I don't know what it means, but I've never seen a line like that before in that file.

4. It might also help to make sure that the DNS servers in /etc/resolv.conf are correct.  In Windows, open a command prompt and type:
```

ipconfig /all
```

Scroll down towards the end and you'll see a section about DNS servers.  Make sure that the IP addresses specified there are the same as the ones that Ubuntu is using, 24.93.41.127 and 24.93.41.128.

5. if your modem can be connected via USB as well as ethernet cable, did you try that to see if it would help (you may have to reboot the modem for the USB connection to kick in)?

I hope one of these things will help, as I'm really puzzled as to what's going wrong.  If these don't work, maybe you could try calling your ISP?  If your Internet used to work fine before you moved, then really the only variable that's changed is on the ISP's end, after all.

---

### Post by peeskey on 2008-06-27
Thank you to everyone who was assisting with my problem.

It has been resolved.  I feel silly at this point since the suggestion:

1.  After starting Ubuntu, turn off modem and plug back in.

was the one that worked.

Sorry to have wasted anyones time on this matter.

---

### Post by pytheas22 on 2008-06-27
> Thank you to everyone who was assisting with my problem.

It has been resolved. I feel silly at this point since the suggestion:

1. After starting Ubuntu, turn off modem and plug back in.

was the one that worked.

Sorry to have wasted anyones time on this matter.

It's alright; I actually don't know why I didn't think to suggest it sooner.  The reason I thought of it is I remembered that I had a modem from Roadrunner once that was very fickle--if you switched the machines plugged into it, the second one wouldn't get an IP address until you rebooted the modem.  I don't know why it was but I suspect that it has to do with Time Warner's trying to prevent you from connecting all of your computers easily (they told me I needed to have a separate line installed for each machine in the house...they probably get a lot of people that way who don't know that all they have to do is go buy a ten dollar switch or get wireless).

Anyway I'm glad you got it solved.

---

