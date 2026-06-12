---
title: "No Sound in Games"
date: 2005-10-28
forum: Gaming &amp; Leisure
---

### Post by Gaming_Junkie on 2005-10-28
Sound works great on Rhythmbox, and system sounds. However, if I try to play UT 2004, Doom 3 or any game for that matter there is no sound.  Also, no sound when I play movies.

Strange thing with Doom 3 though -- I can get the sound to work by:  First, when I load it, the Sound Backend has to be set at OSS.  Then, immediately after I change it to ALSA, it works perfectly.  But, then I exit, and restart it (set on ALSA) and the sound does not work.

      My sound settings are at output=ESD and input=OSS as of now.

      How do I get sound to work correctly in my games and other applications as well?

---

### Post by Abild on 2005-10-28
Try running "killall esd" prior to starting a game and see if you get sound then.
When you're done with playing the game you can get system sounds again by running "esd"

---

### Post by Gaming_Junkie on 2005-10-28
Thanks for that helpful tip.

After trying that, I actually switched my sound multimedia selector to ESD and OSS respectively.  Sound seems to work on both my games and my other applications now.

The only problem is that UT 2004 still has no sound.

---

