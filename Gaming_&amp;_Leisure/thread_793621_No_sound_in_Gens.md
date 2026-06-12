---
title: "No sound in Gens"
date: 2008-05-13
forum: Gaming &amp; Leisure
---

### Post by drunkmatador on 2008-05-13
Just got Gens compiled on my x64 computer using dpkg to force install the 32 bit version. Works fine with the exception that there is no sound. Every time I open the emulator, sound is disabled, and when I click to enable nothing changes.

Also, looking at the terminal I opened it with, every time I change a sound setting I get this: 

ALSA lib ../../../src/pcm/pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave

What's the problem?

---

### Post by disturbedite on 2008-05-14
i'm not an expert with alsa, but my best guess (i stress guess) would be that alsa is using your soundcard for something else.  (audacity has this "issue").
try closing down anything that might be using/accessing the soundcard & try running gens again.

oh, and btw, it might be a good idea to name the package version you're using.  i.e. i use 2.13-cvs20070625~8.04.

---

### Post by drunkmatador on 2008-05-14
Well I restarted my computer, and now for some reason it only works when I uncheck the "Enable Sound" box. Weird.

---

### Post by disturbedite on 2008-05-14
heh, thats funny.  its prolly a bug.

---

### Post by jukingeo on 2008-05-29
Hello All!

I have the same problem here with Gens, however Sound Enable has NO effect at all.  I am using OSS on a Sound Blaster X-Fi.  Sound is working overall, but not in Gens.

Any assistance would be appreciated.

---

### Post by disturbedite on 2008-05-30
i don't even know if gens supports OSS.  try asking about this in the "gens package for ubuntu" thread.

---

