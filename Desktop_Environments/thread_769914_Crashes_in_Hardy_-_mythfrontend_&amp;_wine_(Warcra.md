---
title: "Crashes in Hardy - mythfrontend &amp; wine (Warcraft III)"
date: 2008-04-27
forum: Desktop Environments
---

### Post by soulcoughy on 2008-04-27
Hardy locks / crashes / freezes on me when I run either mythfrontend or Warcraft III (via wine).

Mythfrontend will only lock if i try to move the window while something is playing, and when it locks it takes the whole system with it.

Wine/WC3 will lock at random in a game and is usually recoverable by killing the wine process.  The game will simply freeze and I lose the mouse.  Last bit of audio from game before crash will loop.  Other processes still run fine, including sound.

These are both things that worked flawlessly in Gutsy.  Here is hardware info:

Nvidia Nforce2 (Athlon 3200+)
-onboard rtl-8169 ethernet and ac97 sound
emu10k1 soundcard
nvidia 7600 gs

I've searched this forum heavily and found several posts of people experiencing similar lockups, but all on different hardware and nobody seems to have a solution.  I'm really starting to regret upgrading.  Can anyone help?

I forgot to mention I'm running KDE3 on Kubuntu using nvidia-glx-new drivers from hardy repository.  Wine is the Gutsy version, as the Hardy version has a bug that won't let you host games in Warcraft.

Compiz is off.

Update:  Disabling "Enable OpenGL vertical sync for timing" in the playback preferences seems to fix the problem on the mythtv end.

---

