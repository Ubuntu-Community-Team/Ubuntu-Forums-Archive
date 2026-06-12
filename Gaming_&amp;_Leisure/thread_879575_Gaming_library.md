---
title: "Gaming library"
date: 2008-08-04
forum: Gaming &amp; Leisure
---

### Post by rewpparo on 2008-08-04
Hello Ubuntu people !

I'm a recent fan of Ubuntu, which I love. But my problem is that I still need to keep a windows copy on my machine because that's where all the good games are.

Ever since I was a kid, I've been learning about programming, dreaming about the cool games I'd make. I've had lots of projects since then, and I've been using most C++ libraries available out there (Ogre, Irrlicht,...) and none of them seemed quite satisfactory.
I think the community is now ready to make their own games. Some have already started, and there are some great projects out there. But I don't believe everyone doing his project is going to cut it for something as complicated as a game.

What the community needs is a library. A good library, that can be used to make any type of game. And it is my belief that it is possible to make such a library. A library that would be portable, through the use of a portable infrastructure, and a plugin system to port it to different systems and APIs. A library that would provide all the tools required to make a game : rendering, physics, sound, scripting, AI,.. A library that would make all those tools work in a coherent way, to provide a good learning curve. A library that would provide an interface for each of the smallest subsystems, so that code reuse would be trivial. Even full gamestates could be reused, and popular gamestates would have their own editors so that people can create their own games the same way mods are done.

It's my dream, and after more than 5 years of hobby game programing experience, I think I know how to do it.

But this experience also thought me that it's not something one can do alone. If some of you are experienced programmers and share the same dream as I, I'd love to discuss this further, as a lot is yet to design and implement.

---

### Post by Akingboy on 2008-08-04
[Allegro]("http://alleg.sourceforge.net/")
I'm not quite sure what you were looking for. Confusing post but allegro is kinda good c++ graphics library im using

Only problem is that its really hard to get started with it since there aren't good and easy to learn tutorials or game examples out there.

---

### Post by Vadi on 2008-08-04
PyGame is pretty good, for python. [Love]("http://love.sourceforge.net/") for lua.

---

### Post by rewpparo on 2008-08-04
Thanks for the pointers, but I've tried most of the existing libraries.
What I want is to make an engine, as I haven't found one that fits what I want to do.

Most of them require a lot of knowledge when you want to hack into the core of the engine. With the structure I have in mind, almost nothing is implemented in the engine core, but is implemented in plugins. This will make my engine very modular, and will allow for flexibility and community involvement.

What I'd like is to meet programmers that are interested in this project so that we can discuss it. I need the input, I know this kind of project usually fails because of bad design. It's the third time I start it all over again because of this, and I'd like to do it right this time.

---

### Post by bobulator on 2008-08-05
So, am I right in saying that your proposal will be a new game engine, that combines the strengths of it's predecessors in order to provide a tool that does all of the stuff needed to make a game work?

:D

Sounds like a great plan, but there are simply TONNES of other engines out there, and this should have something that makes it stand out, a "unique selling point", in order to make it different from the rest. (it will have to be GPL'd though, ;D)

---

### Post by Zeotronic on 2008-08-05
@rewpparo: My background sounds similar to yours (just noting it)... if your talking about making libraries that would be of use in making any type of game, I think they all already exist. I've used SDL for input, 2D graphics, and audio. I haven't used it for networking, but I know you can. Or I could use Allegro if I didn't want to use SDL, and it supports most of that correct? I've used Box2D for 2D physics and/or 2D collision testing (if I didn't need physics, or it to handle them), then of course there is OpenGL, and Ogre for 3D graphics, and Bullet for 3D physics. If you need a good way to access files you can use Boost Filesystem. If anyone would need anything far beyond everything I just mentioned it would be surprising.

If your talking about one all encompassing engine, I personally have come to the conclusion that anything capable of making everything would be so convoluted that it would be incredibly difficult to make. Anything that even falls slightly short of that would only be able to make a bunch of games which seem, in comparison to their peers in the genre, rather generic. Its also of concern that a bunch of designers who don't have much of a vision would make a whole bunch of crappy games using this technology (an example of crappy games by designers with no vision includes the Tux games, especially the Tux Karts IMO). And finally there is the branding of these games... I don't know if your familiar with Game Maker for Windows? A few of the games that were ultimately made with that were quite notable games (though no examples come to mind, I am *so* far removed from that scene), however, being that most of the games were of poor quality, eventually you would come to dismiss any game made with the Game Maker as a game that couldn't possibly be any good in comparison to any 'real' game.

---

### Post by rewpparo on 2008-08-06
I'll try to go into more details about what I really want to do and my experience with other engines. As for licence, I plan on releasing it either GPL, LGPL, or ZLIB, I haven't quite decided yet.

zeotronic, you speak of all the great engine parts there is out there. I believe you, I've tried them. But there are two things driving good people away from those tools. 
The first is the fact that they're all different designs. Some are C, some are C++, each has it's own coding conventions (did that library use capital letters at the beginning of each function ?), each has it's own design patterns, and at the point where two parts link together, you often have to hack your way through horrible code to make it work. It's inelegant, and hard work.
The second one is that if you want to slightly change something, say make a RPG instead on FPS, you'll probably have to change a lib (physics for example), and to do that you'll have to redesign most of what you did.

As for the possibility of a "all encompassing engine", I believe it's possible. I have a structure in mind, where each subsystem is clearly identified and can be changed at will. If you have been working on a RPG and you want to make it FPS, you can reuse the characters, but you'll probably have to change the physics for static geometry (from BSP to paging heightmap for example), and in this structure it will be as easy as loading a different plugin in the engine. 

It will make heavy use of factories. For each subsystem, there will be a list of factories that will give you different means to do what you need to. Adding new feature to the engine will be as easy as making a different implementation of that subsystem.
For example, to port the engine to a different platform, you'll have to make a new Window plugin, a new input plugin, a new sound plugin. You may even be able to reuse plugins made for other platforms if it works. I even found a way to easily re use skeletons so that you can reuse mesh animations.

Every part of the engine will work the same way. This will make the engine a lot easier to use, when you know one part you know all of it. It will also make it easier to create new code that will be easily reused.


Another selling point is that it will go all the way to the topmost level. There will be units. Units are characters, bonuses, anything that is supposed to have an action in the game. They have attributes, techniques, inventory... making the reuse of spells, items and such trivial. Units are controlled by controllers. This is a way to abstract player input, networking, AI... And can be reused.
Finally there will be a gamestate manager. You can reuse a whole gamestate, which means creating mini games or reusing another game inside yours will be trivial. It will also allow you to set up your game instantly if it's something someone has already done.
It is my belief that this structure will allow for maximum creativity while taking your mind off the technicalities you're not interested with.

And the nice thing is, it doesn't even require that much work. There will be a structure to define interfaces for each subsystem, a way to list factories and make the basic manager structure, and that's easy.
Then comes the nice part : everyone can start making plugins for their favorite platform or game.


Short answer now : selling point is simplicity (everything works about the same), ease of code reuse (through factories and plugins), high level programming (units, gamestates)
And about final product quality : I think with that kind of structure it can only go up. The best plugins will emerge, and people will use them for their gamestates, and people will use the best gamestates.

---

### Post by Frem on 2008-08-06
It occurs to me that if you decide you want to make a FPS instead of an RPG, you'll have to change libs and redesign most of what you did with most ANY engine, even stuff for Windows.

Don't get me wrong though, if you make this engine, I'll definately use it. :-)

---

### Post by curvedinfinity on 2008-08-07
I'm an independent game dev here, and maybe I could offer some input on this. The reason why there are many open source 3D game libraries out there, but not many open source 3D games is because of the kind of work that is involved. In a 3D library, it is easy to leverage smart decision-making to reduce the amount of work that needs to be done. In a 3D game, there is a lot of grunt work -- gameplay code and content creation -- which is extremely hard to streamline. To make matters worse, as the quality of a 3D game rises, gameplay code takes up a larger and larger proportion of the code-base. And, of course, as the quality of a 3D game rises, the amount of content required scales exponentially.

I personally love 3D games, but as an independent developer, I had to make the tough choice to stick to 2D work, because I can actually make decent 2D games in reasonable time frames. As a bonus, 2D games *are* better for experimenting with game design, which does reconcile the format's deficiencies considerably for me.

Now, all that was unbiased, but now I'm going to do a shameless plug for the project that I've worked on in my spare time for two years. As a matter of fact, I made it while faced with the same conundrum you're facing (why the hell aren't games easier to make already?), so in that sense, it is made specifically for people a lot like you. The catch is that its only for making 2D games.

In a pinch, MirthKit is cross-platform game client, and it includes an online arcade. The online arcade has a store (meaning people can buy games), but all the games available on it, including the commercial ones, are open source. That seems like a contradiction, open-source and commercial, but it not the way we've done it. Anyone can make and publish a game (regardless of whether they want the game to be free or commercial) on MirthKit's arcade for free. Check it out here:

[http://www.mirthkit.com](http://www.mirthkit.com)

Me and my two partners _just_ finished yesterday. We have a game that showcases what the platform is capable of (in addition to being pretty fun by itself). Maybe its not what you're looking for, but I hope you at least find it inspirational. ;)

---

### Post by rewpparo on 2008-08-10
thanks for the input.

CurvedInfinity, I tried Mirthkit, the game works fine, but I can't seem to launch dev mode, it just closes down without any error message. Nice looking and fun though from what I could see.

I realised it was kinda stupid on my part to ask people to discuss my design without actually presenting it in details. I'm in the process of collecting my notes and polishing my design, I'm doing it on a wiki. The adress is [http://rewpparo.wikidot.com](http://rewpparo.wikidot.com). There isn't much right now, but I'm working on it. I'll post again when I have more material to show.

---

### Post by curvedinfinity on 2008-08-12
rewpparo, try using a terminal, and cd-ing to your project directory and launching the mk-dev.sh from there. If it doesn't tell you anything more specific about what's wrong, tell me. ;)

---

