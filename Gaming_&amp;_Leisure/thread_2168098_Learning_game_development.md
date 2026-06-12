---
title: "Learning game development"
date: 2013-08-16
forum: Gaming &amp; Leisure
---

### Post by NigelRen on 2013-08-16
As a project I'm looking at ( more art than games ) I was thinking of developing a simple first person type environment.  

So basically 
[LIST]
[*]areas to wonder around ( definite )
[*]some form of interaction with others ( optional )
[*]combat - probably not
[/LIST]

I don't game although I have programming and design skills - but the thing I'm not sure about is what to use as the game engine.  I've had a look through a few books about Unity - but that seems to only have development on Windows or Mac.  This is limiting as I don't have either :(

Are there any suggestions of a widely used engine that can be developed and played on Ubuntu ( or any other flavour using a VM ) - preferably which will also run on Windows and Macs ( ideally )?

Thanks

---

### Post by leg on 2013-08-16
[Blender]("http://blender.org") could be an option. It is a 3D modelling program but it goes much further than that. It contains a games engine and includes Python as a scripting language. [Irrlicht]("http://irrlicht.sourceforge.net/") is a nice rendering engine if you want to put something together yourself as is [Ogre]("http://www.ogre3d.org/") but you will need to also research and add other libs as you require them. [JMonkey]("http://jmonkeyengine.org/") is a java games engine that seems popular and I was considering using this in a project I will be doing soon but no real experience of it yet. [Andengine]("http://www.andengine.org/") if you want one for android I have used this and I found it fairly intuitive and useful. [Wikipedia]("http://en.wikipedia.org/wiki/Game_engine") has a fairly long list if you wnat more than that.

---

### Post by oldrocker99 on 2013-08-16
Excellent answer!

---

### Post by King Dude on 2013-08-16
You may want to check out [Allegro]("http://alleg.sourceforge.net/") if you'd like to make a simple 2-2.5D (3D is possible if you use OpenGL with Allegro) game. If you'd like my opinion, start programming 2D games with sprites before you begin making 3D games.

Also, if you'd like to use Blender, I recommend [Leadwerks]("http://www.leadwerks.com/werkspace/page/home?showbanner=0"), a game engine coming to Linux soon. Leadwerks uses Lua as a scripting language, so you might need to learn how to use Lua alongside C++.

Goodluck!

PS
Here's Leadwerks' Facebook page.
[https://www.facebook.com/Leadwerks](https://www.facebook.com/Leadwerks)

---

### Post by Sslaxx on 2013-08-17
On a Lua-related note, there's also [LÖVE]("http://love2d.org/"), a 2D engine which supports physics via Box2D.

---

### Post by NigelRen on 2013-08-20
Thanks - I've been learning Blender for 3d modelling so it would make sense to have a look into the game engine at the same time.

---

### Post by King Dude on 2013-08-21
> **NigelRen said:**
> Thanks - I've been learning Blender for 3d modelling so it would make sense to have a look into the game engine at the same time.
To tell the truth, I think Blender's game engine is kinda dinky. Since the game engine isn't quite the main purpose of the software, its quality may be questionable. Just my two cents.

---

### Post by Meze0nix on 2013-08-21
Being a gameplay dev is a great job. Blender is a good free Open-source 3D modelling suite. 
And there's a variety of free to use game engines. I think the Quake engine is free to use now.
Obviously you're never going to get as advanced as perhaps, The Frostbite engine without a huge amount of experience and dedicated programmers.
So start out small.

---

### Post by King Dude on 2013-08-21
> **Meze0nix said:**
> Being a gameplay dev is a great job. Blender is a good free Open-source 3D modelling suite. 
And there's a variety of free to use game engines. I think the Quake engine is free to use now.
Obviously you're never going to get as advanced as perhaps, The Frostbite engine without a huge amount of experience and dedicated programmers.
So start out small.
[http://ioquake3.org/](http://ioquake3.org/)

Also, here's the idTech 4 engine.

[http://www.iodoom3.org/](http://www.iodoom3.org/)

---

### Post by texaswriter on 2013-08-22
There is a lot to game development. Owing to this, people recommend that you start small. 

Although you may be working by yourself, game development will typically involve one or more people fulfilling the following roles that correspond to the functions.

1) Set the schedule and manage the project/timeline
optional for a personal game development project obviously, but basically handle any marketing, distributing, and funding
2) Handle the overall game design, game type/rules, writing, and other game mechanics.
3) Create all the game art
4) Program the UI, game, sound, graphics, input, AI (if applicable), etc
5) Design all levels in the game (if applicable)
6) Procure all sound effects and voices 
7) Test the game

Just a partial grouping of tasks that you may need to do even in a small project.

---

