---
title: "Dell Dimension 1100: Just scrubbed XP and installed Jaunty, but can't get sound."
date: 2009-04-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by nogoodreason on 2009-04-27
I'm fixing up my girlfriend's old Dell Dimension 1100, so have added some RAM and scrubbed Windows entirely.  Jaunty installed without a hitch and all is going good, however I can't seem to get any audio. :S

Are there any generic audio drivers out there I should try?

_More info_:
I'm sure I heard some African drums being played during startup when I first booted the machine up, but since then there's no sound at all, and trying to play a movie/audio file causes the program to close itself as soon as it opens.

I found a file online called Realtek-linux-audiopack-5.01 which I tried installing, but still nothing.  I'm not sure what soundcard is *in* this machine, it may not even be a Realtek.  I believe the Dimension 1100 was released before Dell started shipping with Ubuntu.

---

### Post by ukblacknight on 2009-04-27
Sup Dan :D

First off, this might sound crazy, but if you go the volume control and look for "PCM" - make sure it is turned up.

Right click volume control -> Open Volume Control

For some reason for me, it keeps muting itself and thus me thinking that my sound is no longer working.

---

### Post by nogoodreason on 2009-04-27
Sorted. :)

I'd already been into volume settings and cranked everything up to maximum, but didn't realise that clicking on the 'not working' icon actually enabled it again.

Dunno why it had muted itself in the first place, but I'll keep an eye to see if it does it again.

Thanks for your help.

---

### Post by putz3000 on 2009-04-27
> **ukblacknight said:**
> Sup Dan :D

First off, this might sound crazy, but if you go the volume control and look for "PCM" - make sure it is turned up.

Right click volume control -> Open Volume Control


I have a Dell XPS M1530 and this volume issue has been going on for at least the last 1 or 2 versions of Ubuntu.  This time (9.0.4) it seemed to be even worse then before.  It was to the point that using my linux partition was virtually pointless.  But I saw your comment regarding PCM and I pushed the sliders all the way up and got sound at least as good as under 8.10.  So then I decided to push the slider for "front" all the way up and wouldn't you know it, sweet volume was pumping out of my speakers.  I did not need head phones to hear and I actually had a need to turn down the volume.  So if you are one of the poor Dell users, try both the "PCM" and "Front", you may be pleasantly surprised.

---

