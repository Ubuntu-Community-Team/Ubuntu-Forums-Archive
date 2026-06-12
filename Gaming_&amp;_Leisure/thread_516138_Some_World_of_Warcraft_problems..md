---
title: "Some World of Warcraft problems."
date: 2007-08-02
forum: Gaming &amp; Leisure
---

### Post by Kujen on 2007-08-02
Okay, so WoW installed perfectly, but I'm having a couple issues.


1) Inside buildings and cities I get about 60FPS or more... the moment I step outside it drops to about 18. Playable, but not very.  (This is playing at full screen 1280x1024. When I have it windowed at 1024x768 it plays decently, and I get about 30fps outside. I'd prefer to play at 1280x1024 though.)

2) There's a tiny delay in the sound from when something happens to when I hear it. It's very minimal, but very noticable. I've tried OSS and ALSA with the same results. i've tried changing the sound buffer to many different numbers, and nothing.

Specs:

128MB NVIDIA GeForce 8300GS (Yes I have the newest drivers. I used the envy script to install nvidia drivers.)
1GB of RAM
1.8ghz core2 duo

More than enough to run the game at full settings you would think. And before someone links to it, I've used the guide posted in every other WoW thread.

---

### Post by AndrewRiedi on 2007-08-02
1) Try both OpenGL and Direct3D modes.  Go [here]("http://wiki.winehq.org/UsefulRegistryKeys") and look at the **UseGLSL** and **VideoMemorySize** keys.  Run WoW with **WINEDEBUG=-all**

2) There really is not much you can do about the sound problem except wait.  There is a developer actively working away on ALSA to bring it up to speed.

1 & 2) I hear the new kernel will have the CFS scheduler which may or may not help when it gets integrated into Ubuntu.

---

### Post by Kujen on 2007-08-02
Thanks, but unfortunately that didn't work.

---

### Post by AndrewRiedi on 2007-08-02
For comparison, what FPS do you get under Windows?  (If you have Windows.  If not, no big deal.)

---

### Post by darksidedude on 2007-08-02
hmm i didnt know that the new nvidia cards have LESS nv ram then the old ones 

( proud user of the nvidia 6200 with 256 nv ram)

anyway... did you turn off death effects and do the regestry tweak? 

[https://help.ubuntu.com/community/WorldofWarcraft#head-925a415ac06599c37e2a869e926566bb59430ceb](https://help.ubuntu.com/community/WorldofWarcraft#head-925a415ac06599c37e2a869e926566bb59430ceb)
worked like a dream for me, give it a shot

---

### Post by Kujen on 2007-08-02
Sorry I never installed windows on here, I just bought the computer. Yet to compare, I isntalled the Quake 4 demo and can run it at 1280x1024 on High settings perfectly.

And yeah I did the registry thing and turned off the effects.

---

### Post by Kujen on 2007-08-03
Any other thoughts, or am I stuck?

---

### Post by darksidedude on 2007-08-03
you could update wine? what version are you useing now?

---

