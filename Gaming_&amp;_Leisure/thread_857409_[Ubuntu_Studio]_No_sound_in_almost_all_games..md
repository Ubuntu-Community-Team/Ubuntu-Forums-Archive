---
title: "[Ubuntu Studio] No sound in almost all games."
date: 2008-07-12
forum: Gaming &amp; Leisure
---

### Post by Ninja Krow on 2008-07-12
I'm having a bit of an issue. I'm sure my sound card works. I am listening to "The Who" right at this very moment from .ogg files I made from my CD. But I have never once heard any of my games downloaded and/or installed from repo. 

Game such as PlaneShift, FreeDroidRPG, KQ and others don't play any sound effects or music. but this is not all games. Scorched 3D plays music and sound effects and glest does as well.

This is really bugging me that I can not hear sound effects or music where I am almost 100% sure there are sound effects and music and that it is trying to play them.

Is this an issue with Ubuntu Studio or the like? I don't see how as Ubuntu studio is supposed to be a Multi Media production flavor of Ubuntu. It may be that it uses the sound card differently but differently enough to disable sound from games?

Do I have to download/install or set something up to get sound and music to work in my games? and if so will that effect my ability to produce sound effects and music of my own when I get around to it?

---

### Post by NovruzeliH on 2008-07-12
well thats an issue to most of us, well i hope in the next versions of ubuntu it will be fixed but just bare with it, sometimes its actually good to have no volume in games, cuz i like it :p i listen to my own music all the time :p

---

### Post by timong on 2008-07-12
> **Ninja Krow said:**
> I'm having a bit of an issue. I'm sure my sound card works. I am listening to "The Who" right at this very moment from .ogg files I made from my CD. But I have never once heard any of my games downloaded and/or installed from repo. 

Game such as PlaneShift, FreeDroidRPG, KQ and others don't play any sound effects or music. but this is not all games. Scorched 3D plays music and sound effects and glest does as well.

This is really bugging me that I can not hear sound effects or music where I am almost 100% sure there are sound effects and music and that it is trying to play them.

Is this an issue with Ubuntu Studio or the like? I don't see how as Ubuntu studio is supposed to be a Multi Media production flavor of Ubuntu. It may be that it uses the sound card differently but differently enough to disable sound from games?

Do I have to download/install or set something up to get sound and music to work in my games? and if so will that effect my ability to produce sound effects and music of my own when I get around to it?

Well, probably you already tried this: Try disabling Pulse Audio in sound administration menu. Use ALSA for audio input/output etc. instead. Stop any programs using audio before starting the game.

---

### Post by NovruzeliH on 2008-07-12
yo timong i actually tried that and that worked wow, well i guess thanks :p

---

### Post by Ninja Krow on 2008-07-12
> **timong said:**
> Well, probably you already tried this: Try disabling Pulse Audio in sound administration menu. Use ALSA for audio input/output etc. instead. Stop any programs using audio before starting the game.I actually have tried that. It's all ALSA down the board. as for disabling PulseAudio from with in the PulseAudio Preferences link in the system menu, I can see where it would allow me to disable that as well.

I still have no Audio from my game. but I am glad at least one of us got sound to work.

Hmmm. maybe a step by step of how one would go about doing this would help. I'm still fairly new with Linux or more notably Ubuntu Studio. So Some things are just not the common norm for me still.

thank you for the hints already.

---

### Post by Ninja Krow on 2008-12-20
Well it's been a while, But I finally got the problem all fixed up for all but one of my favorite Linux games.

A fresh install of Ubuntu studio come with **[FONT="Courier New"]libsdl1.2debian-alsa[/FONT]** Which is just not working very well for me at all.

What i did instead was used **[FONT="Courier New"]libsdl1.2debian-all[/FONT]** instead which kicks out the ASLA version and replaces it with one that supports them all as far as I can tell. this from the word **GO** fixed 99.9% of all the games I could download from the repository. Even some of the ones that would just crash out and not even start.

One game I'm interested in player with sound is KQ - An old school Final Fantasy like game, that one still has no sound. I've gone to it's menu and it says its sounds (Both Effect/Music) turned off for some reason. and Worse yet, I can't turn them on from the menu.

I'm thinking that either we don't have the sounds files for the game from the repository or that you have to do something with the Configuration files. But for the Life of me I can't seem to find said Configuration file even when I look for the Hidden folder in my Home folders in the File System.

This Issue has been almost 100% solved I guess. and that is how I did it. just in case the whole turning off Pulse Audio didn't work for some of you like it didn't work for me.

I'll keep working at it. One sure way of becoming less of a Linux Noob is to fix the problem your self from trial and error. and boy have I made me a grand list of "USER ERRORS"

Laters Y'all...

---

