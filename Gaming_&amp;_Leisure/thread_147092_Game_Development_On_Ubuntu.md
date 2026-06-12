---
title: "Game Development On Ubuntu"
date: 2006-03-19
forum: Gaming &amp; Leisure
---

### Post by jlacroix on 2006-03-19
Hello all,

First of all I didn't know where to post this. If this is the wrong place please move this topic to the appropriate place.

That being said, I develop games using Game Maker. I like Game Maker alot. The most recent game that I made can be found here:
[http://gamemakergames.com/?a=view&id=3621](http://gamemakergames.com/?a=view&id=3621)
Unfortunately, it was made for the Windows platform. Some day, I would like to make cross-platform games. Designing games is very fun for me, and while I can't say that the games I created will win any awards or be available at your local retailer, I can say that it's worthwhile to me.

Anyway, sorry to babble on. I would like to learn to develop games using Ubuntu. Preferably KDevelop unless there is an easier way. I know the very basics of programming, and the language I would like to learn more about is C++.

Most of the C++ books I find are for Windows. That being said, there are quite a bit of Windows Platform Only syntax, and of all the C++ books I have, it's hard to sort the Windows only syntax from the usual C++ syntax.

Here are some things I was hoping you guys could help me with:

1.) An easy to use Development solution for games. Something for beginners.
2.) A C++ tutorial for absolute beginners, for Linux.
3.) Howto's for writing simple games that can be extended into larger games when I get more practice.

So basically, I would like a Game Maker like system for Linux, if one exists. I tried one but I didn't like it. I forgot the name. Going further, I would like to program games from scratch. My goal is to some day make a game that will be on the Ubuntu repositories. What would really help is for a tutorial that tells you how to create a really simple game. My first game was a really stupid space shooter, but it served as the foundation upon which to build up my skills.

Any links to information you guys might have would help. Google isn't being especially helpful in sorting the Windows development from Linux development.

---

### Post by charlieg on 2006-03-19
[www.pygame.org](www.pygame.org)

That or join an existing project.  Like this:
[http://scourge.sourceforge.net](http://scourge.sourceforge.net)

Lots of options.

---

### Post by jlacroix on 2006-03-19
Pygame is the one that I didn't like, I have tried it. However I know there has to be other options.

---

### Post by Mr Green on 2006-03-20
[QUOTE=jlacroix]Pygame is the one that I didn't like, I have tried it. However I know there has to be other options.[/QUOTE]

How about [Allegro]("http://www.talula.demon.co.uk/allegro/").

---

### Post by charlieg on 2006-03-20
Allegro is a bit low-level though.  However, if you are looking at allegro, you'll want to look at [SDL](http://www.libsdl.org) and [Clanlib](http://www.clanlib.org) which are probably the two most popular game development libraries.  There's also [PLib](http://plib.sourceforge.net) but only a handful of games use that.

These, however, are not really the higher-level things the OP is perhaps looking for.

---

### Post by talonsnow on 2006-03-20
As for your question on C++, there isn't different types. C++ will work on linux as it does on windows, there is no difference. The only thing when creating games, and using your int language is that most are not supported in linux. i.e. DirectX, so you will want to focus on using OpenGL instead. 
If you have any further questions on how to get started on creating games using C++, feel free to send me a message.
In the beginning, you will want to focus on a simple 2d game, like connect 4 or tic-tac-toe or something, then slowly progress into more complex projects.

*edit* Also download Anjuta or some other development GUI with a compiler to learn c++ on.

---

### Post by jlacroix on 2006-03-20
Feel free to talk to me on email, [email]jlacroix82@gmail.com[/email]. Give me as much info as you can about C++.

I'm not saying that there are different types of C++, however there are operating system specific syntax that Microsoft puts in. This is not the exact code, but things such as this are operating specific:

include <win32.h>

Stuff like that is what I'm referring to. I'd love to learn as much about C++ as I can, from very very very very very very basic entry level, to later on reading advanced things. (With an emphasis on game design). I tried Google, however the most I can usually find is tutorials on how to make Win32 apps, instead I'd like to try to be cross platform, if I can.

---

### Post by Mr Green on 2006-03-21
I used "Sams Teach Yourself C++ in 21 Days" in school and find it a very good beginners book. Check it out.

---

### Post by mvaniersel on 2006-03-21
> 
Allegro is a bit low-level though. 

But I find Allegro is very easy for beginners. Also, SDL only handles graphics and Allegro also handles sound, keyboard, mouse and joystick input, etc.

Plus allegro has a very [friendly community]("http://www.allegro.cc") where you can go for questions.

---

### Post by talonsnow on 2006-03-21
[QUOTE=jlacroix]Feel free to talk to me on email, [email]jlacroix82@gmail.com[/email]. Give me as much info as you can about C++.

I'm not saying that there are different types of C++, however there are operating system specific syntax that Microsoft puts in. This is not the exact code, but things such as this are operating specific:

include <win32.h>

Stuff like that is what I'm referring to. I'd love to learn as much about C++ as I can, from very very very very very very basic entry level, to later on reading advanced things. (With an emphasis on game design). I tried Google, however the most I can usually find is tutorials on how to make Win32 apps, instead I'd like to try to be cross platform, if I can.[/QUOTE]

These are includes, that have nothing to do with the standards of c++. Any c++ book will work on linux, as long as it's sole purpose is to teach the c++ language you should be safe. 
As for win32, I am sure you are refering to online tutorials or books that are trying to teach game programming, this is because almost all of them start with how to setup your base application using the win32 library.
I would advise just to go into your local bookstore, and cruise through there books on c++ and see which one seems the best for you, or hit online c++ tutorials. 
[http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)
[http://www.cprogramming.com/tutorial.html](http://www.cprogramming.com/tutorial.html)
[http://www.programmingtutorials.com/cplusplus.aspx](http://www.programmingtutorials.com/cplusplus.aspx)

I am probably for my next project going to try to port a game, or create a game to linux. If you want to help, more for fun then anything else, then just let me know. However, at this point I am still trying to finish a game for windows that is using DirectX.

---

### Post by Keffin on 2006-03-21
[quote=mvaniersel]But I find Allegro is very easy for beginners. Also, SDL only handles graphics and Allegro also handles sound, keyboard, mouse and joystick input, etc.

Plus allegro has a very [friendly community]("http://www.allegro.cc") where you can go for questions.[/quote] 
[FONT=Verdana]*Simple DirectMedia Layer is a cross-platform multimedia library designed to provide low level access to audio, keyboard, mouse, joystick, 3D hardware via OpenGL, and 2D video framebuffer.* -- [http://www.libsdl.org/index.php]("http://www.libsdl.org/index.php")


[/FONT]

---

### Post by talonsnow on 2006-03-21
As for networking, the best engine I came across for the years on developing games is Raknet, which is cross-platform.

[http://www.rakkarsoft.com/](http://www.rakkarsoft.com/)

---

### Post by Hacim on 2006-03-21
I like SDL you can get deveplment packages in the ubunu repository it comes with some simple demos and setting a window is as easy as a couple  of lines of code.It was also used in some commercial ports such as civilizations.I think you making the right choice trying to make games from "scratch" as it's much more rewarding than GM.Feel free to email me at [email]Hacim.H@gmail.com[/email] if you have any questions about SDL or compiling programs with gcc (the c/c++ compiler you'll use an linux,should be on the cd if not already installed).goodluck:D

---

### Post by slavik on 2006-03-21
learn some C and use OpenGL :D

---

### Post by charlieg on 2006-03-22
Of course, for OpenGL tutorials, there's the infamous [http://nehe.gamedev.net](http://nehe.gamedev.net)!

---

### Post by EviL_Me on 2006-03-22
If you don't want to learn how to program, you could use blender with there game engine. It's pretty easy to use if you know howto use blender. It's a bit harder to use than gamemaker, but you can do more. (I don't know if you want to make 2d or 3d program's, but i think blender can only do 3d)

---

### Post by Hacim on 2006-03-22
I could never find many tutorial on the blender game engine so I don't know if that would be a good transistion from GM,plus I think you should try to make some simple 2d games first just to get used making a good game loop,something GM took care of for you.Choosing a library or engine is always a matter choosing the right balance simplicty and ease of use,and features and power.So you 'll probaly have experiment a little with different ones.

---

### Post by Master Shake on 2006-03-22
I have used GameMaker in the past too, and I love that.  Its one of the reasons I don't get rid of windon'ts myself...

I'm looking at Gambas right now.  It's more like Visual Basic, but it may be what I'm looking for.

As far as that Teach Yourself c++ in 21 days book...  I have both that book, and its smaller 24 hours cousin cousin.  The author of those books needs to get off his fixation with cats.  Plus, I was disappointed in the fact that it didn't have more realistic useable examples for the beginner.

---

### Post by Mr Green on 2006-03-23
[QUOTE=Master Shake]As far as that Teach Yourself c++ in 21 days book...  I have both that book, and its smaller 24 hours cousin cousin.  The author of those books needs to get off his fixation with cats.  Plus, I was disappointed in the fact that it didn't have more realistic useable examples for the beginner.[/QUOTE]

I must agree about the catfetish. Still, after completing it you have a good understanding of c++' features IMO.

---

### Post by Master Shake on 2006-03-23
[QUOTE=Mr Green]I must agree about the catfetish. Still, after completing it you have a good understanding of c++' features IMO.[/QUOTE]


I dunno.  I'm still confused about the whole concept of 'classes'

Maybe I should go learn plain 'ol C first

---

### Post by charlieg on 2006-03-23
Going back to C will not help you with classes.  Classes are an object oriented paradigm, and C has little inbuilt support for OO design.

Just think of a class as an object blueprint.  Using it, you create new objects and you form your application from the interaction of the various objects you define.

---

### Post by Hacim on 2006-03-24
yes the class thing can take a bit to grasp.If your familiar with structs and function pointers (callbacks) you can just think of a class as a typedef struct with function pointers as members.As for c/c++ books, the only out put there going to show you is on terminal but I recommend reading them any way because you need knowledge
of  file IO and string manipulation to make a decient game.[Here]("http://www.freeprogrammingresources.com/") is a  site with some useful links.

---

### Post by boosted69 on 2006-03-31
im relatively new to programming myself and have never tried c. i am however taking sequential classes in J++ which is very similar im told. If you want a real grasp on learning what a class is and how to call it up and stuff you might want to get a real book on it. i find websites harder to read then a good old paperback intro book. they come with a working builder program and they walk you through the steps. im using Introduction to java programming by daniel lang BTW. i figure when i get a real solid grasp of j++ i can cross over to c++ relatively easy. long story short, get a college intro book and it will make it easier. And i wouldnt overlook taking a few classes at the local community college. its a lot easier when you have someone showing you how things work.:)

---

### Post by Master Shake on 2006-04-01
I just read about "Real Basic" which is a VB "compatile" programming language.  I may give it a try, seeing as you can also use it to develop programs accross platform.

---

