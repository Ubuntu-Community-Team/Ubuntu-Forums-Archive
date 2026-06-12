---
title: "Cedega Sound problem"
date: 2007-03-26
forum: Gaming &amp; Leisure
---

### Post by tommy1987 on 2007-03-26
I have Cedega 5.2.3 and am primarily playing Battlefield 2: Special Forces HOWEVER...

When running the system test for sound ALSA passes BUT OSS does not!

I can't seem to get sound in Battlefield whatsoever, but have had it in the past (Only considerable change I can think of is that I now use KDE where I used to use GNOME, could that be it?).

The details of my kit is integrated sound card on my motherboard(ECS NFORCE3-A939 SKT939 nforce3 250 AGP SATA 6channel audio).

I sure hope someone can shed some light on this, since its baffling the hell out of me

---

### Post by frodon on 2007-03-26
The problem with OSS is that it don't support software sound mixing, that mean that only one apps can use the sound card at the same time.
For example when you have a music player opened then the game won't able to use the card with the OSS driver therefore no sound in game. The solution is just to close your music player in this case.
In a more general way type this command to know which apps is using (understand blocking) your sound card : ```
lsof /dev/dsp
```

---

