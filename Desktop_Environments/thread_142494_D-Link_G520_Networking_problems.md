---
title: "D-Link G520 Networking problems"
date: 2006-03-10
forum: Desktop Environments
---

### Post by KaridaSerious on 2006-03-10
I've installed Ubuntu a while ago and everything else works fine but my wireless isn't working.I have tried to look around the forums but none of the instructions have worked for me :(. I've followed the instructions in [http://wiki.ubuntu.com/WPAHowto](http://wiki.ubuntu.com/WPAHowto) but no use. The wireless card interacts with the router correctly but the problem is that the card doesn't receive a IP address from DHCP. When I read my routers connection log there is a mark that says my computer had connected with wireless device. I use WPA encryption. When I link my computer with RJ45 it receives IP just right. Here's some output:

ifconfig ath0:
ath0    Link encap:Ethernet  HWaddr 00:11:95:91:6E:01
          inet6 addr: fe80::211:95ff:fe91:6e01/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:72 errors:413 dropped:0 overruns:0 frame:413
          TX packets:456 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:9488 (9.2 KiB)  TX bytes:138393 (135.1 KiB)
          Interrupt:16 Memory:f8d20000-f8d30000

iwconfig:
ath0    IEEE 802.11g  ESSID:"xxxxx"  Nickname:"xxxxxx"
          Mode:Managed  Frequency:2.437 GHz  
          Access Point: 00:13:46:AC:C5:FA
          Bit Rate:36 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=34/94  Signal level=-61 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sudo lspci:
0000:00:0c.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

sudo dhclient ath0:

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/ath0/00:11:95:91:6e:01
Sending on   LPF/ath0/00:11:95:91:6e:01
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

... can you help me :)

---

### Post by KaridaSerious on 2006-03-10
I unfortunately placed this thread in wrong part of this forum, I don't know how to delete this thread so can moderators delete this thread for me? I will make a new one in Networking section!

---

