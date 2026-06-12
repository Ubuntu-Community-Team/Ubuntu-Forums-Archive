---
title: "x3270 not connecting to IBM mainframe host."
date: 2008-12-13
forum: General Help
---

### Post by ProgramErgoSum on 2008-12-13
Hi all,
I am having a tough time connecting to IBM mainframe host from my Ubuntu Intrepid. I think, the issue is with VPNC though. I just want to understand *where* the problem might lie.

At home, I use vpnc to get to customer network, where the Unix machine is accessed easily. It is the mainframe on the customer network that I am unable to connect to. However, my colleagues are able to connect and work easily from their Windows machines.

A trace when connecting from x3270 results in following :```

Trace started Fri Dec 12 23:15:38 2008
 Version: x3270 v3.3.7p3 Thu May 22 07:52:49 UTC 2008 buildd
 Command: x3270 -geometry +549+113 -trace
 Model 3279-4-E, color display, extended data stream, color emulation, bracket c
harset
 Data stream:
Connection pending.
Connected to nnn.nnn.nnn.nnn, port 23.
< 0x0   fffd28
RCVD DO TN3270E
> 0x0   fffb28
SENT WILL TN3270E
Now operating in TN3270E mode.
< 0x0   fffa280802fff0
RCVD SB TN3270E SEND DEVICE-TYPE SE
> 0x0   fffa28020749424d2d333237382d342d45fff0
SENT SB TN3270E DEVICE-TYPE REQUEST IBM-3278-4-E SE
< 0x0   fffa28020449424d2d333237382d342d45015443505444433635fff0
RCVD SB TN3270E DEVICE-TYPE IS IBM-3278-4-E CONNECT TCPTDC65 SE
> 0x0   fffa280307000204fff0
SENT SB TN3270E FUNCTIONS REQUEST BIND-IMAGE RESPONSES SYSREQ SE
< 0x0   fffa280304000204fff0
RCVD SB TN3270E FUNCTIONS IS BIND-IMAGE RESPONSES SYSREQ SE
TN3270E option negotiation complete.
RCVD socket error 104
SENT disconnect
```

When connecting through VPN, there are options available for IPSec/UDP and IPSec/TCP etc. As of now, my configuration file does not have anything set, which means it takes the default. The default probably being cisco-udp.

Would you think setting some values for --natt-mode might help ? I did try with other values. (I referred these [man pages for x3270]("http://manpages.ubuntu.com/manpages/hardy/man8/vpnc.html").) But, it didn't work.

Therefore, as you can see, I am not sure, where the problem would be (I am guessing the first one might be the reason) :
[LIST]
[*]vpnc connection
[*]x3270 s/w
[*]Ubuntu installation
[*]My broadband connection
[*]??
[/LIST]

---

### Post by ProgramErgoSum on 2009-01-07
Guess what...? 

When I am connected thru" PCMCIA card, everything works perfectly ! The problem that I mention above happens when I was connected thru" WiMax connection. 

I am still not convinced that this could be entirely due to the gateway provided by the connection provider. This is because, I had a friend come over to my place and she connected to the WiMax connection, do vpnc and then connect to mainframe easily. Difference ? She is on Windows XP.

So, honestly, I don't know if this thread requires to be marked as 'SOLVED'.

---

