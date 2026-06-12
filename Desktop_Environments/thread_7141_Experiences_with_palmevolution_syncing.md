---
title: "Experiences with palm/evolution syncing"
date: 2004-12-04
forum: Desktop Environments
---

### Post by anders on 2004-12-04
I just spent the afternoon trying to get my Palm Tungsten T to sync with Evolution with no luck. I've had this working on Evo 1.2 and Debian some time ago so I thought it shouldn't be that difficult. This is basically what I did before giving up:

- Configured the palm through evolution (gpilotd-control-applet), went smooth after I figured out I needed to use /dev/ttyUSB0 as device
- Added the pilot applet to the panel. Left-clicking the applet made it crash
- Tried to sync contacts, went fine except for lots of duplicate entries
- Tried to sync calendar, made the calendar really slow to navigate in evo
- Purged the evolution calendar, made evo hang
- Had to remove ~/.evolution/calendar to be able to start evo again
- Installed pilot-link and tried to backup palm using pilot-xfer. On the first two tries the transfer started normally but after a while the system completely locked up so I needed to do a hardware reset. The third try only resulted in a segfault, then I gave up.   

After searching through the forums it seems many people are having trouble with palm syncing. Is it even worth trying? Has anyone succeeded? Should I try multisync instead?

---

### Post by tmyster on 2004-12-04
Hello,

Last night I took the plunge and moved from Libranet to Ubuntu. I did this once I tried the live CD on my laptop first. As far as I can tell, the basics work well. So I did the install and I was happily surprised on how fast the install went for this laptop. I got a new dig camera (Kodak CX7330) to work. I connected it, used gThumb and there were my test pictures. I downloaded and deleted them also. That surprised me alot. 

Next, I figured I give my Handspring Visor a try. So I connected the cradle and went to the palmOS devices. The program didn't recognized it automatically. But I did check the kern.log to see if there was USB information. There was so I change the device type and followed through the program steps. And the hotsync worked. So I enabled address and hotsync'd again and there it was in evolution. I haven't tried much more cause this is only the second night. I will test some more functions and get back here  with the results.

---

### Post by jeremy on 2004-12-05
I have a T2, and haven't had any real problems, except that the pilot applet crashes for me too (so I stay away from it while synching).

---

### Post by Marauder1 on 2004-12-05
I have an Handspring Visor and its hooked to
/dev/ttyUSB1.
The thing simply works like a charm.
I have another USB device on my system
which is a scanner so that must be the reason
why its using ttyUSB1 instead of ttyUSB0 ?

---

### Post by anders on 2004-12-05
Thanks all for the input! Maybe I'll try to get it working after all. 

Marauder1: It seems that palms register two serial port devices: /dev/ttyUSB0 and /dev/ttyUSB1 and which one to use depends on the model:
[http://community.pilot-link.org/title/Palm+Device+Matrix](http://community.pilot-link.org/title/Palm+Device+Matrix)

---

### Post by Marauder1 on 2004-12-05
[QUOTE=anders]Thanks all for the input! Maybe I'll try to get it working after all. 

Marauder1: It seems that palms register two serial port devices: /dev/ttyUSB0 and /dev/ttyUSB1 and which one to use depends on the model:
[http://community.pilot-link.org/title/Palm+Device+Matrix](http://community.pilot-link.org/title/Palm+Device+Matrix)[/QUOTE]

Thanks for the tip !!!

---

