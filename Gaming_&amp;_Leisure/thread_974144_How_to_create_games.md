---
title: "How to create games?"
date: 2008-11-07
forum: Gaming &amp; Leisure
---

### Post by cristo-father on 2008-11-07
Hello
I would like to know how to create games(3d, 2d...).
Even if i have to learn calculus, C++, Linear algebra, opengl, make music, create engine...
The main problem for me is i need a guide that will teach me everything involved in game making.
Anyone know of such a thing?

---

### Post by MonkeyBoy on 2008-11-07
[Ogre]("http://www.ogre3d.org/") is probably a good thing to have a look at.  That combined with [Blender]("http://www.blender.org/") is a pretty good way of making quite advanced 3d games.

There are other engines such as [Crystalspace]("http://www.crystalspace3d.org/main/Main_Page") for making specific types of game.

If you want to make simpler games then [pygame]("http://www.pygame.org/docs/tut/intro/intro.html") might be worth a look.

There really are loads and loads of ways of making games and lots of online resources for tutorials etc.  These are just a few ideas.  Try Googling "open source game engines" and you will find a lot to choose from.

I hope you make something good!  :)

---

### Post by Sockerdrickan on 2008-11-07
Learning C++ is a good start. [www.cplusplus.com](www.cplusplus.com) and later [www.cppreference.com](www.cppreference.com)

---

### Post by cristo-father on 2008-11-07
Is C++ the most "math based"?

---

### Post by scragar on 2008-11-07
> **cristo-father said:**
> Is C++ the most "math based"?

C++ is fast and powerful, which is what you need for games(most games anyway), if you want a maths language play about with a little fortran, there's a maths based language for ya(I am not serious about this, fortran is horrible, don't use it, honestly, don't).

---

### Post by EMR on 2009-06-29
> Is C++ the most "math based"?

I've found python to be very close to most math-that is, if you know plenty of math, python will make sense.  C++ has much more syntax, will be buggier, but will also be much faster.

All programming languages are math based-heck, computers are math-based.  LISP is an interesting case, as it is it's own nifty little kind of math-though I would not recommend it for game development.

An existing engine is nice to have-I'm still trying to get pyogre to work, but it looks like a good option.

I'd like to see more games for Linux, so good luck...

---

### Post by efikkan on 2009-06-30
C++ is a very good choise, most games are written in C++.

I don't know what kind of games you want to make, but if you are targeting real games, you need several years of programming experience.

---

### Post by CrazyMonkeyFox on 2009-06-30
Stackless Python is good also. Eve-online is written in stackless python, and they manage to hold 40k+ users on the one server relatively lagless. It can depend on the game what you use, the console for bf2 and bf2142 is written in python also. That being said the majority of FPS's tend to be written in C++, and there are several open source engines on the internet. try googling Irrlicht for a good source engine, in my experience its quite good. You need more than one person to make any sort of reputable game, otherwise I'd dive into making a 2d game, there are tons of tutorials on the web for them.


_______________
CrazyMonkeyFox

---

### Post by efikkan on 2009-06-30
Using Python for scripting and C++ for the game engine would be better than just python, for larger projects.

---

### Post by joangracoffande on 2009-06-30
I work at a game studio as a rendering programmer, so I'll throw my 2 cents in. Most professional games are written in C/C++, but you don't *have* to write them in that. I'd start by getting a good grasp of programming in general. I actually started by writing small applications in java.

Heavy math is not required to be a game programmer. I'd go so far as to say you probably don't need much more than basic high school level math, unless you're going to be doing cutting edge graphics or physics. You're just starting out, so stick with something like OGRE (although this is strictly a rendering engine), or use a full engine such as Delta3D.

Be prepared to spend at least 4-5 years learning the basics.

---

### Post by efikkan on 2009-06-30
You'll need to know how to calculate vectors, and perhaps quaternions if you want to perform advanced camera movements.

---

### Post by tomd123 on 2009-06-30
> **cristo-father said:**
> Hello
I would like to know how to create games(3d, 2d...).
Even if i have to learn calculus, C++, Linear algebra, opengl, make music, create engine...
The main problem for me is i need a guide that will teach me everything involved in game making.
Anyone know of such a thing?

[http://nehe.gamedev.net/](http://nehe.gamedev.net/)

Although if you don't know C++ then even this is way over your head.

If you're just looking to create a small game then you could try python as it is a little forgiving on beginners. But be forewarned that python (interpreted) is ridiculously slow compared to C.

I'll create a guide for you right now...
1. Read and learn python. Do a lot of examples because just reading will not make you even a half decent programmer.
[http://docs.python.org/](http://docs.python.org/) read the tutorial, library and language references along with some other links on that page.
2. Learn a graphics api or game engine.
[http://www.pygame.org](http://www.pygame.org) again, read all documentation and go through their tutorials to get started.

IMO this is the least amount of effort you could put into programming a game starting from no experience in programming at all. Don't forget there is still audio and etc, but I will create another guide for you once you finish step 1 and 2. Hopefully this wasn't a waste of time.

---

