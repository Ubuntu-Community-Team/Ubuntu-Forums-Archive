---
title: "Beginner: 2 Issues: 1 Network (Sporadic unconnectivity); 1 Video (Monitor artifacts)"
date: 2009-01-16
forum: General Help
---

### Post by bonsai_halcyon on 2009-01-16
Hi, I'm new here, obviously, and I need some help. Before you ask, I did search the forums quite a bit already about my network issue and nothing seems to quite match - several close calls but nothing for sure. If you want to just provide a link to the existing thread that seems to answer my question, great, thanks, sorry for wasting your time.  Issue 2 I admit I haven't looked up quite as much (though I have done some research).

Issue 1:
I'm on an Inspiron 9200, previously running XP. I did a total format and installed Intrepid Ibex. My wireless router is a D-Link DI-524.
I was finally able to connect to the network, after changing my WEP from 64 bit to 128 bit. My wireless card is the Intel PRO/wireless with ipw2200.  I'm able to connect, but the performance is about 1/4 what it used to be on XP.  I often lose connection now, and have trouble regaining it unless I restart the pc.  My router is on the other side on one thin wall, I don't have a cordless phone to interfere.  
So my question is, what driver/app/update/crack/fix do I need to get my Ubuntu 8.10 to receive and maintain my wireless signal as well as XP did on the same machine?  Here are the results of sudo lshw -c network:
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:11:43:6a:64:d3
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=32 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:df:c3:0d
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=192.168.0.100 latency=32 link=yes maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 46:f9:90:18:f8:8e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

Issue 2:
Same laptop.  When the pc comes back from standby, I get strange green horizontal glitchy lines/artifacts (artefacts?) across the top of my screen. They are usually about 10-15 pixels wide.  I don't think I need to update my graphics drivers, as the hardware update thingy in Ubuntu says it can't find any new updates.  Does anyone know why Ubuntu doesn't like the display driver on my Inspiron 9200?  Can you point me toward the fix please?

Sorry for all the words, and sorry for probably posting this in the wrong place.  I really did do numerous searches for these issues,  and couldn't find much that exactly matched my problems (plus it's awfully difficult to search for these kind of bugfixes when you have sporadic network connectivity).  Thanks for the help, and from what I've seen so far I'm really excited to get to know Ubuntu :)

---

### Post by redilyn on 2009-01-16
Hi,

Don't worry, around here you normally won't get the "use the f*ing search" remarks. We are here to help. :)

Issue #1 - While I am not expert on wireless in ubuntu I have had my fair share of problems so I will try to help.

The first thing I would try is changing from WEP to WPA. WEP is not secure these days and if you hardware supports it there is no reason not to use WPA.

Don't know if this will solve your problem but it may help.

Issue #2 - Are you using compiz? If so can you try disabling it for a bit to see if the problem goes away?

---

### Post by bonsai_halcyon on 2009-01-16
Thanks Redilyn for the quick reply.  I will try both disabling compiz and changing to WPA tonight and let you know if it doesn't help. (I have a feeling disabling compiz will help issue 2 but I also have a feeling my problem with issue 1 is not WPA/WEP related. It's about time I switched to WPA anyway though.)

---

