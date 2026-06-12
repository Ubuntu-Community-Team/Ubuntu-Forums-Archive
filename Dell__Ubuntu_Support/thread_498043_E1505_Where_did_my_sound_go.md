---
title: "E1505: Where did my sound go?"
date: 2007-07-10
forum: Dell  Ubuntu Support
---

### Post by DonA on 2007-07-10
Well, I've just been enjoying the pogies out of my E1505N (Dell preloaded Feisty) for almost 2 weeks now.  But just this evening I noticed that the sound had stopped. The front panel buttons still seem to work, and I have the volume turned up.  Nothing appears to have changed in System=>Preferences=>Sound, and the Volume Control stuff seems normal.  It doesn't indicate that it's muted, but there's just no sound out of the speakers.

I've tried Restarting, and Shutdown/Reboot, but the sound is gone--not even the Ubuntu start-up.

Any clues?

Thanks:   ..DonA

---

### Post by Paul S on 2007-07-10
no problem here on my e1505 using kubuntu.  you can cross check the volume settings by opening a terminal and typing "alsamixer", which will allow you to see the actual volume levels and whether anything is mutes (see man:alsamixer for info).

One of the multimedia buttons on the front of my e1505(not n) can mute/unmute sound.  check that too.

if none of that helps, you can reboot and run the dell diagnostics and do a hardware check.

HTH,

---

### Post by Darkcloud on 2007-07-10
just had the same problem on a friends laptop  turned out it was the audio mixer in the music player Kaffeine  that for some reason was turned all the way down   turned it up and success! 
This is with gxine installed as well as alot of addons I had configured for her so she could watch movies and so forth it doesn't appear as if default app has the mixer/equalizer until you install the addons  but maybe look around  and see if you have something of that type in one of the apps  in Applications>Sound and Video

---

### Post by DonA on 2007-07-11
After letting the laptop sit powered down for the evening, this morning on boot-up, the sound is back.  This is a bit puzzling, as the previous power-down-reboot didn't have this effect.  Thanks for the hint about alsamixer; I'll keep that in mind if/when the sound disappears again.

Thanks!    ..DonA

---

### Post by DonA on 2007-07-11
It did it again.  No sound, but all of the sound utilities appear normal.  I think vmplayer may be involved.  I have a virtual WinXP defined, and while I was shutting it down, a window popped up indicating something like "/dev/dsp busy or unavailable."  (I'm pretty sure I saw that same popup earlier when the sound went away.)  Any idea how to bring sound back after getting such a message from /dev/dsp ?

Thanks again:   ..DonA

---

### Post by Darkcloud on 2007-07-11
thats actually part of sound capabilities according to what I read   check this other forum thread out [http://ubuntuforums.org/showthread.php?t=341846]("http://ubuntuforums.org/showthread.php?t=341846") and if that doesn't help  keep looking   I am too  finding some solutions to sound issues has sort of become a thing for me   not that I need it I have yet to have any sound problems on any machine I have installed Linux on   just a compulsion thing

---

