---
title: "General Ubuntu questions..."
date: 2005-06-19
forum: Desktop Environments
---

### Post by Stealth on 2005-06-19
Hey guys, I'm building my second machine for my Uncle, who will be using his machine for SOHO purposes. He's tired of all the Windows crap and bloat and is willing to try out Linux. So I built him:

A AMD 3500+, 1GB RAM, 80GB SATA, Geforce 6200 machine. 

I have a couple questions though:
[list]
[*]Is there a performance game using the 64 bit version of Ubuntu over the 386?
[*]Will using 64 bit harm any compatibility with stuff? I know Windows has the worst driver support and junk on their nw 64 bit version, though I'm sure Ubuntu won't have that prob, but for instance will I need special version of packages or drivers?
[*]How does Ubuntu work on SATA? Fast and fine? Anything I should know?
[*]If I were to attach the PC to my network via ethernet during install, if I were to move it to his house and set up his own network over there, will it auto detect on boot or will it get screwy and try to find mine?
[/list] 

Thanks for any help! 1 more conversion to the Linux world!    :smile:

---

### Post by afonic on 2005-06-19
Hi,

the 64bit version is faster but for a not so experienced user I'd suggest using the i386 version. It will save you from many problems (including searching for 64bit drivers), and since most apps are 32bit I don't see a reason to move for now.

SATA works fine and fast on Ubuntu. I am not sure 100% of SATA controllers work though, so a good idea would be to get the live CD and try it out.

Network is easy to be configured, nothing to worry.

Good luck!

---

### Post by Stealth on 2005-06-20
Ok, thats cool, so I can pretty much configure Ubuntu and everything from my house, and just move it over there and it'll reconfigure network settings and stuff by itself?  :grin:

---

### Post by derrick1985 on 2005-06-20
[QUOTE=Stealth]Ok, thats cool, so I can pretty much configure Ubuntu and everything from my house, and just move it over there and it'll reconfigure network settings and stuff by itself?  :grin:[/QUOTE]

Yes, as long as your network is a DHCP (the ISP gives you the ISP) and you do not have to specify one, then you will be fine.

---

### Post by coniferous on 2005-06-20
>Is there a performance game using the 64 bit version of Ubuntu over the 386?
Some. But not enough to make the trouble worthwhile..

>Will using 64 bit harm any compatibility with stuff? I know Windows has the worst driver 
>support and junk on their nw 64 bit version, though I'm sure Ubuntu won't have that prob, 
>but for instance will I need special version of packages or drivers?
I *highly* doubt it. just to be sure though, try out the live cd. try both the i386 one out and the 64 bit one. I'd just choose the one you like better, and if there isnt much difference, go for the 64 bit one. 

>How does Ubuntu work on SATA? Fast and fine? Anything I should know?
shouldnt work any different then a regular IDE controller. be careful with raid - if your controler supports it. 

>If I were to attach the PC to my network via ethernet during install, if I were to move it to >his house and set up his own network over there, will it auto detect on boot or will it get >screwy and try to find mine?

If you both have a router then it shouldnt be a problem at all :) DHCP gets an ip address at startup.

Oh and, stupid question.. Whats SOHO?

---

### Post by shakin on 2005-06-20
[QUOTE=coniferous]I'd just choose the one you like better, and if there isnt much difference, go for the 64 bit one.[/QUOTE]

You'll find a few annoyances with the 64-bit version. Older programs that can't find the 32-bit libs won't run and 64 bits won't improve performance at all. It's only useful if you need more than 4GB of RAM.

[QUOTE=coniferous]Oh and, stupid question.. Whats SOHO?[/QUOTE]

Small Office / Home Office

---

