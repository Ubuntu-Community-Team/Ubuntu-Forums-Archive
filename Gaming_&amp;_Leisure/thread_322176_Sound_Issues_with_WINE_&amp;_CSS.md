---
title: "Sound Issues with WINE &amp; CS:S"
date: 2006-12-20
forum: Gaming &amp; Leisure
---

### Post by willskills on 2006-12-20
Hi folks,

I'm at work at the moment, so I can't append any logs or anything (not that I really know what I'm looking for) but, I am having some problems with sound in CS:S.

My soundcard works correctly with XMMS etc (all ALSA) AND my sound works in World of Warcraft (using OSS in winecfg).

This is why I'm stumped, as my sound doesn't seem to work with CS:S. The sound is turned on in CS:S, I just get nothing through the speakers.

Anyone have any ideas as to what I should be looking at?

Any help would be greatly appreciated!

I am in IRC @ irc.freenode.net #ubuntu, when I get home from work about 6pm GMT.

---

### Post by willskills on 2006-12-21
Just an update on this.

It seems that I have no problems running WoW like so;

aoss wine ~/WoW.exe -OpenGL (and sound works great - including GAIM etc while I play WoW)

Unfortunately, the only way I can get my sound to work in CS:S though, is to do a "killall esd" and run CS:S like this;

wine ~/Steam.exe - sound works fine with OSS, it just means I get no sound from GAIM/IRC/etc......

Seems a little bit strange, if anyone has any ideas.... grab me in IRC! :mrgreen:

---

