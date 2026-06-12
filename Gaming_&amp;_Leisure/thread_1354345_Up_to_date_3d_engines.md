---
title: "Up to date 3d engines"
date: 2009-12-13
forum: Gaming &amp; Leisure
---

### Post by Elys on 2009-12-13
[B]      I am interested in making an up to date opengl 3d engine, and tools. I'm not bad at programming, but I am more of a business man. If anyone is interested in working on this project with me, please let me know. 
       This will not be an easy project as it will be time consuming, and normally these things take quite some time to make. 
        I have done programming in C/C++, Java, Python, Pearl and many others.
I would prefer this be done in C++. If anyone here is a modeler, or artist in general Help would be greatly appreciated. I have started a new group called [/B]3d teams.[B] Feel free to check it out.

Sorry just noticed I put this in the wrong place. I meant to put it in the programming section.
[/B]

---

### Post by del_diablo on 2009-12-14
Why reinvent the wheel? I would recommend a fork a an existing project, or use a base:
*Ogre(not an engine, just a pretty damn good renderer)
*Nexuiz engine(pretty decent)
*Crystalspace
*Others(LOADS)

---

### Post by Jestersage on 2009-12-14
Also, the Sauerbraten is a good choice too (I like it better than the DarkPlace Engine). if you prefer client-server archietecture, Intensity engine, which is based upon Sauerbraten, is a good choice.

---

### Post by 3rdalbum on 2009-12-14
Unigine is an excellent commercial one that's cross-platform. You can sample what it does by downloading their Sanctuary and Tropics tech demos (if you're on Windows you can download their latest Heaven demo, or wait a couple of weeks for a Linux version).

---

### Post by hessiess on 2009-12-14
Instead of re-inventing the wheel (graphics engines are very complicated), take an existing engine and improve it.

Personally I like irrlicht for 3D

---

### Post by cb951303 on 2009-12-14
Definitely checkout Horde3D => [http://www.horde3d.org/](http://www.horde3d.org/)

Note that it's only a 3D graphics engine. It's not a game engine.
Which makes it perfect for other purposes too.

On the other hand. Combine it with SDL and you have pretty good game framework :)

---

### Post by Sand &amp; Mercury on 2009-12-14
^ Agreed with everyone above. You'd just be duplicating effort if you started on your own without anything to make your project distinct from the rest, so why not contribute to one that's already going?

Sauerbraten seems like an obvious choice to me, Darkplaces may be a good starting block too though I think that may mostly be a one-man job.

---

### Post by Elys on 2009-12-14
I see what you mean there are a lot of choices. Why re-invent the wheel? No offence here, this just reminded me of what a friend used to say. "Because the wheel used to be square. If no one re-invented, it where would we be now?" Not saying this is true but it does have a point. 
   Do any of the engines you know of use a 100% shader driven rendering pipeline?

---

### Post by cb951303 on 2009-12-14
> **Elys said:**
> 
   Do any of the engines you know of use a 100% shader driven rendering pipeline?

I'm not sure but I think Horde3D does.

---

### Post by Xidram on 2009-12-15
[QUOTE=Elys]Do any of the engines you know of use a 100% shader driven rendering pipeline?[/QUOTE]

What about Panda3D? ([http://panda3d.org]("http://panda3d.org"))

It is a very well developed BSD-licensed 3D game engine built in C++ and wrapped with Python. It's been used in several large commercial games by Disney already and is getting better and better. One other thing I love about it is its awesome, helpful community.

As for shaders, Panda3D supports GLSL and Nvidia Cg.

---

### Post by del_diablo on 2009-12-15
> **Xidram said:**
> Nvidia Cg.

The crap is quite buggy, avoid using at all costs.

---

### Post by Xidram on 2009-12-15
> **del_diablo said:**
> The crap is quite buggy, avoid using at all costs.

What is--Cg? I personally don't use Cg. The reason Panda3D has Cg in the first place is compatibility with both OpenGL and Direct3D. However, I personally wouldn't want to write shaders that depend on a proprietary toolkit, so I'll stick with GLSL.

---

### Post by del_diablo on 2009-12-17
Well, shall we get this topic on? Its decaying, and that is a bad sign for something that might evolve.
I would recommend Panda or Ogre, maybe a look at some of the engines just to se the underling framework. I would recommend to avoid Luascript for scripting language.

---

### Post by Elys on 2009-12-18
Sorry about not posting sooner, I had family over for a few days.  Thanks to everyone who has responded to my post. 

Anyways could you tell me what it is about Luascript that you don't like, and what you think would be the prefered scripting language?  

Question:
I have heard the line don't re-invent the wheel several time. This is understood and they have some great points. So I guess what I was wondering, Is if we have good game engines, and Linux in a whole has a lot of programmers. Why do you think there are very few commercial games?

---

### Post by PaulInBHC on 2009-12-18
People who look for open source and free operating systems look for open source and free games.
Not much commercial value in that.

---

### Post by Elys on 2009-12-18
That is true, However most of the people who I personally know who use linux changed to it for its stability, and security. Not because it was free, or open source. So it seems like there should be plenty of people that would not mind paying for a game, as long as they feel they are not having to pay to much for it.

---

### Post by PaulInBHC on 2009-12-19
You open an office, hire a couple of programmers and graphic artists. Several years and hundreds of thousands of dollars later you have a game. You make a deal with a distributor to market and sell the game. You get your cut and after a year you are in the hole big time.
Or you work from home, get people to program and artwork for free. That is how open source games work.
What is your idea?

---

### Post by Elys on 2009-12-19
I'm Very Happy Today. I made a deal that will help me tremendously.   
   
After today I will be supported with mostly free work done by two universities, and a local technical school. They will be helping me with the code, models, and artwork. They will be paid in a manner. They get to use this for part of there grades, and finals. Also get to claim this as experience in the work place.  Most of them think it is worth it, just to possibly get there name known.
That being said. I don't need to pay for any of the work in a conventional way. I get access to a lot of fresh talent and ideas. 

This is all very exciting for me.

---

### Post by Arthur_D on 2009-12-21
That sounds really cool! Best of luck with your project. :)

---

