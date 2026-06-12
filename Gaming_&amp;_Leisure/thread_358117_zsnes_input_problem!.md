---
title: "zsnes input problem!"
date: 2007-02-10
forum: Gaming &amp; Leisure
---

### Post by sympeltun on 2007-02-10
Every time i start zsnes this is the error i get:


ZSNES could not find any joysticks.
zsnes: pcm.c:893: snd_pcm_state: Assertion `pcm' failed.
Aborted

i dont have any joysticks, and i want to go back to the keyboard input, i tried almost every combination of commands possible to start, eg: zsnes 1 game.smc to get it to use keyboard, but it still gives the same problem


can anyone help me please?

thanks a lot
Sai

---

### Post by disturbedite on 2007-02-10
i wish i could help ya more.  but i wouldn't be sure what to do to fix it.  i guess i'd try reinstalling [zsnes]("http://www.madman2k.net/files/zsnes_1.510-0ubuntu1_i386.deb").  thats a link to madman2k's zsnes 1.51 package.  hope he doesn't mind the linking.  the reason i linked to it is cuz he only has version 1.5 listed on his site, but 1.51 is there, just not listed.

---

### Post by sympeltun on 2007-02-10
i tried reinstalling zsnes... it still didnt work :( the last thing i did in it was disable the sound since it was crackling a lot, and i'd rather have music being played through xmms, the next thing i know it just stopped working..

---

### Post by po0f on 2007-02-11
sympeltun,

What about deleting all of your settings?

```
[FONT="Courier New"]$ rm ~/.zsnes/zsnesl.cfg[/FONT]
```

This should start you off with a clean slate config.

---

### Post by sympeltun on 2007-02-11
hm, that just might work!! i installed snes9express and removed zsnes, but i prefer zsnes much better because that's what i use in windows, thanks a lot, i'm pretty sure it'll fix my problem
:D

---

### Post by honeybear on 2007-02-11
> **sympeltun said:**
> hm, that just might work!! i installed snes9express and removed zsnes, but i prefer zsnes much better because that's what i use in windows, thanks a lot, i'm pretty sure it'll fix my problem
:D

which games are you playing ?
znes is indded cool

---

