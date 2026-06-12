---
title: "Internet download only 1/5th in Kubuntu compared to XP! HELP!"
date: 2005-07-13
forum: Desktop Environments
---

### Post by derrick1985 on 2005-07-13
Hey all.

I was getting tired of waiting for web pages to load up in Kubuntu, so I decided to do a speed test on my Windows HD, and then the Kubuntu one, and see if there was a difference... and believe me, there is.
Both tests were done using Firefox as the browser, and pretty much within 5 minutes of each other.

Windows

:::.. Download Stats ..:::
Connection is:: 4032 Kbps about 4 Mbps (tested with 2992 kB)
Download Speed is:: 492 kB/s
Tested From:: [http://testmy.net/](http://testmy.net/) (server2)
Test Time:: Tue Jul 12 2005 11:48:00 GMT-0300 (Atlantic Daylight Time) 
Bottom Line:: 72X faster than 56K 1MB download in 2.08 sec 
Diagnosis: Awesome! 20% + : 56.1 % faster than the average for host (eastlink.ca) 
Validation Link:: [http://testmy.net/stats/id-S3GF6JUTL](http://testmy.net/stats/id-S3GF6JUTL) 

:::.. Upload Stats ..:::
Connection is:: 576 Kbps about 0.6 Mbps (tested with 579 kB)
Upload Speed is:: 70 kB/s
Tested From:: [http://testmy.net/](http://testmy.net/) (server1)
Test Time:: Tue Jul 12 2005 11:48:37 GMT-0300 (Atlantic Daylight Time) 
Bottom Line:: 10X faster than 56K 1MB upload in 14.63 sec
Diagnosis: Awesome! 20% + : 33.33 % faster than the average for host (eastlink.ca) 
Validation Link:: [http://testmy.net/stats/id-8X0WT67CJ](http://testmy.net/stats/id-8X0WT67CJ)

Linux (Kubuntu)

:::.. Download Stats ..:::
Connection is:: 1181 Kbps about 1.2 Mbps (tested with 748 kB)
Download Speed is:: 144 kB/s
Tested From:: [http://testmy.net/](http://testmy.net/) (server1)
Test Time:: Tue Jul 12 2005 11:55:27 GMT+0000 (UTC) 
Bottom Line:: 21X faster than 56K 1MB download in 7.11 sec 
Diagnosis: May need help : running at only 45.76 % of your hosts average (eastlink.ca) 
Validation Link:: [http://testmy.net/stats/id-ICO2JL0NB](http://testmy.net/stats/id-ICO2JL0NB) 

:::.. Upload Stats ..:::
Connection is:: 833 Kbps about 0.8 Mbps (tested with 1496 kB)
Upload Speed is:: 102 kB/s
Tested From:: [http://testmy.net/](http://testmy.net/) (server1)
Test Time:: Tue Jul 12 2005 11:55:33 GMT+0000 (UTC) 
Bottom Line:: 15X faster than 56K 1MB upload in 10.04 sec
Diagnosis: Awesome! 20% + : 91.94 % faster than the average for host (eastlink.ca) 
Validation Link:: [http://testmy.net/stats/id-AU1PGODMR](http://testmy.net/stats/id-AU1PGODMR)

Is there anyway to speed this up?

---

### Post by rmjokers on 2005-07-13
It might be helpful if you provided some information about how you are connected to the internet (cable, dsl) and what type of network card you have.

---

### Post by derrick1985 on 2005-07-13
Ok, here it is:

I'm using a Cable Modem hooked into a router (only pc on right now on the network, usually is the only one) that is supposed to be 5mbps down, and 700 up. (the down is going up to 10 by the end of the month) and the Network card (from Kinfocenter) is:

Ethernet Controller: Via Technoligies INC, VT6102 [Rhine II] (rev 43)
Subsystem: D-Link System INC, DFE-530TX rev A
Flags: Bus master, medium devsel,  latency 32, IRQ 16
I/O Ports at C800 Size=256

---

### Post by rmjokers on 2005-07-13
No obvious problems come to mind given your setup.  There are a few things you might try to narrow down the problem:

Turn off IPV6 in firefox
about:config -> network.dns.disableIPv6 = true

Try the test with a different browser (e.g. konqueror)

Make sure your ethernet card finds a 100Mbps full duplex link (usually in /var/log/messages after reboot)

Attempt a direct file transfer between your linux box and another machine through the router and see what kind of throughput you get (should be ~ 100Mbps if your systems are fast enough)

Check for errors in /var/log/messages related to ethernet card

Good luck!

---

### Post by derrick1985 on 2005-07-20
Ok, I did the same tests on my other kubuntu box (cyrix II 250mhz and 128mb of ram) and it's speed was 4 times faster than my pc (p4 2.4 1 gig ram) so, I switched network cards, and voila! It works now!

AFter Switching NIC

:::.. Download Stats ..:::
Connection is:: 9228 Kbps about 9.2 Mbps (tested with 12160 kB)
Download Speed is:: 1126 kB/s
Tested From:: [http://testmy.net/](http://testmy.net/) (server2)
Test Time:: Wed Jul 20 2005 18:08:13 GMT+0000 (UTC) 
Bottom Line:: 165X faster than 56K 1MB download in 0.91 sec 
Diagnosis: Awesome! 20% + : 257.81 % faster than the average for host (eastlink.ca) 
Validation Link:: [http://testmy.net/stats/id-3A4ZYBLS7](http://testmy.net/stats/id-3A4ZYBLS7) 

:::.. Upload Stats ..:::
Connection is:: 916 Kbps about 0.9 Mbps (tested with 1496 kB)
Upload Speed is:: 112 kB/s
Tested From:: [http://testmy.net/](http://testmy.net/) (server1)
Test Time:: Wed Jul 20 2005 18:09:29 GMT+0000 (UTC) 
Bottom Line:: 16X faster than 56K 1MB upload in 9.14 sec
Diagnosis: Awesome! 20% + : 109.13 % faster than the average for host (eastlink.ca) 
Validation Link:: [http://testmy.net/stats/id-Z6LBSN2OE](http://testmy.net/stats/id-Z6LBSN2OE)

---

### Post by Terracotta on 2005-07-20
ok, first of all :s 1181kbps is not slow at all, can't believe you have to wait for a site to open, it won't be due to your internet connection, but to that of the sites server, my maximum download is limited to 800kbps, and I hardly have to wait for sites to open. Second 1181 is more than 1/4 so it won't be 1/5th quite misleading. After the flame, the slime: :-) interesting specs, what internet provider are you on? I want such a connection mjammie +9000kbps??????? And please tell me the name of the card, didn't know that could make such a difference :s, not that it's gonna work here (belgium) since they limited the download speed grrrrrrrrrr.
btw: did you test your system with xp after you changed your cards? i'm interested in the results you get.

---

### Post by derrick1985 on 2005-07-20
[QUOTE=Terracotta]ok, first of all :s 1181kbps is not slow at all, can't believe you have to wait for a site to open, it won't be due to your internet connection, but to that of the sites server, my maximum download is limited to 800kbps, and I hardly have to wait for sites to open. Second 1181 is more than 1/4 so it won't be 1/5th quite misleading. After the flame, the slime: :-) interesting specs, what internet provider are you on? I want such a connection mjammie +9000kbps??????? And please tell me the name of the card, didn't know that could make such a difference :s, not that it's gonna work here (belgium) since they limited the download speed grrrrrrrrrr.
btw: did you test your system with xp after you changed your cards? i'm interested in the results you get.[/QUOTE]

I'll try out in xp and see what it goes to from there. My Internet provider (eastlink) here in canada, offers 10 mbps download now, from 5 previously. So, the speed difference is definately noticable now. I can usually get the kubuntu .iso file in under 15 minutes (shortest was 10)

An as for the card, it's a Realtek  RTL-8139/8139c/8139c+

---

### Post by PhilippWollermann on 2005-07-21
I knew that the VIA Rhine based network cards are really evil, when you look at throughput and cpu utilization, but I didn't know that they are THAT bad. ;)

Philipp

---

### Post by derrick1985 on 2005-07-21
[QUOTE=PhilippWollermann]I knew that the VIA Rhine based network cards are really evil, when you look at throughput and cpu utilization, but I didn't know that they are THAT bad. ;)

Philipp[/QUOTE]

Yeah, the cheapy card that I got from work beat out the other one real well.

---

