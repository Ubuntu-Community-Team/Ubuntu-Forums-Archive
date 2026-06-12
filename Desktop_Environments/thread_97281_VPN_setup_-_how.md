---
title: "VPN setup - how?"
date: 2005-11-30
forum: Desktop Environments
---

### Post by pigulsky on 2005-11-30
Got a problem with my ISP and VPN.
The ISP doesn't know anything about Linux and especially about VPN setup in Linux. I have all needed preferences for VPN for Win platform but I really need some suggestions to set it up in Ubuntu.

I tried a lot of methods of setting it up, but pptp always gives me something like this:

Log of pptp working:
```
Nov 30 20:39:10 cpd-ubuntu pppd[32020]: pppd 2.4.3 started by root, uid 0
Nov 30 20:39:10 cpd-ubuntu pppd[32020]: Using interface ppp0
Nov 30 20:39:10 cpd-ubuntu pppd[32020]: Connect: ppp0 <--> /dev/pts/2
Nov 30 20:39:13 cpd-ubuntu pppd[32020]: MS-CHAP authentication failed: Invalid!
Nov 30 20:39:13 cpd-ubuntu pppd[32020]: Connection terminated.
Nov 30 20:39:13 cpd-ubuntu pppd[32020]: Exit.
```

or this (dump, according to pptpclient.sourceforge.net/howto-debian.phtml)
```
pppd options in effect:
debug           # (from command line)
nodetach                # (from command line)
logfd 2         # (from command line)
dump            # (from command line)
noauth          # (from /etc/ppp/options.pptp)
name unlim291           # (from /etc/ppp/peers/ZKVPN)
remotename PPTP         # (from /etc/ppp/peers/ZKVPN)
               # (from /etc/ppp/options.pptp)
pty pptp 172.16.253.254 --nolaunchpppd          # (from /etc/ppp/peers/ZKVPN)
crtscts         # (from /etc/ppp/options)
               # (from /etc/ppp/options)
asyncmap 0              # (from /etc/ppp/options)
lcp-echo-failure 4              # (from /etc/ppp/options)
lcp-echo-interval 30            # (from /etc/ppp/options)
hide-password           # (from /etc/ppp/options)
ipparam ZKVPN           # (from /etc/ppp/peers/ZKVPN)
proxyarp                # (from /etc/ppp/options)
nobsdcomp               # (from /etc/ppp/options.pptp)
nodeflate               # (from /etc/ppp/options.pptp)
noipx           # (from /etc/ppp/options)
using channel 10
Using interface ppp1
Connect: ppp1 <--> /dev/pts/2
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x3e465324> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x3e465324> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x3e465324> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x1 <accomp> <pcomp> <asyncmap 0x0> <mru 1500> <magic 0xd7a25d0d> <auth chap MS-v2>]
sent [LCP ConfAck id=0x1 <accomp> <pcomp> <asyncmap 0x0> <mru 1500> <magic 0xd7a25d0d> <auth chap MS-v2>]
sent [LCP EchoReq id=0x0 magic=0x3e465324]
rcvd [CHAP Challenge id=0x1 <6a569792f73fd1f697ea6d1c1de06b94>, name = ""]
sent [CHAP Response id=0x1 & #60;d624755c32f174a0377ed85e30f98d344300000000d20000b26215b1dc571cf4080438c3310f
fcfc602f39e22d2f360bb7>, name = "unlim291"]
rcvd [LCP EchoRep id=0x0 magic=0xd7a25d0d]
rcvd [CHAP Failure id=0x1 "E=691 R=0 C=6A569792F73FD1F697EA6D1C1DE06B94 V=3 M=Invalid!\000"]
MS-CHAP authentication failed: Invalid!
sent [LCP TermReq id=0x2 "Failed to authenticate ourselves to peer"]
rcvd [LCP TermReq id=0x2]
sent [LCP TermAck id=0x2]
rcvd [LCP TermAck id=0x2]
Connection terminated.
Waiting for 1 child processes...
 script pptp 172.16.253.254 --nolaunchpppd, pid 8490
sending SIGTERM to process 8490
```

Both password and login are correct, though it still shows ***MS-CHAP authentication failed: Invalid!***

---

### Post by HermanAB on 2005-11-30
PPTP???  It is not secure, so I would not bother with that one...

However, the module to use for PPTP is called poptop or some such - some Googling will find you info on it.

The easiest way to VPN in Linux is with SSH:
[http://www.aerospacesoftware.com/samba-ssh-tunnel-howto.htm](http://www.aerospacesoftware.com/samba-ssh-tunnel-howto.htm)

Cheers,

Herman

---

### Post by pigulsky on 2005-11-30
Well, actually the problem is not with ssh or pptp but with authorization.

It seems to me that the password I specified couldn't be transferred to the server because I got a message like:
**can't find any secret (password) to auth. **

But! The password is in the /etc/ppp/chap-secrets file!!! How can it be?

---

### Post by cwaldbieser on 2005-11-30
[QUOTE=HermanAB]PPTP???  It is not secure, so I would not bother with that one...

However, the module to use for PPTP is called poptop or some such - some Googling will find you info on it.

The easiest way to VPN in Linux is with SSH:
[http://www.aerospacesoftware.com/samba-ssh-tunnel-howto.htm](http://www.aerospacesoftware.com/samba-ssh-tunnel-howto.htm)

Cheers,

Herman[/QUOTE]

From what I have read, the PPTP protocol is not insecure-- however, the MS implementation of it is.

---

### Post by cwaldbieser on 2005-11-30
[QUOTE=pigulsky]Well, actually the problem is not with ssh or pptp but with authorization.

It seems to me that the password I specified couldn't be transferred to the server because I got a message like:
**can't find any secret (password) to auth. **

But! The password is in the /etc/ppp/chap-secrets file!!! How can it be?[/QUOTE]
Have you tried using a front end configuration program like kvpn?  I might make things easier.

---

### Post by pigulsky on 2005-12-01
[QUOTE=cwaldbieser]Have you tried using a front end configuration program like kvpn?  I might make things easier.[/QUOTE]
Is it in the distro? If not - does it have any dependenses? 
Cause it is very problematic to switch between two OSes on computer to download something piece by piece.

---

### Post by pigulsky on 2005-12-01
Well, any suggestions?

---

### Post by cwaldbieser on 2005-12-01
[QUOTE=pigulsky]Is it in the distro? If not - does it have any dependenses? 
Cause it is very problematic to switch between two OSes on computer to download something piece by piece.[/QUOTE]
kvpnc is in universe.

---

