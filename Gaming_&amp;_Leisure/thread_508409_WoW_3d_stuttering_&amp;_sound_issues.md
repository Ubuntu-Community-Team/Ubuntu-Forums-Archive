---
title: "WoW 3d stuttering &amp; sound issues"
date: 2007-07-24
forum: Gaming &amp; Leisure
---

### Post by chromerium on 2007-07-24
Hi all,

Recently installed 7.04 to see how Wine is coming along, and whether or not I can finally ditch windows (I only play one game, WoW) and was pleasantly surprised that I could pretty much just copy everything over and it worked.

Ended up doing some tweaking, to make it smoother, but I ran into an intermittant stutter that basically locked up the screen for seconds at a time, or it would slow the framerate to 1 FPS or so. Made raiding Karazhan last night a little interesting, but I persisted with it.

Tonight I got home and was mucking around, found the Services tool and turned on hdparm, turned off powernowd and the power management daemons then started up WoW and everything is suddenly smooth as silk :)

So, I thought I'd pass on my success to anyone else who is having stuttering with WoW under Wine in Ubuntu Fiesty 7.04.

Now the only last issue I have is, predictably, sound. I need to run Teamspeak and WoW at the same time but I find the conventional solution of using aoss to add too much latency to the sound output; it's adding almost a second to how long after an event happens onscreen and then the sound for it playing. ugh!

I obviously need to hack the /dev/dsp devices some more; the game is using /dev/dsp which is the playback/recording device, and I need to set that device to being the second playback device, and then create a /dev/dsp1 device that is the primary recording/playback device and point TeamSpeak at that, and it should solve my issues. But I have no idea how to mangle udev to make it do this. Can anyone point me to a good howto?

---

### Post by Sgood1971 on 2007-07-24
> **chromerium said:**
> 
Tonight I got home and was mucking around, found the Services tool and turned on hdparm, turned off powernowd and the power management daemons then started up WoW and everything is suddenly smooth as silk :)

Thank you for this, can't wait to get home and try.

---

### Post by darksidedude on 2007-07-24
I cant tell if this thread is dead but here goes,

i am sort of new to linux so , can you give me a step by step for this fix, it lags and i get about 7fps inside!! i have an nvidia 6200 if that helps thanks

---

### Post by chromerium on 2007-07-24
System->Administration->Services

Enable Hard disk tuning (hdparm)
Disable CPU Frequency manager (powernowd)
Disable Power managemenet (acpid)
Disable Power managemenet (apmd)

Close Services, and start WoW.

I confirmed that at least for me this was the problem; in dmesg i was finding messages relating to the speedup/slowdown on the CPU while I was playing. Ouch!

---

