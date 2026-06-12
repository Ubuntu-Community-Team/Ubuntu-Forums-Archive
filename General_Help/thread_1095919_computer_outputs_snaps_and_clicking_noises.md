---
title: "computer outputs snaps and clicking noises"
date: 2009-03-14
forum: General Help
---

### Post by Unstablist on 2009-03-14
So I have a weird problem, my computer with ubuntu 8.10, and I'm having a problem where when I mute the computer, and then unmute it, thecomputer will only output clicks.  Now this happened earlier in the week, and I went through a bunch of tests to find the problem, but seemed to fix itself with a restart.

Unfortunately this time that doesn't seem to be helping, most annoying Is that I don't remember muting the computer in the first place, but I did un mute it last night, and since then nothing I've done has gotten the sound to work properly.  

The main factor I think is that it output clicks instead of what should be coming out, if the computer would be quiet, then the speakers are quiet, if I play music, then the clicks correspond with when sound should start playing.

thanks,
Unstablist

---

### Post by unutbu on 2009-03-14
I think this clicking problem usually is due to the "PCM" audio channel having zero volume, while the "Main" audio channel volume is turned all the way up. 

To test if this is correct, right-click on the gnome panel, and "Add to Panel" a "Volume Control" applet. An icon which looks like a speaker should appear in the panel. Right-click the speaker icon. Select "Open Volume Control". (All the above is the same as running gnome-volume-control in the terminal). 

A window should appear. In that window turn up the PCM audio channel. 
If you don't see a PCM audio channel, click the Preference button and enable it.

---

### Post by Unstablist on 2009-03-14
That did it, thanks tons!

-Unstablist

---

