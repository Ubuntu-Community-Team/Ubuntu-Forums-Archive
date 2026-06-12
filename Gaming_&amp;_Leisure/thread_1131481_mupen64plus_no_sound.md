---
title: "mupen64plus no sound"
date: 2009-04-20
forum: Gaming &amp; Leisure
---

### Post by lindberg.bill on 2009-04-20
I have ubuntu 8.10 on a lattitude d510 I have mupen64plus and project64 via crossover. 

Project64: has sound, must use lowest resolution, slows down when there is a lot of action in a game.

Mupen64plus: Everything works great but, no sound.

I have heard that project64 is great in wine.  Does that mean it might be better than in crossover?  I don't think it would.  My old laptop may just not be able to handle it.
Mupen64plus seems to be great if some one can help me with sound.

Test Results
--
Error opening audio device:
-no available audio device
unable to get requested output audio format.
unable to get the requested output frequency.

---

### Post by UltimusRex on 2010-03-02
I'm having the same issue with mupen64plus... no audio. Occasionally it will randomly do some sound, but those times seem to be few and far between.

---

### Post by rflores2323 on 2010-03-03
same problem no sound for me running ubuntu 9.10.  video in mupen64plus works great but no sound at all. I have alsamixer and uninstalled pulseaudio but no sound.  everything else works ok with audio. just mupen64plus.

---

### Post by UltimusRex on 2010-03-09
No idea if this will work for anybody else, but these are the audio settings that I'm using in mupen64plus:

Volume Control: OSS mixer
Resampling: Unfiltered

Changing those seems to be all it took for mine to start working correctly.


The problem I'm still having with it -- though I got the sound to "work" -- is that the sound is delayed by like half a second. No huge deal for some games, but would be a real pain for others.

If anyone knows how to fix that, by chance... that would be great.

---

### Post by rflores2323 on 2010-03-10
are you using pulse or alsamixer??

---

### Post by UltimusRex on 2010-03-12
you'll have to excuse my ignorance... i've seen mention of "pulse" but I think i'm running SDL... To fix my SNES emulator audio issues, I used the Synaptic Package Manager to install "libsdl1.2debian-all". I don't actually know if SDL and Pulse are even related, that's how little I know about this issue.

But looking through Synaptic now, I do see that "pulseaudio" is installed.

Beyond the fact that it's installed, I don't know anything else about it. I'm a bit of a noob to Ubuntu.

However, it would appear I am using pulse over alsamixer, since there is nothing installed in Synaptic with "alsamixer" in the name, just a few things like "alsa-utils" and such.

---

