---
title: "HP LaserJet P1005 in Ubuntu 8.04 LTS"
date: 2008-12-23
forum: General Help
---

### Post by tdn on 2008-12-23
Hi

I have a new HP LaserJet P1005 and a fresh install of Ubuntu 8.04. 

When I connect the printer to USB an turn it on, Ubuntu recognizes the printer and installs it; then it tells me that the printer is ready to print.

However, when I print a test page, nothing happens.

I have tried adding the printer manually via CUPS administration (localhost:631), but that did not help.

I really hope you can help me with this.

---

### Post by tarbox on 2008-12-31
I've also had this problem and spent enough time looking around to have come to a few conclusions.

First, there is something massively wrong with printing in general.  The need for drivers, kernel compilation etc. is entirely nuts and speaks to deep flaws in the architecture and industry.  I mean, its printing... didn't we solve this one a couplea decades ago?

So, while Ubuntu appears to be exceedingly incompetent WRT printing, the trouble does indeed run very deep.

On the P1005 issue, I recommend giving up.  I've spent a few weeks on and off, installed just about everything... and the best you can hope for is a couplea days of printing before it stops.  The many threads on the topic and some searching will support this conclusion.

You're way better off finding a printer which is known to work and buy that... the P1005 isn't worth your time with Ubuntu.

-glenn

---

### Post by yellerKat on 2009-01-27
Go [here]("http://hplipopensource.com/hplip-web/gethplip.html") and follow the instructions - works brilliantly! Never give up!

---

### Post by waltereo on 2009-01-30
Hi,

   I have exactly the same problem. Ubuntu 8.04 detect the printer. then I install the driver from the link in the previous post. Installation work fine.
Then when it comes to print, nothing happen. The job is in the queue.   Then I got a pop up saying that the printer may not be connected even thought the usb cable  is fully plugged.


Need help !!! 


Thansk

---

### Post by asuwannarat on 2009-03-04
I use Ubuntu Server 8.10 and cups with HP LaserJet P1005.

However I think follow this should resolve your P1005 problem.

1. go to [http://foo2xqx.rkkda.com/](http://foo2xqx.rkkda.com/) and follow to the web suggestion.

2. go to [http://ubuntuforums.org/showthread.php?t=240282](http://ubuntuforums.org/showthread.php?t=240282) and follow to the suggestion by use ppd file that locate in

/usr/share/ppd/foo2zjs/HP-LaserJet_P1005.ppd.gz

3. Everything should be resolved.

Thank for these two links.

Asuwannarat

---

### Post by jigme on 2009-06-06
I have the same setup as you, printer and version.

I visited [http://forums.linux-foundation.org/read.php?20,4643](http://forums.linux-foundation.org/read.php?20,4643)

Followed the recommendation to sudo hp-setup with a fresh install of HPLIP and I won. 

Hope you have the same win.

Sammy

---

