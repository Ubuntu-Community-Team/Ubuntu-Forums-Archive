---
title: "Syntensity: New FOSS Platform for 3D Games + 2 Games (FPS, drawing)"
date: 2009-10-23
forum: Gaming &amp; Leisure
---

### Post by kripkenstein on 2009-10-23
I'd like to bring your attention to a new open source platform for multiplayer 3D games, Syntensity. Here is a screenshot of the lobby (from where you can enter portals that send you into different games):

[[img]http://www.syntensity.com/static/screenshot_lobby_m.jpg[/IMG]]("http://www.syntensity.com/static/screenshot_lobby.jpg")
(click for bigger version)

Syntensity isn't a single game, but rather a platform that can run all kinds of 3D games. There are already a few games, and we and other people are working on more. Currently the main games are a racing game, a first/third person shooter (sort of like Quake 3 Arena), and a simple drawing game. All of the games are multiplayer (the racing and drawing games are also fun in singleplayer).

You can see both games in action in [size="3"]**[this video]("http://www.youtube.com/watch?v=J8KMwU1UJmw")**[/size].

**Links:**
[list]
[*][Website]("http://www.syntensity.com/")
[*][Screenshots and Videos]("http://www.syntensity.com/toplevel/screenshots/")
[*][Engine Page]("http://github.com/kripken/intensityengine")
[/list]


[SIZE="6"]Getting started [/SIZE]

[LIST]
[*][size="4"]**[.debs for Ubuntu on Playdeb (32/64-bit)]("http://www.playdeb.net/software/Syntensity")**[/size]
[*][size="3"]**[Downloads for other OSes]("http://www.syntensity.com/toplevel/download/")**[/size], instructions for how to compile from source if you want that, etc.
[*]Log in (you need to [register on the website]("http://www.syntensity.com:8888/accounts/register/") first), and then click 'connect to lobby...'
[*]It will download a little content (only stuff that changed since the .deb was built), and then you will enter the world you see in the screenshot above.
[*]Press 'H' for an interactive tutorial (it explains basic stuff like the controls).
[*]Further explanations appear in the [Quick Start Guide]("http://wiki.syntensity.com/introduction/quick-start-1") and [Introduction]("http://wiki.syntensity.com/introduction").
[/LIST]


[SIZE="6"]More Details[/SIZE]

Among the main features of this platform is that it downloads game content for you automatically. So once you have the Syntensity client installed, you can play any of the games without needing to manually download or install anything (like you can use Firefox to view websites). Also, when you create or modify a game, you can easily upload the new version, and then everyone can immediately play it. Basically, we are trying to make it as easy as possible to create and play 3D games.

Another major feature is that anybody can modify any game on Syntensity. So if you're playing a game and you think, "it would be cool if that weapon did more damage", or "the game would be more balanced if that position was less fortified", then you can modify a version of that game, and other people can play your modified version.

Note that this is what we are doing on Syntensity (letting anybody modify any game), but you are free to use the open source engine to run your own games, however you want.


[size="6"]Background and Engine Stuff[/size]

Syntensity is the result of about a year and a half of intensive coding, and also uses a lot of existing open source code. To briefly summarize, we started with Cube 2/Sauerbraten, made it much more flexible and generic, added a new scripting API using Google V8, and wrote a lot of infrastructure like asset distribution and management in Python.

The core engine is in C++, while games are written in JavaScript and plugins can be written in Python. The master (metadata) server is written in Python and Django. All the components (client, server, master server) are open source under the AGPL (note that just like Blender, the license only applies to the engine, not to games you make with it. You own copyright to your games and can license them however you want).

Binaries are currently available for Windows and Ubuntu (Ubuntu is where I did most of the development, btw, so it probably works better there ;)). Compiling on other Linuxes, and/or on 64-bit, is very easy.


[size=6]Summary[/size]

Disclaimer: There may be bugs, please let us know if you find one. If you are having trouble starting the client, try to run it on the commandline ('syntensity') to see the output (you can also get it to show more logging output, see [here]("http://wiki.syntensity.com/troubleshooting")).

Feedback is welcome, here, or on IRC (I - kripken - am usually on FreeNode, at #syntensity, #intensityengine, #ubuntu-gaming, etc.).

Thanks for reading this far :)

- kripken and the Syntensity people

---

### Post by Vadi on 2009-10-23
Impressive! Should submit to linuxgames.com too.

Waiting on Playdeb to package it so I can install on 64bit the lazy way.

---

### Post by samh785 on 2009-10-23
wow, this is really impressive! I'm definitely going to install this.

---

### Post by oldrocker99 on 2009-10-23
A most impressive project, and one that I hope more imaginative (and talented) people than I can make good use of for all!

:guitar:

---

### Post by kripkenstein on 2009-10-24
> **Vadi said:**
> Impressive! Should submit to linuxgames.com too.

Waiting on Playdeb to package it so I can install on 64bit the lazy way.

Playdeb just packaged it for 9.04, 32&64-bit: [link]("http://www.playdeb.net/updates/Syntensity") :)

As for 64-bit, I don't know much about how that works, but I have heard that
```

sudo dpkg -i --force-architecture PACKAGE.deb
```
should let you install 32-bit debs on 64-bit systems. So the existing 9.10 deb might already be usable on 64-bit that way. EDIT: Apparently you also need to install the 'ia32-lib' package.

---

### Post by 569874123 on 2009-10-24
Installing :)

---

### Post by conorsulli on 2009-10-24
The registration page is down....

---

### Post by kripkenstein on 2009-10-24
> **conorsulli said:**
> The registration page is down....

Strange, [http://www.syntensity.com:8888/accounts/register/]("http://www.syntensity.com:8888/accounts/register/") works for me.

What error are you getting?

---

### Post by inpxfx on 2009-10-24
its fun has alot of potential gpx were awesome even on high setting  on my computer no lagging what so ever. keep it up!!!:KS

---

### Post by CharmyBee on 2009-10-24
A customizable avatar system would be great for this, 

Ideas:
- Virtual trivia game show studio, feeding questions from a db using a text-to-speech service to speak the questions out aloud from the host
- Bumper cars
- Game within a game, executing x or terminal games and using them in a 3d panel in the world.

---

### Post by DeadSuperHero on 2009-10-24
I tried this out today on my underpowered Karmic laptop and I have to say, it runs like a charm. In fact, my first thought as I logged in and tested things out was "Wow, this is smooth!"

I'm looking into this project now with a lot of hope. To have a functional engine that can knock the iDTech stuff off its throne would be nice.

I'm curious though, is there a chance of Syntensity getting some kind of catalogue for games that build on its engine, sort of like a FOSS alternative to Steam? I think that could really give this entire project an edge over the numerous other gaming projects, as well as encourage budding developers to use standardized FOSS tools to deploy their applications.

---

### Post by hansdown on 2009-10-24
That is absolutely good stuff kripkenstein.

Keep at it.

---

### Post by kripkenstein on 2009-10-25
> **CharmyBee said:**
> A customizable avatar system would be great for this, 

Yeah, that is definitely something we are thinking about. It has to be done right, though, because if you can change how you look in every game, you can 'cheat', like by making yourself very very tiny and hard to hit in an FPS game ;)

But for the lobby and similar areas, it would make a lot of sense.

> 
Ideas:
- Virtual trivia game show studio, feeding questions from a db using a text-to-speech service to speak the questions out aloud from the host
- Bumper cars
- Game within a game, executing x or terminal games and using them in a 3d panel in the world.
Nice ideas :)

In particular the 3d panels showing other games would be cool. Maybe it could be done as a plugin somehow, but I really don't know if it's technically feasible.

---

### Post by kripkenstein on 2009-10-25
> **Mr. Psychopath said:**
> I tried this out today on my underpowered Karmic laptop and I have to say, it runs like a charm. In fact, my first thought as I logged in and tested things out was "Wow, this is smooth!"

Glad you like it :)

But we can't take all the credit for that, as most of the rendering stuff is due to Sauerbraten, and we are really thankful for the work they did (and support they give us). Also some of the speed is due to the Google V8 JavaScript engine which we use.

By starting from Sauerbraten, V8, etc., Syntensity was able to focus on the new stuff we wanted, like a flexible scripting API for game creation, asset/content distribution and management, etc., which together allow stuff like the portals in the screenshot.

> 
I'm looking into this project now with a lot of hope. To have a functional engine that can knock the iDTech stuff off its throne would be nice.

I'm curious though, is there a chance of Syntensity getting some kind of catalogue for games that build on its engine, sort of like a FOSS alternative to Steam? I think that could really give this entire project an edge over the numerous other gaming projects, as well as encourage budding developers to use standardized FOSS tools to deploy their applications.
Yeah, there are some similarities to Steam, in that you have a directory of games, and game distribution is handled automatically and transparently. Differences are that Syntensity has no DRM, all the games are moddable, 100% support for Linux, but also that all games must use our engine (in order to be sandboxed, something Steam doesn't need, but we do).

---

### Post by DeadSuperHero on 2009-10-25
So when all is said and done, will developers be able to submit games that use your engine to your catalog?

---

### Post by kripkenstein on 2009-10-25
> **Mr. Psychopath said:**
> So when all is said and done, will developers be able to submit games that use your engine to your catalog?
Well, right now, you can create games in Syntensity and run them on Syntensity's servers (or your own, of course). Those games would be in the main catalog, which can be seen [here]("http://www.syntensity.com:8888/tracker/activities/") (in raw form). Those are games which have been created (well, most were just started ;)), but are not necessarily running (but you can easily run any of them on a server).

The lobby with its portals is also a kind of catalog of games, which are currently running, and that we decided to add a portal to - there is limited space there, at the moment. We will certainly add nice games that people make to the lobby (if they agree).

Aside from that, you can use just our engine, without creating the game in Syntensity. In that case you can have your own catalog of games, user account system, and so forth - however you want. You can also make a game and put it both on Syntensity and in your own system (but synchronizing assets might be a little tedious).

The benefit to making games on Syntensity, as opposed to just using our engine, is that you can publish your game easily for anybody using Syntensity to play (and collaborate on), and that you can run games on our servers without needing to set up your own. The 'price' of making a game on Syntensity is that you agree to let everybody else on Syntensity play and modify it. I hope most people won't see that as a price, though :)

Ok, I think that summarizes the current situation. I'm open to ideas for improvements, btw.

---

### Post by DeadSuperHero on 2009-10-26
So then, in theory could one write an application that integrated with the Syntensity member system, provided some kind of member-based instant messaging, and pulled up a catalogue of Intensity-engine based games that connected with a server lobby?

Like a true alternative to Steam?

---

### Post by samh785 on 2009-10-26
Just wanted to say that I created an account for Syntensity and I expect great things from this project after seeing what it's like in-game first hand. This is a very well made project, and I was truly blown away with the presentation. It's totally user friendly, and I think that this has the potential to really take off. Viva la FOSS!

---

### Post by DeadSuperHero on 2009-10-26
I'm RazorSandwich on there if anyone wants to play.

---

### Post by kripkenstein on 2009-10-27
> **Mr. Psychopath said:**
> So then, in theory could one write an application that integrated with the Syntensity member system, provided some kind of member-based instant messaging, and pulled up a catalogue of Intensity-engine based games that connected with a server lobby?

Like a true alternative to Steam?

Sure, that's possible. It would be best to add those features to Syntensity itself, and I'd help with work on the patches. For example, currently we have instant messaging between members logged on the same server, but not between servers (or for people not currently on a server), so adding that would be nice. Also friends lists and so forth.

That stuff (messaging, friends lists, etc.) is on the roadmap, and as with any open source project, the more help we get the faster we'll get there.

---

### Post by sudhanshu_pandey on 2009-10-27
The Game Graphics are too cool. The game is great too.
.............................
sudhanshu
[google]("http://www.google.com")

---

### Post by Jestersage on 2009-11-07
I will be honest, syntensity is the main reason I go Ubuntu. Playing that Sauerbraten on Mac OSX makes me realize how good this engine will be, and the speed is far better than OpenSim/SL.

---

### Post by FiveSidedPoly on 2009-11-07
This is very exciting, I'll be looking into it more.  I'm a 3d artist working with a Indie Game Dev team.  I've been wanting to do some game work with Ubuntu.

---

### Post by Woojoo//.deb on 2009-11-08
i just tryed sytensity and it looks realy nice even if its just atm a beta it looks realy complete ^^

---

### Post by kripkenstein on 2009-11-26
Hi everyone, wanted to let you know about some updates:

[LIST]
[*]We have a new racing game, which you can see in **[this video]("http://www.youtube.com/watch?v=kXqbdwFirJA")** and this screenshot:

[[IMG]http://www.syntensity.com/static/screenshot_430540_s.jpg[/IMG]](http://www.syntensity.com/static/screenshot_430540.jpg)

You can get to the game from the lobby world.

[*]Version 1.1 has been released. Playdeb has updated to that version, and there is a non-Playdeb deb as well (see link on the first post in this thread).
[*]For the 1.1 release we made a **[new video](http://www.youtube.com/watch?v=J8KMwU1UJmw)**
[/LIST]

---

### Post by kripkenstein on 2010-01-09
We just launched a new game on Syntensity, a co-op FPS, called **Razanak**. There is a **[YouTube Video]("http://www.youtube.com/watch?v=1M80DN-5Xgk")**, and a screenshot here:

[[img]http://www.syntensity.com/static/screenshot_226138_s.jpg[/IMG]]("http://www.syntensity.com/static/screenshot_226138.jpg")
(click for bigger version)

More details in the [launch post]("http://syntensity.blogspot.com/2010/01/razanak-aka-swarm.html").

---

### Post by Ubuntiac on 2010-01-21
Damn! I'm impressed... :D

I'd love to see multiplayer, story / mission based fps stuff explored more. Imagine storming an enemy spaceship with a 100 other players to try and steal an alien weapon about to decimate your homeworld... The pieces are coming together... :D

---

### Post by mrphoenix on 2010-01-23
Please help howto download the .deb file!

Thanks!

---

### Post by jpv2 on 2010-01-23
> **mrphoenix said:**
> Please help howto download the .deb file!

Thanks!

I installed if from [http://www.playdeb.net](http://www.playdeb.net)
Just add repository

deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) karmic-getdeb games

and use package manager to install it.

---

### Post by portets on 2010-01-23
where do i go to give suggestions to the devs?

---

### Post by Bios Element on 2010-01-24
> **portets said:**
> where do i go to give suggestions to the devs?
Posting them here works. Kripken = a dev.

---

### Post by portets on 2010-01-25
well, i have a few suggestions for the painting game.

1. hold the right mouse button to erase. but only your own work.
2. someone in there one day said the ability to fly. i think that'd be great. and if it's too hard to implement you can just use the water from the other games for physics, just don't draw the water.
3. a pond in the corner.
4. **a bunch of buttons under the tv looking thing.**
  
  4.1 button to initiate fly-mode
  4.2 button to initiate solid walkable lines
  4.3 button to choose color without erasing work
  4.4 basically normal drawing tools from a drawing program, like square or circle tool.
  4.5 cube tool? :D

so, i know there's alot of stuff in my list. but they would make such a unique 3d drawing program.

oh, and THANKS for such a great game engine. i love the games so far and they look great and run very smooth at highest settings on my computer.

great work guys!  :biggrin:

---

### Post by Zerp64 on 2010-06-25
Getting about 10 fp/s average (game runs smoothly for about .5 seconds, then pauses for 1).

Where's the log file I can edit so I can post t?

*EDIT:* I just noticed my ping is 200+, and increases steadily when I hold tab (or however you get your connection information to show). Where's this thing hosted?

---

### Post by kripkenstein on 2010-06-26
> **Zerp64 said:**
> Getting about 10 fp/s average (game runs smoothly for about .5 seconds, then pauses for 1).

Where's the log file I can edit so I can post t?

*EDIT:* I just noticed my ping is 200+, and increases steadily when I hold tab (or however you get your connection information to show). Where's this thing hosted?
You can get it to run faster by changing the settings. For example, reduce the water effects, texture quality, etc.

The servers are in the east coast of the US, fairly cheap ones though, so don't expect great performance ;) But it should work fairly well for most of the US and Europe. You can also host your own servers of course.

Btw, the best place to get help is in #syntensity on FreeNode IRC, or on [our forums]("http://forum.freegamedev.net/viewforum.php?f=27").

---

### Post by Zerp64 on 2010-06-26
Sorry, I managed to fix it on my own but forgot about my post. I just got a new computer that doesn't support my last video card (agp). I sorta forgot that the silly 'graphics' thing doesn't work so well on integrated cards.

---

### Post by Helios747 on 2010-06-27
This looks impressive! I'm definitely installing.

---

### Post by djinnkeeper on 2010-06-27
Very fun to goof around with when you're alone, so it must be even more fun with others.  Played racing and insta-ctf.. again, alone.. but it was still neat.  Very smooth - was getting like 90fps most of the time; only went down to about 70 when I was under water.  Had a door sound effect not play after finishing a race, but that's the only real error I received.

Great job.  Keep it up. :guitar:

---

