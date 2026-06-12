---
title: "ZynAddSubFX sound quality through Jack..."
date: 2006-09-15
forum: Desktop Environments
---

### Post by Jockster on 2006-09-15
Hello all, first post here from a relatively new Ubuntu user. Must say that I have been gobsmacked how much I've enjoyed using it, so much so that I haven't logged into Windows for several weeks! 

Anyway, to the point of my post. I would love to be able to get a midi setup working in Ubuntu, and I am almost there. I have been able to get my midi keyboard working with Jack, such that it can feed into the Muse midi sequencer, which then talks to ZynAddSubFX and Hydrogen. I have even managed to compile and run the real-time kernel to get as low a latency as possible.

My problem, however, is the sound quality with ZynAddSubFX and Hydrogen when I run them via the Jack server and Alsa (using the QJackCtl front end). The sound is perfect when I use OSS, whether directly or through Jack, but all crackly when I go via Jack and Alsa, no matter which of the many different setting combinations I use in Jack. Note that I get great latency whatever method I use - it's the quality that's the issue.

I was wondering whether anyone has experienced this, and has a solution to the problem or any Jack/Alsa tips? Is it simply that I need a better sound card if I want to use Jack/Alsa? The sound card I have is on the motherboard (Realtek ALC or something...), which I suspect is rather, well, crappy. But then again, the sound is perfect using OSS, so is the issue with the Ubuntu sound configuration somewhere?

Fingers crossed I can get this one sorted, as midi sequencing is one of the reasons I will otherwise need to resort to logging into Windows......

Thanks in advance...
Jockster.

---

### Post by Jockster on 2007-03-18
Thought I'd better answer my own post... I got a better sound card - A Soundblaster Audigy 2. And everything runs fine now. So I guess the problem was my rubbish on-board soundcard!

Oh, and see that ZynAddSubFX? What a blimmin' awesome soft synth :)    If only we had more like this on Linux....

---

