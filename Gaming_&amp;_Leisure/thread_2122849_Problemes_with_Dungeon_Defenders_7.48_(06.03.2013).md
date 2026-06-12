---
title: "Problemes with Dungeon Defenders 7.48 (06.03.2013)"
date: 2013-03-06
forum: Gaming &amp; Leisure
---

### Post by cRaZyBisCuiT on 2013-03-06
Hi,

I am running Dungeon Defenders from the HiB website on my mashine ...

Q6660, HD5850, 4 GB RAM

uname -a
Linux gaming 3.5.0-18-generic #29-Ubuntu SMP Thu Oct 25 07:26:14 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: ATI Radeon HD 5800 Series 
OpenGL version string: 4.2.12002 Compatibility Profile Context 9.012

I have two Bugs:

1. When connecting to GameSpy I get an error like that. "An unknown error occured, please try again later." Of course it does NOT work when I try again later.

2. After playing the tutorial which works great and trying to play online, I don't even have a chance of playing offline anymore. After selecting a hero and pressing start the loading screen will appear. After a while I will just be kicked back to the menue screen. How to solve that?

(3.) In Addition:
The Intro and also the loading Screen is a bit laggy sometimes and is stuttering, too.

I can provide additional terminal outputs if you let me know how to start in a proper way in the terminal.

Thanks in advance,

cRaZy

---

### Post by cRaZyBisCuiT on 2013-03-06
Got that loading loop fixed:

> Ryan C. Gordon                                                  2013-03-06 18:29:08 EST                    
Ok, so this is really embarrassing.  The game went out with an accidental last-minute change in an .ini file.  In the directory where you installed the game, edit the file:      UDKGame/Config/DefaultDunDef.ini  Right near the top are two lines like this:      DefaultGameplayLevel=LobbyLevel_Valentines2013.udk     DefaultGameplayLevelRanked=LobbyLevel_Valentines2013.udk  Change them both to be LobbyLevel.udk ... then it will work.  I'm really sorry about that, we were working on the Steam version at the same time, and it still had the Valentine's Day customizations in it, which were taken out for the Humble Bundle. That simple edit will get you going, so no need to redownload something, but I'll also update the Humble Bundle build.  --ryan.

[https://bugzilla.icculus.org/show_bug.cgi?id=5894#c2](https://bugzilla.icculus.org/show_bug.cgi?id=5894#c2)

---

