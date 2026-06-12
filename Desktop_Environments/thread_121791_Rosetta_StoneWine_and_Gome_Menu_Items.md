---
title: "Rosetta Stone/Wine and Gome Menu Items"
date: 2006-01-25
forum: Desktop Environments
---

### Post by Supaiku on 2006-01-25
I spent all this time making a nice menu icon for Rosetta Stone (after finally getting it to work (in wine) and now when I run it from the short cut it won't work!

In the console it works fine (ish... there are tons of fixme errors but the program runs) but when I click on the gnome menu Icon there's no sound! No Rosetta Stone error messages, just no sound. Is there any way to fix or at least debug this somehow? I guess I could check my log eh? Know where I'd fine this log info?

____________________________
Also, if anyone happens to know [were to go/howto] off the top of their head: How do I get xmms AND Rosetta/wine to play at the same time? I remember when I using gentoo I had to do all this wacky stuff with dmx or something to get two programs to play at once but I hoping it's differnt w/ ubuntu. 

wine is set to use hardware acceleration emulation ie. "Emulation=Hardware Acceleration" or mayeb it's the other way around in the dsound seciton of wine's config, afaik this is necissary for rosetta stone. 
when rosetta is running and:
xmms is set to use alsa it says: Failed to open audio output: ALSA 1.2.10 output plugin
xmms is set to use oss it says :roughtly the same thing only with the OSS pluing instead of ALSA
xmms is set to use esound it acts like it's playing the sound file really fast only there's no sound.

xmms doesn't work with vlc either:p
________________________________
I can find the answer to the second quesiton on my own if no one knows real quick like.

---

### Post by BSmucks on 2008-01-15
I just started using ubuntu yesterday and I'm getting the same problem, I think it has to be something with the rosetta stone program itself because it would do the same thing to me on windows xp, but it only did this if I opened rosetta stone before putting in the CD or if the CD was already in but didn't autorun, when I'd put the disc in and let it automatically start rosetta stone it would work fine.

I haven't been able to autorun the program by inserting the disc on ubuntu, not even sure if it's possible.

---

