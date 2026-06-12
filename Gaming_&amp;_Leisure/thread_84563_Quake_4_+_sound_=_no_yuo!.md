---
title: "Quake 4 + sound = no yuo!"
date: 2005-10-31
forum: Gaming &amp; Leisure
---

### Post by hanover.fiste on 2005-10-31
Running breezy, got Q4 installed without problems, found a fix for the segfault I was having, but now I can't get sound working. Funnily (or not so funnily) sound works with doom 3 and all my other games. It's only Q4 I can't get it going on. All I get is:

```

-------- Initializing Sound System ----------
sound system initialized.
---------------------------------------------
--------------- R_InitOpenGL ----------------
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
8/8/8/8 RGBA bits, 24 depth bits, 8 stencil bits
dlopen(libasound.so.2)
asoundlib version: 1.0.9
Alsa is available
------ Alsa Sound Initialization -----
opened Alsa PCM device surround51 for playback
snd_pcm_hw_params failed: Cannot allocate memory
close pcm
dlclose
WARNING: sound subsystem disabled

```

I've tried upgrading/downgrading alsa, SDL, openal, changing the alsa device for playback, and various combinations, but no luck. Anyone else run into this and find a fix? OSS doesn't work either, so I'm starting to think there's something weird with Quake 4 and the emu10k1 driver.

---

### Post by evilghost on 2005-10-31
No issues here, and I'm emu10k1.  Of course, I'm still Hoary, so not sure if that matters.  What's lsmod give you?

---

### Post by Kirzzy_Boy on 2005-11-01
At first I had a similar problem then I used the following in the command line:
```
quake4 +set s_driver oss
```

but then I went hunting after the game started crashing with sound overflows. I posted my solution in the HOWTO forum [here]("http://ubuntuforums.org/showthread.php?t=84891")....
 Hope this helps....

---

### Post by hanover.fiste on 2005-11-02
[QUOTE=Kirzzy_Boy]At first I had a similar problem then I used the following in the command line:
```
quake4 +set s_driver oss
```

but then I went hunting after the game started crashing with sound overflows. I posted my solution in the HOWTO forum [here]("http://ubuntuforums.org/showthread.php?t=84891")....
 Hope this helps....[/QUOTE]

Thanks, but you missed an important point; namely that sound in Doom3 works. Since Quake 4 uses the same engine as Doom 3 (and Doom 3 is still working), there must be something screwy in the Q4 setup. That's what I'm trying to nail down. I'm also looking for anyone else having this problem, since ID won't look at a bug unless it affects multiple systems.

---

