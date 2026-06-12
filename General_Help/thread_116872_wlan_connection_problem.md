---
title: "wlan connection problem"
date: 2006-01-13
forum: General Help
---

### Post by gimliy on 2006-01-13
Hi there.

I'm pretty new to Ubunutu/Linux, so please go easy on me.

The situation:

Laptop A (WinXP, wlan, eth)
Laptop B (Ubuntu, wlan vivanco usb 11mbit, eth)

We have a wired connection on Ubuntu and would like it to share this connection via wlan for the other Laptop. 
So far i have eth configured correctly and a working link for the 2 wlan adapters thus i cannot ping A to B and vice versa (wireless). Looks like i made a mistake for the tcp/ip settings on A->wlan and B->wlan but i don't know what it could be..

A
192.168.0.2 # 255.255.255.0 # 192.168.0.1


B
192.168.0.1 # 255.255.255.0 # 192.168.0.1

Besides that i have absolutely no idea how to enable Ubuntu to route the wlan-connection to eth0 either ^^

Any ideas?

Michael

---

### Post by Mr_Grieves on 2006-01-13
I guess

> 
A
192.168.0.2 # 255.255.255.0 # 192.168.0.1


B
192.168.0.1 # 255.255.255.0 # 192.168.0.1


Means IP-address # Netmask # Default gateway

Do you have both W-LAN and Wired connection between between both computers? Could you please make up a schemetic over how things are connected.

If so.. B side need to have 192.168.0.2 as default gateway.

---

### Post by gimliy on 2006-01-13
hmm.. except having some problems with 2 default gateways now it seems as nothing changed so far. no ping/http-connect, nothing.

but the windows-machine is still able to get information about the wireless network..

### EDIT ###

allright i'll try to explain. my english is a mess, so this is gonna be interesting :)

My Ubuntu Laptop has a wired connection to a LAN which gives me internet connectivity and I want to share this connectivity with a second Laptop(WindowsXP) via WLAN. The ethernet LAN is working fine and i don't need to touch that, but what robs me my sleep is the wireless connection. I have an excellent signal, I use ad-hoc mode and for testing reasons no encryption so far. But i can't get TCP/IP to work on this signal.

I must admit that i have never dealt with WLAN before.. 

I hope you can help me out

---

### Post by gimliy on 2006-01-14
Problem Update.

I played around a little bit with iwlist, iwconfig and tcpdump. The results are:

I still have a working Link between both WLAN adapters.

I dumped requests from my Windows-machine. At first only ARP-request since it was looking for its router, then i entered a static line in the windows' arp-table resulting in tcpdumping tcp-requests from my windows machine via WLAN. 

So far so good.. the problem is my USB dongle (Ubuntu machine) refuses to do the same thing. I cannot get a single packet OUT of my WLAN adapter.

Could this be a routing/interface problem or something? I'm pretty stuck right now.. help appreciated.

---

### Post by BathroomNinja on 2006-01-14
What settings are you using for each?  Go into SYSTEM > ADMINISTRATION > NETWORKING, click on your wireless card, then look at it's properties and settings.  let me know what you have for each card in all of the tabs.  If you can take a screenshot and attach it to your message, that would be great.

---

### Post by gimliy on 2006-01-14
here they come:
 (hope this works)

---

### Post by BathroomNinja on 2006-01-14
I will try to set this up on my network tommorow to attempt to recreate your problem.

---

### Post by BathroomNinja on 2006-01-15
I was able to get mine setup with no problems. I'm not really sure where you are going wrong..

---

### Post by gimliy on 2006-01-18
after a lot of asking around in the ubuntu-channels on irc i still haven't figured out what's the problem here. i will post a list of output that might be useful to understand the issue.
i hope someone can help me...


Machine A                                                                                                                                 
WinXP          
192.168.0.2 
  
via   ad-hoc wlan to


Machine B
Ubuntu 5.10
192.168.0.1



## ifconfig wlan0

wlan0     Protokoll:Ethernet  Hardware Adresse 00:40:F4:AA:F3:E0
          inet Adresse:192.168.0.1  Bcast:192.168.0.255  Maske:255.255.255.0
          inet6 Adresse: fe80::240:f4ff:feaa:f3e0/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST  MTU:1500  Metric:1
          RX packets:331 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:22042 (21.5 KiB)  TX bytes:0 (0.0 b)

## iwconfig wlan0

wlan0     IEEE 802.11-DS  ESSID:"interfaces"  Nickname:"ubuntu"
          Mode:Ad-Hoc  Frequency:2.457 GHz  Cell: 02:00:B5:DC:A7:44
          Bit Rate:11 Mb/s   Tx-Power=15 dBm
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B
          Power Management:off
          [COLOR="Red"]Link Quality=0/0[/COLOR]  Signal level=122/255  Noise level=0/0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

## iwlist wlan0 scan

wlan0     Scan completed :
          Cell 01 - Address: 02:00:B5:DC:A7:44
                    ESSID:"interfaces"
                    Mode:Ad-Hoc
                    Channel:10
                    Encryption key:off
                    [COLOR="Red"]Quality:0/0[/COLOR]  Signal level:56/255  Noise level:0/0
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s

## lsusb

Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 03eb:7613 Atmel Corp.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

## ping 192.168.0.2


PING 192.168.0.2 (192.168.0.2) 56(84) bytes of data.

--- 192.168.0.2 ping statistics ---
8 packets transmitted, 0 received, 100% packet loss, time 6998ms


## route -n


Kernel IP Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
0.0.0.0         192.168.0.2     0.0.0.0         UG    0      0        0 wlan0


## sudo tcpdump -i wlan0

tcpdump: listening on wlan0, link-type EN10MB (Ethernet), capture size 96 bytes
15:45:24.615189 arp who-has 192.168.0.1 tell 192.168.0.2
15:45:25.617021 arp who-has 192.168.0.1 tell 192.168.0.2
15:45:27.572694 arp who-has 192.168.0.1 tell 192.168.0.2
15:45:28.593523 arp who-has 192.168.0.1 tell 192.168.0.2
15:45:29.596370 arp who-has 192.168.0.1 tell 192.168.0.2
15:45:30.600185 arp who-has 192.168.0.1 tell 192.168.0.2
15:45:31.803987 arp who-has 192.168.0.1 tell 192.168.0.2
15:45:33.609687 arp who-has 192.168.0.1 tell 192.168.0.2
15:45:34.632517 arp who-has 192.168.0.1 tell 192.168.0.2
15:45:37.842980 arp who-has 192.168.0.1 tell 192.168.0.2
15:45:39.546698 arp who-has 192.168.0.1 tell 192.168.0.2
15:45:40.772493 arp who-has 192.168.0.1 tell 192.168.0.2
15:45:41.977293 arp who-has 192.168.0.1 tell 192.168.0.2
15:45:43.577024 arp who-has 192.168.0.1 tell 192.168.0.2
15:45:44.985793 arp who-has 192.168.0.1 tell 192.168.0.2
15:45:46.027615 arp who-has 192.168.0.1 tell 192.168.0.2
15:45:47.050446 arp who-has 192.168.0.1 tell 192.168.0.2
15:45:48.113269 arp who-has 192.168.0.1 tell 192.168.0.2
15:45:49.981956 arp who-has 192.168.0.1 tell 192.168.0.2
15:45:51.022786 arp who-has 192.168.0.1 tell 192.168.0.2
15:45:52.289572 arp who-has 192.168.0.1 tell 192.168.0.2

---

