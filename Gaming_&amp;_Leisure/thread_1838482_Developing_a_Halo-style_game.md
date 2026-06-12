---
title: "Developing a Halo-style game"
date: 2011-09-03
forum: Gaming &amp; Leisure
---

### Post by Glenn nl on 2011-09-03
Hi,

there are plenty of games available for Linux.
We have many many Quake clones and even a good Call of Duty alternative.
What I really miss is a Halo-style game.
Could the open-source community develop a game together?
A game resembling Halo: Combat Evolved as close as possible but not copying it.

As an engine the ioQuake3 engine or Cube 2 engine could be used.

Here is a list of the most important stuff we need with their H:CE counterparts.

___________________________

**Characters:**

-Cyborg (inspiration from [http://pcmedia.gamespy.com/pc/image/article/687/687231/ihalo-2i-coming-to-windows-vista-20060209092831676.jpg](http://pcmedia.gamespy.com/pc/image/article/687/687231/ihalo-2i-coming-to-windows-vista-20060209092831676.jpg) ) 
-Big alien (inspiration from: [http://www.entertainmentearth.com/images/AUTOIMAGES/MF18262lg.jpg](http://www.entertainmentearth.com/images/AUTOIMAGES/MF18262lg.jpg)) 

**Weapons:**

-Pistol (inspiration from: [http://images.wikia.com/halo/images/2/20/M6d-pistol.jpg](http://images.wikia.com/halo/images/2/20/M6d-pistol.jpg) ) 
-Automatic Rifle (inspiration from: [http://images.wikia.com/halo/images/0/08/MA5B.png](http://images.wikia.com/halo/images/0/08/MA5B.png) )
-Shotgun (inspiration from: [http://images.wikia.com/halo/images/d/d6/M90_Shotgun_%28Torch_Side%29.png](http://images.wikia.com/halo/images/d/d6/M90_Shotgun_%28Torch_Side%29.png) )
-Sniper Rifle (inspiration from: [http://images.wikia.com/halo/images/2/2f/S2_AM_Sniper_Rifle.jpg](http://images.wikia.com/halo/images/2/2f/S2_AM_Sniper_Rifle.jpg) )
-Rocket launcher (inspiration from: [http://images.wikia.com/halo/images/f/f2/Rocketlauncher.jpg](http://images.wikia.com/halo/images/f/f2/Rocketlauncher.jpg) )
-Frag Grenade
-Plasma Grenade
-Plasma Rifle (inspiration from: [http://images.wikia.com/halo/images/f/f0/Plasmarifle.png](http://images.wikia.com/halo/images/f/f0/Plasmarifle.png) )
-Plasma Pistol (inspiration from: [http://images.wikia.com/halo/images/3/3f/Plasmapistolrender.png](http://images.wikia.com/halo/images/3/3f/Plasmapistolrender.png) )
-Energy sword (inspiration from: [http://images.wikia.com/halo/images/3/3b/Type-1_Sangheili_Energy_Sword.png](http://images.wikia.com/halo/images/3/3b/Type-1_Sangheili_Energy_Sword.png) )

**Vehicles**

-Military jeep
-Alien vehicle (inspiration from: [http://cdn1.gamepro.com/blogfaction/images/Ghost_of_Halo1.jpg](http://cdn1.gamepro.com/blogfaction/images/Ghost_of_Halo1.jpg) )

___________________________

The gameplay should be slow, no running, no trick jumping etc.
You can only carry two weapons and your health regenerates.
The player can chose his multiplayer character (Cyborg or Alien) and his colour for playing Free for all.
You can drive vehicles and weapons spawn in the map.
Possible modes: Capture the flag, Free for all, Team Deathmatch.

People needed for:

-3D modeling 
-Texturing
-Coding
-Sound
-Mapping

I have experience as a pixel artist (and playing Halo) but that´s it.
Please open-source community, help me realise not only my dream, but many peoples dream.

-Glenn :D

---

### Post by donkyhotay on 2011-09-04
You're going off volunteer work, there is a reason most FOSS games don't have much in the way of a campaign but are focused more on multiplayer. You are of course always welcome to build and create any project you want.

---

### Post by Glenn nl on 2011-09-05
> **donkyhotay said:**
> You're going off volunteer work, there is a reason most FOSS games don't have much in the way of a campaign but are focused more on multiplayer. You are of course always welcome to build and create any project you want.

Understood. :D

---

### Post by mastablasta on 2011-09-05
not only they are only multiplayer but they also don't have any vehicles...  :-D

what you want to do would be easiest to do with a mod or using one of the available engines. Doom3 will soon be released (if it hasn't already) then there is unreal engine available. 

another option is to mod these games.

---

### Post by spoons on 2011-09-05
You should probably start with the Xonotic engine. That supports vehicles, though I don't know about car-like physics, but you could create a Ghost and Banshee easily enough. You'd have to modify the source code to support save games as well as the GUI you want, and know QuakeC inside and out to control speeds of things, AI etc. You would probably need triggers and things as well for the AI only to trigger at a certain point. I don't know how you'd do this.

The Doom 3 engine will be released sometime this year but in what state it will be in we don't know. It might be missing some important things you need for singleplayer.

---

### Post by Howy on 2011-09-06
Halo-style game, you say?
I assume you've played the original game?
Well, then you'd know that the logics in the engine are quite complex. Kudos to Bungee, they did something extraordinary for their time.
The AIs in the game are pretty good, as well. There are TONS of triggers: sound-triggers, raytracing-like triggering and so on. But they also had access to DirectX, so they had it all on a silver plate. But it's totally doable as open source if you know how it works.
As you could expect, the game is module-based. You can modify maps and it's parameters: The warthog's speed for instance, and the placement of weapons, inside .map files. Most likely, we can't use their data. And it's unlikely that we can reproduce something that can interpret the files to every little detail. Most of the functionality lies within the game's engine. (Yes, it uses an engine. The Halo engine.)
To specify what you'd need for an open source Halo engine, this is it:
-Physics for all objects, from bodies to weapons.
-Support for a large amount of bumpmaps. Seriously.
-Advanced AI system; support for them talking but also internal parameters for friendliness to a certain "team".
-Vehicles which can be controlled by multiple players, but also individually
-Familiarity with shaders
-A lot more.
However, Halo is not an easy game to try reproduce. It was written across a couple of years by a dedicated team. To get the same in open source would take a lot of time.

---

### Post by mastablasta on 2011-09-08
> **Howy said:**
> However, Halo is not an easy game to try reproduce. It was written across a couple of years by a dedicated team. To get the same in open source would take a lot of time.
 
 
heh well, actually it would take a couple of years and a dedicated team :-)
 
but seriously there are some really good opensource games out there with AI. For example plenty quake using games (ok AI is simpler in those), then you have the likes fo Vega (and it's mods) or Babylon 5 or i've also seen some good space fighting games made by one guy. ok they really are not HALO but just show that it is doable. 
 
but you are quite correct. you need knowledge and most of all dedication.

---

### Post by nightshadowfx on 2011-09-13
a halo based game would be fun but like everyone is saying it would take allot of work and dedication and some(most) people dont want to spend that type of time unless they are getting something out of it.

---

### Post by Judo on 2011-09-27
I'd considered programming something like this at one point.  I can do basic modelling well enough to make a game and then rely on actual artists to make it look good.  I came to a few conclusions when making a weak attempt:

Quake-style engines are a bad choice for this
There is a scheme to multiplayer maps that differs slightly from other games
The campaign heavily relies on good AI

I would highly discourage Quake engines for their use of BSP and the lack of vehicle physics.  There is also a general lack of flexibility when it comes to weapons.  For example, I don't see anything Quake-like being capable of a needler.

The scheme of the maps appears to revolve around having three attack vectors, one being open, one being enclosed (like a tunnel), and the last being filled with objects and/or corners.  Placing Halo gameplay into Counter-strike maps, then, would make an entirely new game.

Lastly, the campaign would have been nothing without support fire from marines and the enemy AI's ability to limit itself to a certain area and duck for cover when needed.


In the long run, I think you have the right idea but lack the technical skills to understand the process of making it.  Although I will say this: with things like ODE, Bullet, OGRE, and Irrlicht available, it could potentially be programmed by one person although that would be quite slow.  Most of the work would be down to artists, I'm sure.

---

### Post by juancarlospaco on 2011-09-27
*" If you're a writer, programmer, artist, musician or possess any other awesome talent and want to contribute, then we're totally interested. "*

-http://projectbossanova.com FAQ

---

### Post by thatguruguy on 2011-09-27
> **juancarlospaco said:**
> *" If you're a writer, programmer,  artist, musician or possess any other awesome talent and want to  contribute, then we're totally interested. "*

-http://projectbossanova.com FAQ

The best thing about the Bossanova project is that you get to "contribute" your talents to a commercial project!  You're given the rare opportunity to supply your time and expertise to a game that they want to eventually sell, without receiving anything in return!  What else could you possibly want?

---

### Post by juancarlospaco on 2011-09-27
FOSS software == commercial project

Read the licence asap, i can do a 2 lines hello world and sell it on 20$ and its foss

---

### Post by thatguruguy on 2011-09-27
I have no idea what you mean.

Anyway, from the Project Bossanova FAQ:

> **Will your game be FOSS software?**

The short answer is: yes!  However, the engine we will be using,  Unigine, is not Open Source, and neither is the shader technology they  developed.  The rest of the client code will be Open Source.It's difficult, at best, to see how a game that uses an engine that isn't open source can still be considered "FOSS".  That point aside, there's no mention of the actual assets of the game (the character designs, music, etc.) being FOSS; only the "client code".  Their answer isn't really an answer.

id software released the id Tech 3 engine to the world, but that doesn't make Quake III Arena (or Call of Duty, or any of the other commercial games based on the id Tech 3 engine) open source.  When id Tech 4 gets released at the end of the year, Doom 3 won't magically become FOSS, since the assets will still be proprietary.

Again, there is nothing to indicate on the Bossanova website that the assets will be released.  There's no mention of what kind of license they'll be using for the game. It appears that any game actually produced will be at least partially proprietary, and presumably the intent is to get the community to provide the assets for free so that the "developers" of whatever game is eventually produced can simply pocket the money.  I put the word "developers" in quotes, because they are A) buying the engine and B) getting the assets for free, which makes me wonder what Benjamin Humphrey and the rest are actually "developing."

There are other puzzling aspects of this project.  For instance, despite the claim on the Project Bossanova homepage that they will "deliver the first ever 3D game to run exclusively on Linux", they state in the FAQ that " it will also be cross-platform." It's hard to imagine how a game can run exclusively on Linux and still be cross-platform. Do they mean it will run on both Ubuntu and Fedora?

Last, but not least, there has been no apparent development of anything by Project Bossanova since March 28 of this year, if their twitter account is any indication.  The forum which they mention in their faq doesn't exist.  This sounds like nothing more than vaporware.  Given Benjamin Humphrey's tendencies (as demonstrated by the UbuntuGamer site which he launched and then closed within 6 months), I don't expect that anything positive will ever come from this.

---

### Post by thatguruguy on 2011-09-27
One more point, now that I'm warmed up.

Project Bossanova is creating a MMORPG (and incidentally, one that looks particularly crappy).  What in the world does that have to do with developing a Halo-style game?

---

### Post by juancarlospaco on 2011-09-27
> **thatguruguy said:**
> 
What in the world does that have to do with developing a Halo-style game?

[http://en.wikipedia.org/wiki/Example](http://en.wikipedia.org/wiki/Example)

How do you know its crappy?, have you played it ?

---

### Post by thatguruguy on 2011-09-27
> **juancarlospaco said:**
> [http://en.wikipedia.org/wiki/Example](http://en.wikipedia.org/wiki/Example)

How do you know its crappy?, have you played it ?

What in the world does that link to wikipedia have to do with anything?

I didn't say that the game is crappy.  I said it LOOKS crappy. I have no intention of playing it, since you have to pay $10 ***just to play the alpha version of the game***. You can tell that it looks crappy by simply looking at the youtube video of it:

[http://www.youtube.com/user/NomadRunserver](http://www.youtube.com/user/NomadRunserver)

Seriously, it looks awful.  And again, it has ABSOLUTELY nothing to do with developing a Halo-style game.

---

### Post by DangerOnTheRanger on 2011-09-28
> **juancarlospaco said:**
> FOSS software == commercial project

Read the licence asap, i can do a 2 lines hello world and sell it on 20$ and its foss

thatguruguy's point is, 1) If you *do* contribute to Project Bossanova, if/when they make any money, you're not going to get any coming your way - not enticing. 2) It has absolutely nothing to do with the subject at hand - developing a Halo-ish game.

---

### Post by Desktop_n00b on 2011-09-29
I think it would save lots of time just to get Halo working properly in wine. Plus it would prob be better. have you tried that? or did you just want something new?

---

### Post by DangerOnTheRanger on 2011-09-29
> **Desktop_n00b said:**
> I think it would save lots of time just to get Halo working properly in wine. Plus it would prob be better. have you tried that? or did you just want something new?

The OP author wants a FOSS clone (for lack of a better word) of Halo. That way, 1) we wouldn't have to pay (probably) for the clone :D 2) We'd be perfectly free to modify the clone as we wished 3) The clone, as it would be open-source, could be included in the Debian and/or Ubuntu package repositories. The same can never be true for Halo, unless it magically becomes open-source, or Ubuntu starts putting proprietary applications in the repos *and* Halo gets a native port to Linux.

---

### Post by thatguruguy on 2011-09-29
> **DangerOnTheRanger said:**
> The OP author wants a FOSS clone (for lack of a better word) of Halo. That way, 1) we wouldn't have to pay (probably) for the clone :D 2) We'd be perfectly free to modify the clone as we wished 3) The clone, as it would be open-source, could be included in the Debian and/or Ubuntu package repositories. The same can never be true for Halo, unless it magically becomes open-source, or Ubuntu starts putting proprietary applications in the repos *and* Halo gets a native port to Linux.

Ubuntu already provides proprietary applications through the Software Center. The odds of Halo getting a native port to Linux, however, are slim.

FWIW, Halo CE runs perfectly fine under Wine.  But, as DangerOnTheRanger pointed out, that's not the point of this thread.

---

### Post by mastablasta on 2011-09-29
> **Judo said:**
> I'd considered programming something like this at one point. I can do basic modelling well enough to make a game and then rely on actual artists to make it look good. I came to a few conclusions when making a weak attempt:
 
Quake-style engines are a bad choice for this
There is a scheme to multiplayer maps that differs slightly from other games
The campaign heavily relies on good AI
 
I would highly discourage Quake engines for their use of BSP and the lack of vehicle physics. There is also a general lack of flexibility when it comes to weapons. For example, I don't see anything Quake-like being capable of a needler.
 
The scheme of the maps appears to revolve around having three attack vectors, one being open, one being enclosed (like a tunnel), and the last being filled with objects and/or corners. Placing Halo gameplay into Counter-strike maps, then, would make an entirely new game.
 
Lastly, the campaign would have been nothing without support fire from marines and the enemy AI's ability to limit itself to a certain area and duck for cover when needed.
 
 
In the long run, I think you have the right idea but lack the technical skills to understand the process of making it. Although I will say this: with things like ODE, Bullet, OGRE, and Irrlicht available, it could potentially be programmed by one person although that would be quite slow. Most of the work would be down to artists, I'm sure.
 
well Half-life (even the first one) doens't have plenty of those issues. Another option would be to use unreal engine. But neither of these are Open Source i believe, or am i wrong? or maybe even far cry engine. now that would be cool, even with the old one...
 
 
also the AI in halo CE is not that clever. I mean most of the game is runnning from checkpoint to checkpoint and they spawn quite close to player for the most part. there is no sneaking from behing (also the maps are not designed in that way. most are just like you are on a rail and doing the shooting. they are just composed nicely together (in some parts at least).
 
i haven't played any other halo than the first one so i can't comment on those.

---

### Post by 8_Bit on 2011-09-29
> **mastablasta said:**
> well Half-life (even the first one) doens't have plenty of those issues. Another option would be to use unreal engine. But neither of these are Open Source i believe, or am i wrong? or maybe even far cry engine. now that would be cool, even with the old one...

Those are not open source and never will be.
Don't hold your breath. :P

---

### Post by Judo on 2011-09-29
> **mastablasta said:**
> well Half-life (even the first one) doens't have plenty of those issues. Another option would be to use unreal engine. But neither of these are Open Source i believe, or am i wrong? or maybe even far cry engine. now that would be cool, even with the old one...
 
 
also the AI in halo CE is not that clever. I mean most of the game is runnning from checkpoint to checkpoint and they spawn quite close to player for the most part. there is no sneaking from behing (also the maps are not designed in that way. most are just like you are on a rail and doing the shooting. they are just composed nicely together (in some parts at least).
 
i haven't played any other halo than the first one so i can't comment on those.

I didn't say they were problems and I didn't say the bots were clever.  By 'good' I meant appropriate, but I wasn't trying to imply they were advanced.

There's absolutely no need for those engines, though.  The open-source engines are just as capable if not more.

---

### Post by Glenn nl on 2011-10-01
Good to see this topic still alive, I expected it dead. :popcorn:

---

