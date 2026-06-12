---
title: "VOSTRO 3350 - SOUND PROBLEMS with 10.04 Lucid"
date: 2011-10-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by nyotorono on 2011-10-21
Greetings.
I have installed Ubuntu 10.04.3 on my Vostro 3350. But sound the speakers are not recognized. They do not work.
A newer version of Ubuntu (with the sidebar) worked pretty well, although it was constantly crashing, and youtube had problems.
Any idea of how can I solve it, or a better version to install?

---

### Post by mikewhatever on 2011-10-24
Can you post the output of the **aplay -l** command.

---

### Post by collisionystm on 2011-10-24
> **nyotorono said:**
> Greetings.
I have installed Ubuntu 10.04.3 on my Vostro 3350. But sound the speakers are not recognized. They do not work.
A newer version of Ubuntu (with the sidebar) worked pretty well, although it was constantly crashing, and youtube had problems.
Any idea of how can I solve it, or a better version to install?

You need to change the default sound device. I had the same problems... well I never fixed it in 10.04 but when I ran LMDE and did alsamixer from the command line, I noticed that it was using pulse audio as the default and sound worked. Under 10.04 it has my default as the hdmi audio.

---

### Post by mikewhatever on 2011-10-24
> **collisionystm said:**
> You need to change the default sound device. I had the same problems... well I never fixed it in 10.04 but when I ran LMDE and did alsamixer from the command line, I noticed that it was using pulse audio as the default and sound worked. Under 10.04 it has my default as the hdmi audio.

Pulseaudio is not a sound device, it's a sound server.:p

---

### Post by collisionystm on 2011-10-25
> **mikewhatever said:**
> Pulseaudio is not a sound device, it's a sound server.:p


I know, but it was the output of alsamixer on a working system!! :D

---

