---
title: "RDP to Windows Server 2008 Terminal Session"
date: 2009-03-31
forum: Desktop Environments
---

### Post by jaket on 2009-03-31
We are trying to get some additional life out of some older machines in our organisation by making them into effective thin clients that connect to our Terminal Server. 
I am wondering if there is a way to connect to a Terminal Session run by Windows Server 2008 using an RDP client on Ubuntu. 
I found a UNIX based client: rdesktop which says it is compatible with Server 08 but before I try I was wondering if anyone had had any luck implementing this before? Are there any other programs that are able to do this? 

The other semi-related question then is am I going to run into issues installing Ubuntu on old-er machines? 

Much appreciate any help - thank you all in advance.

---

### Post by zeealpal on 2009-04-01
How old are the old-er machines? Any specs?

---

### Post by jaket on 2009-04-01
Hey, There are quite a range and none the same - probably range from 5-8 years old. They vary from Win95 computers (don't hold much hope for them) to Win 2000 computers. An example of some specs from one of our Win 2000 computers is as follows:

Bios
Default System BIOS	Award Software, Inc.	Award Modular BIOS v6.0	EVAL
CD-ROMs
ASUS CRW-4012A	E:
Memory
256.00 MB	unknown	DIMM	
Network Card
Intel(R) PRO/100 VE Network Connection	
Processors
Intel(R) Pentium(R) 4 CPU 1.80GHz	x86 Family 15 Model 2 Stepping 4	x86 Family 15 Model 2 Stepping 4
Physical Drives
IOMEGA ZIP 100	unknown	IDE
Maxtor 6E040L0	38.29 GB	IDE
Hard Drives
C:	38.28 GB	33.80 GB
Sound Devices
Unimodem Half-Duplex Audio Device	Microsoft
Avance AC97 Audio	Avance
Motherboard
Base Board	System Manufacturer	
Video Controller
Intel(R) 82845G/GL Graphics Controller	800x600	60Hz

---

### Post by dabbner on 2009-04-06
I am interested to know if you got this working.  I am currently having a ton of issues connecting to 2008 TS with my Ubuntu install.  Other than that, the install runs flawlessly on my HP laptop.

---

### Post by jaket on 2009-05-13
Hey Dabbner, 
We just started testing this - unfortunatly the RDP wasn't able to utilise the ts gateway so can't use rdesktop outside of the wired network. 
How we get a terminal session working is by keeping the linix machines on the same DNS as our servers and then simply remoting into the ts session that way. This works for us as we have all our offices connected via VPN anyway so actually was pretty easy in the end. :-)

---

### Post by plnnightsky on 2009-07-06
Posted this question as well a few weeks ago, and didn't hear anything.  I thought it might help anyone with issues RDPing to Windows Server 2008, understand where the problem might be.  If anybody has an answer, I am in urgent need of it as well.  This is what needed to be added to the registry for RDP to work from XP "tspkg".


Our office has switched all the servers to using NLA for authentication via RDP. This meant all the XP boxes had to have a registry hack so they could connect. It also means I cannot RDP to the servers from Ubuntu anymore.

Does anybody know what I need to do to make it work? I am running the 9.04 updated, using tsclient 0.150 version. I have not been to find any searches on the forum on google.

thanks

---

