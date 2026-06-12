---
title: "ZSNES too fast or too slow"
date: 2008-09-02
forum: Gaming &amp; Leisure
---

### Post by zerantoss on 2008-09-02
Hi. I'm new to ubuntu and just started running zsnes. My problem is the game speed. I know there's an option in the terminal to adjust the frame rate from 0 to 9. But 0 just seems too slow to be fun, and anything from 1-9 is way too fast to play properly. Any suggestions? When I ran windows I had snes9x, which could alter the frame rate to a more precise degree. Can Zsnes do that? Does anybody run snes9x on ubuntu?

---

### Post by dfreer on 2008-09-02
> **zerantoss said:**
> Hi. I'm new to ubuntu and just started running zsnes. My problem is the game speed. I know there's an option in the terminal to adjust the frame rate from 0 to 9. But 0 just seems too slow to be fun, and anything from 1-9 is way too fast to play properly. Any suggestions? When I ran windows I had snes9x, which could alter the frame rate to a more precise degree. Can Zsnes do that? Does anybody run snes9x on ubuntu?

I'd post on the zsnes forums, but what you are doing is not adjusting the frame rate. On the windows version there is a "Max frame skip" and "emu speed" options, but unless you are running a really old system you shouldn't need to use those at all.

I don't know that much about zsnes, but I'm pretty sure "Emu Speed" is basically a fast forward/rewind feature. Unless you specifically want games to run faster than a standard SNES, I wouldn't touch these. If your system is simply not rendering ZSNES fast enough, fast forward/rewind is not the solution.

Need to know exactly what option you are trying to configure, and system specs. Or just post on zsnes boards where there are more experts.

---

### Post by zerantoss on 2008-09-02
I'm running Zsnes on an Acer Aspire1 notebook, processor is 1.60GHz Intel Atom N270, and it has 512MB DDR2 533MHz memory. It was just Linux when I bought it, but my friend helped put ubuntu on it.

I opened terminal and put it sudo apt- zsnes, or somethin like that which installed zsnes, and when I run it I type in the terminal:

zsnes -f 0
and this loads zsnes and further loading a game plays it at its "normal" speed I guess, which is slower than a typical snes game on a console, so I then try to run it faster so I changed the terminal instructions to:

zsnes -f 1
this changes the "frame rate" i guess, but the speed becomes almost twice that of a typical snes game on console. I'm trying to get a standard speed, but there doesn't seem to be one. And there are zsnes boards on ubuntu forums? Thanks for the reply, and I hope I didn't just waste your time.

---

### Post by dfreer on 2008-09-02
ZSNES forums are located here:
[http://board.zsnes.com/](http://board.zsnes.com/)

Hmmm, I don't know what fixed frame rate does, never had to use it. Frame rate should be a value between 0-60 for NTSC games and 0-50 for PAL games, so the whole 0-9 thing throws me off. Anyways, ask there.

---

### Post by mister_k81 on 2008-09-02
> **zerantoss said:**
> Does anybody run snes9x on ubuntu?

I do. This GTK port works well for me, and is highly polished:  

[http://www.snes9x.com/phpbb2/viewtopic.php?p=22874](http://www.snes9x.com/phpbb2/viewtopic.php?p=22874)
PPA is also here: [https://launchpad.net/~bearoso/+archive](https://launchpad.net/~bearoso/+archive)

---

### Post by FranMichaels on 2008-09-03
Launch zsnes. Config > Speed, then tick auto framerate.

Screenie

---

