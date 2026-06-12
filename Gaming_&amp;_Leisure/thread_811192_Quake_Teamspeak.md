---
title: "Quake Teamspeak"
date: 2008-05-28
forum: Gaming &amp; Leisure
---

### Post by Bnosidda on 2008-05-28
Whenever I have teamspeak running AND quake wars it cancels out all sound and doesn't seem compatible with it, it doesn't even respond to it, I can log on to a channel for that server but apparently the game doesn't pick it up, and I'm guessing either it overrides the quake sound or linux sets that as the only program the lets audio in or out any help?

---

### Post by doorknob60 on 2008-05-28
Teamspeak uses OSS, which unfortuanetly doesn't support sound mixing.```
sudo apt-get install alsa-oss
```
Then launch Teamspeak with this command:
```
aoss teamspeak
```

Note that using aoss may decrease audio quality in Teamspeak (I use it with Runescape with no noticable difference though, never tried with TS), but there's not much else you can do until there's ALSA support in Teamspeak (which I think is planned for the next version/0.

---

### Post by brento73 on 2008-05-29
Since I'm having a similar issue with EverQuest II, I tried running 'aoss teamspeak' and the sound was so garbled that is was unusable. For me, at least, I'm still without sound in-game if I want to use TS.

---

### Post by Bnosidda on 2008-05-30
> **doorknob60 said:**
> Teamspeak uses OSS, which unfortuanetly doesn't support sound mixing.```
sudo apt-get install alsa-oss
```
Then launch Teamspeak with this command:
```
aoss teamspeak
```

Note that using aoss may decrease audio quality in Teamspeak (I use it with Runescape with no noticable difference though, never tried with TS), but there's not much else you can do until there's ALSA support in Teamspeak (which I think is planned for the next version/0.

I tried that but it returned this error 
ERROR: ld.so: object '/usr/$LIB/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.
and then started teamspeak and still did not work

---

### Post by Bnosidda on 2008-06-01
Bump

---

