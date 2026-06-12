---
title: "Need help with VPN connect"
date: 2006-09-10
forum: Desktop Environments
---

### Post by kkting on 2006-09-10
Hi, 

I have done quite a bit of searching here and on google trying to get VPN to work on my ubuntu box I installed a few days ago.

Basically I tried both Cisco VPN client 4.8 and VPNC from apt-get. I can get the cisco VPN client compiled with no problem (running i686 version of latest kernel from apt-get). I can also connect to my company's vpn server and proceed beyond authentication. Same goes with vpnc.

However, I can't get any traffic at all after the vpn connection. Resolve.conf is updated by vpn client (cisco or vpnc) to use company's dns server. The only thing I can access are external websites like google using it's ip address. I can't ping any computers in the vpn network.

I have no firewall running. Sorry for the long post, your help is much appreciated ](*,) 

Thanks!!

kkting

---

### Post by tuxinvader on 2006-09-10
Are you sure it's not the firewall at the other end causing you problems? Alternatively it could be nat causing you problems. 
Try adding enableNAT=1 to your vpn profile.

---

### Post by kkting on 2006-09-10
Thanks for the reply. enableNAT is on by default in my profile, I tried toggling this but it makes no difference.

What do you mean by firewall on the other end? You mean server end? I can connect to the vpn using clients on windows and mac os x (on same local network as my ubuntu box). So that should rule out problems of router or server end configurations.

Any more ideas?  :-k 

kkting

---

### Post by NetworkGuy on 2006-09-10
> However, I can't get any traffic at all after the vpn connection. Resolve.conf is updated by vpn client (cisco or vpnc) to use company's dns server. The only thing I can access are external websites like google using it's ip address. I can't ping any computers in the vpn network.

After you are connected to the VPN, do a ifconfig.  You should see (I think) ppp0 (using vpnc) with an IP address given to you by the VPN concentrator on the other end.   If you don't have that, you aren't fully connected.   

If you do have that, using a terminal, try performing traceroutes instead of pings.  It should tell you where the connection is failing at.  Try tracerouting your DNS server and see if it is resolving over the VPN or the Internet.

---

### Post by tuxinvader on 2006-09-10
you can also try: vpnclient stat route
to view the routing info for the vpn client or just "vpnclient stat" to see all info. 
If you still can't figure it out try changeing enableLog to 1 in /etc/opt/cisco-vpnclient/vpnclient.ini and you can increasae the log level. Log levels go all the way up to 15.

---

### Post by kkting on 2006-09-10
Thanks for the suggestions:

Here's my ifconfig output after connecting the vpn using cisco client:

cipsec0   Link encap:Ethernet  HWaddr 00:0B:FC:F8:01:8F
          inet addr:10.50.0.90  Mask:255.255.255.0
          inet6 addr: fe80::20b:fcff:fef8:18f/64 Scope:Link
          UP RUNNING NOARP  MTU:1356  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 **dropped:24** overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:12:3F:7D:F0:38
          inet addr:192.168.2.102  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:fe7d:f038/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:255 errors:0 dropped:0 overruns:0 frame:0
          TX packets:325 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:106008 (103.5 KiB)  TX bytes:45980 (44.9 KiB)
          Base address:0xcce0 Memory:ef7e0000-ef800000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:65947 (64.4 KiB)  TX bytes:65947 (64.4 KiB)
The number of dropped packets on cipsec0 interface seems to related to the problem....

I tried tracepath <company dns server> and the only error I get is:

tracepath <server>
 1:  send failed
     Resume: pmtu 65535

I also enabled logging in the vpnlcient, but all I see in the logs are the kept alive messages:

24     14:54:48.002  09/10/2006  Sev=Info/6     IKE/0x43000055
Sent a keepalive on the IPSec SA

25     14:54:58.006  09/10/2006  Sev=Info/6     IKE/0x43000055
Sent a keepalive on the IPSec SA


Thanks

kkting

---

### Post by kkting on 2006-09-10
Here's the route table (pretty long):
my local gateway is 192.168.2.1


```


Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
66.63.144.74    10.50.16.127    255.255.255.255 UGH   0      0        0 cipsec0
199.74.247.2    10.50.16.127    255.255.255.255 UGH   0      0        0 cipsec0
192.35.156.162  192.168.2.1     255.255.255.255 UGH   0      0        0 eth0
216.52.36.10    10.50.16.127    255.255.255.255 UGH   0      0        0 cipsec0
213.212.68.144  10.50.16.127    255.255.255.255 UGH   0      0        0 cipsec0
128.18.246.2    10.50.16.127    255.255.255.255 UGH   0      0        0 cipsec0
216.52.36.6     10.50.16.127    255.255.255.255 UGH   0      0        0 cipsec0
140.98.193.112  10.50.16.127    255.255.255.255 UGH   0      0        0 cipsec0
216.52.36.1     10.50.16.127    255.255.255.255 UGH   0      0        0 cipsec0
198.160.78.20   10.50.16.127    255.255.255.255 UGH   0      0        0 cipsec0
199.222.69.55   10.50.16.127    255.255.255.255 UGH   0      0        0 cipsec0
199.222.69.54   10.50.16.127    255.255.255.255 UGH   0      0        0 cipsec0
200.196.67.8    10.50.16.127    255.255.255.248 UG    0      0        0 cipsec0
62.160.241.32   10.50.16.127    255.255.255.224 UG    0      0        0 cipsec0
203.117.168.160 10.50.16.127    255.255.255.224 UG    0      0        0 cipsec0
194.87.160.64   10.50.16.127    255.255.255.192 UG    0      0        0 cipsec0
63.162.134.128  10.50.16.127    255.255.255.192 UG    0      0        0 cipsec0
199.106.104.0   10.50.16.127    255.255.255.192 UG    0      0        0 cipsec0
63.100.176.128  10.50.16.127    255.255.255.128 UG    0      0        0 cipsec0
211.45.17.0     10.50.16.127    255.255.255.128 UG    0      0        0 cipsec0
65.169.144.0    10.50.16.127    255.255.255.0   UG    0      0        0 cipsec0
203.30.171.0    10.50.16.127    255.255.255.0   UG    0      0        0 cipsec0
216.52.37.0     10.50.16.127    255.255.255.0   UG    0      0        0 cipsec0
199.106.111.0   10.50.16.127    255.255.255.0   UG    0      0        0 cipsec0
199.106.126.0   10.50.16.127    255.255.255.0   UG    0      0        0 cipsec0
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
199.106.124.0   10.50.16.127    255.255.255.0   UG    0      0        0 cipsec0
210.124.30.0    10.50.16.127    255.255.255.0   UG    0      0        0 cipsec0
204.179.122.0   10.50.16.127    255.255.255.0   UG    0      0        0 cipsec0
10.50.16.0      0.0.0.0         255.255.255.0   U     0      0        0 cipsec0
205.241.40.0    10.50.16.127    255.255.255.0   UG    0      0        0 cipsec0
199.106.102.0   10.50.16.127    255.255.255.0   UG    0      0        0 cipsec0
199.106.114.0   10.50.16.127    255.255.254.0   UG    0      0        0 cipsec0
199.106.96.0    10.50.16.127    255.255.252.0   UG    0      0        0 cipsec0
129.46.0.0      10.50.16.127    255.255.0.0     UG    0      0        0 cipsec0
10.45.0.0       10.50.16.127    255.255.0.0     UG    0      0        0 cipsec0
10.44.0.0       10.50.16.127    255.255.0.0     UG    0      0        0 cipsec0
10.46.0.0       10.50.16.127    255.254.0.0     UG    0      0        0 cipsec0
172.16.0.0      10.50.16.127    255.240.0.0     UG    0      0        0 cipsec0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
```

---

### Post by kkting on 2006-09-10
Hi 

I finally got it working ... using vpnc ](*,)  all I need to do is  do an apt-get upgrade on vpnc and reboot.

Although I still have no luck with the cisco client --- but screw proprietary solutions ... :mrgreen: 

btw, here's a good tool to decode encrypted vpn group passwords: (used in vpn profiles):
[URL="http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode"]
http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode[/URL]

Thanks a lot for your time !!

kkting

---

