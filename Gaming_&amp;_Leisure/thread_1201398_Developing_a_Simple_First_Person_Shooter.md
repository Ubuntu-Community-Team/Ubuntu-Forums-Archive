---
title: "Developing a Simple First Person Shooter"
date: 2009-07-01
forum: Gaming &amp; Leisure
---

### Post by PrimoTurbo on 2009-07-01
I want to create a simple free team based multiplayer FPS game. 2 Teams, 4 weapons (Knife, Pistol, Sawed-Off Shotgun, Sniper Rifle), a number of items (Kevlar Vest, Bandolier, Stealth Footwear, Agility Footwear, Silencer). During each round each team tries to eliminate each other, the gameplay and weapons are very simple and balanced. The gameplay is based on Action Quake2, but with out automatic weapons.

By developing a simple game I want to learn how to program, all I know is some very basic C. I'm pretty good with graphics, but need to relearn how to model and map.

I'm trying to figure out what would be the simplest and easiest engine to create my game. So far I've looked at Quake3 engine (especially ioquake3) and Nexuiz (Darkplaces). I don't really care too much about graphics, I just want to create a simple multiplayer game, preferably under a GPL or similar opensource license.

Which FPS engine(s) would you recommend? What is the simplest engine to develop for that has a large community and good support?
 
Should I create a mod for a commercial engine (eg. Half-Life2) or focus on creating a standalone game using one of the many free engines.

---

### Post by noerrorsfound on 2009-07-01
With DarkPlaces being based on Quake 1, you'll be using [QuakeC, an interpreted language,]("http://en.wikipedia.org/wiki/QuakeC") instead of pure C. There are advantages and disadvantages to this, but QuakeC is easier than C yet still powerful enough that Quake's actual gameplay is programmed in it. Take away the QuakeC and you've got just an engine, no game. You can actually try that out, too. Unfortunately, creating games with the Quake engine is the only thing you can do with it, so it's not useful elsewhere.

Using a newer Quake engine, you'll be programming everything in C. This may be what you want if you're intent on learning C instead of something else, but it won't be as easy.

If you don't want to use C++ then the Quake engines are your best bet. Making a mod for the Source engine requires people to have or purchase a game like Half-Life 2 to play it, and the Source SDK is C++.

Your game idea doesn't sound complicated. It would probably be easiest and fastest to accomplish in QuakeC. The time saved is time you'll need to make some good models, textures, and levels for your game.

---

### Post by PrimoTurbo on 2009-07-01
Thanks I appreciate your suggestions. Whatever I choose, I won't be using steam/Half-life2 because I plan on developing the game on Linux. I'm thinking maybe give ioquake3 a chance then move onto something else if it doesn't work out.

---

### Post by Irritant on 2009-07-01
Definitely Ioquake3 sounds like the engine that will be best suited for what you want to do.

---

### Post by CharmyBee on 2009-07-01
> **PrimoTurbo said:**
> The gameplay is based on Action Quake2, but with out automatic weapons.

I've been playing Action Half-Life 2 a lot lately, so this idea, as a free FPS, has me sold. You do not need to make a HL2 mod since this gap was just [recently filled](http://www.ministryofaction.net/).

Quake3 would be too bouncy for this idea, I think. It didn't work too well for Reaction Quake3 which is your idea in the Q3 engine. Levels felt too wide, gunfire felt too hollow and the overall feel was grueling.

---

