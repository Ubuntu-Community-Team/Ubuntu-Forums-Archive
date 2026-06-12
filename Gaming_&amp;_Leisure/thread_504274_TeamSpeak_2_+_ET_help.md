---
title: "TeamSpeak 2 + ET help"
date: 2007-07-18
forum: Gaming &amp; Leisure
---

### Post by herbster on 2007-07-18
I want to get both to playback sound at the same time, and I have tried a tun of HowTo's and wikis. I am running ET and TS2. Now, if I use the "aoss" wrapper both work, except when I use my mic it sounds really really distorted no matter what sound settings I change. If I run it normally (using OSS) my voice sounds fine and it is working right. So it appears AOSS is not the way to go for me.

I have tried [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Sound](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Sound) as well, and honestly I know a little about configuring sound as I took part in customizing my .asoundrc but I don't have a clue what it may be telling me to do.

And I have an M-Audio Revolution card that plays a bunch of sound programs at once (amarok, vlc, firefox, etc. simultaneously) all just fine.

Basically I need to get TeamSpeak2 to use ALSA somehow, is it possible?

---

### Post by meborc on 2007-07-19
EDIT: sorry... never mind... my link was not a solution :)

---

### Post by splintercellguy on 2007-07-19
Hell yes, you need to install wine-oss, then run TS with it:

wine-oss ./TeamSpeak (run in TS directory)

---

### Post by arron on 2007-07-19
Im not sure the difference, but I run TS (one) the linux client with aoss with no problems at all.

---

### Post by herbster on 2007-07-19
> **splintercellguy said:**
> Hell yes, you need to install wine-oss, then run TS with it:

wine-oss ./TeamSpeak (run in TS directory)

I tried apt-get install wine-oss but there's no package. I have wine installed, and I just checked winehq.com but couldn't find it. Where can I get that?

---

### Post by herbster on 2007-07-23
bump, still unable to get this to go :(

---

### Post by arron on 2007-07-24
Can you confirm what you are trying to do?  Are you trying to run TM2 the windows client threw wine or linux client?  Are you trying to run a linux game or a windows game threw wine?  I can run a wine game with teamspeak going.  In wine use the alsa sound driver (or try the oss if that dont work) use "winecfg".  To run the linux TS client run "aoss teamspeak".

---

### Post by herbster on 2007-07-24
> **arron said:**
> Can you confirm what you are trying to do?  Are you trying to run TM2 the windows client threw wine or linux client?  Are you trying to run a linux game or a windows game threw wine?  I can run a wine game with teamspeak going.  In wine use the alsa sound driver (or try the oss if that dont work) use "winecfg".  To run the linux TS client run "aoss teamspeak".

I'm running the linux client, no wine. I am also running the linux client of Enemy Territory.

If I run TS itself it sounds great, but I can't use sound for anything else (can't run the game).

If I run TS using "aoss teamspeak" the quality of my microphone is horribly garbled, and no sound settings at all change it.

So I am basically trying to run TS and the game with both having sound, and without having to use "aoss."

---

### Post by chuck_h1987 on 2007-09-13
Install aoss and get the ET sdl hack.

Terminal: aoss /where/ts/is/teamspeak

terminal :./et-sdl-sound

and this will let u hear both game and ts at the same time

Good Luck
Chuck

---

### Post by esodin on 2007-10-20
My problem is similar and, based on discussions in various other forums, seems to be a problem related to newer drivers.
[B]
The good news[/B]
With Gutsy, *wine* (as downloaded from the Ubuntu repositories) works well on the sound side (great improvement has been made in the use of alsa in *wine* from the *wine* version that came with Feisty to the one that comes with Gutsy). Steam games (CS:S and Team Fortress 2) now work perfectly without the need to get *wine* directly from wineHQ.

**The bad news**
As observed in *herbster's* post, to get sound from more that just TeamSpeak, you need to use *aoss* (*aoss teamspeak*). When running teamspeak using aoss this results in crackling or lagging sound. The problem gets worse with much activity on the TS channel.

While I do not fully grasp the workings of aoss, alsa, oss or anything that has to do with sound for that matter; from what I have read (over the past 2 days) about this issue - it would seem that the problem has something to do with the buffer sizes *aoss* has access to.

**Other information**
- I have tried to increase the priority (niceness) of the process - this has no effect
- My computer has 8Gb of RAM and CPU is Q6600 - resources should not be an issue

Any constructive thoughts and ideas would be appreciated.

---

### Post by esodin on 2007-10-21
A follow-up to my post above:

I gave up trying to find a solution to my AOSS problem in TeamSpeak and decided to play some games. Something strange occurred.
1. I started up TeamSpeak first. Observed a lot of crackling or lag.
2. I started a CPU incentive game (ETQW). As CPU load increased the crackling/lag in TeamSpeak **disappeared** :confused:
3. I loaded a Steam game (CS:S) as well and the TeamSpeak sound was perfect.:confused::confused:
4. As CPU load fell the crackling came back.

I  tested this throughout the weekend and the findings were consistent. 

Anyone care to take a crack at explaining.

---

### Post by herbster on 2007-11-10
I'm trying again with TeamSpeak and I have the same issue:

I start TeamSpeak, it works mint. But I start ET with TS running and I get this error for the game:

```
------- sound initialization -------
SDL audio driver initializing...
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
SDL audio driver is "(UNKNOWN)"
./etsound: line 4: 24943 Segmentation fault      (core dumped) LD_PRELOAD="/home/bobby/et-sdl-sound.so" ./et.x86 $*
bobby:~$ 
```

It just doesn't even start.

Then I run TS using "aoss ./TeamSpeak" and both work, but every voice sounds like a monster including my own. It's all horribly slowed down and strange, so this is not an option.

I hate giving up but I have zero idea how the hell to get this to work. I just cannot run TS and ET together and have functionality in both. :confused:

---

### Post by Dogfighter on 2007-11-10
i guess u have sound on board.
i had it too, and no chance to get it work.
get a cheap soundcard (a soundblaster or something) and the problem is pretty much history.

---

### Post by herbster on 2007-11-10
> **Dogfighter said:**
> i guess u have sound on board.
i had it too, and no chance to get it work.
get a cheap soundcard (a soundblaster or something) and the problem is pretty much history.

Nope, I've got an M-Audio 7.1 card.

---

