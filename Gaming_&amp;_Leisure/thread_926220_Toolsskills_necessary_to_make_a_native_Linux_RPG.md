---
title: "Tools/skills necessary to make a native Linux RPG?"
date: 2008-09-21
forum: Gaming &amp; Leisure
---

### Post by Holonet on 2008-09-21
I have an interest in creating an RPG native to Linux.  A friend and myself have been designing the idea/story aspect for a long time, and it recently occurred to me to screw publishing and money-making, and make a native Linux game (if possible).  Combined, we have the potential to do things like artwork and music and such.  Unfortunately, we're not programmers (aside from a paltry amount of C).  However, we've been working on this for years, and are not opposed to learning if necessary.

My questions revolve around just what the requirements are for this.  What I'm looking to do graphically is the isometric view as done in Final Fantasy 7 and 8.  I'm curious if anything has been done similar to RPG Maker on Linux...or just a method of creating "events" on a map.  If not (which I suspect), where does one start as far as tools and methods to create maps and sprites that can move over them?...Perhaps blender and Misfit?  A language best used for doing this.  Basically I'm confused as to what the steps are to creating a game engine, or modifying/using one that exists that would work for the aforementioned purposes.  Anyone know how to point me in the right direction and/or outline the basics?

---

### Post by Ethyrdude on 2008-09-21
You may want to look at Sauerbraten and cube 2.  While this is basically a first person shooter, there is no reason why you can't also use this game engine to create an RPG.  Instead of having one large map, you could have multiple maps using various cubes, that link back and forth depending on how you route the portals, use one cube for your starting town or camp, with enough room for some minor skirmishes to allow for character development and then add cubes as modules to grow your environment. 

This engine does support multi player interaction and could be developed into something huge, with many towns, different scenarios with virtually no limit, as players would only need to load one module at a time rather than the entire world.  As far as I know, there is already an RPG being developed using Cube2, there is no reason why you couldn't create your own using the same engine.

---

### Post by Perfect Storm on 2008-09-21
> **Ethyrdude said:**
> You may want to look at Sauerbraten and cube 2.  While this is basically a first person shooter, there is no reason why you can't also use this game engine to create an RPG.  Instead of having one large map, you could have multiple maps using various cubes, that link back and forth depending on how you route the portals, use one cube for your starting town or camp, with enough room for some minor skirmishes to allow for character development and then add cubes as modules to grow your environment. 

This engine does support multi player interaction and could be developed into something huge, with many towns, different scenarios with virtually no limit, as players would only need to load one module at a time rather than the entire world.  As far as I know, there is already an RPG being developed using Cube2, there is no reason why you couldn't create your own using the same engine.

Aye, there's already someone using that engine for making a RPG;

[http://gaming.gwos.org/doku.php/games:alphabetical:c:cube_2_eisenstern](http://gaming.gwos.org/doku.php/games:alphabetical:c:cube_2_eisenstern)

---

### Post by charlieg on 2008-09-22
The most important thing you can do is not believe you can do everything from scratch.  Many people come, think that, and fail.

First check out some engines.  [Sauerbraten]("http://www.sauerbraten.org/") was a very good suggestion already made.  That way you can not worry too much about the programming side of things and focus on the art and try and get a tech demo [which attracts contributors] together before tackling some of the deficiencies of whichever engine you are using.

---

### Post by Holonet on 2008-09-23
Thanks for the replies.  I agree that completing a game alone is a monumental task and unrealistic.

I've got ahold of the Sauerbraten engine for looking at.  I think it's great that there's a 3D engine that *can* be made to suit RPGs.  A few things that make me a little wary.  

Like I said, I'd like to do the isometric style view.  I'm not opposed to doing 3D.  In some ways, it might be easier than trying to make 3D models interact with a 2D environment.  I'm not crazy about the first-person aspect.  I suppose there must be a way to modify the camera positioning though.

One important thing for us is the customizability of battle system.  By that, using our own algorithms and creating stats that interact with each other as we choose.

Again, thanks for the suggestions, all are welcome.  Honestly, some of what I need to do is simply familiarization with terms like scripting for example.  I have a vague understanding of what a script is lol.  I understand it's a set of instructions, like one that can be incorporated into the Ubuntu shell for example...but how that's structured in a game and/or engine, among other things...well yeah.  Time to hit the books :popcorn:

---

### Post by swoody on 2008-09-23
I think an RPG would be an incredible task if sucsessfuly completed, but it is a TON of work, organization, skill, and time that will be required. Best of luck, and I'd be behind any effort like that :)

---

### Post by Holonet on 2008-09-24
> **smwoodruff0908 said:**
> I think an RPG would be an incredible task if sucsessfuly completed, but it is a TON of work, organization, skill, and time that will be required. Best of luck, and I'd be behind any effort like that :)

Nail on the head, and unfortunately, even the best RPGs have things about them that suck...silly things, which I wager are a result of just how much time and effort it does take to do it right.  Zelda:  Ocarina of Time was a good example.  Miyamoto pushed back that release date for AGES...I remember having Nintendo Power and watching the release date and going completely mad at it going back months...and eventually just said "future."  I wanted to kill him :-P...but hey, when I compare that game to the rancid sequels, I'd rather he take the time.  The commercial world doesn't allow an RPG to reach its full potential.

On the other hand, some things that are botched have no excuse.  I could rant on this subject for pages, but I'll digress lol.

We came up with the idea for this game about 8 years ago, and it gets off and on attention (story development mostly), admittedly; and it'll probably take 8 more to complete it in any form.  And sure, it's possible it won't get completed.  But gotta try it.  The bummer of it is we're not programmers yet...  The plus is we have all the time in the world, and we'll need it.  But along the way, there will be no 1st grader dialogue (Lufia), no sore-thumb plot devices (endless list here), insultingly easy puzzles (Chrono Trigger), near perfection to be ruined by a boss you can beat while high on chloroform (FF6), linear gameplay to the point of suicide (Illusion of Gaia), and certainly not the 31483274810th game whose depth of plot consists of kings, princesses, crystals, etc...

This is part of the point...  We LIKE those games I was ripping on just now...but so many nagging things that were done poorly and didn't have to be.

Another pet peave we have is the "difficult" games that the Japanese version differs from our "easy" version.  Most of the "difficulty" in these games is based almost entirely on battles, such that it takes more tenacity building levels than it does ingenuity.  So it's more you have to be patient than proficient. 

Have a look at the dialogue for some of these games, where there could be real challenge and depth by implied meanings, clues, etc...and you get stuff like "Monsters are appearing outside of town, just like the war 1000 years ago..."  "Are you saying the same thing is happening again?  1000 years have passed..."  ....feel like I'm in the special video game olympics here.  Things like that which game designers don't seem to think about in creating characters and many other things...the characters say things that make no sense for them to say in order to act as a plot device...1st grade writing ability.  It's like if two of us were to discuss bathrooms in the following fashion:...

"These toilets certainly are great, not like the old days when we had to dump our waste out the window and above-ground sewage 1000 years ago..."

So I guess I ended up ranting anyway :D...but to tell the whole story, that is a large chunk of the inspiration behind this idea.  Peace.

---

### Post by Bios Element on 2008-09-24
Yes, we 'all' think we can do it perfectly. Thus why people try. I think that's why every Program, Or for that matter anything is made. Because someone things they can do it better. It's not a bad thing of course.

**I was going to make this a bit longer but my fingers ache so I'm cutting it a bit short.*

---

### Post by Holonet on 2008-09-24
No doubt.  I would never claim to be able to do something perfectly, I suppose it sounded that way a bit though.  Better, yes--perfect, no.  There's really no such thing since people have different tastes and it's a subjective thing.  I just think some of the things that are overlooked just beg the question "why?"  So many great things are done in a handful of games, yet some things within those games are like walking to work and forgetting your pants :popcorn:

---

### Post by KatanaMonk on 2008-09-24
I like your idea, Im no expert But I can code a little.  Also could you tell us the plot?

---

### Post by Naegling23 on 2008-09-24
Im no game maker certainly, but I do have a concept that I had thought through a little while ago.

An rpg would create a huge burden with the storyline, artwork, etc that needs to go into it.  The best way to tackle something like that would be to create a game, complete with gameplay, mechanics, basic artwork, game world, etc.  Create a small storyline to go along with it.  But instead of trying to create 100's of hours of gameplay (artwork, weapons, dialog, quests, npc's, towns, etc) make it modular so that the community can add to it.  Sort of like how neverwinter nights did it.  They created a base game, but let the community make it into a huge game.  I would think that there is enough work to go into the gameplay and engine, that the storyline may suffer in the end.  By making it modular, the community can create the story, you would just want to give them a push.

---

### Post by Holonet on 2008-09-25
Yeah, there's going to be a mandate for us to learn some stuff, no two ways about it.  A while back I read most of C for Dummies, but that brings me no closer to understanding how to incorporate game events, graphics, etc....  Using an engine sounds fine though if it's modifiable as I mentioned.

The plot would be a massive undertaking to post lol...but the genre is sort of science fiction-ish.  A society is entirely deceived by a group of people who set up an organization to do the "dirty work," and become lazy and disconnected, and the organization becomes an altruistic society on its own--in essence an altruistic way of life as a result of a headless blunder.  There are different groups of people that evolved in different ways...twists and such.  The antagonist (aka last boss :-P) is dynamic in the same way...ends up "evil" because of his highly moral values which are unrealistic.  That's another pet peave...black and white good and evil.  Also, the plot is outlined, but the details and dialogue far from complete.

Thanks for all the interest and such.  Right now, I'm starting by reading about the sauerbraten engine...which first starts talking about it's data structure...so now I'm reading about data structures.  Heck, by the time we finish this thing, there should be tools that will let me talk to the computer and have it done in a few hours lol.

---

### Post by MaximB on 2008-09-25
If you want to create isometric fallout style game I can suggest using the FIFE engine : [http://fifengine.de](http://fifengine.de)
But I think you can only use spirits (fallout) and not full 3d (NWN).
This engine is still in development but I suggest you to try it.

There is also an RPG in development (full 3d, 1st person) using the J monkey engine : [http://www.jmonkeyengine.com](http://www.jmonkeyengine.com) , as it uses java based engine porting to other platforms should be very easy.

There is also the Crystal Space engine (full 3d) : [http://www.crystalspace3d.org/main/Main_Page](http://www.crystalspace3d.org/main/Main_Page)
, Planeshift mmorpg uses that engine.

There are MANY MANY MANY other free engines out there, just google for it ;)

---

### Post by Holonet on 2008-09-25
Thanks very much, I will investigate.

---

### Post by hessiess on 2008-09-25
personally I like C++ with Irrlicht.

---

### Post by ZarathustraDK on 2008-09-25
Actually, Sauerbraten can have 3rd-person view just like World of Warcraft, check out the rpg-maps that come with the latest version, they have it enabled by default. In those you are a little goblin/impish thing in frag-vest(?!) running around.

Come to think about it Sauerbraten-3rd-person-characters handle exactly like WoW-characters, although a bit fast. I also think Sauerbraten has the potential to look better than WoW, it has a ton of graphics-features WoW doesn't have (water-reflections, bump-mapping, etc).

Anybody wanna port WoW to Sauerbraten? :lolflag:

---

### Post by KatanaMonk on 2008-09-26
I love Sci-fi, And the plot outline seems interesting enough, What codebase does Sauerbraten use?

---

### Post by ZarathustraDK on 2008-09-26
> **KatanaMonk said:**
> I love Sci-fi, And the plot outline seems interesting enough, What codebase does Sauerbraten use?

Pass, I don't know I'm not a coder :)

Sauerbraten is based on Cube if that's what you mean.

---

### Post by bulletxt on 2008-09-27
I am personally starting to work out on an RPG with RPG Maker VX. the bad thing is that Wine still doesn't work very well with it, it's missing some parts .

---

### Post by Holonet on 2008-09-28
I just had a look at that program, and yeah, wine still doesn't quite cut it.  I'm not sure what the potential is with that one.  It'd be cool if we could put 3D maps in there as well as...well I'm dreamin' anyhoo hehe.

---

### Post by bulletxt on 2008-09-28
> **Holonet said:**
> I just had a look at that program, and yeah, wine still doesn't quite cut it.  I'm not sure what the potential is with that one.  It'd be cool if we could put 3D maps in there as well as...well I'm dreamin' anyhoo hehe.

Hi! rpg maker vx has very strong potentials for rpg's! there are a lot of "made scripts" from users. for example I will use night-day quests, limit breaks, turn combat in sideview like in final fantasy, skills, learning skills by experience ecc.

about 3d, yes it is possible!! look at this video from youtube it's great:

[http://it.youtube.com/watch?v=6RRF5KGseek](http://it.youtube.com/watch?v=6RRF5KGseek)

maybe we can join are "forces" together if you want.

---

### Post by itix on 2008-10-03
There are a bunch of open graphical engines around. Irrlicht is my favorite. I have been interested in it for some time. I too planned to create an RPG but I gave up my plans due to the scale of the project (and the fact that I couldn't connect the damn c compiler to eclipse).

If you don't mind, I'll be glad to help. I have some programming skills (mainly C++, java and minor python skills). Unfortunately though, I don't have any large-project experience. Are you planning to build your own engine or use some open source engine already out there?

As I said, I'd recommend Irrlicht.

OK, EDIT: I read the whole thread. C/C++ is probably what you want. Python is open source and quite easy to program, but it is an interpreted language and not a compiled one which makes it a bit flawed for games. It's ideal for common applications due to it not being very strict.

Irrlicht is an open source graphical engine that has some nice features. It's fairly easy to create a 3d environment

---

### Post by Holonet on 2008-10-04
Truth is, it would be a while anyway before any programming was ready to start.  I'm mainly trying to get a grip on what it truly involves.  I'm quite sure I'm not up for creating an engine, that'd take forever even if I were a seasoned programmer, I think.  I honestly am unclear what some of these things do...  except maybe blender.  I've been looking at blender, and there's a book for gaming that claims it to be uniquely suited for the task...that is...having game logic tools and such built into a 3D program.  Others I've installed like Ogre, I can't even find an executable to run the program, or a GUI, so I don't understand, being of little programming experience, how to even use it.  Then still I don't understand exactly what can be done with these "engines" as far as creating events for RPGs and such or object detection, a slew of other things, and what has to be done at a higher level in conjunction with that engine.  I basically get the concepts, but the specifics are rather elusive.

That in mind, I've been looking at blender, and that at least, is a little more clear.  It boasts the ability to be able to do all of the game logic, interactive stuff from within the 3d GUI.  That sounds attractive enough to me, at least as a means of familiarizing myself with the process.  If it can handle triggered events for an RPG, then even more so.  The only thing that I'm certain needs to be done outside the engine is the battle system.  which I'm assuming can be done with a simple Python script (which blender uses).  However, just how that works is unclear to me as well.  

Don't get me wrong, we've got no large project experience either hehe.  We simply have what we think is an excellent game idea, and I've been on here to try to figure out just what we're in for if we really try to program it.

The offers for help are much appreciated, but to be honest, I'm still just not even sure what exactly it is we'd need help *with* haha.

Another thing I should mention--we really don't *want* a 3D RPG, that is, one which the camera moves around and such.  We feel as though that creates too much focus on controlling the character and takes away from the "world" and relaxing nature of this genre.  This is why I mentioned the isometric view.  Given the available tools, it is my anything-but-experienced guess that using a 3D engine with the camera in fixed positions would not be a whole lot more troublesome than trying to get sprites to mesh well with a 2D backdrop.  It would also look plenty nicer.

---

### Post by charlieg on 2008-10-09
You could try adapting an existing engine like [Sauerbraten]("http://www.sauerbraten.org/").

---

### Post by punkbohemian on 2008-10-09
I thought I'd chime in since I'm in a similar situation.

Building an RPG (or any game) engine sucks. Ok, I'm being dramatic, but it's a lot of work. Then again, I'm not exactly as far as game design yet, so take it with a grain of salt. I would probably "borrow" something already out there, but there are some different things I want to do with system (regarding levels and character building) which I doubt any existing system can address (if so, I would be playing -that- game instead of working on my own).

I don't exactly have a strong programming background, so I've been teaching myself Python (and will eventually learn Pygame). I have a feeling that I'm going to also have to develop some skills in C#, but Python is a good language to start with for a non-programmer.

There's a free ebook called "Invent Your Own Computer Games With Python" that you should check out. Even if you don't do your own programming, it presents a very rudimentary idea as to what game design is like. I was a little surprised when I saw that it took around 300 lines of code for just a simple tic-tac-toe game using ASCII-based graphics.

While 3d graphics are "pretty", their functionality is vastly underutilized (i.e. a bit of a waste) in an RPG like FFVII+. I think it's possible to have just as compelling of a game using 2d isometric graphics (which will be much easier to build). What I'm using for visual inspiration is Final Fantasy Tactics (PSX). Technically, it's a 3d environment using sprites, but I'm hoping to work around that with a slight twist on a 2d iso.

Anyway, regarding the workload, I'm kinda hoping I'll be able to farm out sound, graphics, and possibly AI to other merciful souls (when I get to that point), and I'll put together the other elements myself. But, like I said, I'm pretty far from this point. Originally, I thought I'd try to do the whole thing on my own, but as the idea evolved, working solo became more and more absurd. You and your friend have an idea, I'd suggest trying to build a team with at least a few others who are interested in the project. Then, you all can divide the task into more digestible chunks.

---

### Post by UlteriorMotive on 2009-12-28
If you are going to program in C, then look into Programming Linux Games by Loki Games [http://www.mediafire.com/?rnnyyinztng](http://www.mediafire.com/?rnnyyinztng) . A very useful resource, but it's long.:popcorn:

---

### Post by Ferrat on 2009-12-28
Some time perspective of the different parts for a one or two man show doing a 3D rpg with unique models etc where there is active work but still just a hobby (from scratch to a small fairly basic rpg)
Creating a working 3D engine ~2years+ 
Creating the game engine for a RPG ~1-2years (depending a bit on complexity)
Creating models ~1year
Creating sounds ~1year
Creating tools for world development ~6-12 months 
actually putting everything together scripting, story, quests etc 1-3years

Now this is the least amount of time you should count on and this would be no highend Dragon Age :P and this is not really counting the time you you need to learn to do this stuff, a RPG is a massive undertaking and takes years even for a game company with people that have worked in the game industry for years and have ample knowledge.
I'm not saying it's impossible but you should be aware of the hugh amount of work you have to do even using ready 3D engines ect it's still years worth of production and most likely it will be at least a year or two before you can even show anything of value to others :)

---

