---
title: "Revitalizing an old project."
date: 2008-02-13
forum: Gaming &amp; Leisure
---

### Post by RemmyLee on 2008-02-13
Back in 2004, I started working on a project to teach myself C/C++. It was to be a "clone" of The Legend of Zelda: The Minish Cap. I decided to use Allegro for it and managed to get quite a bit of the base done. The thing is, I was a windows user at the time and did almost all the work in Visual Studio.

A flood ended up destroying the computer I was using to create the game engine and it pretty much left my mind afterward.

Well, I recently remembered that I had put this on sourceforge, so I grabbed the code and started hacking away at it to get it running on Linux and managed to get most of it going, save the sound.

The images below are just placeholder graphics that I used for testing and I plan on recreating them using blender. This makes use of 2xsai, which anyone familiar with emulators will know as an incredible pixel scaling routine created by Kreed.

I know that 2D is "so retro" in this day and age, but if anyone is interested in it, I'll be happy to put the linux port up. The code is pretty well documented so it shouldn't be much of a hassle to understand. Perhaps someone could take the base and create a decent 2D isometric engine.

---

### Post by AvengingAngel718 on 2008-02-13
Maybe 2D is retro, but that doesnt mean it's bad. The game looks pretty cool.

---

### Post by Sockerdrickan on 2008-02-13
I love this game but I love Links awakening way more (best game ever) please make a clone of that one!! :KS

---

### Post by RemmyLee on 2008-02-13
It was my favorite as well. This is actually aiming to be a 2D engine, so it could essentially emulate any of the isometric Zelda games. A funny side effect of the conversion is the enemy sprites. Their movement and animations have become flipped. I'll work on that some tomorrow and try and get it all straightened out.

The best part is that Allegro offers pretty much all the tools needed, save the map data which was generated with Mappy. It runs fine under wine, so it'll be pretty easy to continue it.

[Here is a little video of it in action]("http://www.youtube.com/watch?v=EzToc9egnm0"). Sorry for the quality/framerate. I have a relatively old system.

---

### Post by Perfect Storm on 2008-02-13
2D is quiet ok with me (if you ask me ;) ). Graphic is nice but gameplay have highest priority in my book.
A game can look übergod and have total lousy gameplay as the developers tend to focus on what looks nice (seen too often in the commercial games nowadays IMHO).

---

### Post by Vadi on 2008-02-13
Imo, 2d is so not out. See Teewars, and awesome game.

That said, you thing looks pretty good too. Have you seen Love ([http://love.sourceforge.net/](http://love.sourceforge.net/)) though? Depending on how you feel like it, maybe you'll want to switch to that as a frame work, since it's a new & active project :)

---

### Post by charlieg on 2008-02-13
2D is great, stick with it.  Also let me know how you get on (freegamerblog@gmail.com) and I'll post you on Free Gamer and get you a bit of web traffic!

---

### Post by Beren Camlost on 2008-02-13
I play 2D and text-based games to this day, so keep up the good work :)

---

### Post by Steveway on 2008-02-13
> **Artificial Intelligence said:**
> 2D is quiet ok with me (if you ask me ;) ). Graphic is nice but gameplay have highest priority in my book.
A game can look übergod and have total lousy gameplay as the developers tend to focus on what looks nice (seen too often in the commercial games nowadays IMHO).

Exactly, the best example for that are the games by Introversion.
Uplink is awesome while it's graphically very well, unique.
Good Open-source gameengines are always welcomed.
BTW, what license do you use? I hope GPL.

---

### Post by disturbedite on 2008-02-13
this looks very nice.
you should consider (as an option) including blargg's ntsc filter to give it that old "ntsc tv feel".  his filter libraries are released under the LGPL.
here is the site:
[http://www.slack.net/~ant/libs/ntsc.html](http://www.slack.net/~ant/libs/ntsc.html)

---

### Post by RemmyLee on 2008-02-13
Wow. Thanks for the encouraging comments about 2D. You hear so many people talking about how Linux can't play this or that 3D game that I wasn't sure that it would be received with any enthusiasm.

To go in to a bit more detail about how it will work: 

Coding wise, you'll need to know next to nothing. Since the main character instance is already initialized. Enemies can be spawned by changing the number in the code. If you want 1 or a hundred, it's as simple as changing a number.

Maps are generated with an external program, so it is as simple as throwing them in to the source tree and adding:

#include mapname.h

The program will load up the data and display it. It uses a quad buffer system which allows for multiple layer maps as you can see in the video. It allows you to pass under objects.

Collision Detection is done on a 16x16 pixel basis while sprites are 32x32 pixels which gives you a really easy and accurate system to work with. Collisions are represented as 1 and walking areas are 0. Really simple.

Now the things that I need to add before it's of any use to game makers:

**Triggers**: I need to create a triggering system that is dead easy to use. For instance, when changing maps, you would simply do something like, 

if (coordx == 1213 && coordy == 547)
trigger(mapname);

The same would be used for cut scenes or special circumstances.

**Save System**: I plan to use an XML base for the save system as it is easy to work with and hack for people testing their games. It removes the need to mess with the code while allow full freedom to add remove any feature implemented by the game creator.

**Scripting**: I want to fully implement python for scripting, but do it in a way that is very easy to use.

**A make system**: I haven't decided if I should use autotools, cmake, or scons yet. I'm leaning towards scons for its ease of use and extensibility.

The idea being that there are a lot of "Game Makers" for Windows and they are all... well, they're awful. You have to rely on their tools and systems and never truly seem **yours**. This is all GPL'ed and uses mainly open tools for content creation, so you have freedom to do whatever you want.

Whether you are a programmer or not, you should be able to understand it without any trouble at all and be able to get started immediately.

Thanks for the link to the ntsc library. I'll definitely take a look at it and try to implement it.

EDIT
[The sprite data is fixed.]("http://www.youtube.com/watch?v=yYWT0O0ovh4")

---

### Post by RemmyLee on 2008-02-13
Okay. I encapsulated both enemies and NPCs in to the same set. For instance:

```
npc[2].Enumber = 0;
npc[2].Ex = 963;
npc[2].Ey = 745;
npc[2].Emax = 1;
npc[2].Ecounter = 0;
npc[2].EcounterMax = 4;
```

This says, "Enemy number 2 should use sprite set 0 and spawn 963 pixels on the x axis and 745 pixels on the y axis. Emax is the number of frames in a certain direction, 1 meaning two sprites. 0 and 1. Ecounter tells us to start drawing the sprite using animation block 0 and EcounterMax tells us that their are 4 animation blocks, 1 for each direction, up, down, left and right.

If anyone is running a 64 bit Linux variant, [here is a binary for you to play with]("http://uploader.polorix.net//files/1104/tlebuild.tar.gz"). Just note that it's in no way mature enough to really be useful and it doesn't contain enemy collision, so enjoy walking through them.

It requires the Allegro library, Alogg library and the 2xSai library that I've included. You can hit F1 to take a screen shot and 2,3,5 and 6 will toggle between the different pixel scaling routines. 1 and 4 use methods that I have yet to convert, so pressing them will segfault the progam.

---

### Post by CarpKing on 2008-02-13
Looks promising!

---

### Post by grossaffe on 2008-02-14
in a world where emulators thrive, 2d is never out of style.

---

### Post by disturbedite on 2008-02-14
> **RemmyLee said:**
> ...
You can hit F1 to take a screen shot and 2,3,5 and 6 will toggle between the different pixel scaling routines. ...
so does that mean you've implemented the (optional) ntsc filter?

---

### Post by Steveway on 2008-02-14
Yup very nice like I allready said.
Extending it to something like RPGmaker from Enterbrain with the possibiltiy to use python for scripts would make this more than awesome.

---

### Post by Nevon on 2008-02-14
Is there any way to get ones hands on the source code? I've really taken quite an interest to programming lately (I've only been dealing with web programming before), and getting a chance to look at your code could prove to be a valuable lesson.

---

### Post by RemmyLee on 2008-02-14
@disturbedite: I'm using a variant on the ntsc filter. 2 and 3 will look better on a computer screen while 5 and 6 will look better on a television.

@Nevon: I'd be happy to post it, but there are no makefiles in its current state. I started this project in Visual Studio 4 years ago and converted over the project files in code::blocks, then made some changes to get it running in Linux. If you or anyone else is interested in though, i'd be happy to post it.

---

### Post by RemmyLee on 2008-02-15
Okay. I had a few free minutes, so I went ahead and created a build environment for the engine using scons. I'll throw this up on Launchpad tomorrow, so if you know anyone that would be interested in contributing to it in any way, they can stop by the page, grab the source, join the project, any help will be appreciated.

---

### Post by santiagoward2000 on 2008-02-15
WOW!! Looks great!!
Good job! Keep it up!

---

### Post by Sockerdrickan on 2008-02-15
> **santiagoward2000 said:**
> WOW!! *Looks great!*!
Good job! Keep it up!


Yes *Nintendo* made those sprites though.:lolflag:

---

### Post by RemmyLee on 2008-02-15
Yep, but I'm trying to recruit some people to help with the project and just finished setting it up on Launchpad.

[https://launchpad.net/linkengine/]("https://launchpad.net/linkengine/")

I thought that this could be a great opportunity for us to show people that:

A. Not everything fun has to come from a Windows world.
B. That the Ubuntu community can collaborate and create something to share with other gaming communities. Remember, this is all cross platform so it will compile on Windows as well.

The source is up there. Check the README on compiling. :)

Now some questions for you:

Would you prefer this to stay a 2D engine or focus more on a complete 2D isometric game creator? I really want this to be a community effort so your decisions will decide the direction of it.

As for the art, here is the proposed octorok model:

[IMG]http://farm3.static.flickr.com/2231/2266081539_c6c872930d_m.jpg[/IMG][IMG]http://farm3.static.flickr.com/2341/2266081507_59062b2e51_m.jpg[/IMG][IMG]http://farm3.static.flickr.com/2101/2266081479_eea3952564_m.jpg[/IMG]
[IMG]http://farm3.static.flickr.com/2371/2266870174_3de35212fc.jpg[/IMG]

---

### Post by Extreme Coder on 2008-02-15
That's great looking!
Good luck with this project, I will be watching it! I am a great fan of Zelda after all ;)

---

### Post by Vadi on 2008-02-15
How can I download it?

---

### Post by RemmyLee on 2008-02-15
[Here is the latest revision. ]("http://uploader.polorix.net//files/1104/LinkEngine.tar.gz")

The README has all the instructions needed I hope.

---

### Post by Takmadeus on 2008-02-15
> **RemmyLee said:**
> [Here is the latest revision. ]("http://uploader.polorix.net//files/1104/LinkEngine.tar.gz")

The README has all the instructions needed I hope.

so, the quuestion is... doyou have a name for the project?.... it looks great, you did nice on reviving it

---

### Post by Sockerdrickan on 2008-02-15
why would it **not** be link engine ?

---

### Post by charlieg on 2008-02-15
That looks great but bear in mind that if you copy the graphics too closely you'll end up with copyright problems.  Probably best to be a bit more original and have different looking / named characters in your game.

---

### Post by RemmyLee on 2008-02-15
Actually, it won't have any of this in it when it's finished. It's an engine. People will have to provide their own sprite sets. These were just for testing. I'm clearing them out locally now and will release a dat set featuring basic outlined blocks once I actually have a little more coding complete.

The idea is simply to simulate the feel of the games while allowing people to use whatever they wish graphically.

About using these now. Nintendo has taken a very passive stance on fan created games. [Zelda Classic]("http://zeldaclassic.armageddongames.net/") is the best example and from what I hear, they are porting it to Linux. Woohoo!

---

### Post by Sockerdrickan on 2008-02-15
Where can I find lib x2sai so I can compile this?

---

### Post by disturbedite on 2008-02-15
cool.  i'm glad you implemented the ntsc filter.  (or a variant of it, which is interesting & a good idea imo).

---

### Post by Sockerdrickan on 2008-02-15
3D seen as 2D is always the best option these days.

---

### Post by RemmyLee on 2008-02-17
Just a little update to the build system here.

[http://uploader.polorix.net//files/1104/LinkEngine.tar.gz]("http://uploader.polorix.net//files/1104/LinkEngine.tar.gz")

As long as you have Allegro and Alogg installed from the repositories, you should be able to build this by simply typing **scons** now.

I wish I could have more time to work on this. It's awful having ideas running through your head and not enough time to make them.

---

### Post by Sockerdrickan on 2008-02-17
The src/2xsai/lib/unix/lib2xsai.a was 64 bit :P

---

### Post by RemmyLee on 2008-02-17
Oops! [Here you go]("http://uploader.polorix.net//files/1104/LinkEngine.tar.gz").

Sorry about that. Fixed again. Thanks for pointing it out. I wouldn't have caught that. No 32bit system.

---

### Post by madsmeg on 2008-02-17
This all looks very interesting, i will be looking into this when i get home (darn work using Windows :()

---

### Post by Sockerdrickan on 2008-02-17
> **RemmyLee said:**
> Oops! [Here you go]("http://uploader.polorix.net//files/1104/LinkEngine.tar.gz").

Sorry about that. Fixed again. Thanks for pointing it out. I wouldn't have caught that. No 32bit system.

It's the same file...

[www.sendspace.com](www.sendspace.com)

---

### Post by janfsd on 2008-02-17
> **RemmyLee said:**
> Oops! [Here you go]("http://uploader.polorix.net//files/1104/LinkEngine.tar.gz").

Sorry about that. Fixed again. Thanks for pointing it out. I wouldn't have caught that. No 32bit system.
For me that still didn't work. But I managed to compile lib2xsai.a by myself, so I attach it if anybody needs it. Just put it in src/2xsai/lib/unix/ and should work.
Btw, I attach a screenshot on how it runs on my system, it seems that just half of the screen appears, so Link is always on the middle. I dont know if this is a bug. 
Anyway keep the good work!

---

### Post by RemmyLee on 2008-02-17
Thanks for posting that. In 64 bit systems, certain pointer types work differently. Double precision. The problem is in buffer.h

Change:
```

	//---------------------------------------------------------
	// ASSIGN FILTERS TO BUTTONS AND ENABLE SWITCHING
	// (REFFER TO INPUT.H)
	//---------------------------------------------------------
	// FULLSCREEN STRETCH
	if (filter==4)
	{
		stretch_blit (buffer2, screen, 0, 0, screen->w, screen->h, 0, 0, screen->w, screen->h);
	}

	// FULLSCREN STRETCH WITH SUPER EAGLE
	if (filter==5)
	{
		SuperEagle(buffer2, saibuffer, 0, 0, 0, 0, screen->w, screen->h),
			stretch_blit (saibuffer, screen, 0, 0, 960, 640, 0, 0, screen->w * 2, screen->h);
	}

	// FULLSCREEN STRETCH WITH SUPER 2xSAI
	else if (filter==6)
	{
		Super2xSaI(buffer2, saibuffer, 0, 0, 0, 0, screen->w, screen->h),
			stretch_blit (saibuffer, screen, 0, 0, 960, 640, 0, 0, screen->w * 2, screen->h);
	}

	// SUPER EAGLE
	else if (filter==3)
	{
		SuperEagle(buffer2, saibuffer, 0, 0, 0, 0, screen->w, screen->h),
			stretch_blit (saibuffer, screen, 0, 0, 960, 640, 0, 0, screen->w * 2, screen->h);
	}

	// SIMPLE2X IMPLEMENTATION
	else if (filter==2)
	{
		Super2xSaI(buffer2, saibuffer, 0, 0, 0, 0, screen->w, screen->h),
			stretch_blit (saibuffer, screen, 0, 0, 960, 640, 0, 0, screen->w * 2, screen->h);
	}

	// STANDARD 1X
	else if (filter==1)
	{
		stretch_blit (buffer2, screen, 0, 0, screen->w, screen->h, 0, 0, screen->w, screen->h);
	}

}


```

To:
```

	//---------------------------------------------------------
	// ASSIGN FILTERS TO BUTTONS AND ENABLE SWITCHING
	// (REFFER TO INPUT.H)
	//---------------------------------------------------------
	// FULLSCREEN STRETCH
	if (filter==4)
	{
		stretch_blit (buffer2, screen, 0, 0, screen->w, screen->h, 0, 0, screen->w, screen->h);
	}

	// FULLSCREN STRETCH WITH SUPER EAGLE
	if (filter==5)
	{
		SuperEagle(buffer2, saibuffer, 0, 0, 0, 0, screen->w, screen->h),
			stretch_blit (saibuffer, screen, 0, 0, 960, 640, 0, 0, screen->w, screen->h);
	}

	// FULLSCREEN STRETCH WITH SUPER 2xSAI
	else if (filter==6)
	{
		Super2xSaI(buffer2, saibuffer, 0, 0, 0, 0, screen->w, screen->h),
			stretch_blit (saibuffer, screen, 0, 0, 960, 640, 0, 0, screen->w, screen->h);
	}

	// SUPER EAGLE
	else if (filter==3)
	{
		SuperEagle(buffer2, saibuffer, 0, 0, 0, 0, screen->w, screen->h),
			stretch_blit (saibuffer, screen, 0, 0, 960, 640, 0, 0, screen->w, screen->h);
	}

	// SIMPLE2X IMPLEMENTATION
	else if (filter==2)
	{
		Super2xSaI(buffer2, saibuffer, 0, 0, 0, 0, screen->w, screen->h),
			stretch_blit (saibuffer, screen, 0, 0, 960, 640, 0, 0, screen->w, screen->h);
	}

	// STANDARD 1X
	else if (filter==1)
	{
		stretch_blit (buffer2, screen, 0, 0, screen->w, screen->h, 0, 0, screen->w, screen->h);
	}

}


```

I'll add ifdefs to this in a bit so it'll work "out of the box".

I really wish that I had a volunteer to help with 32 bit issues as I have absolutely no access to a 32 bit system.

---

### Post by Sockerdrickan on 2008-02-17
I'm pretty sure you can somehow tell gcc it's gonna be 32bit, or you can run ubuntu32 with virtualbox

---

### Post by RemmyLee on 2008-02-17
Running a virtual machine on this computer is painful. I'd be fine compiling, but running it would be out of the question, so testing is pretty much impossible.

1.8GHz processor with 500MB of ram. It's like watching paint dry.

---

### Post by Sockerdrickan on 2008-02-17
Ok well good luck with this anyway!

Some notes:
It feels like I walk faster vertically
You can hold down forward,backward keys and he stalls, same with left, right

When you've fixed this I'd recommend adding code for Link to get hurt by the octos :)

---

### Post by janfsd on 2008-02-17
I can help testing the 32 bit versions.
Now it works. Is it suppose to make any sound?
Btw checkin the project of zeldaclassic, it seems there are linux builds, however without sound. Other thing is that it isn't open source.

---

### Post by RemmyLee on 2008-02-17
The sound system is in there, I just haven't "turned it on" yet. I used ogg files for sound. The compression to quality ratio was pretty good in 2004 and I never really thought size limitations. It would be just as easy to throw in a different library such as APEG that would support a lot of different formats.

The problem with my current sound system is that the library I used to create it is no longer developed and seems to have vanished. There was a certain release that I used and the one in the repositories is different. I'll work on getting it back in there next.

Then it'll be time to actually start adding new features. Thank you very much for testing it for me.

Almost forgot, you'll notice the huge peak in processor use. This is the graphics routines at work. I'm thinking about using OpenGL to draw the output to a plane which will introduce hardware acceleration and the possibility of adding some primitive 3D support.

---

### Post by janfsd on 2008-02-17
Yes, I just noticed the huge peak on one of my processors. 
About the sound, I was asking, because I saw the sound library, so just to be sure everything is running ok. Well the alogg library on the repos is newer than the one you use, and it seems shorter. I tried to compile with sound support by uncommenting some lines of your code but so far no good.

---

### Post by RemmyLee on 2008-02-17
Yeah. I'll look at the new version and try to find the incompatibilities so I can get it running. I was going to work on that next, but after mentioning possibly using OpenGL for rendering, I had to at least attempt it and it's almost done. I'll have to work on my frame limiting some however. It's extremely fast. It's not finished yet. I'll have to reposition the plane and resize the blitted output.

---

### Post by RemmyLee on 2008-02-20
New sound system coming down the pipe. 64bit only currently. Threw out the old code completely and went with SPC700 after reading up on the format.

[Here is the test]("http://uploader.polorix.net//files/1104/linkplay.tar.gz").

To run it:

./linkplay Zelda.spc | aplay -f S16_LE -r 32000 -c 2

It'll be integrated with the next commit. SPC creation tool to follow.

---

### Post by janfsd on 2008-02-20
Great to hear that, when you make a 32bit version I'll test it.

---

### Post by RemmyLee on 2008-02-20
As soon as I get the scons system fixed up for it, I'll commit it and post it here. There will be an OpenGL branch coming too. Got that all worked out. Preparing GUI based tools for creating sprite sets and maps after this. Once I have that down decently, I'll finish enemy collisions, fix up the movement a bit, and start building an inventory/life system.

There needs to be more hours in the day.

---

### Post by Beren Camlost on 2008-02-20
> **RemmyLee said:**
> There needs to be more hours in the day.

Oh, I soo wish.. :)

---

### Post by CarpKing on 2008-02-20
Now someone needs to start coming up with a great plot for such a game.

---

### Post by Beren Camlost on 2008-02-21
> **CarpKing said:**
> Now someone needs to start coming up with a great plot for such a game.

RemmyLee had cookies. Then the dark and evil Beren Camlost came and stole his cookies (presumably, cliche-style, he killed his family in the prosess). Time passes. RemmyLee, eager for revenge, sets out on the long adventurous journey to free his cookies and avenge his family. To be continued..

:popcorn:

---

### Post by RemmyLee on 2008-02-21
haha

I'm going insane trying to figure out the best way to drop the sound engine in to the existing code. While I have been trying to figure that out, I've been working on porting a tool that will take MOD, IT, or XM files and convert them to SPC format so you can use simple tracker software for creating your game music.

In the example above, I have the data being piped out to STDIN, and then I'm using aplay to grab it and output it to the speakers. I would use this in the engine except I have absolutely no idea how to communicate inetmediately with pipes.

popen() opens the stream and expects wait4() before terminating the stream and returning to the program. pclose() will not work until said stream has been closed. I've tried to send a carriage return to the stream with fputs() but it doesn't seem to work, so I may need to write a new method of terminating the stream or find/write a library to handle it.

---

### Post by RemmyLee on 2008-02-22
Finished porting the software for SPC creation.

[Here is the source]("http://uploader.polorix.net//files/1104/xm2snes.tar.gz") and [here is the original website]("http://ekid.nintendev.com/xms/") containing the original source and the documentation.

Use scons to build. No extra libraries are needed. The documentation is lacking a bit, so I am trying to translate some Japanese sites that go in to detail about its usage so I can hopefully provide a decent tutorial on using it efficiently.

---

