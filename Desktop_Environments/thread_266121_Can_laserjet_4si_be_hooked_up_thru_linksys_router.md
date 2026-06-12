---
title: "Can laserjet 4si be hooked up thru linksys router"
date: 2006-09-26
forum: Desktop Environments
---

### Post by BirdZerk on 2006-09-26
I have two computers connected through a linksys router to the internet, I also have a HP Laserjet 4si printer with an ethernet connection.  Question, can I use the printer, through the router, from both computers and if so how?  I have never networked two computers before so some detail would be helpful.

---

### Post by drpaul on 2006-09-27
I've done exactly this, but this is what I would try.

Setup Samba server on one computer and work throught the conf file issues to allow communication between computers.

Setup CUPS for your printing services [both computers]. Then do a little searching to find detailed instructions for adding a printer at an IP address in CUPS.

Not easy, but learning rarely is.

HTH

Paul

---

### Post by BirdZerk on 2006-09-27
OK, I must be blind, because I cannot find howto get the IP address of the printer?

---

### Post by ash211 on 2006-09-27
I believe the Laserjet 4Si has a little LCD panel with some configuration buttons on it.  Navigate to Toplevel->Configuration->Print to get a nice printout of data directly from the printer.  The IP address is on the second of the two pages.

---

### Post by BirdZerk on 2006-09-28
Thanks for the info, I printed a self test page from the control panel and it had the IP address on the print out.  What I have done so far is to have my Ubuntu system and Windows system connected to the Linksys router, I also connected the Laserjet 4si printer to the router also.  I used ping to check the router and yep it came back with readings, however when I try to ping the printers address nothing.  Any ideas what I should try now, because as of now I don't think the printer is being seen.

---

### Post by Iowan on 2006-09-28
Forgive me if this is a stupid question - my system connects through hubs instead of directly through a router...
Is the printer address in the same subnet as the other computers?

---

### Post by BirdZerk on 2006-09-28
Just checked, the router and the printer have the same subnet.

---

### Post by Iowan on 2006-09-28
Same subnet - not just subnet mask?  If subnet is the usual 255.255.255.0, The router might be 192.168.0.1, one computer might be 192.168.0.11 and the printer might be 192.168.0.200.  The printer couldn't be 192.168.1.12 even with 255.255.255.0 subnet mask (for example).  
   If the printer is in the same subnet as the other machines, then can it be pinged from either box (or the router? (You mentioned it was unreachable from ONE box).
   Another point to check - is the ethernet port active on the printer?  Just 'cuz it has one doesn't necessarily mean it's been turned on.
   Yet another test might be to use a crossover cable or hub to connect one of the boxes to the printer - bypassing the router short-term.
   It's my opinion that the printer *should* work through the router... but the devil's in the details.

---

### Post by drpaul on 2006-09-28
Read the printer manual to see if it can respond to a ping; not all addresses have that capability.

Paul

---

### Post by drpaul on 2006-09-28
As a 2nd thought, if you have CUPS installed, go to System Administration Printing

double-click on New Printer, and try installing a Network [IPP] printer. Putting the IP address and the proper driver should give you access from your Ubuntu box.

Did it work?

Paul

---

