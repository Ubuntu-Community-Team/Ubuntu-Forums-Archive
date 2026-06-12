---
title: "Network not working!"
date: 2006-06-15
forum: Desktop Environments
---

### Post by cope on 2006-06-15
Hey Guys, 
I just installed a fresh copy of 6.06 from breezy,and since doing so have lost all my network connections.. i am receiving an ip address from the DHCP off the router, but i can't ping the router... I think the IP address is being assigned to the machine on startup, because once i get into the gui i can't contact the router again. 

i've tried resetting the pc, the adapter, all the broadcast/subnets are correct. its a hardwire connection straight to the router, and the router light is on so its powered.. (obviouslly) 

does anyone have any ideas?

---

### Post by costoa on 2006-06-15
Please post the dump from ifconfig please.

---

### Post by cope on 2006-06-15
Below is the ifconfig, also, interestly, if i release the ip address and try re-assign, it doesn't re-assign...
i'm guessing its a software problem.. i wish i wasn't such a newbie at this

eth0      Link encap:Ethernet  HWaddr 00:08:A1:05:9F:7E  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::208:a1ff:fe05:9f7e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:18 dropped:0 overruns:0 frame:0
          TX packets:11 errors:6 dropped:0 overruns:0 carrier:6
          collisions:0 txqueuelen:1000 
          RX bytes:2225 (2.1 KiB)  TX bytes:870 (870.0 b)
          Interrupt:217 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

---

### Post by cope on 2006-06-15
can anyone help?
my server doesn't have a working network connection...

---

### Post by costoa on 2006-06-15
Sorry, please also please /etc/network/interfaces.

---

### Post by cope on 2006-06-15
i reinstalled, and i get the same problem.. the live cd internet works throughout the install, but when i first boot up i'll start terminal and ping 192.168.0.1 (the router) and it works for about 30seconds, and then stops working...

and /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth1
iface eth1 inet dhcp

iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by costoa on 2006-06-15
[QUOTE=cope]i reinstalled, and i get the same problem.. the live cd works throughout the install, but when i first boot up i'll start terminal and ping 192.168.0.1 (the router) and it works for about 30seconds, and then stops working...

and /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth1
iface eth1 inet dhcp

iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp[/QUOTE]


The starting and stop part is weird. Let's take the dhcp server out of the mix by assigning a static ip.

```
auto eth0
iface eth0 inet static
address 192.168.0.50
netmask 255.255.255.0
gateway 192.168.0.1

```

I'm playing spin'n win with the numbers but you get the idea. Once that's in then

```
sudo ifdown eth0
sudo ifup eth0

```

Start by pinging lo (127.0.0.1) to see if the stacks are up. Then eth0 (192.168.0.50) to see if that's up. If that works then hit the router.

Again, the up and down thing is weird. Give the cable and plugs the once over and look for anything weird. Are the link lights always solid?

---

### Post by cope on 2006-06-15
thanks, i've done what you suggested, i get a reply from the loopback and the .50 but not he router itself..
 
i'm on a windows machine thats right next door and its working fine..

correct me if i'm wrong.. but if i ping .50 won't that go from my pc to the router then back to my pc?

its 100% not physical, i've changed ports on the router and swapped the cable with the working winXP cable. crazy stuff, should i be looking at PCBSD? or do you think this is fixable?

---

### Post by costoa on 2006-06-15
"correct me if i'm wrong.. but if i ping .50 won't that go from my pc to the router then back to my pc?"

Pinging .50 is just local. It will work the same if a cable is plugged in or not.

My first guess now is a bad NIC (since you tested the cables). I think the Ubuntu stuff is correct. Can you beg/borrow/steal another ethernat card? Also when you ping the router does the traffic light on the card come on? What about on the router end?

(added)
The "working for 30 seconds" is strange. It's not a problem one normally sees with a configuration issue. If you have a nonUbuntu live cd I suspect you'll get the same results as the Ubuntu live cd.

---

### Post by cope on 2006-06-15
i just changed network cards, and the same thing is happening..
uhmm..
i'll put XP on it, and see if its doing the same thing. So much for a productive day in the web development hut...

---

### Post by costoa on 2006-06-16
[QUOTE=cope]i just changed network cards, and the same thing is happening..
uhmm..
i'll put XP on it, and see if its doing the same thing. So much for a productive day in the web development hut...[/QUOTE]

This is an odd problem. (Using the numbers from before) if you can ping .50 w/o failure I feel confident in saying the Ubuntu end is configured correctly. Setup for an ethernet card is normally a simple thing

One last thing, fire up "cat /var/log/syslog | grep eth" and if you see something like  "eth0: link up, 100Mbps, full-duplex, lpa 0xxxxx" or "link down"

You could hop on IRC (irc.freenode.net - #ubuntu), point them to this exchange and ask what they think. It's quite possible they'll know what's up.

---

### Post by cope on 2006-06-16
no worries, i'll give it a go on friday when i'm back at work, xp works fine on that pc, so i'm sure its something to do with ubuntu 6.06 (as ealier versions worked fine) 

I'll let you know how i go.

---

### Post by helpdeskdan on 2006-06-16
Actually, the ping will not go to the router to reach .50  .  You could disconnect your router and it wouldn't care!  The .50 is on your local subnet.  Your machine will take the address, put it through the subnet mask, and say, "Hey, this is a local address.  We don't send this to the router, we send it direct."  It will then look in it's arp table for the mac address.  (If the address isn't there, it sends out an arp request, but we'll not ramble on too long)  

Now, something from your output here alarms me:

RX packets:12 errors:18 dropped:0 overruns:0 frame:0
TX packets:11 errors:6 dropped:0 overruns:0 carrier:6

You're getting errors galore here.  You claim that it works fine under XP, so, by process of elimination I am thinking driver problem.  You've also got carrier errors which, as I remember, means that the card is not seeing the echo of the information it is sending out. 

Have you run mii-diag?  Half the frames are generating errors and that sounds like a classic duplex mismatch as I remember.  It's worth looking into at least.

What card is it?  Can you borrow a good card from somebody?  (IE - intel or something)  Is it plugged into a hub or switch?

The only other thing I can think of that would be strange would be a router configuration problem.  If the router had a strange subnet mask, it would recieve the ping just fine, but say "this ain't for me, I'm not going to respond."

---

### Post by cope on 2006-06-22
costoa, 

mii
```

Using the default interface 'eth0'.
SIOCGMIIPHY on eth0 failed: Operation not supported

```

cat syslog | grep eth0 gave me no results. 

helpdeskdan, i'm thinking drivers as well, but why does eth work 100% on live cd, but install dies?


and the card is a dec ethernet

---

### Post by cope on 2006-06-23
anyone?

---

### Post by cope on 2006-06-29
bump.. can anyone help?

---

### Post by X3n0n on 2006-07-01
I have EXACTLY the same problem! The network works just fine with live cd and dies after the first boot! I go now to check everything you suggested and tell if it will work....

---

### Post by X3n0n on 2006-07-01
There is only one difference with cope: I connect directly to the windows xp machine which has a usb adsl modem on it with ICS


Here are the outputs of the commands you sugested:


**cat /var/log/syslog | grep eth**  :

```
Jul  1 16:49:13 localhost kernel: [4295234.205000] eth0: no IPv6 routers present
Jul  1 16:50:57 localhost kernel: [4295338.164000] eth0: no IPv6 routers present
Jul  1 16:53:11 localhost dhclient: Listening on LPF/eth0/00:08:a1:90:d5:51
Jul  1 16:53:11 localhost dhclient: Sending on   LPF/eth0/00:08:a1:90:d5:51
Jul  1 16:53:15 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port  67 interval 3
Jul  1 16:53:18 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port  67 interval 4
Jul  1 16:53:21 localhost kernel: [4295482.172000] eth0: no IPv6 routers present
Jul  1 16:53:22 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port  67 interval 11
Jul  1 16:53:33 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port  67 interval 10
Jul  1 16:53:43 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port  67 interval 18
Jul  1 16:54:01 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port  67 interval 15
Jul  1 16:54:36 localhost dhclient: Listening on LPF/eth0/00:08:a1:90:d5:51
Jul  1 16:54:36 localhost dhclient: Sending on   LPF/eth0/00:08:a1:90:d5:51
Jul  1 16:54:40 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port  67 interval 7
Jul  1 16:54:47 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port  67 interval 10
Jul  1 16:54:48 localhost dhclient: Listening on LPF/eth0/00:08:a1:90:d5:51
Jul  1 16:54:48 localhost dhclient: Sending on   LPF/eth0/00:08:a1:90:d5:51
Jul  1 16:54:49 localhost dhclient: receive_packet failed on eth0: Network is do wn
Jul  1 16:54:49 localhost dhclient: receive_packet failed on eth0: Network is do wn
Jul  1 16:54:57 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port  67 interval 11
Jul  1 16:55:08 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port  67 interval 10
Jul  1 16:55:18 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port  67 interval 11
Jul  1 16:55:29 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port  67 interval 8
Jul  1 16:55:37 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port  67 interval 4
Jul  1 16:55:53 localhost dhclient: Listening on LPF/eth0/00:08:a1:90:d5:51
Jul  1 16:55:54 localhost dhclient: Sending on   LPF/eth0/00:08:a1:90:d5:51
Jul  1 16:55:59 localhost dhclient: Listening on LPF/eth0/00:08:a1:90:d5:51
Jul  1 16:55:59 localhost dhclient: Sending on   LPF/eth0/00:08:a1:90:d5:51
Jul  1 16:56:02 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port  67 interval 5
Jul  1 16:56:07 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port  67 interval 8
Jul  1 16:56:09 localhost kernel: [4295650.055000] eth0: no IPv6 routers present
Jul  1 16:56:15 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port  67 interval 12
Jul  1 16:56:27 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port  67 interval 14
Jul  1 16:56:41 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port  67 interval 16
Jul  1 16:56:57 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port  67 interval 6
Jul  1 16:57:16 localhost dhclient: Listening on LPF/eth0/00:08:a1:90:d5:51
Jul  1 16:57:16 localhost dhclient: Sending on   LPF/eth0/00:08:a1:90:d5:51
Jul  1 16:57:16 localhost dhclient: receive_packet failed on eth0: Network is do wn
Jul  1 16:57:19 localhost dhclient: Listening on LPF/eth0/00:08:a1:90:d5:51
Jul  1 16:57:19 localhost dhclient: Sending on   LPF/eth0/00:08:a1:90:d5:51
Jul  1 16:57:23 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port  67 interval 8
Jul  1 16:57:29 localhost kernel: [4295730.225000] eth0: no IPv6 routers present
Jul  1 16:57:31 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port  67 interval 20
Jul  1 16:57:51 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port  67 interval 20
Jul  1 16:58:11 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port  67 interval 13
Jul  1 16:59:10 localhost dhclient: receive_packet failed on eth0: Network is do wn
Jul  1 16:59:10 localhost dhclient: receive_packet failed on eth0: Network is do wn
Jul  1 16:59:12 localhost dhclient: Listening on LPF/eth0/00:08:a1:90:d5:51
Jul  1 16:59:12 localhost dhclient: Sending on   LPF/eth0/00:08:a1:90:d5:51
Jul  1 16:59:12 localhost dhclient: receive_packet failed on eth0: Network is do wn
Jul  1 16:59:21 localhost dhclient: receive_packet failed on eth0: Network is do wn
Jul  1 16:59:27 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port  67 interval 5
Jul  1 16:59:32 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port  67 interval 13
Jul  1 16:59:45 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port  67 interval 13
Jul  1 16:59:47 localhost kernel: [4295868.350000] eth0: no IPv6 routers present
Jul  1 16:59:58 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port  67 interval 20
Jul  1 17:00:18 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port  67 interval 10
Jul  1 17:00:19 localhost dhclient: receive_packet failed on eth0: Network is do wn
Jul  1 17:00:32 localhost kernel: [4295913.643000] eth0: no IPv6 routers present
```


**ifconfig**  :

```
eth0      Link encap:Ethernet  HWaddr 00:08:A1:90:D5:51
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::208:a1ff:fe90:d551/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:2358 (2.3 KiB)
          Interrupt:209 Base address:0xd800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:331 errors:0 dropped:0 overruns:0 frame:0
          TX packets:331 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:17146 (16.7 KiB)  TX bytes:17146 (16.7 KiB)
```


**/etc/network/interfaces**  :

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```


**mii-tool**  :

```
eth0: negotiated 100baseTx-FD, link ok
```






PLEASE help me!




Sorry for the huge post :(

---

### Post by Phosphoric on 2006-07-01
Seems like loads of people have this problem,  LIve CD workd fine, installed OS dies.  I've been trying to resolve this for a couple of weeks now, trying all sorts of things in other threads, all to no avail.

It can't be hardware as I'm using the same kit to communicate here via Windows XP.

It must be the drivers that are loaded in the OS install.  Why can't it use the same ones as in Live CD?

Close to giving up now. :(

---

### Post by X3n0n on 2006-07-01
I gave up until I saw this post....but again no solution....Can't anyone figure out what is happening and tell ubuntu people to correct it :( :(

---

### Post by X3n0n on 2006-07-02
Does anyone has a network like this intalled on his pc in ubuntu WORKING? I need info...I google too much these days but no solution :cry: :cry: :cry:

---

### Post by FujiMan on 2006-07-02
Hey all,

I'm still having problems with network. Full install from CD and I got updates when I was connected to the router connected with CAT5. I then moved the box to the basement, where I have wireless bridge. No connection what so ever. No DHCP or static ip setup works. The routing table is BLANK. The networking part of Ubuntu is absolutely _WEAK_.  If I take an Wintel or Mac box downstairs, I get connected immediately. There are no config tools for network interfaces. Some clown keeps posting to disable IPv6, but gives no links or clues on how to PROPERLY do this (if it needs to be done at all!?!)

Fujiman

---

### Post by cyberdyne on 2006-07-02
I seem to be having a similar problem.
I have Ubuntu 6.06 connected to a router by lan and a laptop using winxp connected to the router wirelessly.
I do not get a response from .50. Should i be?
I noticed when i first installed ubuntu 2 days ago that both this and my laptop showed in 'network' but now, nothing, yet I haven't changed anything.

Any help appreciated - please note im a newbie, so be gentle, lol.
Thank you.

---

### Post by scollyp on 2006-07-04
I'm having exactly the same problem.  I've disabled IPv6, configured a static address, and so on, but I can't ping my router (in this case, an Actiontec gt701-wg).

Dual-boot to Windows XP, and everything works great.

Scott

---

### Post by hotice3100 on 2006-07-10
I had internet problems when I installed 6.06.  I'm not sure if this is what you are trying to track down or just some networking problem, but i followed the instructions in the link below and it worked.

[http://www.ubuntuforums.org/showthread.php?t=186430]("http://www.ubuntuforums.org/showthread.php?t=186430")

---

### Post by cope on 2006-07-20
something really strange..

i installed breezy and then updated to dapper and bingo it works..

---

