---
title: "Native Games in Linux"
date: 2006-05-20
forum: Gaming &amp; Leisure
---

### Post by gonesolo on 2006-05-20
Ok So I'm newish to linux (well I've been using various distros for about 6/8 months now and linux has become my desktop OS of choice) I've tried quite a few but I keep coming back to Ubuntu.

Currently I have Dapper Drake flight 6 installed and, majoritively, working fine. I've been using Cedega to play most of my Windows games for a while but am moving towards native games a lot more. I got a copy of Quake 4 from work as a productivity reward and I have a copy of Warzone 2100 at home also but I'm slightly confused with native games in linux.

Quake 4 - I've downloaded the client and copied the files from the DVD to /usr/local/games/quake4 but when I run it I get a missing libsdl file (don't have exact message as I am in work at not at my home PC)

Warzone 2100 - The linux version is that just another client that uses my Windows CD's to run? Or is it a full game in it's own? I did d/l it a while back but it didn't ask for my CD's and I could get no sound..

X2 - I think this is a full copy of the linux native game am I right? So I have to buy the game again even though I have the Windows version already?

NWN  - heard good things, i like RPG's but never bought it (yet) Again I believe this is a client like Quake 4 above am I right I need to buy the Windows version first?

Unreal Tournament - (original NON GOTY) I d/l the installer/linux client for this but when I run it, nothing appears to happen. I have the CD in my drive but it is never accessed and when I type UT afterwards nothing happens (unknow command error I think it's been a while)

---

### Post by it.henrik on 2006-05-20
Im no expert on this but this is how I think it works.

The so called linux client of the games you are mentioning are just teh executable that have all the linux specific code in it and then all the data in the game is the same for both linux and windows versions. (it is the same game ;) ) This is the data that is accessed by the "linux client" .. thats why it still needs the cd.

the UT error you get is just because you do not have the UT executable in your PATH.

if you know where you installed it then go to that folder ans start UT with ./ before it 

eg.

```
cd /my/installed/unreal/tournament/
./UT
```

now you should be able to get either a nice session of unreal tournament or some fancy error messages :)

---

### Post by Perfect Storm on 2006-05-20
> Quake 4 - I've downloaded the client and copied the files from the DVD to /usr/local/games/quake4 but when I run it I get a missing libsdl file (don't have exact message as I am in work at not at my home PC)

Should be easy to fix, when you get the exact libsdl file name you're missing.


> X2 - I think this is a full copy of the linux native game am I right? So I have to buy the game again even though I have the Windows version already?

Yep, you need a new copy, check tuxgames.com or linuxgamepublisher.

> NWN - heard good things, i like RPG's but never bought it (yet) Again I believe this is a client like Quake 4 above am I right I need to buy the Windows version first?

You can buy the Windows version and then download the stuff to get it working in linux or buy your copy at tuxgames.com

---

### Post by gonesolo on 2006-05-22
[QUOTE=Artificial Intelligence]Should be easy to fix, when you get the exact libsdl file name you're missing.




Yep, you need a new copy, check tuxgames.com or linuxgamepublisher.



You can buy the Windows version and then download the stuff to get it working in linux or buy your copy at tuxgames.com[/QUOTE]

- Got the Quake 4 thing sorted. plays great now using OSS (everytime I use ALSA the sound is crap) only problem is it "pauses" now and again for no reason.

- Hmmm not sure I want to buy a new copy of X2 to play in Linux. It's a good game and all but I haven't played it much. Besides got to pass all game purchase requests pass the other half - don't think she'll agree to buying a game I already have.

- Checked tuxgames for NWN - $40 is not bad for the linux version but I saw over the weekend that a "Gold edition" is available for windows - game plus 2 expansions - for the same price so I might buy that and download the linux client instead.

Thanks for the assist guys. Anyone know on the Warzone 2100 question??

---

### Post by ELD on 2006-05-22
[QUOTE=gonesolo]
Thanks for the assist guys. Anyone know on the Warzone 2100 question??[/QUOTE]

The warzone 2100 game for linux is the full game. You should just download, set it up and be away :)

---

