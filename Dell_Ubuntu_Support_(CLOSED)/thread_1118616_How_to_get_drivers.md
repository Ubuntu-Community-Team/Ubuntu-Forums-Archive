---
title: "How to get drivers?"
date: 2009-04-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by deceptionpoint on 2009-04-07
Hey guys just need to know how to get drivers for my Dell Dimenson 2400.
[IMG]http://img408.imageshack.us/img408/6240/screenshotsystemmonitor.png[/IMG]

Currently have no sound..

I've been told it may be due to issues with my graphics driver or something.

Any help?

---

### Post by mhgsys on 2009-04-07
please open a terminal and typ:
```

lspci

```

post output here afterwards.

---

### Post by deceptionpoint on 2009-04-07
Here you go.

```
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:05.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

```

---

### Post by mhgsys on 2009-04-07
A little googleing teaches a lot. But I didn't find a easy solution which I'm sure of.
        
     (and I can't really try anything out since I don't have that card myself)

Good thing is your on a good forum, and maybe other people can help you out with this.
Anyway; the solution below seems pretty easy, though it's from 2005 and for fedora, I hope it will work for you.
[https://www.redhat.com/archives/fedora-list/2005-January/msg05487.html](https://www.redhat.com/archives/fedora-list/2005-January/msg05487.html)


if not, keep a eye on this thread as well.

[http://ubuntuforums.org/showthread.php?t=1078702](http://ubuntuforums.org/showthread.php?t=1078702)

---

### Post by deceptionpoint on 2009-04-07
That makes no sense to me =\

I'm a noob =\

---

### Post by mhgsys on 2009-04-07
That's Ok, I'm not sure if this will work , but this is in the link.
Stripped is Simplified


 Open a terminal
type:
```
    
alsamixer

```

-Use the arrow keys and go to Headphone Jack Sense,

At the top of the bar may appear (or not) "MM"; typing an "m"
  toggles the "MM" on and off
MAKE SURE THE MM APPEARS at the
  top of the "headphone jack sense" bar

  -Go to "line jack sense", found by pressing
  the right arrow sufficient times,


  Do the same thing to "line jack sense 

Hope it works

---

### Post by deceptionpoint on 2009-04-07
Pressing the arrow keys doesn't do anything for me..

Edit: I should've made it clear, I'm using output method OSS.
Also I'm just having issues with sound in Flash and amsn.

---

### Post by abn91c on 2009-04-07
go to [http://www.dell.com](http://www.dell.com), click on the support page, enter your service tag and download the drivers there for windows. The 2400 sound works plug and play with Ubuntu/kubuntu 8.xx, the video card i845 will not run compiz in 8.10 due to a driver bug so carefully check the ubuntu sound settings, run the alsa check, make sure nothing is muted( I hvae a dimension 2400 by the way)
Look at this thread for a sound fix that may help you [http://ubuntuforums.org/showthread.php?t=1117252](http://ubuntuforums.org/showthread.php?t=1117252)

---

### Post by JUSTINBEAIRD on 2009-06-21
i have the same computer to get sound working on mine i had to disabele headphone jack sense and not sure what else also use the headphone volume to control it under volume controle prefrenses mess in their

---

### Post by mattwilkes512 on 2009-06-24
For those of you who have a dimension 2400 can you report on what version of Ubuntu your using and whether or not your sound and graphics work?  I'm running 9.04-and sound & graphics are both down.  I figure to get graphics back up I'm getting a PNY PCI 512mb 8400GS from amazon-they're cheap right now with rebate.  The driver they come with and in Jockey (180) doesn't work so I'll have to install a 185.xx or 190.xx series driver (in forums or from PNY site).  
But how do I fix audio then?  Don't think the graphics card (its video too) will remedy that too.  Will it?  Or do I need a seperate PCI sound card?  Or can I get onboard sound to work in 9.04 while running graphics off a card?  Thanks all!

---

