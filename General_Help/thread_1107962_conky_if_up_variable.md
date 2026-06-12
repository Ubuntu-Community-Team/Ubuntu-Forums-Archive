---
title: "conky if_up variable"
date: 2009-03-27
forum: General Help
---

### Post by ViMMeD on 2009-03-27
I have a block in my .conkyrc for my network details (wired and wireless), eth0 and eth1 respectively.  I have IP/down/up for eth0 and IP/signal strength/down/up for eth1.  This is the section of my .conkyrc:

```
IP ${alignr}${execi 3600 wget -O - http://whatismyip.org/ | tail}
${if_up eth1}Local IP ${alignr}${addr eth1}
Signal Strength ${alignr}${wireless_link_qual_perc eth1}%
${wireless_link_bar 4 eth1}
Down ${downspeed eth1} k/s ${alignr}Up ${upspeed eth1} k/s
${downspeedgraph eth1 25,107 cccccc ffffff} ${alignr}${upspeedgraph eth1 25,107 cccccc ffffff}
Total ${totaldown eth1} ${alignr}Total ${totalup eth1}${else}Local IP ${alignr}${addr eth0}
Down ${downspeed eth0} k/s ${alignr}Up ${upspeed eth0} k/s
${downspeedgraph eth0 25,107 cccccc ffffff} ${alignr}${upspeedgraph eth0 25,107 cccccc ffffff}
Total ${totaldown eth0} ${alignr}Total ${totalup eth0}${endif}
```

When I first boot the computer on eth0 (defaulted) the signal strength and local IP variables display as if they were reading eth1 values, even though eth1 isn't connected.  So it gives NO ADDRESS and UNK% for IP and signal strength.  It's displaying eth1 values even when it's not up, defying ${if_up}.

The only way i can get around this is if I connect to eth1 (it then displays the proper output) then reconnect to eth0 (it reads the proper values for eth0).  The only problem is on the boot it displays the wrong interface info.  Any way around this?  I don't mind even having to use a script to switch between connections on boot.  Thanks, ifconfig if anyone needs them:

```
eth0      Link encap:Ethernet  HWaddr 00:16:36:15:5e:3f  
          inet addr:192.168.0.141  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe15:5e3f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6362 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5995 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5651690 (5.6 MB)  TX bytes:866949 (866.9 KB)
          Interrupt:16 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:13:ce:cd:9f:f9  
          inet6 addr: fe80::213:ceff:fecd:9ff9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:432 (432.0 B)
          Interrupt:17 Base address:0x8000 Memory:b0101000-b0101fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:165 errors:0 dropped:0 overruns:0 frame:0
          TX packets:165 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16675 (16.6 KB)  TX bytes:16675 (16.6 KB)
```

---

### Post by sagara on 2011-01-22
ViMMeD, the ${if_up interface} variable in conky does not work as expected.  As you can see from your results.  A workaround for this problem is discussed on this [thread]("http://ubuntuforums.org/showthread.php?t=644463") [[ubuntuforums.org]](ubuntuforums.org]).

---

