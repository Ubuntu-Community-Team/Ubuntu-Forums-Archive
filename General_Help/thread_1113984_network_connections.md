---
title: "network connections"
date: 2009-04-02
forum: General Help
---

### Post by lo2lo2a on 2009-04-02
[CENTER]

hi

i am new to Linux system and i am using ubuntu 

i have problem the connection is there but the net is not opening any pages 

i think it is something about proxy because when i try to enter the irc server for ubuntu he banned me and sad 

my english is not good and it is my first using the forum so please help me "127.0.0.1 (Banned"

maybe there is no connection between the irc issue and the net problem and i hope it is an easy problem 

i will search for solutions until you answer me 

and if there is a way to communicate whit some one in an online chat that will be more help 

thank you 


[/CENTER]

---

### Post by jigsaws on 2009-04-02
First of all check if you firefox is in off-line mode.
Then you can try to ping any server (ie. ping [www.wp.pl](www.wp.pl)).

---

### Post by lo2lo2a on 2009-04-02
[CENTER]

ok i will see that 

by the way how can i ping any server 

just remember it is my first time to ubuntu and Linux system


thank you 
[/CENTER]

---

### Post by lo2lo2a on 2009-04-02
[CENTER]OK i have checked that and i am not offline  

by the way when i use terminal prog and try to setup my ethernet he told me that there isnot any 

and i am using winxp in the same partion and i am using the net with no problem 

[/CENTER]

---

### Post by jigsaws on 2009-04-02
Run terminal, type "ping www.wp.pl", press <Enter> key
:-)

---

### Post by lo2lo2a on 2009-04-02
[CENTER]OK thank you

i will try that command 

by the way i downloaded some books about ubuntu and i also want some articles about it with picture explaining the system do you know any ???

 [/CENTER]

---

### Post by lo2lo2a on 2009-04-06
[CENTER]ok i did the ping command 

and it gave me this 


network is unreachable 

any idea what this mean 

thank you 
[/CENTER]

---

### Post by oobe-feisty on 2009-04-06
it means either your network connection is broken possible a dns issue or that address is down just try ping google.com its never down


EDIT: opon reading more of this thread i think you need to set your nameservers you need to know your ISP's namservers or use your access point gateway as a nameserer when you find out the correct  info add it into /etc/resolv.conf

e.g # this assumes you are connected to the net using a router with the ip of 192.168.0.1



sudo nano /etc/resolv.conf


namserver 192.168.0.1

#or you can use the nameservers provided by you isp should be found on there support page

---

### Post by lo2lo2a on 2009-04-06
[CENTER]

i dodnot know how to do what you said 


i will give you more info 



abdullah@abullah-desktop:~$ sudo netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.2.0     *               255.255.255.0   U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0

------------------------------
abdullah@abullah-desktop:~$ ip route show all
192.168.2.0/24 dev eth0  proto kernel  scope link  src 192.168.2.51  metric 1 
169.254.0.0/16 dev eth0  scope link  metric 1000 
---------------------------------
abdullah@abullah-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:92:92:09  
          inet addr:192.168.2.51  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:fe92:9209/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:170 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:18792 (18.7 KB)  TX bytes:5604 (5.6 KB)
          Memory:fdfc0000-fdfe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:378 errors:0 dropped:0 overruns:0 frame:0
          TX packets:378 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:26632 (26.6 KB)  TX bytes:26632 (26.6 KB)
-----------------------------------
abdullah@abullah-desktop:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

----------------------------------

sudo nan /etc/resolv.conf

nameserver 192.168.2.1
nameserver 208.67.222.222
nameserver 208.67.220.220

---------------------------
abdullah@abullah-desktop:~$ ping [www.google.com](www.google.com)
connect: Network is unreachable
abdullah@abullah-desktop:~$ ping 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.021 ms
------------------------------






hope this could help 

by the way what does that mean " ISP's namservers"

thank you for your help 


[/CENTER]

---

### Post by oobe-feisty on 2009-04-06
ok all that info looks ok so im a little puzzled as a last ditch effort you can try using wicd 


[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)


for this to work you need to uninstall network-manager 

sudo apt-get remove network-manager network-manager-gnome


then open wicd and try configuring your network that way i do not use wicd so i cannot guide you further with this i suggest it due to other people's success rate it seems to work better than the default network-manager. i configure my network in a way that will be to confusing to explain 


the wicd website contains full instructions on how to get it going


good luck

---

### Post by lo2lo2a on 2009-04-06
[CENTER]ok 

thank you for your help 

[/CENTER]

---

