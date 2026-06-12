---
title: "where, oh where, did my sound go?"
date: 2009-05-14
forum: General Help
---

### Post by adamspurgin on 2009-05-14
so, i just downloaded VLC media player and was using it for a bit. a little while later i tried youtube and there was no sound. i thought "no big deal, i don't youtube much anyways" but then i went back to VLC and it stopped working also.

so now i have reason to get worried.

a quick check revealed that ***all*** sound has stopped working, not a peep. here's some info that might help out a bit

i'm using a **dell xps m1530 laptop**
i'm running **8.10**
**yes,** my system is recognizing my sound card
**no,** my volume is not muted
**yes,** my speakers are plugged in
**yes,** i have checked alsamixer and according to it, everything is fine
**no,** i am not getting sound out of anything, speakers, 3.5mm jacks, hdmi, nothing. not even static

any help would be apreciated, i don't want to have to do a system restore again.

---

### Post by alexandari on 2009-05-14
uh...how about running 
```
alsamixer
```
and checking out the "volumes" of the sound devices?

---

### Post by adamspurgin on 2009-05-14
> **alexandari said:**
> uh...how about running 
```
alsamixer
```and checking out the "volumes" of the sound devices?

> **adamspurgin said:**
> 
**yes,** i have checked alsamixer and according to it, everything is fine

tried that. it was all good, except for the fact that i have no sound..

---

### Post by adamspurgin on 2009-05-14
bump

---

### Post by Carl Hamlin on 2009-05-14
Have you tried swapping everything over to PulseAudio?

---

### Post by adamspurgin on 2009-05-14
no, i haven't. would you mind filling me in?

---

### Post by Carl Hamlin on 2009-05-14
> **adamspurgin said:**
> no, i haven't. would you mind filling me in?

You betcha. Go to System > Preferences > Sound, and swap your playback preferences away from Alsa in favor of Pulse Audio. I've had all sorts of trouble with Alsa, but Pulse Audio fixed all my sound issues, and activated my onboard microphone.

---

### Post by adamspurgin on 2009-05-14
ah, thank you very much, that solved all of my problems. 

:KSX 100

---

### Post by Carl Hamlin on 2009-05-14
> **adamspurgin said:**
> ah, thank you very much, that solved all of my problems. 

:KSX 100

Most excellent.

---

