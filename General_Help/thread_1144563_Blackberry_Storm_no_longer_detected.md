---
title: "Blackberry Storm no longer detected"
date: 2009-04-30
forum: General Help
---

### Post by Weidbrewer on 2009-04-30
Hey, all.  I had a Blackberry Storm that I would hook to my PC and laptop to exchange media files.  It was always detected by default (didn't always auto mount.)   However, my phone bricked over the weekend and I had to get a new one.  This one no longer mounts.   I have MTP and Mass Storage enabled, as well as Auto Enable Mass Storage Mode When Connected.  It doesn't auto mount, nor do I see it listed under Places->removable media. I believe that it is in lsub by these lines:

```
Bus 001 Device 002: ID 0fca:8001 Research In Motion, Ltd. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

``` 

I know the USB port is fine on both ends, because it connects to the desktop manager under Windows.   Argh.   Any ideas out there?

---

### Post by Weidbrewer on 2009-05-01
To eliminate variables, I tried it on another Windows machine (worked) and two other Ubuntu machines (no dice.)

---

### Post by Weidbrewer on 2009-05-04
*bump*

---

### Post by MeanEYE on 2009-05-25
> **Weidbrewer said:**
> *bump*

Hey, I see no one is replying... am about to purchase 9500 myself so I'll try to help.

Can you provide dmesg output after you hookup your phone.

---

### Post by Weidbrewer on 2009-05-25
Thanks for popping in.  I was never able to get much info, even from the Linux corner of the BB site.  Know what actually fixed it?  New Storm.  (My third.)  Once I got that new one, it was detected just fine.

Other bits of info that I had found was that evidently a lot of people had trouble with the newest version of the OS, and downgrading solved the problem.  This was not true in my case, and it appears that I just had a defective unit.

I love the phone...when it works.  But there seems to be a very high rate of bricking.  Most of the people I know with them are on at least their second unit.

---

### Post by FrankVdb on 2009-06-06
I just bought a Blackberry Storm too, me too I'm still on Intrepid. 

I have the same issue, i.e. the phone isn't detected although lsusb sees it.

Don't know what to do either...

---

### Post by paul@cyberengel.com on 2009-09-04
I just got a 9630 Tour.  If I use Mass Storage Mode it works fine, but I want to try it in MTP.  However whenever I connect it to my laptop a "Mass Storage Drive" appears but I cannot mount it.

> [ 2137.372240] usb 1-4.1: new high speed USB device using ehci_hcd and address 12
[ 2137.493560] usb 1-4.1: configuration #1 chosen from 1 choice
[ 2137.512955] scsi9 : SCSI emulation for USB Mass Storage devices
[ 2137.513578] usb-storage: device found at 12
[ 2137.513584] usb-storage: waiting for device to settle before scanning
[ 2142.513228] usb-storage: device scan complete
[ 2142.514416] scsi 9:0:0:0: Direct-Access     RIM      BlackBerry SD    0003 PQ: 0 ANSI: 4 CCS
[ 2142.515822] sd 9:0:0:0: Attached scsi generic sg2 type 0
[ 2142.518253] sd 9:0:0:0: [sdb] Attached SCSI removable disk


I updated to the latest libmpt and I've been Googling for a while and can't seem to find any info on troubleshooting what's going on.

---

### Post by Tootler on 2009-11-13
I have just got a Blacberry Storm 2 and so far it has mounted OK. I have other queries but they are for another thread.

Geoff

---

