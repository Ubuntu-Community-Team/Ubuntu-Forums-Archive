---
title: "Weird sound issue"
date: 2006-03-31
forum: Desktop Environments
---

### Post by IndigoMontoya on 2006-03-31
I have a wierd issue.  I like to listen to online musci via Pandora.  It uses Flash to play stuff through firefox.  I have no problems setting it up, but after sometime (seems sometimes to be as little as 5 songs, and others hours and hours, my sound just stops.  I cant get audio through anything.  To boot, when I try to play an audio cd, the cd gets no sound as well but the counter goes really fast.  A reboot fixes this, but anyone have an idea of either A) what is going on, B) an easier way to restart the sound without rebooting or C) how to prevent it form happening all together?

Thanks

---

### Post by IndigoMontoya on 2006-04-14
The problem has not gone away, but for anyone having a similar problem (or know why this happened), it turned out acroread was trying to use /dev/dsp.  I killed acroread and everything worked fine.

I don't know if it will always be acroread that causes it.  So far I have fixed it once with this method, but I used ```
 lsof | grep /dev/dsp 
``` to find what was still using it, and I killed it.  For me it was acroread.

---

### Post by Bionic_Beefpile on 2007-04-12
I have a similar problem with Pandora, actually.  As for you, my sound cuts out, but my issue may be different, as simply refreshing the Pandora page gives me sound again.
It seems to be tied to opening Document Viewer (for PDFs) or emacs.

I tried running the command you list, and didn't get anything, however...

---

### Post by ComplexNumber on 2007-04-12
dsp is the device which allows you to use more than 1 device at a time (i believe).

i recently had the issue with the sound going fast and skipping seconds when playing cds. it turned out that my sound card was loose. after a while, it gave up completely. i took the sound card out, put it back in, and problem solved. but usually things like that is a hardware problem.

---

### Post by Bionic_Beefpile on 2007-04-17
Hmmm... I kind of doubt it's a hardware problem, because listening to other sources of audio doesn't lead to the same symptoms.  I feel like it's something with flash player, but there's not much we can do to check that out ;)

---

