---
title: "FFVIII freezes in PCSX-R"
date: 2011-10-28
forum: Emulators
---

### Post by jswhite on 2011-10-28
So I decided to give FFVIII another whirl after recently installing Oneiric. I had previously been using pSX, which is awesome, but apparently does not work on Oneiric. So, I decided to give PCSX-R a try and downloaded it from the repos.

Final Fantasy 8 appears to work OK, at least until the first time I try going into battle. As soon as I hit a random encounter, the game freezes up. The music properly switches to the battle music, but the graphics freeze and I can't hear any battle effects (like the cursor moving or me getting hit). I've tried changing graphics plugins, enabling/disabling various game fixes, fighting in different places, etc. Nothing works. Every time I hit a battle, it totally locks up.

Anybody have a fix? Or, even better, a way to get pSX working on Oneiric, because it's awesome and I REALLY don't like PCSX-R?

---

### Post by jswhite on 2011-11-04
I can only conclude that I'm the last person still playing Final Fantasy 8.

---

### Post by caligula2 on 2011-11-23
I'm also having the same problem, except i can't even save on the memory cards.

---

### Post by caligula2 on 2011-11-23
I spoke too soon. It turns out that PCSX uses its own BIOS. You should change the BIOS to SCPH7003.bin, which you would have to download on your own. This should fix the problems (both the combat freeze and the saving).

---

### Post by jswhite on 2012-01-03
> **caligula2 said:**
> I spoke too soon. It turns out that PCSX uses its own BIOS. You should change the BIOS to SCPH7003.bin, which you would have to download on your own. This should fix the problems (both the combat freeze and the saving).

That did it. I thought I'd cycled through all of the possible BIOS files, but I left that one out. Switching to 7003 fixed it. Thanks!

---

