---
title: "Trying to Stream Doom Eternal in Discord and Fix Sound Crackling for Doom Eternal"
date: 2020-11-30
forum: Gaming &amp; Leisure
---

### Post by pratir2 on 2020-11-30
Hello,

I am trying to stream Doom Eternal for a friend in Discord, however I am having a few problems. I can start the game just fine, but I can not tab out of the game. If I tab out, the game minimizes, and when I tab back in, the game is just a black screen. I AM able to play and stream the game in 1080p and borderless window with no issues. I would like to play in 4k resolution, but in borderless window and 4k, the game's performance is very poor. Also, there is a crackling/popping noise in the game's music (menu and during gameplay), and I am not sure how to get rid of it. Any suggestions?

Thanks in advance.

---

### Post by CelticWarrior on 2020-11-30
Welcome.

Your question is about Windows software. How is it related with Ubuntu?

---

### Post by DuckHook on 2020-11-30
I believe that Discord was finally made available for Linux just a few months ago.

@OP

I don't use Discord, so can't help you with technical particulars, but even for those knowledgeable enough to help, you need to provide a lot more detailed info:

[LIST]
[*]Describe your HW in detail. Graphics, CPU, make, model, system RAM, video RAM, etc.
[*]Which Ubuntu flavour? Version? Which graphics driver? How was it installed?
[*]What does the Discord site say? Since it has only been available on Linux so recently, what are its known bugs?
[/LIST]

---

### Post by mastablasta on 2020-12-01
also - Doom Eternal is run through Proton, Lutris or Wine?

---

### Post by pratir2 on 2020-12-01
Thanks for that information mastablasta! That will help a ton.

Doom has an issue with tabbing out, however I have found that Discord does not stream audio. I will find another way to stream the game, but I am still faced with the sound crackling problem. Below is my system specs.

Linux: Ubuntu 20.04.01 LTS
Graphics: EVGA GTX 1080 (8 GB)
RAM: G. Skill (2x16 GB, 3200 MHz, DDR4)
CPU: Intel i7 7700K (Quad, 8 thread, 4.2 GHz)

Graphics drivers were installed automatically on Ubuntu install. Perhaps, my audio drivers may need an update as well. Since other applications' audio work, I am not not sure if that would help. May I ask for good sources that are in reference to graphics and audio drivers updating?

Also, Doom Eternal uses Wine from what I understand.

---

### Post by CelticWarrior on 2020-12-01
> **pratir2 said:**
> 
Also, Doom Eternal uses Wine from what I understand.

It would be nice to know for sure.
There are many Wine versions and other alternatives built upon Wine that aren't Wine *per se*. Can you please describe how did you install the game?

---

### Post by pratir2 on 2020-12-01
Okay. I see now. It is using Proton 5.13-2. I just downloaded the game through steam and am using it's preferred settings. I will try other versions of proton, however I mostly see people using 5.13-2.

---

### Post by pratir2 on 2020-12-01
It turns out, changing to Proton 5.0-10 fixed my issues. I did not know to try that earlier. Anyway, I appreciate everyone's time. I would still like to see about updating (or determining if an update is needed) audio and graphics drivers.

---

### Post by mastablasta on 2020-12-02
nvidia PPA may provide newer drivers (if they are actually needed and if they offer any improvement for particular game)

---

### Post by CelticWarrior on 2020-12-02
Not in this case.

Nvidia still recommends 450.xx for the OP's card. That version is in the Ubuntu repository and it's the one that should have been installed.
If any update is needed for this and any other drivers it will come along all the other system updates. No need for user actions.

---

### Post by CatKiller on 2020-12-02
You don't have audio drivers as you're thinking of them.

There is a means of addressing audio hardware built into the kernel, with a group of settings and quirks for particular hardware as they're discovered, called ALSA. Then there is a piece of software, with its own settings (which ALSA device should be used, whether audio should be resampled to a different rate, and so on), for handling audio streams called PulseAudio.

---

### Post by pratir2 on 2020-12-02
Okay. Thanks a ton!

---

