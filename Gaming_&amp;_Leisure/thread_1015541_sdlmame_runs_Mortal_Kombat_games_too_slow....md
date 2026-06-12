---
title: "sdlmame runs Mortal Kombat games too slow..."
date: 2008-12-18
forum: Gaming &amp; Leisure
---

### Post by Moonfrost on 2008-12-18
Hi, I'm using sdlmame 0.128 (NOT u1 or u3) and I have Kubuntu 8.10 with KDE 4.1.3. my specs are:

AMD Athlon 64 3500+ (2.2 ghz rated at 3.50)
1.5gb Ram
Nvidia 6150LE (integrated graphics)

I always ran Mortal Kombat 1, 2 and 3 (including Ultimate MK3) at full speed on Windows even when I had only 512ram (back then!) and also on older versions of mame on Linux. But now all MK games run pretty slowly while most other games run at full speed and sound perfect, were the MK games broken in this release? because I knew already that Ultimate Mortal Kombat 3 was broken in this release somehow but I didn't know the others were too.

Anybody know what might be the problem? am I the only one with this problem? my specs should be able to run these games perfectly.

---

### Post by wingnux on 2008-12-18
You might want to edit the mame.ini file and set it to use opengl as default renderer.

---

### Post by Moonfrost on 2008-12-18
> **wingnux said:**
> You might want to edit the mame.ini file and set it to use opengl as default renderer.

I'll try and see, because I've tried 0.123 from the repos and the MK games run perfectly at full speed.

---

### Post by Dan_Dranath999 on 2008-12-29
running latest 0128u7...

All games are slow.
The sound is choppy.

--edited the mame.ini file and everything is normal now: Video plays at normal speed, and the sound is fine (but i just changed video from "soft" to "opengl", as seen below)

```
# VIDEO OPTIONS
#
#video                     soft #changed this line to comment---
video			  opengl
```

---

### Post by Moonfrost on 2008-12-29
> **Dan_Dranath999 said:**
> running latest 0128u7...

All games are slow.
The sound is choppy.

Well only the MK games for me (so far) but it's still awful considering 0.123 from the repos runs beautifully.

---

### Post by Dan_Dranath999 on 2008-12-29
MK 2 runs fine now (see my previous -**and edited**- post) but the sound is corrupted...


-had to change a lot of ROM names from UPPERCASE to lowercase: today i remembered **Linux is case-sensitive and windows is not**. I almost deleted 200 games, thinking for sure that they were corrupted.

ANYWAY some games that used to run in Windows mame, ask me for some "missing ROM or CHD images"... as Marvel vs Capcom: Clash of Superheroes (that used to work fine!)

---

### Post by Moonfrost on 2008-12-29
> **Dan_Dranath999 said:**
> MK 2 runs fine now (see my previous -**and edited**- post) but the sound is corrupted...


-had to change a lot of ROM names from UPPERCASE to lowercase: today i remembered **Linux is case-sensitive and windows is not**. I almost deleted 200 games, thinking for sure that they were corrupted.

ANYWAY some games that used to run in Windows mame, ask me for some "missing ROM or CHD images"... as Marvel vs Capcom: Clash of Superheroes (that used to work fine!)

I know! and that something I tried on Windows too with mame 0.128u7 and it's the same, instead of fixing games or getting better they break with each release...I guess I'll stick to 0.123 for now.

---

### Post by BigSilly on 2008-12-29
The Mame team break as much as they fix with each release. I'm sticking with my 0.120 set for now. I kept a .deb of SDLMame 0.120 if anyone wants me to post it up (if I am allowed). The MK games all work fine for me.

---

### Post by Moonfrost on 2008-12-29
> **BigSilly said:**
> The Mame team break as much as they fix with each release. I'm sticking with my 0.120 set for now. I kept a .deb of SDLMame 0.120 if anyone wants me to post it up (if I am allowed). The MK games all work fine for me.

Oh yeah, that would be great because 0.123 actually doesn't play UMK3 for some reason, just MK3 so yeah. I play a lot of games but the MK games are very important to me!

---

### Post by hikaricore on 2008-12-30
Please keep the discussion of how many roms you have out of this thread.

I'd much rather not have to close it. :)

---

### Post by Moonfrost on 2008-12-30
> **hikaricore said:**
> Please keep the discussion of how many roms you have out of this thread.

I'd much rather not have to close it. :)

Sure, sorry about that.

---

