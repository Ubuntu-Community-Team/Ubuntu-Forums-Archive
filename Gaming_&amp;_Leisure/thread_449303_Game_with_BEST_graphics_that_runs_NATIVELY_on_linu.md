---
title: "Game with BEST graphics that runs NATIVELY on linux?"
date: 2007-05-20
forum: Gaming &amp; Leisure
---

### Post by blackjackel on 2007-05-20
I'm curious as to what this operating system can do, its limits, and how far it can go when it comes to graphics, so I want to install the game with the absolute best graphics that I can get that runs natively on linux.

Anyone know which game that would be?

---

### Post by rich.bradshaw on 2007-05-20
sudo apt-get install nethack

nethack

Push the limits baby!

---

### Post by blackjackel on 2007-05-20
I think I know nethack, it's that text game where you pretend to be a hacker... good joke.

---

### Post by MonkeyBoy on 2007-05-20
Hmmm...Good question.

I reckon Doom 3 has the best graphics really.  If you check out the demo you can see how nicely it runs.

Free software wise True Combat Elite is still very good.  

I must say that I really enjoy the stylised cell-shaded graphics of Warsow too.

---

### Post by bastiegast on 2007-05-20
> **blackjackel said:**
> I'm curious as to what this operating system can do, its limits, and how far it can go when it comes to graphics, so I want to install the game with the absolute best graphics that I can get that runs natively on linux.

Anyone know which game that would be?

This operating system can do graphically just as much as ms windows. I don't think you will find a free game for linux that will push your videocard to its limits. Best change is nexuiz I think. ID Software makes commercial and graphic heavy games that run natively on linux, Quake 4 and Unreal tournament will run.

---

### Post by blackjackel on 2007-05-20
Oh, I wasn't limiting it to free only games, commercial software would be fine...

The doom 3 demo runs NATIVELY on linux? Wow... I'm going to go try that right now...

---

### Post by blackjackel on 2007-05-20
doom3-linux-1.1.1286-demo.x86.run

That's what I'm getting, I'm assuming this will work fine on ubuntu.

---

### Post by MonkeyBoy on 2007-05-20
Yeah it should be fine.

Saying that I tried to download it recently from Gamershell and it was a borked download twice.  I have had it working before several times so if it doesn't work perhaps try a different location.

---

### Post by Rinzwind on 2007-05-20
Planescape Torment
Baldur's Gate 1 and 2
Neverwinter Nights


All run native I think (?)

---

### Post by Rizado on 2007-05-20
Quake 4 is native. And prey looks pretty nice, using wine though.

But best graphics must be: Unreal Tournament 3 when it's released :D

---

### Post by rolando2424 on 2007-05-20
> **blackjackel said:**
> I think I know nethack, it's that text game where you pretend to be a **hacker...** good joke.

Hum... Not really a hacker :D It's and Hack and Slash game.

---

### Post by heldal on 2007-05-20
Unreal tournament 2004, although old isn't too bad.

The X-Plane flightsim ([www.x-plane.com](www.x-plane.com) ... demo available), although technically not a game, is in active development on windows, linux and mac.

---

### Post by blackjackel on 2007-05-20
I'm running the doom 3 demo, and the graphics seem comparable to windows... though the sound is very screwed up and I can't seem to figure out how to get it working right...

---

### Post by noerrorsfound on 2007-05-20
> **blackjackel said:**
> I'm running the doom 3 demo, and the graphics seem comparable to windows... though the sound is very screwed up and I can't seem to figure out how to get it working right...
Try starting it with +set s_driver oss.

Like this:
```
doom3-demo +set s_driver oss
```

You don't have to start it like that every time, just once.

You might also want to try the Quake 4 demo. It's also based on the Doom 3 engine and is available for Linux.
[ftp://ftp.idsoftware.com/idstuff/quake4/demo/quake4-linux-1.0-demo.x86.run](ftp://ftp.idsoftware.com/idstuff/quake4/demo/quake4-linux-1.0-demo.x86.run)

---

### Post by blackjackel on 2007-05-20
Oh yeah, I'm currently scouring the ubuntu forums for solutions, I actually found that solution and it dosen't seem to work for me...

I get no sound whatsoever when I try that....

I've seen recommendations to change the sound to oss inside the doom 3 settings but I see no such setting in doom 3, I'm still looking for a solution.

Though the framerate was MUCH faster with the sound set to oss... via +set s_driver oss

---

### Post by blackjackel on 2007-05-20
Just to help with the resolution, when the doom3 installer ran doom 3 at the end of the install, I saw the following error messages in the terminal:

idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024


these error messages repeated over and over and over...

---

### Post by raver31 on 2007-05-20
Enemy Territory

Army Ops

Glest

---

### Post by DeadSuperHero on 2007-05-20
America's Army works very well in Linux.
You can still get it at: [http://www.linux-gamers.net/](http://www.linux-gamers.net/)

---

### Post by jorgerosa on 2007-05-20
> **blackjackel said:**
> I'm curious as to what this operating system can do, its limits, and how far it can go when it comes to graphics (...) Anyone know which game that would be? Im sure you will find THE ONE [here]("http://ubuntuforums.org/showthread.php?t=427205&highlight=top+games"), ;) Cya.

---

### Post by RomeReactor on 2007-05-20
> **Rinzwind said:**
> **Planescape Torment**
Baldur's Gate 1 and 2
Neverwinter Nights


All run native I think (?)

Hi. Last time I checked there *was* a [loki]("http://liflg.org/?catid=7&gameid=40") installer for Planescape but it required wine.

---

### Post by Enverex on 2007-05-20
> **Rinzwind said:**
> Planescape Torment
Baldur's Gate 1 and 2
Neverwinter Nights


All run native I think (?)

Only Neverwinter Nights on this list is Linux native.

> **blackjackel said:**
> I think I know nethack, it's that text game where you pretend to be a hacker... good joke.

No, it's a D&D type of game (adventure kill stuff thing).

Anyway, in answer to the original question, that would have to be Quake 4 and UT2004. Quake 4 uses the Doom 3 engine but with higher res textures and UT2004 is the next best looking game out that doesn't use the Doom 3 engine.

---

### Post by obsrv on 2008-09-22
Now maybe new game is released with best graphis? :) Any can name it?

---

### Post by SlackerTD on 2008-09-22
Check out [Penumbra: Overture]("http://www.penumbra-overture.com/index.php") & [Penumbra: Black Plague]("http://www.penumbrablackplague.com/site/index.php").

---

### Post by ZarathustraDK on 2008-09-23
Try running Nexuiz on maxed out graphics-settings.

I have this idea that it'd look totally awesome if it didn't push my Nvidia 7800 GT to its knees. :lolflag:

Nexuiz has a ton of graphics settings, including AA, Bloom and HDR.

---

### Post by chaemil on 2010-07-17
What about savage 2? [http://www.savage2.com/](http://www.savage2.com/)

---

### Post by Sockerdrickan on 2010-07-17
What is it with the obsession for graphics? The "best" looking game will look outdated in 2 years either way. Should focuse on more than graphics to be playable.

---

### Post by ucal on 2010-07-17
Even though it features ascii graphics, it can still push your system to the limits (and I'm not joking).  Dwarf Fortress builds a whole world, with 1000 years of history, then keeps track of all the inhabitants, down to the internal organ level.  You then get to build a fortress in it (simcity sort of), or adventure (nethack, sort of).  It also features sort of scientifically accurate materials!  So if you're a gamers gamer, who truly wants to push his system to the limits, say no to graphics, love the gameplay, and install DF :D

---

### Post by BigSilly on 2010-07-17
Prey runs natively on Linux with [the installer provided here]("http://icculus.org/prey/"). Top game too. I don't usually go for FPS games, but Prey I like. :)

---

### Post by Perfect Storm on 2010-07-17
Holy necromancy! Old thread. Thread closed.

---

