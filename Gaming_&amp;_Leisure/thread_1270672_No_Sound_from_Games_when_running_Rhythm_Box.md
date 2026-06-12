---
title: "No Sound from Games when running Rhythm Box"
date: 2009-09-19
forum: Gaming &amp; Leisure
---

### Post by NovaWasp on 2009-09-19
Oi, guys.  I'm on Ubuntu 9.04, and when I try to run a couple of games like Typhoon 2001 or Astromance I can't get sound from the game when running some sort of Media Player.  I normally run Rhythm Box.  There are other games where it's not an issue like Neverball.  This isn't an end of the world issue, but it'd be nice to straighten it out.

thanks,

---

### Post by RedSingularity on 2009-09-19
Do you have pulseaudio installed?

---

### Post by KIAaze on 2009-09-19
If you have pulseaudio, try running the game with padsp:
```
padsp GAMECOMMAND
```
Worked for me with aplay and festival recently, where I had the same problem when media players were running.

---

### Post by NovaWasp on 2009-09-20
Thanks, 

padsp was the key.

padsp ./typhoon 

and sound is back in the game.

---

