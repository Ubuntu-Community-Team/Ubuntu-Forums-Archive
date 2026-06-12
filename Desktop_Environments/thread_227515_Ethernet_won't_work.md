---
title: "Ethernet won't work"
date: 2006-08-01
forum: Desktop Environments
---

### Post by Josty on 2006-08-01
Hello everyone,

I'm quite new to any other OS then Windows (shame on me). Now as I wanted to learn more about OS systems that I installed UBUNTU 6.06. Well the installing proceeded very fine but now I've run into a problem which I can't solve.

The problem is that I can't get on the internet. 

If I use the DHCP from my modem/router (which is a speedtouch alcatel) then I wont get a connection. 

If I try to get a connection with a static Ip with the settings:
Ip: 10.0.0.201
subnetmask: 255.255.255.0
network: 10.0.0.0
broadcast: 10.0.0.255
gateway: 10.0.0.138
I still can't get a connection.

After some talking and reading I found out that ifconfig and iwconfig could tell me some more. (Had two network cards in it, 1 ethernet card, and a wireless card.)
Output ifconfig:

eth0   Link encap:Ethernet HWaddr 00:10:DC:4c:88:70
         inet addr:10.0.0.201 Bcasr:20.0.0.225 Mask:255.255.255.0
         inet6 addr:fe80::210:dcff:f34c:8b70/64 Scope:link
        UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
        RX packets:59 errors:233 dropped:0 overruns:0 carrier:0
        collisions:o txqueuelen:1000
        RX bytes:5549 (5.4 KiB)  TX bytes: 18205  (17.7 KiB)

lo    Link encap:Local Loopback
      inet addr:127.0.0.1  Mask:255.0.0.0
      inet6 addr: ::1/128 Scope:Host
      UP LOOPBACK RUNNING MRU:16436 Metric:1
      RX packets: 16 errors:0 dropped:0 Overruns:0 frame:0
      TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
     collissions :o txqueuelen:0
     RX bytes:2541 (2.4 KiB)  TX bytes:2531 (2.4 KiB)

The following is the output of iwconfig:
Lo         no wireless extentions.

eth0     No wireless extensions.

ath0    IEEE 802.11 ESSID:"  "
          Mode: Managed Frequency 2.412 Ghz Access Point: Not - associated
         Bit Rate: okb/s  Tx-power: 20 dBm  Sensitivity=0/3
         Retry: off TRS thr:off    Fragment thr:off
         Power Management:off
         Link Quality=0/94 Signal level= - 95 dBm Noise level = - 95 dBm
         RX invalid nwid:o Rx invalid crypt:o Rx invalid frag:o
         TX excenssive retries:o    Invalid misc:o   Missend beacon:o

sit0   No wireless extensions.


Therefor I continued with this information and tried to get a connection with the command: "sudo dhclient eth0" with the following output:
Internet System Consortium DHCP Client v3.0.3
Copyright 2004-2005 internet Systems Consortium.
All right reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:10:dc:4c:8b:70
Sending on  LPF/eth0/00:10:dc:4c:8b:70
Sending on  Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS recieved.
No working leases in persistent database - sleeping.

Well still no connection so thats quite bad. The persons who were trying to help me wanted to have more info about my ethernetcard. The ethernetcard info is from the command: "lspci|grep Ethernet".
0000:03:03.0 Ethernet controller: Atheros Commu nications, Inc. : Unknown device 00la (rev 01)
0000:03:08.0 Ethernet controller: intel Corporations 82801DB PRO/100 VE (CNR) ethernet Coltroller (Rev 81)

As we see there are two cards in it. They told me this could be the reason why it weren't working. After that I have taken out the wireless card (via hardware).

After that the asked me to try this commando:"sudo mii-diag eth0" and that gave the following output:
Basic registers of MII PHY #l:  3100 782d 02a8 0330 05e1 41e1 0003 0000.
The autonegotiated capability is 01e0
The autonegotiated media type is 100baseTx-FD.
Basic mode control register 0x3100: auto-negotiation enabled.
You have link beat, and everything is working OK.
Your link partnet advertised 41e1: 100baseTX-FD     100baseTx     10baseT - FD   10 baseT.
End of basic transceiver infromation.

Which had to be good, atleast that is what the told me. This was because of the line:" You have link beat, and everything is working OK."



Well this is as far as I came before I opent a new thread on this forum. Hope any of you could help my out and make me get a conntion with Ubuntu.

Thanks in advance,
Joost

---

### Post by neoeden on 2006-08-01
This might be a stupid question, but under windows are you using DHCP or static IP to get your network address? Is there a router between the machine  and the cable modem?

---

### Post by Josty on 2006-08-01
When I'm using windows it working with the DHCP without any problems.

Technical the right way to name it, it is a 'GATEWAY'. Although the name it a Modem and it's working more like a Router. Choosing between or a Modem or a Router will end up in: Router.

And yes, there is a DHCP server running on it.

---

