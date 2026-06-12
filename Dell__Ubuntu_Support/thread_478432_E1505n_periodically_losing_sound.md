---
title: "E1505n periodically losing sound"
date: 2007-06-19
forum: Dell  Ubuntu Support
---

### Post by digilink on 2007-06-19
My E1505n sometimes loses sound and I can't really understand why. The volume isn't muted and I've turned the controls all the way up and still can not get any sound whatsoever. 

I'm testing by going to system->preferences->sound and clicking on the test button next to sound playback, doesn't matter what sound server I use either (OSS,ALSA, etc) 

I just rebooted and I still have no sound.....

---

### Post by digilink on 2007-06-21
Nobody knows!!??? I could always call Dell I suppose, but I'm afraid they'll tell me to ship my laptop back to them and I want to avoid that if at all possible......

---

### Post by rax_m on 2007-06-21
Could it be after you've done a suspend/hibernate.. 
that's the issue I have on my laptop (but it's not a dell).

---

### Post by digilink on 2007-06-21
Unfortunately not. I have to reboot to get sound back, sometimes it doesn't come back at all. 

It's driving me crazy.....

---

### Post by Threnners on 2007-06-21
There is actually a problem with the E1505 speaker controls/headphone contact- if you plug your headphones in and wiggle the connector, usually the sound will return.

Trust me, I've got two of them and they both have the same #)$* problem.

---

### Post by DonA on 2007-07-12
Hi,

I wonder if you folks are still experiencing this issue.  I have the same problem: sound disappears.  Sometimes after a shutdown/cool-off/reboot, the sound returns for about 5 minutes, and then disappears again.  I just noticed the post suggesting to wiggle a plug connected to the headphone jack.  Never having plugged anything into the jack, I didn't think this would help.  But by golly, there is sound from the headphone!  No amount of wiggling seems to return it to the speakers, however.  

Now I suspect something is amiss with my Bluetooth setup.  I downloaded a Bluetooth Headset Manager utility; it's not currently active, but maybe it's somehow stealing the sound.

Anyway, sound still lives on my e1505; I just need to somehow get it redirected to the speakers again...

..DonA

---

### Post by DonA on 2007-07-12
When I got my E1505 a couple weeks ago, the graphics were terrible from the first power-up.  I ended up sending the unit back for repair, which as it turned out involved simply reseating the cable connector from the nVidia card to the LCD.

Now I get no sound out of my speakers, but I do have sound at the headphone.  I'm beginning to suspect another piece of intermittent hardware,  Here's what I know:
 - I've downloaded every alsa and oss utility I could find, and followed other posts to determine that nothing is muted.
- I booted a LiveCD, and it also has no sound from the speakers, but is OK at the headphone.
- On consecutive days, I've left the unit powered down while I slept, and after ~6 hours rebooted.  The Ubuntu login drums were heard, and I had speaker sound for about 3 minutes.  Then silence.

I think I may have a hairline crack in a circuit board trace or a bad speaker-to-audio-controller connection.

Does this sound logical?  Has anyone else had a similar experience?

..DonA

---

### Post by DonA on 2007-07-23
I saw on another Dell forum that the E1505 losing speaker sound (but headphone is OK) is a known hardware problem.  I contacted the hardware support folks (for Ubuntu) and arranged to send my unit in for repair.  I just received it--and the speakers work.  The note from the repair tech indicates that the system board and speakers were replaced.  So far, so good.  Hope it lasts.

..DonA

---

### Post by randys on 2007-07-23
I just received a e1505 today and yes, the sound did not work on the first boot, but on subsequent boots has been working without a hitch

---

