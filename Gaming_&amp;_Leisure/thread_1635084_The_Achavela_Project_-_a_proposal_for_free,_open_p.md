---
title: "The Achavela Project - a proposal for free, open pokemon-style game"
date: 2010-12-01
forum: Gaming &amp; Leisure
---

### Post by Minkovsky on 2010-12-01
The monster development games (aka Mon games), such as Pokemon or Digimon are very popular and lots of people play them. However, as I browsed the Internet, there seems to be no mature free and/or open Mon games. Enter The Achavela Project.

The Achavela is a project I invented and sketched on boring lessons in school and during my free time. It's supposed to be a free and open Mon game, made in Blender/CrystalSpace and work (quite) well on netbook computers (for the same reason most of the Mon games are on handheld consoles). I even made a more specific plan for the project, in the form of a project proposal document (written in formal language, just because my English teacher was looking :lolflag:).

So while most of the stuff is explained there, I just want to make a quick note: I'm not experienced in creating games, so I'll need some help. Shall the project succeed, I'll try to contribute the most, but for now, I only can provide you with some ideas and concept art, until I learn Blender and the other stuffs.

[INDENT]Link to the project proposal: [http://ompldr.org/vNmJzZA/](http://ompldr.org/vNmJzZA/)
[/INDENT]Regards,
Filip

---

### Post by Cousjava on 2010-12-01
I would be happy to contribute. I am more of a programmer than a graphics designer, and have some experience with C, C#, PHP, MySQL, (X)HTML and Java, and have been planning to learn C++ for a while anyway.:)

Great idea. As a suggestion as this is a collaboration project, is Git/GitHub. I've just started using it, and it is easy for people to share updates in coding, branch out, merge etc.

---

### Post by akromm on 2010-12-01
Hi, I would be happy to contribute as well.  Although I also only have experience in programming, (no art skills).  I have experience in C, C++, C#, Java, and PHP.  I have experience doing 2D (allegro) programming and a little experience doing 3D (OpenGL) programming.  

-Adam.

---

### Post by Minkovsky on 2010-12-02
Right. I'll set up a github repo soon, and post the concept art I've created. There's not much of it anyway. However, I'd kind of need some artists, once the work on the engine has begun.

The first thing to do will be to make the battling engine. As the mons will be in 3D, the battle should take advantage of it. I'm talking about full 3D battlefield with some camerawork.

So, any artists out there? :P

---

### Post by DangerOnTheRanger on 2010-12-03
A bit of advice:

People are more likely to help you with your project if you can also show them something they can currently run/play, i.e, a demo.

Why? 
Because it shows them that you yourself are putting your *own *energy into your project, and you'll not just let them develop your project, and then take full credit.

It shows them that you've thought your project out, and know *what it takes* to finish something this big. What you want to accomplish is *huge*. There's nothing wrong with that. It just means you'll have to devote more time and energy to your project.

Also, I probably can't help, at least right now. I don't really like C++, and I'm just a beginner with Blender. Perhaps in a few months, when I get my current game programming commitments out of the way...

---

### Post by Minkovsky on 2010-12-03
Hi! I'm back. Here's some concept art for you. Includes 4 mons and a mon storage/catching device. And no, it's not a ball. It's rather some kind of a remote control with three buttons. The mon is stored inside, just like Scotty was stored in the Transporter buffer in that TNG episode. Has two modes: Catch and Release. Catch works in two ways: when used on a wild mon, it tries to catch it. When used on your mon, it just switches it out of the battle. Of course, this will be all automatic, just like in any other game.
[[IMG]http://ompldr.org/tNmV2NA[/IMG]]("http://ompldr.org/vNmV2NA")

These are 4 concept mons. They're in XCF format.
Clawtato - a potato with claws!
[[IMG]http://ompldr.org/tNmV2MA[/IMG]]("http://ompldr.org/vNmV2MA")

Domefelix - psychic cat
[[IMG]http://ompldr.org/tNmV2MQ[/IMG]]("http://ompldr.org/vNmV2MQ")


Fridgefish - A frozen fish - Starter Mon
[[IMG]http://ompldr.org/tNmV2Mg[/IMG]]("http://ompldr.org/vNmV2Mg")


Serpentysth - Cool snake.
[[IMG]http://ompldr.org/tNmV2Mw[/IMG]]("http://ompldr.org/vNmV2Mw")


That's all for now, but I will work on more stuff, such as the world and other mons.

Hey - I have an idea. Instead of making up something to go before the mon, why not just keep them called "Mons," and name the game something like FreeMon or OpenMon (too obvious) or VelaMon or AchaMon? Which one is better?

---

### Post by akromm on 2010-12-07
Any of them sound good to me.  It's up to you.

---

### Post by Minkovsky on 2010-12-09
So it is decided then. The name would be VelaMon. And, as you noticed from the first map in my previous post, the region's name would be Acha State. So technically, if we were to do more games, they'd all be codenamed "[region name] + vela".

I'll try to model out few battlegrounds and add concept animation to them (using placeholder velamon, such as Sphere, Sphere2 and Ellipsoid :popcorn:). But now, I have a project open for my IT classes, about internet security for 9 year olds :/ - so I won't be able to do much this weekend.

---

### Post by Zero2Nine on 2010-12-10
My advice, more an idea actually (as I have little experience with big game projects), would be to start with a balanced battle and scoring system and to first make data models of the *mons. Not graphical data but just text.

Make a list of objects in the game (only abstract object no instantiations yet). 
- mons
- battles
- trainers
- worlds
- tournaments
- rewards
etc.

What are the properties of these objects?

Mon
- Name
- Hitpoints
- Level
- Attacks
- Defenses
etc.

Do this for all the objects and then decide how these objects interact, what are the rules of the game?

Once you have a balanced, challenging, battle system (IMO that will determine the success of the game) you could move on to the fun part of designing the mons, trainers, worlds etc.

Good luck with your project!

---

### Post by Cousjava on 2010-12-20
I've created a Github organisation for it with a repository at [https://github.com/AchavelaProject/Achavela](https://github.com/AchavelaProject/Achavela). For my own thought on doing, etc. I have my own fork at [https://github.com/Cousjava/Achavela]("https://github.com/Cousjava/Achavela"). If you tell me your Github username then I will add you as an administrator of the organisation.

---

### Post by Minkovsky on 2010-12-20
Thanks. I already sent you a message on github.

---

### Post by donkyhotay on 2010-12-20
*Another* FOSS pokemon remake? <sigh> Good luck but I must warn you that this forum is littered with many abandoned pokemon remakes. You may want to do a little hunting and either help or take over an abandoned project so you're not recoding from scratch.

---

### Post by Perfect Storm on 2010-12-20
> **donkyhotay said:**
> *Another* FOSS pokemon remake? <sigh> Good luck but I must warn you that this forum is littered with many abandoned pokemon remakes. You may want to do a little hunting and either help or take over an abandoned project so you're not recoding from scratch.

This^

---

### Post by DMKryl on 2010-12-21
I have been thinking of doing something like that, but due to my poor programing knowledge (actually zero), i have been looking from a code with a world map, and a battle system wich i can work on it(i know too naive) but what i have looked around and the only project that i found was ****mon, maybe you want to look at it, I will help with artwork if you want (but only if you have a development roadmap)

[https://sourceforge.net/projects/wildcardmon/](https://sourceforge.net/projects/wildcardmon/)

---

### Post by Minkovsky on 2010-12-21
I think we could use ****mon as a base for the battle engine. I'll try to make a simple testing program.

---

### Post by Perfect Storm on 2010-12-21
test pokemon 1 2 3 

testing the forum

---

### Post by benjabean1 on 2010-12-27
My Github username is benjabean1.

---

### Post by Samaphira on 2011-03-01
I cold do the art 4 u if u want.

---

### Post by Minkovsky on 2011-03-02
The art is currently not the issue (however I do appreciate you asking),  since we're looking primarily for programmers. I'm kinda sorry for the  inactivity, I was doing other stuff. The main idea is to create an  abstract template, in C++ (crystalspace) or Python (blendergame). The  template should include the following:
HP
MaxHP
Moves = { move1, move2, move3, move4 }
DexNumber
Nickname
Status
BattleStats = {Atk, Def, Spd, Acc, SAtk, SDef, Eva}
ContestStats = {Beauty, Cool, Funny, Cute, Bodybuilding}
Exp
NextLvlExp
Level
Item
UseMove(ref move)

Move should include:
ID
Name
PP
MaxPP
MakeMove(ref move, ref invoker, ref targets[])

Etc, etc. Is someone willing to try to write the code? I might try to do this myself, but I'm not that good at programming.

---

### Post by Fableflame on 2011-03-03
Wow, this REALLY makes me wish I knew how to code.
I read the project summary and I really like the idea.
I just hope that this project succeeds, I wish you luck.

---

### Post by ironic.demise on 2011-03-04
> **Fableflame said:**
> Wow, this REALLY makes me wish I knew how to code.
I read the project summary and I really like the idea.
I just hope that this project succeeds, I wish you luck.

Same, I only know BASH and HTML...
About time I learnt something else too :(

The sad thing is that I could code a pokemon game in BASH just without graphics!

---

### Post by MasterNetra on 2011-03-05
This isn't abandoned, half dead maybe but not abandoned:
[http://ubuntuforums.org/showthread.php?t=1359712&page=34&highlight=pokemon+remake](http://ubuntuforums.org/showthread.php?t=1359712&page=34&highlight=pokemon+remake)

And No the forum is not littered with abandoned pokemon remakes. There was a pokemon remake thread but it moved to the thread posted above. It has not been abandoned.

---

### Post by Minkovsky on 2011-07-13
I apologize for me not being here, stuff got in the way. Although I had time to think of design problems, such as what engines should be used and how monsters, moves and types will be handled.

For the engine/language choice:
I think that pure Blender 2.5 BGE with Python 3.1 will be a good choice, since there are blenderplayer binaries for virtually EVERY system, and if we need more than that, it's open source and could be modified.
Still, CrystalSpace is an option, but I'm more into Python than C++.

Monster system:
For all the mons, I suggest that types run off one class (a Type class with values matching types, see below, also same for natures and abilities), and that each kind of mon should have its own class with defined learset and species-specific stuff like models and sprites, but inheriting Monster class which contains all the common mon definitions (stat variables, etc).
```

//defining a mon
myMon = new monsterdex.Pikatchu();
//defining its nature and ability
myMon.Nature = new monsmechanics.Nature("Calm");
myMon.Ability = new monsmechanics.Ability("Pickup");
//thus we have a Calm Pikatchu with Pickup

```

Now for moves...

I'm tempted to have each and individual move as a method of its class (which will, in turn, inherit a generic Move class), but this may be bad for multi-turn moves, like Fly, Dig, or Rollout - or not, since they may have several methods that happen after the move is first used, and they get pushed to the call queue in the Battle Manager.

Battle Manager should be the main focus for now, for this is where main features will get implemented. It will handle turns, moves, item usage, remember stat modifiers and basically everything that we want to happen in a battle.

It should also be as much object-oriented as possible - while rewriting it once it's done wouldn't be a problem, DRY principle should stand.

As always, if you're interested in contributing, feel free do do so!

---

### Post by amiacamal on 2011-07-15
How much input can someone wilt no real experience have? :D This does look like an interesting project and I'd love to see the code now, and throughout development just to see how a project progresses! I'm learning java now (about 2 year basic experience (and i mean baaasic) but would like an oppertunity to learn something new!)

also, for something like this is it not possibly a good idea to start how pokemon did? ie, get the actual game working, battle scenes etc all runnig well, then start adding natures/abilities at a later stage? I could be wrong but if this is properly structured adding an ability or nature shouldnt be too complex (i could be wrong, but design patterns are being triggered here)

---

### Post by Dlambert on 2011-07-17
Not a pig Pokemon fan (anymore) but i always support Open source Gaming!

---

