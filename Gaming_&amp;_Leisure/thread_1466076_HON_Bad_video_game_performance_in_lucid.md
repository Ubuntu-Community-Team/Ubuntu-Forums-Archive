---
title: "HON Bad video game performance in lucid"
date: 2010-04-30
forum: Gaming &amp; Leisure
---

### Post by DeusExM1 on 2010-04-30
is anyone else getting this? I tried both set of video drivers that are recommended. I also tried changing the video settings. Nothing seems to help. Its pretty choppy.

I experience a "Lag" like effect... Any ideas?

---

### Post by dvlchd3 on 2010-04-30
My AMD dedicated card in my laptop (Radieon 200M I believe) has run perfectly since 9.04 with the OSS driver in the kernel.  This includes 10.04 Beta, RC, and final.

What graphics card do you have?  When are you experiencing the "lag"? (I a game, with extra desktop effects, Compiz, etc)

---

### Post by DeusExM1 on 2010-04-30
turns out ALSA was causing bad performance. Changed it to pulseaudio i believe and now i got my performance back. Watch out newbs !

---

### Post by DeusExM1 on 2010-05-01
Okay i have been experiencing more issues and now i know why i was confused. I experience microstutter in game, which basically just made the game not look smooth. I was able to fix this by changing audio to ALSA, and playback to pulse... 

Anyway, i still have an issue, where like clockwork the game starts to lag. Every like 1 minute or 30 seconds it lags for 5 seconds and then is fine. I played nexuiz and i do believe i noticed it there too, although much less severely. Whats strange is that i had this problem before, and in my original post a few months back i fixed it by changing wireless drivers. In this case however, changing drivers for the video card or wireless card doesnt seem to help...


Any ideas? I cant play well at all when it starts to screw up randomly.

EDIT: This is strange. I fixed the problem by reinstalling the wireless drivers (3rd time). But instead of removing the old driver first, i just clicked to activate the alternative driver. For some reason it works fine now.

---

### Post by del_diablo on 2010-05-01
WHAT THE HECK IS YOUR CARD?
I thank you in advice for answering

---

### Post by DeusExM1 on 2010-05-01
i have the 8600M GT. And if i play offline then i dont get the lag spikes (well i did, but changing audio settings fixed that). So i figured it was a wireless problem.

---

