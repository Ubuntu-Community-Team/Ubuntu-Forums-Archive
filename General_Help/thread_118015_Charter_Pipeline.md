---
title: "Charter Pipeline"
date: 2006-01-16
forum: General Help
---

### Post by tbobo05 on 2006-01-16
I ordered Charter Pipeline the other day and still havent got it to work on my Ubuntu 5.10 box.  I have laptop running windows that runs it fine.  I didnt have to set any "client for microsoft networks" or anything on it, just plugged the modem in and plugged it into the nic and it worked.  Does anyone know of any microsoft particular services that charter needs to run?  any info would be helpful at this point.   Thanks

---

### Post by codejunkie on 2006-01-16
[QUOTE=tbobo05]I ordered Charter Pipeline the other day and still havent got it to work on my Ubuntu 5.10 box.  I have laptop running windows that runs it fine.  I didnt have to set any "client for microsoft networks" or anything on it, just plugged the modem in and plugged it into the nic and it worked.  Does anyone know of any microsoft particular services that charter needs to run?  any info would be helpful at this point.   Thanks[/QUOTE]
nope no special settings as far as im aware i use charter pipeline and it just works no configuration of any kind on ubuntu are you using a router, wireless router, hub anything like that?

---

### Post by tbobo05 on 2006-01-16
nope, just running straight out of their provided modem.....but i just tried another windows machine that i had laying around and could not get it running either, so maybe im just have problems with charter....but ubuntu does automatically send out a dhcp request when connected to a network, right? (provided that you havent set a static link of course)

---

### Post by codejunkie on 2006-01-16
[QUOTE=tbobo05]nope, just running straight out of their provided modem.....but i just tried another windows machine that i had laying around and could not get it running either, so maybe im just have problems with charter....but ubuntu does automatically send out a dhcp request when connected to a network, right? (provided that you havent set a static link of course)[/QUOTE]
it's not a problem with ubuntu or charter it's where your swapping computers and the modem can't release and renew the ip for that computer until you powercycle the modem, i've had that problem before. buy a router the router will gain an ip from your modem and then handle giving ip addresses to the computers you have on it. if you wan't a temporary fix for it until you get a router. unplug your modem and make sure the computer your hooking up to the modem is turned off, hook up the ethernet cable to your computer then plugin the modem, make sure the sync and ready lite stay constant before turning on your computer you'll have to do this every time you swap computers until you get a router hope this helps.

---

### Post by kumakun on 2006-01-16
The sync and ready light is specific to Ambit modems. if it's a motorola, the top 4 lights will be on. refer to your modem manual. All of this is correct, powercycling is necessary for the modem to push back a new IP address to a different MAC address behind it. A router will help, be aware that I've run into the issue where the router won't renew the IP lease properly, on occasion. I've not run into it with mine, but I've seen the problem at least once a day for the last 6 months. Powercycling the modem and the router is what will fix this. also, I just skimmed the advice given, but make sure that you set the eth0 to use DHCP, not static. It should already be set that way, but I needed to do it for my laptop, so...y'know just passing it along.

/K

---

### Post by tbobo05 on 2006-01-16
well, i dont guess i thought about that.  Thanks to all for your quick replies.:)

---

