---
title: "N64 emulators won't work"
date: 2019-06-16
forum: Emulators
---

### Post by zacmitche11 on 2019-06-16
Hi I'm using the most updated 32 bit version of lubuntu. For some reason all of the N64 emulators I've tried (including different plugins) won't show video. Some plugins produce sound, so I know the emulator is running. Is my old onboard video too old for opengl or something? It's the only thing I can think of.

---

### Post by oldrocker99 on 2019-06-16
Aren't N64 games 64-bit?

---

### Post by deadflowr on 2019-06-16
*Thread moved to **Emulators***

Which emulators aren't working?

---

### Post by zacmitche11 on 2019-06-17
@oldrocker yes technically N64 is 64 bit, alot of the games are still 32 bit though. I've used N64 emulators under windows 32 bit for 18 years or so and never had trouble. Also the Wii is 32 bit, it has n64 emulators as well. It's something Linux related.
@deadflwr muphen64 plus from the software center, I also tried source from GitHub. I did end up getting a N64 emulator to work in retropi x86 in software mode but it was unplayable due to frame rate.

---

### Post by deadflowr on 2019-06-17
Even though mupen64plus in the software store is a graphical frontend it does come with the mupen64plus command line utility.
Try running a game through a terminal and grab the output it produces.
Fairly simple to do, the basic command is
```
mupen64plus /path/to/game
```
Post back the output as it might give a good idea of where things are.

---

