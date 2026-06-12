---
title: "Designing a new FPS?"
date: 2009-07-04
forum: Gaming &amp; Leisure
---

### Post by CharmyBee on 2009-07-04
An FPS action game not focused on die hard competition (like Open Arena and Alien Arena) but more on fun and cool and lots of weapons [inspired by this thread](http://ubuntuforums.org/showthread.php?t=1203319).

Weapon slots:

1 - Melee: Punches, knives. Knives that can also be thrown.

2 - Secondary weapon: Pistols, pistols, pistols. You can carry up two. You can pick one of any of them. 

3 - Primary weapon: Rifles, sniper rifles, shotguns, plasma guns, etc. If it takes two hands to operate at a minimum, it goes here. You can only carry one primary weapon. You can pick any primary weapon.

4 - Explosive: Grenades, tripbombs, remote mines, etc. You can start with any one explosive. You can find the rest.

5 - The big gun: You can't choose and start with this one. It is found only. You can only carry one. LAWs, LAWs, LAWs.

How difficult would it be to create a FPS game like this? How would I get started? What engine could I use?
I do have a bit of experience in Half-Life modding and Quake1's Quake C, but those experiences were in the 90s, and were personal abominations. I'm very rusty since then.

---

### Post by ruzkie on 2009-07-05
pretty difficult, xreal or ioquake3 would be a good place to start looking.

---

### Post by meborc on 2009-07-05
i would suggest creating a MOD first to quake or UT... since you seem to be only interested in more weapons :)

---

### Post by CharmyBee on 2009-07-05
But then, it wouldn't be a game of its own. Also, they have fixed slot weapon system.

---

### Post by eragon100 on 2009-07-05
Extremely difficult. Checklist:

- math ace, really very good.
- programming ace, really very good.
- physics ace, very good.
- a ton of general intelect.

If you have al these characteristics, you might be able to write a good game, altough you will need an artist if you aren't good at making models and stuff as well.

Sounds like a cool game concept tough, more "Killer" games are always welcome! :guitar:

---

### Post by Vadi on 2009-07-05
I don't think there are any practical solutions to easily great a good product :/

---

### Post by Col-1023 on 2009-07-05
Blender the 3D modeling program has a game engine included in it, so since you have to design levels, modelts, etc, this might be a good place to start.

The Yo Frankie project used blender and the CrystalSpace engine to create their game.

There are tutorials for basic use of the blender game engine, but I think it would TAKE ALOT OF WORK to create a good fps game.

The blender game engine has forums, I think as part of the blender community, people there create small demonstration games to test out and show off there skills and I'm sure they would give some useful advice.

Hope this helps.

---

### Post by CharmyBee on 2009-07-05
> **Col-1023 said:**
> Blender the 3D modeling program has a game engine included in it, so since you have to design levels, modelts, etc, this might be a good place to start.

The Yo Frankie project used blender and the CrystalSpace engine to create their game.

There are tutorials for basic use of the blender game engine, but I think it would TAKE ALOT OF WORK to create a good fps game.

The blender game engine has forums, I think as part of the blender community, people there create small demonstration games to test out and show off there skills and I'm sure they would give some useful advice.

Hope this helps.
Does this support TCP-IP multiplayer?

---

### Post by Col-1023 on 2009-07-05
I Have no programming or game-dev experience, so I can't say, but I'm sure the feature list and or the people in the blender game engine forums could answer that.

From the faq page at [http://wiki.blender.org/index.php/Doc:FAQ/Game_Engine/Making_Different_Game_Types#MMORPG](http://wiki.blender.org/index.php/Doc:FAQ/Game_Engine/Making_Different_Game_Types#MMORPG)

I found this, It talks about networking under MMORPG, and it describes it as very dificult.

FPS

The ever-popular first-person-shooter is one of the most common genres of games that people want to make. Now, thanks to Social's FPS template, they're fairly simple as well. The template includes a gun that shoots and a first-person view and control system. All that you need to make is the scenery and the enemies. Enemy AI is not simple, though, and it will be a significant challenge for you, but recently there have been a number of "bot templates" which make the task simpler, such as this one by Mmph!.
[edit] RPG

An RPG is a sophisticated genre requiring much content creation. As the behavior of an RPG can vary greatly, there can be no encompassing template for their creation. Therefore, an RPG remains a difficult prospect and is a very bad genre to attempt as a first project. Before you can work on a complex genre such as RPG, you should ensure that you have a firm grasp of the GE tools, and at least a rudimentary grasp of Python.
[edit] MMORPG

The MMORPG follows the same laws as the RPG, only with an added wrinkle: you must also have a sophisticated networking setup in order to play over the internet. Networking is a complicated branch of computing, and setting up such a system is not easy by any means. There are a number of projects which seek to make this simpler (such as BZoo or Server X Thin Client), but it will still take a lot of work to make such a game operational. To make an MMORPG will require extensive programming skills, on top of the skills needed for a normal RPG. Making an MMORPG as a first project goes beyond being a bad idea and becomes practically impossible.
[edit] RTS

Real Time Strategy is not a genre that has been inquired about frequently, but it's worth a brief discussion here. An RTS would be a complicated game to try to make, as it requires large amounts of AI and programming to do successfully. Extensive knowledge of Python would be required, as logic brick programming would quickly overwhelm Blender's relatively slow logic processing. Indeed, the biggest hurdle for this kind of game would be finding a way to program it so that it could run smoothly while calculating large amounts of logic. An RTS would not be an easy project.

---

### Post by Col-1023 on 2009-07-06
Sauerbraten does networked multiplayer, and you can modify it's levels from within the game.

Sauerbraten uses the cube2 engine, so check out its features, it might be what you need.

---

### Post by kspncr on 2009-07-06
I'm assuming you want it to be multiplayer? Campaigns are an agonizingly huge amount of work. And are you making a mod or a new game from scratch, with all new models etc? If so, implementing the weapons is probably the least of your worries.

---

### Post by hessiess on 2009-07-06
Not *anouther* FPS...

---

### Post by del_diablo on 2009-07-06
Could not somebody have made a proper Third Person Figther instead of a FPS? <.<

---

### Post by meborc on 2009-07-07
> **del_diablo said:**
> Could not somebody have made a proper Third Person Figther instead of a FPS? <.<

what's wrong with savage2? ... or is it not considered 3rd person?... /me=confused

---

### Post by del_diablo on 2009-07-07
meborc: have not tried savage, but there is ALOT more FPS games than TPA games....

---

### Post by xakh on 2009-07-07
If you give me some concept art, I'd be happy to make some guns for you. Or armor, tanks, vehicles, if you choose to include them, whatever. I have a huge library of old blend files from when I went through a phase making organics, mechs, and weapons, in that order, so I have a ton of big monsters, a bunch of battle robots built for running around arenas and shooting, guns out the wazoo, as well as a bunch of guns of varying shapes and sizes, from a pistol with a gigantic shell loaded into it, to a small, compact ray gun with "Have a nice day!" printed inside the barrel. I'll work on demand as well, but my new stuff will be considerably slower. Also, I'm with the above posters on using the Quake engine, or the Cube 2 engine. Just because it uses a different engine doesn't mean it's not a new game. Portal was made from the same engine as Counter Strike, and they're pretty different. Tremulous was made from the QIII engine, and it looks nothing like it. Starting with a good engine is always a good idea, unless something truly new needs to be implemented, in which case it'd probably be easier just to hack it together over top of the original engine. These are just my $2 since that's way too long for $.02.

---

### Post by Narcolepsy06 on 2009-07-07
I think you might want to consider getting the game engine from somewhere.  Probably an open source one, like I saw mentioned.  Then you just have to worry about putting the pieces together.  Simplifiying your first game greatly.  A game engine from scratch would require a great deal of programming experience.  

So, bottom line, game engine/programming api might make this goal more reach able.  Especially solo.

---

### Post by DarkWolf896 on 2009-07-09
Why no try the Torque game engine its all platform windows,mac and linux and the indi licence is only $150 it come with engine source and has a playable example redy with physics in place,ect have a look [http://www.garagegames.com/products/tge](http://www.garagegames.com/products/tge)

---

### Post by CharmyBee on 2009-07-09
I do not like Torque.

I'm starting to think about Darkplaces, but i haven't gotten a model in that yet that isn't a MDL...

---

### Post by CharmyBee on 2009-07-12
[http://sourceforge.net/projects/tenebrae/](http://sourceforge.net/projects/tenebrae/)
WOW! I could use this.

---

### Post by ruzkie on 2009-07-12
tenebare is just a tech-demo... use ezquake or darkplaces if you want to use a more usable (not 1fps) engine :)

---

