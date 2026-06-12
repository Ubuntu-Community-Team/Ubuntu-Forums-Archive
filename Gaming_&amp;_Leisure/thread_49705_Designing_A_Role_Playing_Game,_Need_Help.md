---
title: "Designing A Role Playing Game, Need Help"
date: 2005-07-17
forum: Gaming &amp; Leisure
---

### Post by jlacroix on 2005-07-17
Hello everyone. :)

The unthinkable has recently happened, my 80GB drive crashed and its beyond repair. On this drive I had sourcecode from an RPG that I am designing, so it's gone, forever. :(

That was my Windows drive. I only used it for that purpose, so other than losing the sourcecode, its no big loss. I still have Ubuntu which is what I use 99.9% of the time.

The program I used to create games with is called Game Maker. That's the only purpose that I had Windows installed, just for that one program. After months of failed attempts, I know now that there is no way to get Game Maker to run good under Linux, and I can't imagine buying another replacement hard drive to install Windows which I barely ever use unless I am designing a game.

My question is this. Are there any good websites that will take someone like me whom has never programmed anything in Linux and teach them how to design games? Preferably, it would be nice also to be pointed in the direction of a good program to use or two.

Keep in mind, although I've designed games in Windows I've never done so in Linux before. So, I am an ultra-super-duper-noob when it comes to Linux programming. Also, I would like to maybe learn 3d Opengl but I think that may be too daunting for someone whom has only used sprites.

---

### Post by DJ_Max on 2005-07-17
Well, the first thing you wanna do is learn a language. Using programs to help make your games just isn't going to cut it in the real world. Do you have any programming experience? C/C++, Java, Ruby?

If not, there are literally tons ofsites. As you can't just start programming a game when you can't program.

[http://devshed.com](http://devshed.com)
[http://devarticles.com](http://devarticles.com)
[http://cplusplus.com](http://cplusplus.com)
[http://python.org](http://python.org)
[http://ruby-lang.org](http://ruby-lang.org)

Then
[http://pygame.org](http://pygame.org)
[http://rubygame.seul.org](http://rubygame.seul.org)
[http://ogre3d.org/](http://ogre3d.org/)
[http://gamedev.net](http://gamedev.net)

Languages like C/C++, Ruby, Python, and Java are cross-platform, so it's not only Linux programming, they run on Windows and OS X.

---

### Post by jdodson on 2005-07-18
gamemaker huh?  never used it, but i have played games made in it years ago, they were really strange.

i would recommend learning how to program.  sure it will take awhile, sure game maker is easier, but you actually will learn a skill worth knowing. no offense, but game maker is only as good as game maker is.  which might be amazing, however, its proprietary, its win only and you only can make win games.  plus you are limited to game makers features.

so i would recommend something like python so read this: [http://www.ibiblio.org/obp/thinkCSpy/](http://www.ibiblio.org/obp/thinkCSpy/)

when you are done with that and know python and programming concepts, the world is your oyster.  i am making a game using python, snag it here: [http://www.ubuntuforums.org/showthread.php?t=40409&highlight=open+fantasy(i](http://www.ubuntuforums.org/showthread.php?t=40409&highlight=open+fantasy(i) will be updating it sometime, I added some new levels, code, etc).

Anyways, I would take this as a sign from God to learn how to use a real language.  In the end it might take more time, but you can do tons with program language knowledge.  Plus python is cross platform(aviod using windows com objects).

---

### Post by DJ_Max on 2005-07-18
[QUOTE=jdodson]gamemaker huh?  never used it, but i have played games made in it years ago, they were really strange.

i would recommend learning how to program.  sure it will take awhile, sure game maker is easier, but you actually will learn a skill worth knowing. no offense, but game maker is only as good as game maker is.  which might be amazing, however, its proprietary, its win only and you only can make win games.  plus you are limited to game makers features.

so i would recommend something like python so read this: [http://www.ibiblio.org/obp/thinkCSpy/](http://www.ibiblio.org/obp/thinkCSpy/)

when you are done with that and know python and programming concepts, the world is your oyster.  i am making a game using python, snag it here: [http://www.ubuntuforums.org/showthread.php?t=40409&highlight=open+fantasy(i](http://www.ubuntuforums.org/showthread.php?t=40409&highlight=open+fantasy(i) will be updating it sometime, I added some new levels, code, etc).

Anyways, I would take this as a sign from God to learn how to use a real language.  In the end it might take more time, but you can do tons with program language knowledge.  Plus python is cross platform(aviod using windows com objects).[/QUOTE]
 I was trying to bring out the same point. Plus when you said games made in Game Maker were strange, that just makes sense considering a program did the work.

Also, about your game, I'm gonna play around with it in OS X.

---

### Post by jlacroix on 2005-07-18
Thanks guys, I am going to give programming a shot and see where I can go with it. I am looking at either Ruby, Python, or C++. 

Now, Windows has Microsoft Visual Studio for application design, what does Linux have?

I tried KDevelop and I hate it. Very ugly and hard to understand. (IMHO, of course). With KDevelop I couldn't even figure out how to testrun my application. I did a simple Hello World program, which I remember the code by heart, and couldn't find a way to run the program. Is there anything else I can use, or a really easy compiler program like Visual Studio?

---

### Post by DJ_Max on 2005-07-18
You don't need an IDE. But if your doing heavy development. Try this thread. [http://ubuntuforums.org/showthread.php?t=49833](http://ubuntuforums.org/showthread.php?t=49833)

---

### Post by jlacroix on 2005-07-18
I would rather use an IDE. I couldn't imagine programming without one, and how much of a nuissance that must be.

---

### Post by DJ_Max on 2005-07-18
[QUOTE=jlacroix]I would rather use an IDE. I couldn't imagine programming without one, and how much of a nuissance that must be.[/QUOTE]
No, not really. Sometimes usuaing an IDE when it's not needed can slow down development. Depending on an IDE can also lead to bad programming skills. Your see what I mean soon.

---

### Post by jlacroix on 2005-07-18
If I'm correct, I'd have to open up a terminal to run commands to bugtest and things like that? I'd rather not, its just the way I am.

---

### Post by jlacroix on 2005-07-18
Forgot to mention this. If my knowledge is correct, those that have made games with C++ and the like are big name companies with a staff of up to a thousand. That is the main reason I use Game Maker. Has anyone made a professional game from coding by hand without a staff or big budget?

---

### Post by DancingSun on 2005-07-19
If program speed is more important to you, I'd recommend C/C++.  Otherwise go with Java, Ruby or Python, because you'll have so much trouble with C/C++ that you'll give up on programming.

Out of Java, Ruby, and Python; Java and Python are probably more suitable, simply because they have more gaming related libraries and projects out there.  Java is faster than Python, but less flexible in my opinion.  Java also has very nice free IDE's, Eclipse and NetBeans.

However, I prefer Ruby's syntax and style over the others.

---

### Post by Lord Illidan on 2005-07-19
Kdevelop can compile from the IDE...and run too...

Ctrl + F8 builds..... 
And there is a button which will run the app..

Many of the great games which come on Linux...like chromium, etc...are programmed by 1 man! I take it you are not coming up with Warcraft 4?

---

### Post by Omnios on 2005-07-19
While checking out games in Synaptic I came across a 3d gl game engine though I forget what it was called. Actual just found it its called Crystal Space not shure how much support it has for the actual programming but you might find it interesting.

 Also I play abound with a lot of idea's for games and have stumbled on a few based on what a lot of players hate about rpg's and one of them is having to go for very long periods between leveling and not gaining anything. I thought of an idea to eleviate that by sub levels which can be done in many ways. Main levels deal with stat points and ubber skills sub levels can deal with things like upping spell power or tweeking a spell or special attacks etc, generaly smaller things but there always earning something. As for sub levels that may be gained by either using experiance or special sub level experiance points or gathering special crstals which makes it very interesting. Always have bosses preferable with a quest associated with it and or huge xp gain it brakes up the click hack and slash rutine. Anyways just thought id mention that personaly Im picky when it comes to rpg's

Cheers

EDIT: And note 2d rpg is not dead I just started 3d rpging a couple years and and that was becasue it was a D&D game otherwise id still be playing 2d rpgs

---

### Post by Juergen on 2005-07-19
I don't know if it's OT, but I'm a fan of Angband and all its variants.

Might be OT because it has D&D influences (and some more), but many experienced players characterize it as 'Inventory-Managment Game' - at least in the later game :-)

But it has a clear codebase, and you can even start with only changing its config-files to make an (entirely?) different game.
Thats why so many variants exist.

To make it really different, you'd have to code a bit in C (not ++)

If you don't know it, maybe look here
[http://www.thangorodrim.net/](http://www.thangorodrim.net/)
and for a quite different variant here:
[http://t-o-m-e.net/screen.php](http://t-o-m-e.net/screen.php)

---

### Post by blu.gecko on 2005-07-19
try this out. it runs on Win32 aswell 

[http://sourceforge.net/projects/nebuladevice/](http://sourceforge.net/projects/nebuladevice/)

---

### Post by Poldi on 2005-07-20
[QUOTE=jlacroix]Forgot to mention this. If my knowledge is correct, those that have made games with C++ and the like are big name companies with a staff of up to a thousand. That is the main reason I use Game Maker. Has anyone made a professional game from coding by hand without a staff or big budget?[/QUOTE]

until the early 90s it was quite possible to create state-of-the-art games with very small teams. so you should (after some learning) be able to code towards that level. 

I did a clean-room reimplementation of Ultima VI for windows (3.1) at that time  even extended the engine to support multiple floor levels and networked multiplayer play [but when I tried to get a sponsor for it everyone told me gaming under Windows made no sense and there was no market for multiplayer RPGs...]. 

the main problem when you are aiming towards todays games quality is not so much the game mechanics and engine but to provide the graphical resources. that's where you won't get far without a team of 20+ members.

good luck. and never belive others when they tell you your business idea is crap.

I suggest you get NetBeans from [www.netbeans.org](www.netbeans.org) in a ready-to-use bundle with jdk 1.5.0_04 and learn Java. 

kind regards,
Carsten

---

### Post by jdodson on 2005-07-20
[QUOTE=jlacroix]Forgot to mention this. If my knowledge is correct, those that have made games with C++ and the like are big name companies with a staff of up to a thousand. That is the main reason I use Game Maker. Has anyone made a professional game from coding by hand without a staff or big budget?[/QUOTE]

tons of free(as in freedom) games are only made on a staff of a few and a small budget.  

[http://www.wesnoth.org](http://www.wesnoth.org)
[http://www.nexuiz.org](http://www.nexuiz.org)
free civ
gtetrinet
and many more

---

### Post by Hezekiah on 2005-07-20
As far as IDEs go, I really like(d) Anjuta.  It is really only well setup for C/C++ development, but if you decide to take that route it's a nice way to go.

I personally would recommend going with an interpreted language (Perl, Python, Ruby) or just use C++.  The interpreted languages are nice because they require less overhead coding on your part and they don't require any compilation between code edits.  C++ on the other hand will (often) produce a much faster program, and if you use features such as the standard template library and other modern C++ niceties it isn't really any harder to use than Java.  I personally find it easier than Java, but that may just be me.

Depending on how dirty you want to get your hands, take a look at the SDL website: [http://libsdl.org/](http://libsdl.org/) - There are a lot of links to support libraries, tutorials, and other goodies.

Good luck!

---

