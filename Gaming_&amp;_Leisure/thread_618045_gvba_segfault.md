---
title: "gvba segfault"
date: 2007-11-20
forum: Gaming &amp; Leisure
---

### Post by djuniah on 2007-11-20
I just installed visualboyadvance-gtk using apt-get and it loads up fine and i can use all the menus, but as soon as i load a game, it gives a segmentation fault.  Does anyone know why this is?

I was using vbaexpress before, but it did not give the option to throttle the game to 100% and it was running exceedingly fast.  And it is kinda important to not have the game run at 150-200% speed.

I'm still having some sound issues (VERY poor quality even at the highest settings).  I assume this has something to do with the syncing of the audio and video and that i will have more luck once i get the throttling issue sorted out.

But my main problem right now is that pesky segfault. Any idea why a package straight from the repo would have that issue?

---

### Post by djuniah on 2007-11-20
Scratch that. I tried mednafen instead and its working a TON better.
Heres the exact command that i use to launch the games.  It uses hq2x filtering and 2x scaling.

```
mednafen -gb.special hq2x -gb.xscale 2 -gb.yscale 2
```

---

### Post by Sockerdrickan on 2007-11-20
Also feel free to try my emulator.

---

### Post by djuniah on 2007-11-20
Oh, looks nice!  I'll give it a shot.  Thanks

---

### Post by djuniah on 2007-11-20
Tried the precompiled one, but kept getting this error:
bash: /usr/local/bin/TuxBoy: cannot execute binary file

(i had run the install script before trying it)

---

### Post by Sockerdrickan on 2007-11-20
Please note that the only available pre compiled version is 64bit, x86_64 "[Linux X86_64]"

---

### Post by djuniah on 2007-11-20
yea, my apologies, that could be why ;)

Although, with the source code, there is no config or make file.  How should i compile this?

---

### Post by Sockerdrickan on 2007-11-21
There is indeed a makefile, just type make

---

