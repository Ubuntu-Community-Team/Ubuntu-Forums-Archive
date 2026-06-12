---
title: "Need help with sound"
date: 2006-01-02
forum: General Help
---

### Post by whiterussian on 2006-01-02
Hey, ive recently installed ubuntu on my nice shiny laptop (Acer travelmate 4101wlmi), and everything works perfectly, except for sound.

Although ive fixed many ubuntu problems, ive nevr had one with sound before, so im wondering if anyone out there can lend me a hand.

It just simply doesnt work... xmms tells me to make sure i dont have any other program blocking my card... and a-play doesnt make a sound.

HOWEVER when the log in screen appears, i hear the drums...

PS. I also use suse10, on which the sound works fine, but i hate having to go around them to get something as simple as wireless support, since every one of my cards apparently isnt novell supported, and gets marked as tainted... woo

So i know sound works, i think the available only to root may have something to do with it.

SOS!

Relevant lspci:
0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
        Subsystem: Acer Incorporated [ALI]: Unknown device 0066
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
        Memory at b0040800 (32-bit, non-prefetchable) [size=512]
        Memory at b0040400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

Relevent lsmod (i think):
snd_intel8x0           30144  3
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  2 snd_pcm
snd                    48644  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer

---

### Post by whiterussian on 2006-01-02
After following this thread:
[http://ubuntuforums.org/showthread.php?t=32063](http://ubuntuforums.org/showthread.php?t=32063)

It works less it seems, now it plays the drums 4 times at the start...

---

