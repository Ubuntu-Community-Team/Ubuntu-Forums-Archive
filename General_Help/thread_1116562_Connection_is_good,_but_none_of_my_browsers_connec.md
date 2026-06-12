---
title: "Connection is good, but none of my browsers connect to any sites."
date: 2009-04-05
forum: General Help
---

### Post by ddixonr on 2009-04-05
I lost power to my laptop in the last hour and when I rebooted, Firefox won't pull up any sites. I have a connection because I restarted some torrents and they continued downloading. I opened a couple other programs that access the internet like skype and it connected no problem. I tried Konqueror and IE6 as well and they are in the same state as firefox. 

I vnc'd to another machine on my network and it connects to the internet and every site I tried. I don't have any complicated proxy setups or anything, so I'm really stumped. Please help.

Edit: "Work Offline" is not checked. I am getting the "Address Not Found" error.

---

### Post by pbpersson on 2009-04-05
go to the command line, type the following, and see what you get:

```
nslookup www.google.com
```

---

### Post by ddixonr on 2009-04-05
Server:		127.0.0.1
Address:	127.0.0.1#53

** server can't find [www.google.com.hsd1.in.comcast.net:](www.google.com.hsd1.in.comcast.net:) REFUSED

---

### Post by pbpersson on 2009-04-05
show me the output of this command:

```
ifconfig
```

---

### Post by ddixonr on 2009-04-05
```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:a0:d1:50:13:fe  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2157 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2157 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:151597 (151.5 KB)  TX bytes:151597 (151.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:de:06:4c:26  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:723965 errors:0 dropped:0 overruns:0 frame:0
          TX packets:738047 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:580729533 (580.7 MB)  TX bytes:468437372 (468.4 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-DE-06-4C-26-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

I just got it working. I tried 'init.d/networking restart' = nothing. I tried 'ifconfig wlan0 down/up' = nothing. Then I right clicked the nm applet and disabled networking, then brought it back up. Worked after that. Weird.

---

