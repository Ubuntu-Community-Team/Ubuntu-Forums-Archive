---
title: "Gridwars 2 Randomly crashes"
date: 2007-08-07
forum: Gaming &amp; Leisure
---

### Post by ZeroXR on 2007-08-07
I downloaded Gridwars and the oddest thing happens with playing the game...

I will play for a bit and then when I have been in game for about 5 minutes, it crashes on me. But on running it in Terminal, It spits out this piece of output below:

appstub.linux signal handler 11

What can I do to stop the game from crashing on me?

---

### Post by ZeroXR on 2007-08-07
On google, there were some mentions saying changing ulimit may have some part to play with it. Anyone have any insight on that?

---

### Post by azanutta on 2007-09-23
got the same error
i figured out that it could be related to the graphics
try to change the game resolution, it says that the module.... something.....

---

### Post by wickstopher on 2008-02-01
Looks like this thread hasn't been answered in a while, but instead of starting a new one I hope to revive this one.  I am having the exact same problem.  I run the game from a terminal, and it crashes after a few minutes, spitting out this message:

```
appstub.linux signal handler 11
```

I'm running a good graphics card (nVidia 8600GT) using envy-installed drivers.  I also had the exact same problem on my old machine with crappy integrated graphics on the Intel mobo, and just sort of assumed it was because of the way outdated integrated graphics (the game also ran at about 1/3 normal speed).  Was hoping to solve this, as I love the game but I can't play for more than a few minutes without it crapping out on me (it doesn't happen in Panther on my G4 Powerbook...come to think of it, I have a Kubuntu partition on there and I'll try it out when I get a chance and report back, but a trackpad just doesn't cut it for this game).  Thanks!

---

### Post by wickstopher on 2008-02-04
bump?  or is it truly dead?

---

### Post by wickstopher on 2008-02-07
Well, I seem to have sort of figured out the problem.  Doing a google search for the crash message in question, nobody really appears to know why it's happening, but I found some mention of having music playing in the background.  I had my Amarok running, which seems to have been the cause of the crash.  I turned all the game sounds off (Amarok overrides them anyways), and it seemed to be fine.  So, in order for grid wars not to crash, you either have to choose between your own music or the in-game sound.  If you have music (amarok, rhythmbox, etc) playing in the background, make certain that you turn off all of the in-game sounds.  After turning off the in-game sounds, I played for about 45 minutes with Amarok running and no crashes.  If anyone has any troubles after this, please post here.

---

### Post by Diabolis on 2008-05-16
I'll just confirm this.

I got the same error message while playing gridwars and listening to music with Rhythmbox.
Setting the "sfx volume" and "music volume" values, in gridwars, to the lowest value fixed it.

---

### Post by Athanasius on 2008-10-29
Hey, I had the same problem and it seems like it is the sound.  I turned it off like you said and now the game doesn't crash.  Thanks.

---

### Post by pixnaps on 2008-11-17
Even after turning off sound and music, the game crashes for me -- yielding the same 'appstub' error -- as soon as I attempt to begin a new game with altered "video" options (e.g. smaller grid size: I want it all to fit on my screen without need for scrolling!)

At least it works when I play on the default settings, but I would really appreciate being able to fix this...

---

### Post by pixnaps on 2008-11-17
Damn, no, it turns out I get "random crashes" during the game even with default video (despite no sound, etc.)  Here's my error msg this time:
```
gridwars: ../common/dri_bufmgr_fake.c:579: dri_bufmgr_fake_contended_lock_take: Assertion `_fence_test(bufmgr_fake, block->fence)' failed.
Aborted
```

---

