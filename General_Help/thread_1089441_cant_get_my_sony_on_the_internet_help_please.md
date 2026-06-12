---
title: "cant get my sony on the internet help please"
date: 2009-03-07
forum: General Help
---

### Post by brit1 on 2009-03-07
Sony vaio PCG-7X1M Laptop
Windows Vista
Ubuntu 8.10

I've installed Ubuntu from within windows to give it a try and hopefully make it a permanent transition, I wont moan on here but I just can't put up with vista and the (Not Responding comment)any more.

I can connect to my wireless network and also via Ethernet cable, the sony receives a ip address from the network, but nothing I do will allow me to see a web page.

Iwconfig read out

lo        no wireless extensions
eth0      no wireless extensions.
wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"*************"  Nickname:""

          Mode:Managed  Frequency:2.437 GHz  Access Point: **:**:**:**:**:**   

          Bit Rate:48 Mb/s   Tx-Power:15 dBm   Sensitivity=1/1  

          Retry:off   RTS thr:off   Fragment thr:off

          Power Management:off

          Link Quality=31/70  Signal level=-65 dBm  Noise level=-96 dBm

          Rx invalid nwid:1184  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

Any help would be appreciated.

TIA

Brit1

---

### Post by brit1 on 2009-03-07
update 1

here is the ifconfig data if that helps.


ath0      Link encap:Ethernet  HWaddr 00:19:7d:f5:7c:e9   
          UP BROADCAST RUNNING MULTICAST  MTU:64  Metric:1 
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:1240 (1.2 KB)  TX bytes:1823 (1.8 KB) 
 
eth0      Link encap:Ethernet  HWaddr 00:13:a9:50:13:3a   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:16 
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:15408 (15.4 KB)  TX bytes:15408 (15.4 KB) 
 
wifi0     Link encap:UNSPEC  HWaddr 00-19-7D-F5-7C-E9-00-00-00-00-00-00-00-00-00-00   
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:1813 errors:0 dropped:0 overruns:0 frame:565 
          TX packets:158 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:199 
          RX bytes:195128 (195.1 KB)  TX bytes:9819 (9.8 KB) 
          Interrupt:18 

really stuck now, I've just used fedora live cd and that worked with no problems ! 

please help

---

### Post by miegiel on 2009-03-07
Just a heads up :)

Try getting your wired connection to work 1st, there are just less things that can go with a wire.

Your ifconfig isn't showing an ip address, maybe the cable wasn't connected when you ran the command?

here's mine as an example:

```
:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:30:1b:b4:0a:68  
          inet addr:10.1.1.5  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::230:1bff:feb4:a68/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9468 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7992 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11108501 (10.5 MB)  TX bytes:1323527 (1.2 MB)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1502 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1502 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:75100 (73.3 KB)  TX bytes:75100 (73.3 KB)
```

---

### Post by brit1 on 2009-03-08
Miegiel thank you for your reply.

I have now tried both the wired connection as you suggested and its the same.

When I go to the icon in the top right of the screen it shows me as connected and it shows that the pc has managed to acquire an IP address, but if I go to the terminal and type in ifconfig I get the above returned.

Regards

Brit

---

### Post by miegiel on 2009-03-08
> **brit1 said:**
> the pc has managed to acquire an IP address, but if I go to the terminal and type in ifconfig I get the above returned.

That can't be right, If your wired network card has an ip address the eth0 section (wifi0 section for your wireless I assume) should have a line like this> inet addr:10.1.1.5  Bcast:10.255.255.255  Mask:255.0.0.0, but with differen adress numbers of course ;)

---

### Post by brit1 on 2009-03-08
ok not 100% sure what I'm doing but here is an update

ath0      Link encap:Ethernet  HWaddr 00:19:7d:f5:7c:e9  
          UP BROADCAST RUNNING MULTICAST  MTU:64  Metric:1 
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:3535 (3.5 KB)  TX bytes:2219 (2.2 KB) 

eth0      Link encap:Ethernet  HWaddr 00:13:a9:50:13:3a  
          UP BROADCAST RUNNING MULTICAST  MTU:64  Metric:1 
          RX packets:12 errors:0 dropped:2 overruns:0 frame:2 
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:1612 (1.6 KB)  TX bytes:1819 (1.8 KB) 
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:258 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:258 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:16144 (16.1 KB)  TX bytes:16144 (16.1 KB) 

wifi0     Link encap:UNSPEC  HWaddr 00-19-7D-F5-7C-E9-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:5022 errors:0 dropped:0 overruns:0 frame:420 
          TX packets:200 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:199 
          RX bytes:540991 (540.9 KB)  TX bytes:12263 (12.2 KB) 
          Interrupt:18 

steve@ubuntu:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

wifi0     no wireless extensions. 

ath0      IEEE 802.11g  ESSID:"Ravensthorpe.net"  Nickname:"" 
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:17:DD:AB:0B   
          Bit Rate:24 Mb/s   Tx-Power:15 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality=30/70  Signal level=-64 dBm  Noise level=-94 dBm 
          Rx invalid nwid:3250  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

pan0      no wireless extensions. 

GUI display from the top right icon

Active Network Connections
Interface eth0
hardware address:
Driver: sky2
speed: 100Mb/s
security None

IP Address 10.0.0.9
Broadcast: 10.255.255.255
Subnet Mask: 255.0.0.0
Default Route: 10.0.0.2
Primary DNS 10.0.0.1

Active Network Connections
Interface 802.11 Wifi (ath0)
hardware address:
Driver: ath_pci
speed: 48Mb/s
security None

IP Address 10.0.0.13
Broadcast: 10.255.255.255
Subnet Mask: 255.0.0.0
Default Route: 10.0.0.2
Primary DNS 10.0.0.1

---

### Post by miegiel on 2009-03-08
Ok, your ifconfig output is still confusing me (for lack of ip addresses)

It looks like you wired network card is using ip 10.0.0.9 and your wireless network card (ath0 and not wifi0, what i thought earlier) is using 10.0.0.13.

"Default Route: 10.0.0.2" refers to the ip number of the machine that is connecting your home network to the internet. 

Here's some stuff for you to verify:
[LIST=1][*]Is 10.0.0.2 really the address of the machine connecting your network to the internet?[*]Do you have a network connection to the machine that connects your network to the internet?[*]Check in windows what ip numbers you get for both your cards (it's a dual boot windows/linux right?)[*]Check what ip addresses (including subnet masks and default route/gateway) the other machines on your network are using[/LIST]

1) Take a look at the network settings of that machine (dsl-modem/router, pc that functions as a gateway, whatever you use).

2) Use the ping command in a terminal (or dos window in windows). Ping is the most simple network program there is, if you have a connection you get a pong back, if there's no connection you get an error or timeout warning.```
ping 10.0.0.2
```The command in windows and ubuntu/linux is the same. Though in windows it does 4 pings and then stops, in ubuntu it keeps running till you hit Ctrl+C. To keep it going in windows use```
ping 10.0.0.2 -t (or was it /t)
```More examples```
ping localhost (ping yourself)
ping ping.xs4all.nl (pings a machine on the internet of the dutch ISP xs4all)
```

3) In windows the ifconfig command is called ipconfig, use ```
ipconfig /all
``` to display more info. But you can also click your way to the TCP/IP settings in the gui, though the ip addresses might not be displayed if they are resolved automatically.

4) In general the first 3 numbers in an ip address are the network numbers, so all the machines on your network should start with 10.0.0. The last number is a unique number for each network card, so you don't want 2 cards (even in the same machine) that both are using the same number from start to finish.

---

### Post by brit1 on 2009-03-08
This is the wifi setup info from vista I cant connect the Ethernet at the moment as my son has it connected to his xbox lol.
 
Connection-specific DNS Suffix: 
Description: [CommView] LAN-Express AS IEEE 802.11g PCI-E Adapter
Physical Address: 00-19-7D-F5-7C-E9
DHCP Enabled: Yes
IPv4 IP Address: 10.0.0.13
IPv4 Subnet Mask: 255.0.0.0
Lease Obtained: 08 March 2009 20:46:31
Lease Expires: 09 March 2009 20:46:30
IPv4 Default Gateway: 10.0.0.2
IPv4 DHCP Server: 10.0.0.2
IPv4 DNS Server: 10.0.0.2
IPv4 WINS Server: 
NetBIOS over Tcpip Enabled: Yes
Link-local IPv6 Address: fe80::7d10:feb0:ecd8:39cb%8
IPv6 Default Gateway: 
IPv6 DNS Server:

and here is the ipconfig/all


C:\Users\Steve>ipconfig/all

Windows IP Configuration

   Host Name . . . . . . . . . . . . : hello
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Mixed
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No

Wireless LAN adapter Wireless Network Connection:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : [CommView] LAN-Express AS IEEE 802.11g PC
I-E Adapter
   Physical Address. . . . . . . . . : 00-19-7D-F5-7C-E9
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::7d10:feb0:ecd8:39cb%8(Preferred)
   IPv4 Address. . . . . . . . . . . : 10.0.0.13(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.0.0.0
   Lease Obtained. . . . . . . . . . : 08 March 2009 20:46:31
   Lease Expires . . . . . . . . . . : 09 March 2009 20:46:30
   Default Gateway . . . . . . . . . : 10.0.0.2
   DHCP Server . . . . . . . . . . . : 10.0.0.2
   DNS Servers . . . . . . . . . . . : 10.0.0.2
   NetBIOS over Tcpip. . . . . . . . : Enabled

Ethernet adapter Local Area Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Marvell Yukon 88E8036 PCI-E Fast Ethernet
 Controller
   Physical Address. . . . . . . . . : 00-13-A9-50-13-3A
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Local Area Connection*:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 02-00-54-55-4E-01
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Local Area Connection* 8:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : isatap.{FFFDFECE-5E7A-465F-8226-5BD677096
586}
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Local Area Connection* 10:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : isatap.{FFFDFECE-5E7A-465F-8226-5BD677096
586}
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Local Area Connection* 19:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : isatap.{7298B06E-2FC3-43E9-9C45-3C8C95E5B
D04}
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Local Area Connection* 25:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : isatap.{7298B06E-2FC3-43E9-9C45-3C8C95E5B
D04}
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

10.0.0.2 is my modems IP which is also my DHCP server

C:\Users\Steve>

hope this helps, and again thanks for your help

---

### Post by brit1 on 2009-03-12
hey guys I'm still stuck with this can anyone help please

---

### Post by miegiel on 2009-03-12
I think I might have spotted it, the address for the dns is probably wrong.

From a few posts up :
> **brit1 said:**
> 
IP Address 10.0.0.9
Broadcast: 10.255.255.255
Subnet Mask: 255.0.0.0
Default Route: 10.0.0.2
**Primary DNS 10.0.0.1**

Active Network Connections
Interface 802.11 Wifi (ath0)
hardware address:
Driver: ath_pci
speed: 48Mb/s
security None

IP Address 10.0.0.13
Broadcast: 10.255.255.255
Subnet Mask: 255.0.0.0
Default Route: 10.0.0.2
**Primary DNS 10.0.0.1**

If this doesn't solve it I'd still like to see your ifconfig output when you're connected to the modem with ethernet. Your network is just the laptop xbox and modem, right? And did you try testing the connection to your modem and/or the internet with ping (see post #7 above)?

---

