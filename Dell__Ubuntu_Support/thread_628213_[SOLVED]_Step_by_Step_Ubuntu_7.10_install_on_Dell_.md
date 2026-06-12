---
title: "[SOLVED] Step by Step Ubuntu 7.10 install on Dell Vostro 1000"
date: 2007-12-01
forum: Dell  Ubuntu Support
---

### Post by cbossio on 2007-12-01
Out of the box, Ubuntu 7.10 Gutsy Gibbon had 3 main problem on my Dell Vostro 1000.
[B]
1. Wireless
2. Visual Effects
3. DVD playback[/B]

I'm putting together this howto in order to save the head ache of searching all the possible solutions posted in the forum.   Just for the record, my Vostro has the following hardware:

[B]Broadcom 1390 WLAN MiniCard
ATI Radeon X1150 Graphics card
AMD Turion 64 X2 Dual-Core[/B]


**WIRELESS SETUP** can be found here:
[http://ubuntuforums.org/showthread.php?t=297092&highlight=Dell+Wireless+1390]("http://ubuntuforums.org/showthread.php?t=297092&highlight=Dell+Wireless+1390")

Post #1 is the one your looking for.  Great thanks to paperdiesel for the step by step.  He posts a special warning about a "clean system".  There maybe another way around using a freshly installed "clean system", but after hours of searching, I couldn't find it.  Save the head ache and just follow the instructions exactly (including a fresh install if necessary). 



**VISUAL EFFECTS** can be found here:
[http://ubuntuforums.org/showthread.php?t=436110&page=2]("http://ubuntuforums.org/showthread.php?t=436110&page=2")

You'll be looking for post #17 by cifrancgx.  Simple. Straightforward. Works.



**DVD PLAYBACK** found here:

The post is #12 by crjackson.  I don't know if my problems were because of the 64 bit processor or not, but this was the only post of many many many that worked.  My two cents is that if your running a similar processor as me, to give this a try.


If your using a vostro with similar specs, this should take care of the major issues.
Again, big thanks to the original posters I mentioned above.

---

### Post by manicnerd on 2007-12-09
> **cbossio said:**
> 

**VISUAL EFFECTS** can be found here:
[http://ubuntuforums.org/showthread.php?t=436110&page=2]("http://ubuntuforums.org/showthread.php?t=436110&page=2")

You'll be looking for post #17 by cifrancgx.  Simple. Straightforward. Works.




I also have a vostro 1000...to get the graphics card working correctly I followed the unofficial ATI linux driver wiki page.  The Ubuntu section can be found [here]("http://wiki.cchtml.com/index.php/Ubuntu")...just choose which version you are running and follow the appropriate instructions.

**_EDIT:_**
I noticed that the ATI Catalyst Control Center reports that my card only has 128mb memory when it should be using 256mb.....does anyone know how to fix this?  

**_EDIT #2:_**
After a re-install it is now recognized as 256mb....dont know what I did differently

---

### Post by mara9ato on 2008-02-03
Note: I've got the wireless device up and running by just enabling it on the Restricted Drivers Manager on a fresh 7.10 install.

---

