---
title: "Quake3 multiplayer hangs, but not single player"
date: 2006-03-04
forum: Gaming &amp; Leisure
---

### Post by Dhar on 2006-03-04
Ok, so I dug out my Quake3 to play against my wife...a big Quake3 fan.  It worked great with Gentoo, so it should work even better with Ubuntu -- after all, everything else seems to, right?  Oops, no...

First I had the sound problem.  That and two sound cards.  So I managed to fix that with the snddevice "/dev/dsp1" and the echo "blah blah disabled" fixes.  Sound is great, single player is great.  I can even play my personal crack -- Enemy Territory just fine! \\:D/ 

But if I try to start a Quake3 multiplayer game, either starting a server or joining someone else's, the game hangs on the first frame of graphics.  I can switch to a virtual terminal to kill it, so it's not a hard hang.  Quake3 doesn't report anything wrong on the console -- in fact, the last thing it reports is "Dhar^7 entered the game".  This is a Total Bummer (tm).  

I tried the Icculus binary, but that doesn't have sound -- I can't even fix that with the fixes I listed earlier, so that's a non-starter.

It's not my driver (nvidia): I can run in single player mode fine.
It's not my network: I can play Enemy Territory until my wife kills me.
It's not sound: I already tackled that one.
It's not hardware of any kind: this worked on Gentoo!

Anyone have any ideas at all?  :confused:   This is close to an Ubuntu-breaker for me, and I'm not overly fond of the "takes a week to install KDE" days of Gentoo, but if I must...

Thanks!

-g.

---

### Post by sorcererx84 on 2006-03-04
I have the same problem. I think it is related to sound because if I start Q3 without sound, it works fine. But q3dm0 works even with sound.

---

### Post by deathbyswiftwind on 2006-03-09
hey have you tried the open source version? works much better heres a guide on everything and a link for the open source
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Quake3](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Quake3)

---

