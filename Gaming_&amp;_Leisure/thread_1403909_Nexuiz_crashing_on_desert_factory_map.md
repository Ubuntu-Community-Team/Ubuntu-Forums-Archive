---
title: "Nexuiz crashing on desert factory map"
date: 2010-02-10
forum: Gaming &amp; Leisure
---

### Post by Eirinjas on 2010-02-10
Nexuiz runs fine in the singleplayer mode until level 4: desert factory.  It might actually load 1 out of every 20 times I try to run it.  The map crashes when loading and gives me this error:

nexuiz-linux-686-sdl: radeon_dma.c:210: radeonRefillCurrentDmaRegion: Assertion `dma_bo->bo->cref == 1' failed.
Aborted



Any ideas?

---

### Post by Eirinjas on 2010-02-10
Okay, so I was trying to load the map for the umpteenth hundred time, playing with the in-game settings to see if anything would work, and now my video card is borked.  Everything is fine except for some artifacting.  What's weird is that it's not affecting videos.  When videos are playing - they look fine.  I took the card out to try it in my other system and the display was fine at bootup.  I pop it back into place in this system and it looks fine at bootup.  Get into Ubuntu and it looks fine.  A few minutes later the artifacting returns.  Is there a way to reset the x server so that it'll test and reconfigure the video display?

---

### Post by MadCatmkII on 2010-03-26
Hello

I'm having the exact same problem with desert factory not loading and I get the same error message. Have you had any luck?

---

