---
title: "Ubuntu 10.04 - Only sound from internal speaker"
date: 2011-02-17
forum: Desktop Environments
---

### Post by inckiekage on 2011-02-17
Hi i have a HP Compaq dc5750 desktop pc, which has a internal speaker for audio playback. My problem is that i can ONLY get audio from this speaker, when i plug something into the rear jack stik, the sound still comes out of the internal speaker.

i have tried to install alsamixer and unmuted AUX and Line IN, and increased volume to 100%.


Note sound **IS** working, but only on internal speaker!.

---

### Post by wjz on 2011-02-17
Sounds like its the physical jack or maybe the wrong hole. Have you done anything out of the ordinary recently and has it worked before.

---

### Post by inckiekage on 2011-02-17
> **wjz said:**
> Sounds like its the physical jack or maybe the wrong hole. Have you done anything out of the ordinary recently and has it worked before.

Never worked in Ubuntu, i just installed it. The machine was running Windows 7 before and sound worked fine, when i plug something in the jack, the internal speaker switches off.

The jack is plugged into the correct port. (it's marked with hearphones and the other one is marked with a microphone).

i also tried to look in bios to somehow maybe disable the internal speaker (no luck)

i also tried the front connectors - Same result.

---

### Post by wjz on 2011-02-17
Well if the internals go off when u plug it in, then the jack is doing its job. So it's most probably a software issue. There's a program called "JACK" which is an audio connection kit which can basically re-route audio around ur machine. I managed to fix the problem i had with it though before i became a competent user. 

Hope this help!.

---

### Post by inckiekage on 2011-02-18
Got it kinda working now. 

The front jack is working, and thats better than nothing. I couldn't get the rear jack working, even not with JACKd.

---

### Post by wjz on 2011-02-18
Cool beans, so its kind of solved then.

---

### Post by inckiekage on 2011-02-18
If someone would have a look at it using VNC or ssh or something i would be glad. 

my IRC nick is inckie @ freenode

---

