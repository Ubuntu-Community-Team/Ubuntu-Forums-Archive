---
title: "Playing Ur Quan, Wesnoth= 100% CPU use, no sound"
date: 2009-11-11
forum: Gaming &amp; Leisure
---

### Post by BenM on 2009-11-11
Hi, I have a fresh install of 9.10 64 bit. Most of the time when I play Battle for Wesnoth or Ur Quan Masters, the game runs at 100 percent CPU and the sound is choppy or non-existent. The game is playable, although I can't close it and have to use the kill command. I suspect it may have to do with pulseaudio (sometimes they work OK, but never when I am using any other media), but don't know how to check that. Any help would be greatly appreciated.

Toshiba Satellite A305
4 gig 64 bit

---

### Post by Arthur_D on 2009-11-12
Hi, I got exactly the same problem as you.
I've experienced that using the command sudo alsa force-reload will temporarily make sound work again. Other than that, I have no advice but to hope for an update that solves this.

---

### Post by BenM on 2009-11-24
It's definitely a pulseaudio issue. If I kill it, the game plays normally with no big CPU usage. It kind of sucks playing without sound, but right now I'm not ready to replace pulseaudio from what I've read on the forum.

---

### Post by tatrefthekiller on 2009-11-24
Just an observation : if a game (or a program) uses 100% CPU, this is not a problem, your processor is designed to handle it.

---

### Post by Sqwishy on 2009-12-25
> **tatrefthekiller said:**
> Just an observation : if a game (or a program) uses 100% CPU, this is not a problem, your processor is designed to handle it.
If the software is using that many clock cycles when it does not or should not be using that many. It is either a bug or poor design and is a problem. This is the case with The Battle for Wesnoth.

---

### Post by zappafrank on 2010-01-07
This is probably a wrong library issue, I had that myself some time ago. But you can fix it: 

apt-get install libsdl1.2debian-pulseaudio

will replace the libsdl-alsa package with the pulseaudio one, making it work perfectly. Ubuntu should install that by default instead while they use the pulseaudio system.

---

### Post by The Spy on 2010-03-06
Both of those fixes worked on my desktop. I have no more sound glitches, Wesnoth quits properly, and my CPU usage has dropped to a reasonable amount.

But they didn't seem to work the same on my laptop. It will quit correctly and CPU usage is down, but the audio still is glitchy.

---

