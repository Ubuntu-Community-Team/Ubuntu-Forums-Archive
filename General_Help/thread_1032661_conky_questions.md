---
title: "conky questions"
date: 2009-01-06
forum: General Help
---

### Post by Wylkar on 2009-01-06
I was wondering what a wifi connection is called in conky, I know that the Ethernet ports are just eth0, eth1 etc. but I tried wifi0 and conky showed 0 kb/s up and down when connected to a wifi network. I was also wondering which 'if' statement I should use when referring to an Ethernet/Wifi connection.
Thanks.

---

### Post by my_key on 2009-01-06
Type "iwconfig" or "ifconfig" in a terminal. This will show you the device's name and some other info.

---

### Post by Wylkar on 2009-01-06
Ok, I did that but all it shows is the ethernet ports and something called 'lo'. here is the what I got in case it is at all helpful:
eth0      Link encap:Ethernet  HWaddr 00:1e:68:78:4d:8d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:21:00:28:cd:49  
          inet addr:10.0.1.200  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:ff:fe28:cd49/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:426 errors:0 dropped:0 overruns:0 frame:104
          TX packets:444 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:418011 (418.0 KB)  TX bytes:81612 (81.6 KB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2200 (2.2 KB)  TX bytes:2200 (2.2 KB)

---

### Post by mtbsoft on 2009-01-06
Try *wlan0* - works on my box.

---

### Post by jordanmthomas on 2009-01-06
Looks like yours is eth1, as it's up and has had data transferred over it.
My wireless is eth1 as well, so don't think it has to be wifi0 or wlan0

---

### Post by Wylkar on 2009-01-06
Yeah it is eth1, thanks jordanmthomas. I was also wonding which if statement to use  in order to prevent things that require internet use from showing when offline.

---

### Post by jordanmthomas on 2009-01-06
> **Wylkar said:**
> Yeah it is eth1, thanks jordanmthomas. I was also wonding which if statement to use  in order to prevent things that require internet use from showing when offline.

[http://bbs.archlinux.org/viewtopic.php?id=60529](http://bbs.archlinux.org/viewtopic.php?id=60529)
Does this help?

---

### Post by Wylkar on 2009-01-06
Not really, because the if_up suggested there applies to both eth0 and eth1.

---

### Post by mtbsoft on 2009-01-07
dup.

---

### Post by mtbsoft on 2009-01-07
I use a set of python scripts to gather state information for wifi, wired and no connectivity.  You might be able to adapt these...

eth0.py - indicates if eth0 is active
```
import commands

eth0 = commands.getoutput("ifconfig eth0")
#wlan0 = commands.getoutput("ifconfig wlan0")

index = eth0.find("inet addr:")
#duplicate = wlan0.find("inet addr:")

if index < 0:
	print "not found"
#if index < 0 and duplicate < 0:
#	print "found"
#elif index >= 0:
#	print "found"
```

wlan0.py - indicates if wlan is active (change to eth1 in your case)
```
import commands

wlan0 = commands.getoutput("ifconfig wlan0")
#eth0 = commands.getoutput("ifconfig eth0")

index = wlan0.find("inet addr:")
#duplicate = eth0.find("inet addr.:")

if index < 0:
	print "not found"
#if index < 0 and duplicate < 0:
#	print "found"
#elif index >= 0:
#	print "found"
```

eth0_or_wlan0.py - indicates if either is active
```
import commands

eth0 = commands.getoutput("ifconfig eth0")
wlan0 = commands.getoutput("ifconfig wlan0")

ieth0 = eth0.find("inet addr:")
iwlan0 = wlan0.find("inet addr:")

if ieth0 < 0 and iwlan0 < 0:
	print "not found"
```

which can be used in conky as follows...
```
${if_empty ${exec python ~/Scripts/eth0.py}}[COLOR="Blue"]Ethernet[/COLOR][COLOR="Silver"] (${addr eth0}) ${color steel blue}${hr 2}${color #000000} 
Down: ${downspeed eth0}kB/s ${alignr} Up: ${upspeed eth0}kB/s
Total: ${totaldown eth0} ${alignr} Total: ${totalup eth0}${alignr}
${upspeedgraph eth0 20,145 333333 cccccc} ${alignr}${downspeedgraph eth0 20,145 333333 cccccc}[/COLOR] 
${else}${if_empty ${exec python ~/Scripts/wlan0.py}}[COLOR="Blue"]Wireless[/COLOR][COLOR="Silver"] (${addr wlan0}) ${color steel blue}${hr 2}${color #000000}
Down: ${downspeed wlan0}kB/s ${alignr} Up: ${upspeed wlan0}kB/s
Total: ${totaldown wlan0} ${alignr} Total: ${totalup wlan0}${alignr}
${upspeedgraph wlan0 20,145 333333 cccccc} ${alignr}${downspeedgraph wlan0 20,145 333333 cccccc}[/COLOR] 
${endif}${endif}${if_empty ${exec python ~/Scripts/eth0_or_wlan0.py}}[COLOR="Blue"]Connections[/COLOR][COLOR="Silver"] ${color steel blue}${hr 2}${color #000000}
Inbound: ${tcp_portmon 1 32767 count}${alignc}        ALL: ${tcp_portmon 1 65535 count}${alignr}Outbound: ${tcp_portmon 32768 61000 count}
 Inbound ${color steel blue}${hr 2}${color #000000}${alignr} Local Service/Port
 ${tcp_portmon 1 32767 rhost 0} ${alignr} ${tcp_portmon 1 32767 lservice 0}
 ${tcp_portmon 1 32767 rhost 1} ${alignr} ${tcp_portmon 1 32767 lservice 1}
 ${tcp_portmon 1 32767 rhost 2} ${alignr} ${tcp_portmon 1 32767 lservice 2}
 ${tcp_portmon 1 32767 rhost 3} ${alignr} ${tcp_portmon 1 32767 lservice 3}
 Outbound ${color steel blue}${hr 2}${color #000000}${alignr} Remote Service/Port
 ${tcp_portmon 32768 61000 rhost 0} ${alignr} ${tcp_portmon 32768 61000 rservice 0}
 ${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice 1}
 ${tcp_portmon 32768 61000 rhost 2} ${alignr} ${tcp_portmon 32768 61000 rservice 2}
 ${tcp_portmon 32768 61000 rhost 3} ${alignr} ${tcp_portmon 32768 61000 rservice 3}
 ${tcp_portmon 32768 61000 rhost 4} ${alignr} ${tcp_portmon 32768 61000 rservice 4}
 ${tcp_portmon 32768 61000 rhost 5} ${alignr} ${tcp_portmon 32768 61000 rservice 5}
 ${tcp_portmon 32768 61000 rhost 6} ${alignr} ${tcp_portmon 32768 61000 rservice 6}
 ${tcp_portmon 32768 61000 rhost 7} ${alignr} ${tcp_portmon 32768 61000 rservice 7}
 ${tcp_portmon 32768 61000 rhost 8} ${alignr} ${tcp_portmon 32768 61000 rservice 8}
 ${tcp_portmon 32768 61000 rhost 9} ${alignr} ${tcp_portmon 32768 61000 rservice 9}
 ${tcp_portmon 32768 61000 rhost 10} ${alignr} ${tcp_portmon 32768 61000 rservice 10}[/COLOR]
${else}
[COLOR="Blue"]No Network Connectivity[/COLOR][COLOR="Silver"] ${color steel blue}${hr 2}${color #000000}[/COLOR]
${endif}
```
Which shows the ip and traffic info for the relevant connection (wired taking precidence over wireless) then the connections, or a simple "No Network Connectivity" if no connections are found.

Works well for me, hope you can use it.

---

### Post by Wylkar on 2009-01-08
Thanks for the scripts mtbsoft, they will probably solve my problem allthough it will be a while before I have the time to incorperate them.

---

