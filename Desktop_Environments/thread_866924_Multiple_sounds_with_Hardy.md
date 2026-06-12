---
title: "Multiple sounds with Hardy"
date: 2008-07-22
forum: Desktop Environments
---

### Post by monnick on 2008-07-22
Im using Ubuntu 8.04 since a couple of months and I'm very very happy with it. Not everything works out of the box but I've managed to setup everything.

Except for one thing which is annoying me all the time. I can't have multiple sounds at the same time. For instance, when I'm listening music and I start Americas Army then I don't have any sound in AA. When I shutdown AA and then shutdown my audioplayer (Rhythmbox) and then restart AA, then I have sound.

But what I can do is listening music and watching a flash movie (with Firefox 3.0) on the same time. So this problem does not always appear.

with lspci in the terminal I found out that I have the following soundcard:

```
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
```

But then, I dont know what soundserver to use: ALSA, PulseAudio or OSS?? :confused:

I dont know 100% for sure but I think I've tried them all, and all of them have the same problem: I cant play multiple sounds at the same time.

Does anyone know what soundserver I should use and how I can fix that I can listen to music and play a game at the same time? :D

thanks in advance!

---

### Post by SunnyRabbiera on 2008-07-22
Multiple sound has always a little issue on linux, mainly because of the interation between the kernel and the soundcard.
The issue mainly comes from both ends of the fence, linux's sound is produced a little oddly and most soundcards like windows only.
I suggest trying out Alsa, alsa has come a long way in this sort of thing so it may work.

---

### Post by monnick on 2008-07-22
> **SunnyRabbiera said:**
> Multiple sound has always a little issue on linux, mainly because of the interation between the kernel and the soundcard.
The issue mainly comes from both ends of the fence, linux's sound is produced a little oddly and most soundcards like windows only.
I suggest trying out Alsa, alsa has come a long way in this sort of thing so it may work.
Im now using ALSA, and even after a reboot, still the same problem. :(

---

