---
title: "No booting under VPC 2004"
date: 2006-03-19
forum: Desktop Environments
---

### Post by d3ejmz on 2006-03-19
Hi all,
I have searched the forum extensively as i know how and have not found a solution to this one. When I try to boot Server version of Breezy Badger (install went fine), it tries to kick into full screen mode and crashes not just VPC but the whole computer. Same with recovery mode. I am running winxp pro sp2, here are my hw specs:
 
soyo dragon plus v. 1.0a mobo
athlon 2600+ processor
2048 MB DDR333 RAM (that's right, 2 gigs!)
Maxtor diamondmax 9 80gb hda
maxtor diamondmax 20gb hdb
Benq 4x dvd+rw
Lite-on 52x24x52 CDRW
 
I think i should be able to run this. I can run mepis and knoppix just fine. I even installed openBSD for fun.
 
TIA,
Jim
:-k

---

### Post by Gallows on 2006-03-19
d3ejmz

When you say > crashes not just VPC but the whole computer What exactly do you mean?  A full Blue Screen or does the machine just lock up?  Do you have any VPC entires on the Application log?

I don't want to be the 1st one to point this out but any MS support probably won't be very forthcoming on this one.

Just checked out this site [vpc.visualwin.com]("http://vpc.visualwin.com") Breezy is reported as working but with X Server issues... However <SURPRISE> Breezy isn't supported by MS </SURPRISE>

---

### Post by d3ejmz on 2006-03-19
What I mean, is, a hard reset. I get the BIOS beep, the vid card bios screen, the BIOS messages, etc. It doesn't retest the memory, thankfully. so, it's like i soft-rebooted from within windows. but even the event log has no record of this occurrence. Normally (in win2k, NT4) it would say "the previous shutdown was unplanned" or something like that.   This seems to be about the time Ubuntu is initializing the vid card, a GeForce 440MX on PCI...
A couple of lines of text in 80x25 fullscreen mode, at the bottom and top of the screen, just a flash, and "beep!" i'm rebooted!  No i haven't yet tried it with the VPC window already full-screened.


I don't know much bout linux, but windows XP has never treated me like this before! (of course i doubt this would be happening if i weren't trying to run inside windows)  ;) 

:-?

---

### Post by d3ejmz on 2006-03-20
Alright, I booted in fullscreen mode. Apparently I do get a BSOD, fr just a split second. 
Still no record of it in the event log.

:cry:

---

### Post by Gallows on 2006-03-20
OK check out [this]("http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/sysdm_advancd_startrecover_recovery.mspx?mfr=true") from the big MS.  Pay attention to the "Write an event to the system log" bit.  Get XP to BSOD again and we'll see what's going on.

---

### Post by d3ejmz on 2006-03-26
[quote=Gallows]OK check out [this[IMG]chrome://targetalert/content/skin/new.png[/IMG]]("http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/sysdm_advancd_startrecover_recovery.mspx?mfr=true") from the big MS.  Pay attention to the "Write an event to the system log" bit.  Get XP to BSOD again and we'll see what's going on.[/quote]

Hmm.. I already have it set up to write an event to the system log. is it possible that whatever is crashing the computer crashes it so bad that it doesn't have a chance to do even that?

](*,)

---

### Post by Gallows on 2006-03-26
Well if it won't tell you why it crashes then we cannot fix it...

If it's any consolation Ubuntu works under [VMWare Server Beta]("http://www.vmware.com/products/server/") works and it's free (as in beer).  And they do a pre-built [Ubuntu Virtual Appliance]("http://www.vmware.com/vmtn/appliances/ubuntu.html")

---

