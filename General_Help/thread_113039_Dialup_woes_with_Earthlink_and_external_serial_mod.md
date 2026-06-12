---
title: "Dialup woes with Earthlink and external serial modem... so close yet so far!"
date: 2006-01-05
forum: General Help
---

### Post by musicinmybrain on 2006-01-05
So... I switched to Ubuntu as my only operating system on my primary computer a few months ago, and I've been loving it. Unfortunately, now that I'm home on break for a while, I have to deal with my parents' dial-up Internet connection. Due to local monopolies, switching to broadband is not a financially viable option. My goal is to get dial-up networking working on my Ubuntu system so I don't have to use the Windows laptop all the time and also to get it working on my parents' computer so I can help them switch to Ubuntu from Windows 98.

Making the process easier is a recently acquired Actiontec serial/USB external modem used in serial mode.

First, I tried using System => Administration => Networking to set up my dial-up connection, then I tried kppp, then pppconfig with pon/poff. All gave, eventually, the same basic result: the computer communicates with the modem just fine. The modem appears to dial and connect to my Internet provider (Earthlink) just fine. Lifting a phone headset on the same line reveals "modem noises," the modem LEDs indicate a connection, and KPPP, when I use it, reports a realistic connection speed.

However, this connection is not actually usable. ping google.com results in a long wait followed by the message ping: unknown host google.com. cat /etc/resolv.conf gives me:

```

nameserver 207.69.188.187
nameserver 207.69.188.186
domain menagerie

```

I believe these to be the correct nameservers for Earthlink, and presumably the addresses were obtained in the connection process. When I try ping 207.69.188.187 (to see if perhaps the connection is working but DNS is broken), I get:

```

PING 207.69.188.187 (207.69.188.187) 56(84) bytes of data.
From 192.168.10.1 icmp_seq=1 Destination Net Unreachable

```

192.168.10.1 is my router, which the computer is plugged into on the eth0 interface. Normally, this would be the path to the wider Internet, but as I have only dialup available at the moment, the router's WAN port is empty.

ping 216.239.37.99, a google.com server, gives the same result.


I would really appreciate any assistance in getting this working. After all, my parents' escape from Windows 98 depends on the resolution of this problem!

---

### Post by musicinmybrain on 2006-01-05
Hurrah! The problem is solved. The issue was that there was a default route pointing to the router on the eth0 interface, which is just fine and all when I'm on a university network, but in this case was interfering with the automatic creation of the appropriate default route for the dial-up connection. Issuing ```
sudo route del default gw 192.168.10.1
``` before connecting cleared up the problem, and assuming I encounter this problem on my parents' computer, I'll be running that command at boot. Sorry to have troubled y'all, but I hope my experience can help another dial-up networking novice with what seems to be a fairly Google-resistant problem.

---

### Post by andlinux21 on 2006-03-11
Thanks for the tip my mom still has dialup so when i take my laptop home i will try to set up my earthlink dialup there...;)

---

