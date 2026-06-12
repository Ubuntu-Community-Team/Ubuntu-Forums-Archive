---
title: "Networked Printer Help (Brother HL-2070N)"
date: 2006-09-09
forum: Desktop Environments
---

### Post by Stelmate on 2006-09-09
I have been using a Brother HL-2070N with no problems to awhile now using the cups wrapper and the brother lpd driver.  All of a sudden the printer stops working.  I know it is getting connected because I goto the setting through my local machine at http://<print address> and I can see it connected in the router.  I can even print out a test page from the http menu but NOT under cups.  I don't remember installing anything since I last updated it and I'm not behind a firewall.  Any help would be much appreciated I really need to get this thing working again.  Also under the gnome CUPS menu and status I see:Unable to connect to printer; will retry in 30 seconds..

---

### Post by jeecol on 2006-11-26
I had the similar problem. Today (Nov 25), I upgraded it to new driver according to this post 
[http://www.ubuntuforums.org/showthread.php?t=68403&highlight=2070n](http://www.ubuntuforums.org/showthread.php?t=68403&highlight=2070n)

brhl2070nlpr-2.0.0-1.i386.deb  and 
cupswrapperHL2070N-2.0.0-1.i386.deb

(old version was 1.1.3)

then my 2070N didn't work, the green LED just flashed for several seconds wihtout printing.  I checked System > Printing, the model number was 2070N (it's correct), but the driver was HL1020

Then I added a new printer, this time I selected 2060, and it worked. (model of HL2400CeN also worked)

I checked these two new drivers and found 
"Converted from a rpm package by alien version 8.51" in synaptic....maybe 

By the way, when I re-start my hub, the printer always use 192.168.0.188 or 192.168.0.189. 
  
Anyway, it works now. Good luck! 

--------
jeecol = one dollar

---

### Post by morphet on 2007-01-01
Dude, jeecool! Thanks! :eek: :D  . I tried other tutorials, but the process was above my head (because the i386 drivers refuse to install in a PPC) for my Mac. Now it works perfectly.

---

