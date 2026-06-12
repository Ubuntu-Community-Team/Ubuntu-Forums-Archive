---
title: "Kubuntu &amp; (the need for a) firewall"
date: 2005-09-20
forum: Desktop Environments
---

### Post by schmappel on 2005-09-20
Hi all,

First off: I'm the noobiest of noobs on Linux en Kubuntu, but I'm willing to learn. I was wondering if there's a firewall included on (the latest version of) Kubuntu. I read some good things about Guarddog and Firestarter, yet i wasn't able to find it through Kynaptic or Sudo apt-get. I've downloaded the Tar file from the Guarddog site and followed the instructions in the INSTALL file. After typing ./Configure in Konsole it says I need some kind of GCC compiler (or so) and that's just too much for my weary brain! Could someone please enlighten me on how to get this thing running, 'cause i was always taught one needs a firewall if one's connected :)

Thanks!

*edit: silly typo*

---

### Post by Hobbsee on 2005-09-20
[QUOTE=schmappel]Hi all,

Fist off: I'm the noobiest of noobs on Linux en Kubuntu, but I'm willing to learn. I was wondering if there's a firewall included on (the latest version of) Kubuntu. I read some good things about Guarddog and Firestarter, yet i wasn't able to find it through Kynaptic or Sudo apt-get. I've downloaded the Tar file from the Guarddog site and followed the instructions in the INSTALL file. After typing ./Configure in Konsole it says I need some kind of GCC compiler (or so) and that's just too much for my weary brain! Could someone please enlighten me on how to get this thing running, 'cause i was always taught one needs a firewall if one's connected :)

Thanks![/QUOTE]
 Hello!

Firstly, if you've enabled the extra repositories, guarddog will be there...

> sudo apt-get install guarddog will find it (in a terminal)

One definetly needs a firewall on windows when one is connected.  From what I understand, ubuntu (and most or all other distrobutions) have a firewall built in, which is editable via the console.  Firestarter and guarddog seem to be GUIs for this...

If someone could confirm this, that would be great.

---

### Post by MartinG on 2005-09-20
Guarddog and Firestarter are in fact both available via Kynaptic, as long as you have the right repositories enabled.  I won't tell you how to do this; try going here:

[http://ubuntuguide.org](http://ubuntuguide.org)

This will tell you how to add repositories and a whole lot more  :) 

Personally, although I'm on Kubuntu I use the Gnome firewall (Firestarter) because I find the instructions less confusing -- feeble, I know!

--
MartinG

---

### Post by schmappel on 2005-09-20
Hey,

Thanks for your answers! Unfortunately ubuntuguide.org seems to be on a DNS break for the moment, but fortunately we still got [Google's Cache](http://66.249.93.104/search?q=cache:oCNVrC8mgQ8J:ubuntuguide.org/+extra+repositories+site:ubuntuguide.org&hl=nl&client=firefox-a).

Thanks again, I'll try adding those extra repositories.

ap

---

### Post by shakin on 2005-09-20
Firewall on desktop computers are good for blocking access to ports that you cannot close. Windows suffers from this because you cannot close all of your ports. However, Ubuntu and Kubuntu ship with no listening ports, so you don't need a firewall unless you install a server and want to restrict access.

A good example of this is SSH. You may want to install an SSH server and only allow access from specific other computers. SSH by itself will listen on port 22 for any connection, so is a possible vector of attack. By using Guard Dog or Firestarter you can block access to anyone other than the computer(s) you want to have access.

---

### Post by schmappel on 2005-09-20
So if I understand you correctly: unless you install a server no firewall is actually needed? Well, it's probably gonna take a while for this Windows user to get comfortable with *not* using a firewall. I'd almost feel naked without one.

---

### Post by Hobbsee on 2005-09-20
[QUOTE=schmappel]So if I understand you correctly: unless you install a server no firewall is actually needed? Well, it's probably gonna take a while for this Windows user to get comfortable with *not* using a firewall. I'd almost feel naked without one.[/QUOTE]
 hehehe....

I assure you, you're not alone.

---

### Post by drizek on 2005-09-20
if you have a halfway decent router, you are going to be safe. in windows, firewalls are actually more usefull to stop spyware and to stop Ms's apps from "phoning home' than actually stopping hackers.

---

### Post by schmappel on 2005-09-21
Somewhat off-topic: what router would that be in your opinion? I was actually planning to buy a new router, so any tips would be very much appreciated.

Thanks!

---

### Post by greyhound4334 on 2005-09-21
Pretty much any router these days is going to have a NAT based firewall and probably Stateful Packet Inspection (SPI) built in.  Just go with a good brand name like LinkSys and you'll be fine.  For a small bit extra, you can get a combined router and Wireless Access Point so that you can have wireless access if/when you need it.

I run software firewalls (zonealarm) on my Windows computers even though they're behind the firewall.  I don't run one on my Ubuntu stations though (probably should, since it's very easy, but I"ve been lazy and it's probably not really necessary).

---

### Post by Takis on 2005-09-21
[QUOTE=shakin]Firewall on desktop computers are good for blocking access to ports that you cannot close. Windows suffers from this because you cannot close all of your ports. However, Ubuntu and Kubuntu ship with no listening ports, so you don't need a firewall unless you install a server and want to restrict access.[/QUOTE]
I've heard this argument before and I must say that I'm not 100% convinced myself. I'm a fan of the dedicated firewall solution, so that your main computer is not going to be the primary target of attacks. This means you don't have to worry so much about what you install opening up ports. To this end, I recommend [www.smoothwall.org](www.smoothwall.org). Fantastic free solution that runs on cheap hardware.

---

### Post by stoneguy on 2005-09-21
Security is a complicated topic. I'm by no means an expert, but as my day job involves operating a number of file, print, and database servers, I've had to learn a bit even though I'm behind a enterprise firewall.

If you're running highspeed, you really ought to be using a router/firewall device. Discontinued SMC and D-Link routers can be had around here for $10-20 with various rebates. That's cheaper, less complicated, and more reliable than rolling your own with an old PC and a couple of network cards. The cheap-cheap routers don't do VPN reliably, so if you're dual-booting something that has to connect to your workplace that way, be careful what you buy.

If you're running a bunch of machines mixing different versions of Wins and Lins like my partner and I do at home, putting edge protection in a separate router/firewall is a good idea.

If all you have is one or more computers permanently connected to a wired lan, you can probably get away with not having firewalls on individual machines. But if you've got laptops jacking into and out of that network or your lan is wireless, well, software firewalls all around could well save your butt if something crawls in from outside.

---

### Post by drizek on 2005-09-21
check this out [http://edealinfo.com/DDCategAll/networking.shtml](http://edealinfo.com/DDCategAll/networking.shtml) for some deals on routers(and other tech stuff on the rest of the site). anything brand name will be fine, like the wireless linksys which is around $18.

Edit: oops, just noticed the rebate is expired. get the 22 dollar netgear then  ;-)

---

### Post by localzuk on 2005-09-26
[QUOTE=Takis]I've heard this argument before and I must say that I'm not 100% convinced myself. I'm a fan of the dedicated firewall solution, so that your main computer is not going to be the primary target of attacks. This means you don't have to worry so much about what you install opening up ports. To this end, I recommend [www.smoothwall.org](www.smoothwall.org). Fantastic free solution that runs on cheap hardware.[/QUOTE]

Hacking comes in many forms. The most common is where an individual scans a computer for open ports and then analyses the ports that are open. They then either use known exploits for the software that is running on that port or do a brute force attack, checking many user/password combinations in order to try and log in.

To spot this, you can install a intrusion detection system - but a firewall will not be much use to you unless you have ACL's in place to prevent access to the ports from anywhere except specific IP's.

So in the case of a default ubuntu install, you are safe from most attacks. A firewall is more of a 'safety blanket' on Ubuntu than an actually useful tool (especially if you are installing firestarter et al as they are overly simplistic).

It can also lead to a lack of active protection on your computer - as you think you have it covered by the firewall and therefore become complacent.

On the point of Smoothwall/IPcop, this is a good solution. However an old system is a power hungry, innefficient beast. So with the money you save on using the free distro, you spend on power. So if you want to be environmentally friendly, you should go with a hardware router with proper firewall/ids/acl policy protection (and you will probably, using my own experience, save about 15% on electricity).

Cisco switchs and routers can be picked up reasonably cheaply on ebay now. I would recommend these to anyone.

---

