---
title: "Making a game for linux?"
date: 2009-03-15
forum: Gaming &amp; Leisure
---

### Post by Rumbl3 on 2009-03-15
Well not sure if this is the right sub-forum to throw this in. But i've been wanting to learn how to make games. 

So i'm just curious where to start? Something simple tho like snes graphics etc not looking to make some 3d game or anything. 

I'm just curious where to start and where to start looking?
Are there any easy type premade stuff to work from?

When i was on windows just before i got rid of it i was going to try out rpg maker.

Just looking for something like that. That's easy to start with and can get more advanced.


btw if this is not the right subforum for this please move it for me sry for the incon.

---

### Post by Firestom on 2009-03-15
I don't know a lot of WYSIWYG game editors on Linux (I'm planning on making one) but if you know a programming language (C, C++, Java, etc...), you just have to install build-essential and the dev package of a third-party library (SDL, SFML, Qt) and start coding.

Else, if you're looking for something easier, you could try Flash with it's built-in Actionscript language. You should find an IDE in short time using Synaptic.

Else, I can't help you. Most game devkits are made for Windows and developpers do not know about a place called Linux AKA Paradise! Hope it can be of any help!

---

### Post by nawitus on 2009-03-15
Learn to program.

If an easy and flexible, yet commercial programming language suits your needs, learn BlitzMax. Otherwise, c++ or python are good choices.

---

### Post by Vadi on 2009-03-15
There are some kits available for Linux. I know the Eshalon game with made with a cross-platform one.

Oh, one tip as a user: stay **away** from SDL. If you use it, your fullscreen game will lack the basic capability to alt+tab.

(yes, that's why 99% of all linux games lack it. Pitiful)

---

### Post by plinydogg on 2009-03-15
If you don't feel like learning to program, I highly recommend this:

[http://game-editor.com/](http://game-editor.com/)

---

### Post by Bölvaður on 2009-03-15
if you are on the other hand willing to learn how to code, it might surprise you how simple it is to make a game.

---

### Post by Sockerdrickan on 2009-03-15
> **Vadi said:**
> There are some kits available for Linux. I know the Eshalon game with made with a cross-platform one.

Oh, one tip as a user: stay **away** from SDL. If you use it, your fullscreen game will lack the basic capability to alt+tab.

(yes, that's why 99% of all linux games lack it. Pitiful)
There is no good cross-platform alternative. alt+tab I hope will be fixed with libSDL-1.3

---

### Post by hessiess on 2009-03-15
> **Tux0r said:**
> There is no good cross-platform alternative. alt+tab I hope will be fixed with libSDL-1.3

SDL on its own is also resolution dependent(your games won't work well at different screen resolutions), and lacks basic things like scaling, rotation and alpha blending (anti-aliased blits). Just stick to OpenGL for rendering, Or you could use Quad-Ren (which is a wrapper over OpenGL).

If you want to create 3D games, look into Irrlicht ;).

---

### Post by Vadi on 2009-03-15
> **Tux0r said:**
> There is no good cross-platform alternative. alt+tab I hope will be fixed with libSDL-1.3

Maybe it's just not known as well - as I was told is the case.

Looking at how sdl 1.3 is in planning for 3 years now, I'm not too eager to see new games use this buggy technology (because everyone then says "Well, not our fault, SDL is buggy!" and these blame games really don't help the program be non-buggy for me the user)

---

### Post by Sockerdrickan on 2009-03-15
> **hessiess said:**
> SDL on its own is also resolution dependent(your games won't work well at different screen resolutions), and lacks basic things like scaling, rotation and alpha blending (anti-aliased blits). Just stick to OpenGL for rendering, Or you could use Quad-Ren (which is a wrapper over OpenGL).

If you want to create 3D games, look into Irrlicht ;).
I never said "use SDL for render" I was merely pointing out that SDL should be used as a base layer. OpenGL should be used for graphics, indeed.

> **Vadi said:**
> Maybe it's just not known as well - as I was told is the case.

Looking at how sdl 1.3 is in planning for 3 years now, I'm not too eager to see new games use this buggy technology (because everyone then says "Well, not our fault, SDL is buggy!" and these blame games really don't help the program be non-buggy for me the user)
wtf. Can you make it more clear I don't get it? :P

---

### Post by Vadi on 2009-03-15
It doesn't look like SDL 1.3 is going to be released anytime soon and starting a new game on it that is already buggy is not a great idea.

---

### Post by Rumbl3 on 2009-03-15
whoa lots of replies lol. 

Well that game maker thing is somewhat what i was looking to get into. Something that i can jump in right off the bat hopefully and make something simple and learn more about programming as i go to make better stuff.

I've just for years and years always though how cool it would be to make a snes type game (the graphics used then gameplay etc). i guess if i get real into it, my dream project would be a secret of mana type graphics dungeon crawler.

Will see might start digging into this stuff and now like it lol.

Also any good resources to learn one of these ways of programming from? whatever is best to use? As for support for os's i'm mainly only got linux in mind if what ever i use allows other os's to use it also that's fine.

---

### Post by Sockerdrickan on 2009-03-15
> **Vadi said:**
> It doesn't look like SDL 1.3 is going to be released anytime soon and starting a new game on it that is already buggy is not a great idea.
Actually there has been a lot of activity recently the only thing missing in my view is a SDL_OPENGL3 flag :P

---

### Post by jacksaff on 2009-03-16
I would look into pygame.
It's a library of games related code for python which is very easy to learn.
You can knock up fun games in just a few lines of code and there are lots of tutorials and beginner projects out there.

---

### Post by hessiess on 2009-03-16
> **jacksaff said:**
> I would look into pygame.
It's a library of games related code for python which is very easy to learn.
You can knock up fun games in just a few lines of code and there are lots of tutorials and beginner projects out there.

PYGame is based on SDL, so has all of the problems which have already mean mentioned(lack of alt+tab, resolution dependence...)

---

### Post by Sockerdrickan on 2009-03-16
Resolution dependance is just if you don't plan on using OpenGL...

---

### Post by Ferrat on 2009-03-16
I would have a look at pyglet, looks very nice, it's in python for all the python lovers here and seems to have all that is needed, a more modern version of pygame is the idea I think.

[http://video.google.co.uk/videoplay?docid=-8788197863800411145](http://video.google.co.uk/videoplay?docid=-8788197863800411145)
really nice presentation

---

### Post by myromance123 on 2009-03-17
Hey, have you checked out GyroVorbis on youtube?
  They have a series called The Adventures of Game Development lol

Although it isn't greatly educational, he does have tips and advice in other newer videos that aren't part of the series which will benefit you if you're serious in making games :D

  Him and his buddies are making a DreamCast game lol
I learned that I have to have a strong knowledge of a programming language (like C++), understand the different departments in game making (such as game engine programmers, game programmers, 2d designers, 3d designers & modellers, network programmers and stuff like that) and a bunch of other cool stuff about game making from their channel.

  Never hurts to scour the web for terms related to subject you're interested in~
  Ohh if you're interested in C++ theres:
[http://www.cplusplus.com/]("http://www.cplusplus.com/")
[www.cprogramming.com]("http://www.cprogramming.com")
[http://www.cppreference.com/wiki/]("http://www.cppreference.com/wiki/")

The site of Stroustrup, the guy who made C++:
[http://www.research.att.com/~bs/C++.html]("http://www.research.att.com/~bs/C++.html")

Despite what the others have said about SDL, its up to you to make the decision :D

So here's some sites that can help you out ;)
[http://www.sdltutorials.com/]("http://www.sdltutorials.com/")
This ones the actual SDL site with tutorials on it.
[http://www.libsdl.org/tutorials.php](http://www.libsdl.org/tutorials.php)[http://www.libsdl.org/tutorials.php]("http://www.libsdl.org/tutorials.php")
 This site's really cool and has an undergound feel to it :D
[http://lazyfoo.net/SDL_tutorials/lesson02/index.php]("http://lazyfoo.net/SDL_tutorials/lesson02/index.php")


Not forgetting GameDev.net!!
 That site has a whole lot of information on game making, be sure to check it out~
[http://www.gamedev.net/]("http://www.gamedev.net/")

 Gamedev is a serious website, they can help you. They even have several books made on the topic :)

Hope something there may help you be it now or later ;)

---

### Post by iamscuzzo on 2009-03-17
[www.pygame.org](www.pygame.org)

You will learn python and a good library for multimedia, SDL. I wouldnt let the comments about SDL keep me from learning pygame, especially if you are new to game dev.

---

