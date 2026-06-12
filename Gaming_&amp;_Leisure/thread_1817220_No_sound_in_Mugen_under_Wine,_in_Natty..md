---
title: "No sound in Mugen under Wine, in Natty."
date: 2011-08-03
forum: Gaming &amp; Leisure
---

### Post by Motorhead Kaze on 2011-08-03
First, Mugen works great in Xp just to let ya know that it isn't the game.
Second, My sound works great for everything else.

So I installed Wine 1.0 today via Synaptic and ran MUGEN and it looks great, but there was "No" sound. I put that in quotations because the very first sound byte in Mugen DID play when starting the game, but then after it is loaded there is no sound.

So I went into the forum and Googled my query too, and based on what I read I opened Wine config audio tab, there was no driver selected so I used ALSA driver and OSS driver. I changed the hardware accel. to "Emulation". Default sample rate is 44100, bits per sample is 16.

Restart MUGEN, no sound at all.

...Yes. My speakers are on (LOL).

---

### Post by DangerOnTheRanger on 2011-08-03
I've never tried MUGEN (I've seen + heard of it, though), but try using WINE 1.2 instead of 1.0:
```

sudo apt-get install wine1.2

```

---

### Post by Motorhead Kaze on 2011-08-03
Thanks for the reply. Funny you should mention 1.2, I did try that last night. I got sound and was happy until I clicked "Enter" (to start) and 3 more instances of Mugen started up, and it got REAL noisy. Esc did nothing so I did a ctrl+alt+del, closed 3 of the 4 Mugens and started to play...and the game crashed.

Tried again a total of 4 times, and every time I would get multiple Mugen when hitting Enter, then close the extras and start to play...crash. The 4th time in fact the entire computer just went into shutdown mode. So...I got the message that Natty really dislikes Mugen. LOL

Hmmm...

---

### Post by Soulcage on 2011-08-04
Wine1.2 is kinda old you should try wine1.3.

---

