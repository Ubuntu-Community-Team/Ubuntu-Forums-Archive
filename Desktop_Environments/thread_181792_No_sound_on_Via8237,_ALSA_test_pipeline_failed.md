---
title: "No sound on Via8237, ALSA test pipeline failed ?"
date: 2006-05-24
forum: Desktop Environments
---

### Post by phyre-x on 2006-05-24
I've not had sound from ubuntu on my laptop yet it has found the harware and correctly identified it as VIA8237, i've installed alsa fresh with the correct modules, unmuted everything and checked everything twice. when i go to the system>prefs>multimedia Systems selector ALSA is selected as both (recommended i hear) but when i press test on Default source i get the error

"Failed to contruct test pipeline for 'ALSA - Advnaced linux sound architecture"

i've also noticed that in the devices there are 2 playback and 2 capture devices under the via8237 branch. Each is called the same "VIA 8237 ALSA Playback device and everythings the same under advanced except that alsa.device is 0 on the first and 1 on the second. So i thought that might have something to do with it and proceeded to edit my asound.conf from 0,0 to 0,1 and now when i go to multimedia systems selector and test the output i can hear this crazy beep noise thing which im presuming is correct so my question is

How Do i Fix the Alsa Source so it works ? 

im just looking for some advice and maybe a pointer in the right direction as i love my sound and would really like to get this working properly.

Cheers, Phyre-x

---

