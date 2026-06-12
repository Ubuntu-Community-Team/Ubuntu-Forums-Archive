---
title: "Really weird network problem after installing Breezy"
date: 2005-10-15
forum: Desktop Environments
---

### Post by mog27 on 2005-10-15
I have a Linksys WRT wireless router.  I just clean installed Breezy.  I set up a static IP address, subnet mask, default gateway, the two DNS servers.  Everything is right.  I also set up the correct WEP key and SSID.  I also verified this in the /etc/network/interfaces files.  Everything looks perfect.  My wireless card even makes a connection.  I can verify that on the Linksys router that there is a connection.  However, I cannot ping the default gateway (the router at 192.168.1.1); I get destination host unavilable.  Same thing happens if I ping my Windows machine (at 192.168.1.5).  I am able to ping localhost successfuly.  I cannot imagine what the problem is.  When I had Hoary I had absolutely no problems connecting; it in fact configured my card during setup (unlike Breezy, but for Breezy I did it myself manually).  Also, when I do an ifconfig I am seeing a lot of errors receiving (RX packets) but just like 2 errors sending (TX packets).  I am really at a lost.  The only thing I did was change the default WEP transmission key on the router from the first to the second - but that should not matter at all, as long as the WEP key matches on my laptop (which it does; I get a connection, just can't get out).

---

### Post by MikeyXX on 2005-10-15
Try pinging the routers ip address. See if you get to it. If you do, then it's probably a dns issue.

---

### Post by mog27 on 2005-10-15
[QUOTE=MikeyXX]Try pinging the routers ip address. See if you get to it. If you do, then it's probably a dns issue.[/QUOTE]

I have. That is my default gateway.  It can't be a DNS issue.  If it was a DNS issue, I would still be able to ping my default gateway by IP address.

---

### Post by drogoh on 2005-10-15
Your problem sounds like a routing issue.  Do you have a default route set up for your interface since you are using static IPs and not DHCP?  Check your routing table with netstat -rn and look at the default route.

---

### Post by mog27 on 2005-10-15
[QUOTE=drogoh]Your problem sounds like a routing issue.  Do you have a default route set up for your interface since you are using static IPs and not DHCP?  Check your routing table with netstat -rn and look at the default route.[/QUOTE]

After making my post, this popped into my head.  Yeah I checked that and it looks fine (I think).  Here is the output (leaving out the last 3 unimportant columns):

Destination              Gateway                    Genmask
192.168.1.0              0.0.0.0                     255.255.255.0
0.0.0.0                     192.168.1.1               0.0.0.0

That look ok?  Does the 192.168.1.0 supposed to have the 192.168.1.1 as the gateway?  I tried doing:
sudo route add default gw 192.168.1.1 
but I get "SIOCADDRT: File exists"

---

### Post by Zwack on 2005-10-16
[QUOTE=mog27]After making my post, this popped into my head.  Yeah I checked that and it looks fine (I think).  Here is the output (leaving out the last 3 unimportant columns):

Destination              Gateway                    Genmask
192.168.1.0              0.0.0.0                     255.255.255.0
0.0.0.0                     192.168.1.1               0.0.0.0

That look ok?  Does the 192.168.1.0 supposed to have the 192.168.1.1 as the gateway?  I tried doing:
sudo route add default gw 192.168.1.1 
but I get "SIOCADDRT: File exists"[/QUOTE]

The above is correct...

This says to get to 192.168.1.0/24 there is a direct connection.  To get to anything else use the gateway at 192.168.1.1...

FYI here is my working set up...
$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.254.0   0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         192.168.254.254 0.0.0.0         UG        0 0          0 eth0


Z.

---

### Post by mog27 on 2005-10-16
[QUOTE=Zwack]The above is correct...

This says to get to 192.168.1.0/24 there is a direct connection.  To get to anything else use the gateway at 192.168.1.1...

FYI here is my working set up...
$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.254.0   0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         192.168.254.254 0.0.0.0         UG        0 0          0 eth0


Z.[/QUOTE]

Ok then this makes absolutely no sense.  I've like eliminated everything.  My routing table is fine.   Maybe my network card or router suddenly went bad somehow?  I highly doubt it.  Very very unlikely. But I can't think of anything else causing it.

---

### Post by mog27 on 2005-10-16
I got it working by switching my default WEP key on my Linksys WRT54G to key number 1 like I had before on Ubuntu Hoary.  It then worked.   This ABSOLUTELY makes no sense to me.  Does anyone have a rational explanation as to why I had these problems when I switched the default key on my Linksys to use key number 2 rather than key 1?  Perhaps some weird bug on the latest Linksys firmware?

---

