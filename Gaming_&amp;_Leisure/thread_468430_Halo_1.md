---
title: "Halo 1"
date: 2007-06-08
forum: Gaming &amp; Leisure
---

### Post by FKi on 2007-06-08
I'm trying to install halo 1, but whenever i get done putting in the product key is says "Cannot load PidGen.dll"

....is it possible to install halo 1?

---

### Post by BarfBag on 2007-06-08
It is possible, but very slow and buggy.  I don't recommend it.

---

### Post by The Noble on 2007-06-09
Download mfc42.dll and stick it in the /home/$USER/.wine/drive_c/windows/system32 folder. The install should work now. If you have an nVidia card better than a 6600 you should run fine. There were some graphics glitches with my x700 pro, but it ran full speed with little problems. I'm hoping all of my problems are because of the fglrx driver; if my hopes are correct you should be playing halo at full speed. 

My appdb report should be up soon; I posted it a few days ago. Use the latest wine version for good results.

---

### Post by reidms on 2007-06-09
Wow- I did not know it was possible to play Halo in Linux

---

### Post by IanW on 2007-06-09
> **reidms said:**
> Wow- I did not know it was possible to play Halo in Linux

Nor does Microsoft! ;)

---

### Post by The Noble on 2007-06-09
I have only been able to play the first half of the first level (with shadows disabled), and it played with no lag at all. This was on an ATI card as well, which was surprising. If anyone tries halo with an Nvidia card, please tell me if you don't get graphical problems. I want to file a bug with ATI cards. 

If anyone wants to see some new pictures from halo on Ubuntu, check out appdb. My pictures are already up. And if anyone was wondering, flashlights now work!

---

### Post by hikaricore on 2007-06-09
Never thought I would,
live to see this day occur,
It is blasphemy.



ROFL

Haiku ftw!

^_^

---

### Post by Enverex on 2007-06-09
> **FKi said:**
> I'm trying to install halo 1, but whenever i get done putting in the product key is says "Cannot load PidGen.dll"

....is it possible to install halo 1?

What "The Noble" said may be correct. It may be something else though, how did you run the installer? Errors like this can occur if you don't run the installer properly, i.e. you need to use a terminal to chdir to the folder where the installer is on the CD then run it. 

e.g.
cd /media/cdrom0 && wine setup.exe

Things should never be run from Nautilus or Konqueror.

---

### Post by The Noble on 2007-06-09
I only double clicked the installer and ran it with wine. The install should work with no glitches, but i did not use the express install. Also, heads up guys:

[http://appdb.winehq.org/appview.php?iVersionId=2720&iTestingId=12614](http://appdb.winehq.org/appview.php?iVersionId=2720&iTestingId=12614)

My test is the second latest one. It seems like a guy using cvs got the game working where I could not. It may be that he has an Nvidia card or there were some DX9 fixes. If someone has an nvidia card, please test halo and tell me how it goes (using .38 ). I'm dying to know if my drivers are the problem.

---

### Post by Cows on 2007-06-09
Are you talking about Halo: Combat Evolved for PC?

---

### Post by Enverex on 2007-06-09
> **The Noble said:**
> I only double clicked the installer and ran it with wine. The install should work with no glitches, but i did not use the express install. Also, heads up guys:

[http://appdb.winehq.org/appview.php?iVersionId=2720&iTestingId=12614](http://appdb.winehq.org/appview.php?iVersionId=2720&iTestingId=12614)

My test is the second latest one. It seems like a guy using cvs got the game working where I could not. It may be that he has an Nvidia card or there were some DX9 fixes. If someone has an nvidia card, please test halo and tell me how it goes (using .38 ). I'm dying to know if my drivers are the problem.

The game doesn't seem to like older cards, me and HAAARP were testing it before and it didn't seem to like his 6xxx series card (i think it was) as it didn't detect it as a high enough level of DX capable. I had the game working damn near perfectly at one point a few versions back.

Although on that note I need to clean up that AppDB page.

Cows: Er, what other "Halo 1" do you know of?

---

### Post by Sockerdrickan on 2007-06-09
Lags pretty bad, but I have integrated 6150 so that might be it?

---

### Post by The Noble on 2007-06-09
> **Enverex said:**
> The game doesn't seem to like older cards, me and HAAARP were testing it before and it didn't seem to like his 6xxx series card (i think it was) as it didn't detect it as a high enough level of DX capable. I had the game working damn near perfectly at one point a few versions back.

Although on that note I need to clean up that AppDB page.

Cows: Er, what other "Halo 1" do you know of?

I should think anything above a 6600 would fly. My card is an x700 pro which is the ATI equivalent. Note that it is an ATI card using fglrx; the 6600 should eat my lunch in linux. I'm thinking his card was not being detected due to problems with wine, not his card. I bet it would work better now.

---

### Post by Cows on 2007-06-09
> **Enverex said:**
> The game doesn't seem to like older cards, me and HAAARP were testing it before and it didn't seem to like his 6xxx series card (i think it was) as it didn't detect it as a high enough level of DX capable. I had the game working damn near perfectly at one point a few versions back.

Although on that note I need to clean up that AppDB page.

Cows: Er, what other "Halo 1" do you know of?

Well I played Halo for Xbox and Halo Combat Evolved for pc.. Im not really a Halo fan so I don't really look at the boxes. Plus that was about 3 years ago.

---

### Post by mitchellthegreat on 2007-06-24
Does any of this apply to halo for the macintosh?

---

### Post by Enverex on 2007-06-24
> **mitchellthegreat said:**
> Does any of this apply to halo for the macintosh?

Not unless you're running Linux on that Mac and trying to use Wine.

---

### Post by lordhebe on 2007-06-24
The first test, the gold one, is me. I'm using an Nvidia 7300. The odd thing is while I didn't have the "Half-visible" bug like you did, I had a few graphical glitches of my own. I haven't changed any settings in regedit, so I have GLSL disabled, maybe I should try enabling it, it could could solve the "flashlight" problem. That would then make the game's single player near perfect, with only the multiplayer (very few servers), copy-protection, sound (glitchy) and the installer preventing it from getting a platinum.

PLUS: I got the game working with Crossover 6.1 using the same method as with wine, most of the same problems occur.

---

### Post by Enverex on 2007-06-24
Crossover is basically Wine with hacks applied to make certain things work better. Unless your app is one of those certain things then it's unlikely to work better (if it's like one of the supported apps it may work better, otherwise chances are it'll be worse).

Also, your rating sounds wrong, should be a Silver. Can you list all the issues wrong with it please?

---

### Post by lordhebe on 2007-06-24
> **Enverex said:**
> Crossover is basically Wine with hacks applied to make certain things work better. Unless your app is one of those certain things then it's unlikely to work better (if it's like one of the supported apps it may work better, otherwise chances are it'll be worse).

Also, your rating sounds wrong, should be a Silver. Can you list all the issues wrong with it please?

Well copy-protection doesn't work, the game requires a nocd crack. The multiplayer works, but has very few servers are showing up, but I think it's probably a by-product of the nocd-crack. Sound is glitchy but everything works. The installer fails without a dll. Some lighting bugs, the biggest being the flashlight not working. These are the only problems and I personally think that the Gold rating is right.

Plus I only tried to see if it ran in Crossover to see if there were any differences for better or worse, and I saw no difference.

---

### Post by The Noble on 2007-06-24
> **lordhebe said:**
> The first test, the gold one, is me. I'm using an Nvidia 7300. The odd thing is while I didn't have the "Half-visible" bug like you did, I had a few graphical glitches of my own. I haven't changed any settings in regedit, so I have GLSL disabled, maybe I should try enabling it, it could could solve the "flashlight" problem. That would then make the game's single player near perfect, with only the multiplayer (very few servers), copy-protection, sound (glitchy) and the installer preventing it from getting a platinum.

PLUS: I got the game working with Crossover 6.1 using the same method as with wine, most of the same problems occur.

Yeah, I don't really know why my card is causing the half-visible problem. Otherwise, it was running platinum/gold status. The only other glitch I was having was that having shadows on was making everything black; even the flashlight worked! I have given the compatibility a thought and I think that an option I made to the registry may be causing this. If I remember correctly, I was following a guide for starcraft in wine and added a key for opengl rendering.

---

### Post by Gidskid on 2009-03-21
I followed the instructions about PidGen.dll but now it says that the setup files is not a valid windows application. the autorun also does not work :(

---

