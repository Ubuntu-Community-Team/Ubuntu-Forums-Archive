---
title: "A New Game For Ubuntu"
date: 2006-10-25
forum: Gaming &amp; Leisure
---

### Post by curvedinfinity on 2006-10-25
Hey Everyone,
I am releasing a new game called Finity Flight II. It is a 2D top down shooter with very nice graphics for a 2D game. What makes it special, however, is that I intend to release a new episode of it every week. This means new things to do and a new bit of an on-going story.

Being that Ubuntu is my OS of choice (I am a HUGE fan of it), I figured I would give the Ubuntu community first dibs at testing it out and playing with it.

Please visit its website for more information and a link to download:
[http://ff2.curvedinfinity.com](http://ff2.curvedinfinity.com)

And just in case you don't read the readme, make sure you have libSDL, libSDL_ttf, and libSDL_image installed.

Here is a screenshot:
[IMG]http://ff2.curvedinfinity.com/wp-content/uploads/2006/10/ff2-1-preview.jpg[/IMG]

---

### Post by ghaz on 2006-10-25
Just downloaded it. Looks very nice and I like the small download size.

I'll definately play a bit tonight at home. Can't get the drivers for this old ati card in my lab pc to work.

---

### Post by airtonix on 2006-10-25
sweet work man, could you add support for mouse controls and custom keys?

---

### Post by curvedinfinity on 2006-10-25
I personally don't mind the current control scheme and I personally don't see a reason to change it, but if more people want it customizable and with mouse support, you can expect it to be added. :)

---

### Post by Lord Illidan on 2006-10-25
Bloody hard for a first level...can you make the controls customisable? I don't like WASD keys..much prefer forward up right down arrow keys meself.

Nice graphics.. but control is sorta unresponsive. Also, no sound?

---

### Post by curvedinfinity on 2006-10-25
Hehe, thats two for the customizable keys. :)

EDIT: Oh, and the arrow keys are already mapped to something ... special :D

Its good that you find it to be a challenge, as I was going for that! I am hoping that the challenge will make it very replayable -- there are even some things you will find in the level which are extremely difficult to accomplish, but will add a very good deal to your score.

EDIT: Ive managed to get around 5200, but it is possible to get well over 10000 points (yes, saving both wingmen IS possible and will net you a giant lot of points if you can do it).

Also, I have had a few comments about the sound. Being that I am the only person working on this game, its really a matter of time, as I have previously worked on projects making both sound assets and programming sound systems. It was really a matter of whether people would like the game to be released every two weeks with sound and a 15 MB download, or a nice tidy download released every week.

I have a section in FF2 forum where anyone is able to submit ideas, artwork, or perhaps sounds for use in an episode. That being, in the future, I will program and include a sound system if the Finity Flight II community creates the assets. :)

---

### Post by curvedinfinity on 2006-10-26
Everyone, I have posted some new articles, including two spoilers, on ff2.curvedinfinity.com.

I hope everyone can't wait for Episode II, which is entitled "Broken Promises." It will be released next week.

---

### Post by simplyw00x on 2006-10-26
This game is simply awesome, and supremem kudos to you for making it. I seriously suck though; high score of about 1500 :(

---

### Post by curvedinfinity on 2006-10-26
Mind if I quote you on the website simplyw00x? :)
EDIT: too late! (check the super-header) 8)

---

### Post by slimdog360 on 2006-10-26
I couldnt find the download link.

---

### Post by tzulberti on 2006-10-26
here: [http://ff2.curvedinfinity.com/?p=13#more-13](http://ff2.curvedinfinity.com/?p=13#more-13)
But i think that curvedinfinity should put a download link in the left menu....

---

### Post by ZylGadis on 2006-10-26
I apologize if the answer is obvious, but the site is a bit confusing. Where can I download the source from?

---

### Post by tzulberti on 2006-10-26
I have been looking for the same but I have not found any. Also, under what licence is the game (GPL, LGLP, etc..)?

---

### Post by d3v1ant_0n3 on 2006-10-26
What are the system requirements for this game?

All I got was a grey window, and then a frankly fantastic lock-up. So that was fun.

---

### Post by curvedinfinity on 2006-10-27
I was a professional game developer, but I decided that the current structure of game-making could be made better. So, this is now my job. I would have liked to make the game open source, and I will eventually, but for now, freeware is the best I can do.

The game requires an OpenGL 1.1 compatible 32MB graphics card.

I'll make the download locations more apparent.

---

### Post by simplyw00x on 2006-10-27
No problem :P

---

### Post by ZylGadis on 2006-10-27
There is a problem, actually. You should not claim that the game is free when it is not. Freeware is not free speech.

Other than that, good luck.

---

### Post by MonkeyBoy on 2006-10-27
That is a bit harsh.  I haven't noticed Curvedinfinity making any false claims about the game, it's licence, or matters of freedom.

---

### Post by curvedinfinity on 2006-10-27
Maybe the game isn't released under the most appreciable license (being free of cost, which is a good start, may I add), but at least I am trying to advocate Linux and other software which is, and I need a platform to do it, so in my eyes, its worth it.

---

### Post by TheMono on 2006-10-28
I wasn't aware the term free software was now no longer applicable to software that is cost-free? I wouldn't call if free / libre software, but free software it is.

Thanks for developing it! You're helping fill an important part of the linux world.

---

### Post by Sukarn on 2006-10-28
Thanks for this great game, though I would like the controls to be customisable as well.

---

### Post by curvedinfinity on 2006-10-29
Hehe, I'm testing a battle in episode II now between 2000 enemy Lockeye drones vs you and 14 other falcons. :)
[IMG]http://ff2.curvedinfinity.com/wp-content/uploads/2006/10/ff2-2-preview.jpg[/IMG]
-- from the preview at ff2.curvedinfinity.com

---

### Post by _simon_ on 2006-10-29
All I get is a grey window and nothing happens, I have to force quit.

Your first post mentions some libsdl packages that need installing. I can't find any with those exact names, I do have these installed though:

libsdl1.2debian
libsdl1.2debian-alsa
libsdl1.2-dev
libsdl-image1.2
libsdl-image1.2-dev
libsdl-mixer1.2
libsdl-net1.2
libsdl-ttf1.2
libsdl-ttf2.0-0
libsdl-ttf2.0-0-dev

Am I missing something?

---

### Post by curvedinfinity on 2006-10-30
Those are the only dependant libraries, and it looks like you have the right ones (you shouldn't need the -dev ones).

It sounds like an opengl init problem... do you have a video card?

---

### Post by _simon_ on 2006-10-30
> **curvedinfinity said:**
> Those are the only dependant libraries, and it looks like you have the right ones (you shouldn't need the -dev ones).

It sounds like an opengl init problem... do you have a video card?

I have a Geforce 6800 using the nvidia drivers. I don't have any problems running games normally, in fact I play Unreal Tournament 2004 daily.

Edit: I just got it to work. Previously I was just trying to run it from where it extracted to (Desktop) I just tried putting it in a folder and it now runs!

I have no sound though, is there sound in this release?

---

### Post by curvedinfinity on 2006-10-30
Thats an odd problem ... perhaps it had something to do with the config file. The screen clears to white if GL is initialized, and there are only two things that happen before that, those being loading that config file and initializing SDL.

No, there is no sound. Hehe -- I need an FAQ with that question in it (its been asked a few times). The reason for this, if you are wondering, is the fact that I don't have time in a week to make all the sounds for the new things that go in. This might change in the future if the community helps out making assets for the game.

Thanks for trying it!

---

### Post by MaximB on 2006-10-30
this game is hard as hell...the mines are one thing...but the shooting in the back...it's hard...
but great graphics - thanks.
good work !

can you say how did you make this game, I mean which programs you used to create it ?

---

### Post by plb on 2006-10-30
Thanks for the hard work, keep it up...Linux needs more quality games. Perhaps you can make a command and conquer clone for us? :)

---

### Post by curvedinfinity on 2006-10-30
I used inkscape to make the source for the ships, which I then edited a bit with gimp. The clouds and terrain are made exclusively with gimp. I'll put up some tutorials in the coming weeks that explain how I made the assets.

The actual programming is C++ using some wrappers I made for SDL.

Also, I put up some links at the bottom of posts to put the post on news websites. There is one for Digg and one for del.icio.us. This is a good way to let more people know about my game. :)

EDIT: Also, a good score to shoot for is 5000. -- That generally requires saving one wingman, and a time bonus of 2700 coming out of the minefield.

EDIT: I just posted the last secret spoiler for Episode I.

---

### Post by MaximB on 2006-10-31
I'm dead in 10-20 seconds... ;)

I really think that the mines were a BAD idea.

---

### Post by curvedinfinity on 2006-10-31
Perhaps only because you don't get through them. :)

Lucky for you, there are no mines for you to fly into in Episode II, just tons and tons of enemies.

---

### Post by kopilo on 2006-10-31
I'm finding it is not working on Ubuntu drapper 64.

"error while loading shared libraries: libSDL_image-1.2.so.0: cannot open shared object file: No such file or directory"

Thus I tried to install it via aptitude...
"Couldn't find any package whose name or description matched "libSDL_image" ".

Edit: are you also going to submit it to somewhere like "megagames.com" by the looks of it I'd definatly say it is up to that standard.

---

### Post by curvedinfinity on 2006-10-31
The name of the package in the Ubuntu repos is libsdl-image1.2 -- the actual library that is installed is libSDL_image. 

By the way, the executable is 32 bit and I haven't tested it on a 64 bit system yet, so please inform me of how it goes.

---

### Post by bastiegast on 2006-10-31
Thats one pretty good looking game. Amazing! 

Did you do it all by yourself? Makes me wanna start learning C right away :p  I only have mastered Java myself.

But dmn.. First level is so hard ](*,) 8) 

Personally id prefer to be able to navigate the menu with my keyboard.

---

### Post by curvedinfinity on 2006-10-31
> **bastiegast said:**
> Thats one pretty good looking game. Amazing! 

Did you do it all by yourself? Makes me wanna start learning C right away :p  I only have mastered Java myself.

But dmn.. First level is so hard ](*,) 8) 

Personally id prefer to be able to navigate the menu with my keyboard since.
I am the sole creator. -- The same effects are possible in Java using the JOGL OpenGL bindings, which support up to OpenGL 1.3 I believe (FF2 uses functions from OpenGL 1.1). :)

---

### Post by Marsan on 2006-10-31
Hey. Your game looks good. Only i cant get it to work. Do i need to install it or somthing. Or is it me beeing a noob and missing the obvious about starting this game?

Marsan


Edit: Ok, i just needed the sdl packages.

---

### Post by curvedinfinity on 2006-10-31
> **Marsan said:**
> Hey. Your game looks good. Only i cant get it to work. Do i need to install it or somthing. Or is it me beeing a noob and missing the obvious about starting this game?

Marsan

The most common problems are not having a graphics card and not having the libraries which are stated on the first page. Those libraries are libSDL, libSDL_image, and libSDL_ttf. Their package names are different so search synaptic for libsdl.

---

### Post by Marsan on 2006-10-31
hehe..yeah..i just needed the libsdl packages. Damn this games is nice looking, and hard! Im pretty colorblind and this game sure takes a great antvatage of my messed up eyes.

Edit: How do i make a starter for this game? When i just use a starter to /home/marsan/.ff2-1/ff2-1 i get a grey window. I really love this game.

Edit2: Oh..it`s not the longest game but its damn nice. I hope u continue build updates and extensions of the game. As i said..love it.

---

### Post by curvedinfinity on 2006-10-31
> **Marsan said:**
> hehe..yeah..i just needed the libsdl packages. Damn this games is nice looking, and hard! Im pretty colorblind and this game sure takes a great antvatage of my messed up eyes.

Edit: How do i make a starter for this game? When i just use a starter to /home/marsan/.ff2-1/ff2-1 i get a grey window. I really love this game.

Edit2: Oh..it`s not the longest game but its damn nice. I hope u continue build updates and extensions of the game. As i said..love it.
Another person was having issues with the location of the files, but he seemed to have mysteriously resolved the issue by containing all of the files in the same folder. 

-- I would double check that the data directory and config file are in the proper places.

Also, there are many extra things to accomplish. You can search the level at various points in time and find a few hidden things. Also, there are hidden objectives that will add to your score considerably.

And as I have mentioned in a couple spots, its planned to have a new episode every week. Tomorrow will be the release of the second episode. :)

---

### Post by kopilo on 2006-11-01
> **curvedinfinity said:**
> The name of the package in the Ubuntu repos is libsdl-image1.2 -- the actual library that is installed is libSDL_image. 

By the way, the executable is 32 bit and I haven't tested it on a 64 bit system yet, so please inform me of how it goes.
I re-installed libsdl-image1.2 unfortunatly there doesn't look to be anything with libSDL_Image in the 64 repos (yes I have both multiverse and universe enabled).

I tried running by typing "Linux32 ./ff2-1" but it still came up with the same error. >_<

---

### Post by MaximB on 2006-11-02
make the file "ff2-1" executable.
then run it
>ff2-1
done.

---

### Post by curvedinfinity on 2006-11-02
By the way, if you guys didn't catch it, I released Episode II yesterday. :)

---

### Post by Marsan on 2006-11-02
W O W!

Episode II rocks! Sweet first fight. Much better than episode I :D keep up the good work.

---

### Post by curvedinfinity on 2006-11-02
Someone asked about how I made the assets for the game -- I just put up a tutorial -- so check the website.

[ff2.curvedinfinity.com]("http://ff2.curvedinfinity.com")

---

### Post by jawa83 on 2006-11-02
Umm, for me the game runs unplayably slow. FPS is about 1/3. I have an ATI Radeon 9200 video card on a 2GHz FS-Scaleo. Is my computer just too slow or is there something I can do about it?

---

### Post by curvedinfinity on 2006-11-03
Chances are the game won't be playable on many ATIs, given their rubish drivers on linux -- I would bet that you could play it on most of the X series ATIs and newer though. 

Sorry, but there isn't much I can do aside from recommend you to buy a new card. Just for your information, though, I've tested the game on a GeForce 4, and it runs at around 60 fps. I really have a bad taste in my mouth as well from ATI, as when I was getting into linux I had an ATI. 

-- If you do upgrade (as you will find low framerates in hardware-accelerated aps a common problem with your current card), I would recommend a 6800XT, which you can find for right around $100 [some places]("http://www.newegg.com/Product/Product.asp?Item=N82E16814141038"), and it still has the AGP interface. -- This card will play FF2 at around 300 FPS.

Hope this helps!

---

### Post by hyper7 on 2006-11-03
I hope episode two is easier than episode one.  The first episode is basically impossible.

---

### Post by Lord Illidan on 2006-11-03
> **hyper7 said:**
> I hope episode two is easier than episode one.  The first episode is basically impossible.

I never survived longer than 1-3 minutes...and I do well at HARD with gl-117...

Please make episode 1 easier, or else get difficulty settings up and running.

---

### Post by hyper7 on 2006-11-03
One minute sounds about right here. 

It's a pretty game thus far.  Keep up the good work.

---

### Post by curvedinfinity on 2006-11-03
Hehe, it will be hard forever -- and it is definitely beatable! I've even beat it once with both wingmen surviving. 8) -- so ha! You guys will have plenty to do with the new episodes -- especially episode IV, which I will say more about next week. ;)

I would like to hear more about episode II if anyone has comments? -- I've only heard "its awesome" so far, and that doesn't leave much room for improvement. :)

---

### Post by hyper7 on 2006-11-03
I can't get interested in a game that only allows me 1 minute of play time.

YOU keep saying you can get past it.  Perhaps I should read back, but I don't think I've seen anyone else say they've gotten past it.

Kinda makes it seem like a weird joke.

---

### Post by curvedinfinity on 2006-11-03
I think two people in this thread have infered that they beat the first episode. If you are so upset about not beating it, you can read the spoilers or just skip to episode II. :)

And if you are still in disbelief, I can FRAPS a run through.

---

### Post by hyper7 on 2006-11-03
> **curvedinfinity said:**
> I think two people in this thread have infered that they beat the first episode. If you are so upset about not beating it, you can read the spoilers or just skip to episode II. :)

And if you are still in disbelief, I can FRAPS a run through.

I'm not trying to be hard on you about it.  It seems I can't shoot mines fast enough to continue progressing forward.  The enemy ships aren't even a problem, the problem is that the mines take too long to destroy.  Maybe I should put a macro for my keyboard to rapidfire? ](*,)

---

### Post by Sukarn on 2006-11-03
> **hyper7 said:**
> I'm not trying to be hard on you about it.  It seems I can't shoot mines fast enough to continue progressing forward.  The enemy ships aren't even a problem, the problem is that the mines take too long to destroy.  Maybe I should put a macro for my keyboard to rapidfire? ](*,)
[COLOR="Red"]**_SPOILER WARNING_**[/COLOR]

You destroy the mines in the beginning? I just go past them by slowing down the ships. It doesn't take much time.

---

### Post by hyper7 on 2006-11-03
> **Sukarn said:**
> [COLOR="Red"]**_SPOILER WARNING_**[/COLOR]

You destroy the mines in the beginning? I just go past them by slowing down the ships. It doesn't take much time.

Great, now i feel stupid.

But he kept making it seem like the time you got through the level was important, so i never figured slowing down was a good idea.. 

*sigh*](*,)

---

### Post by curvedinfinity on 2006-11-03
For anyone interested in how I made the game, I just released the source for the library I made for it under the LGPL. :)

Its called libcig-a, and is designed to be as simple as possible -- I can almost say that anyone who has never thought about programming graphics could use it without even looking at a tutorial, its that straight-forward. I hope this helps the Linux gaming community!!

Here is the link:
[http://ff2.curvedinfinity.com/?p=30]("http://ff2.curvedinfinity.com/?p=30")

---

### Post by curvedinfinity on 2006-11-03
Here is a screenshot from one of the demo aps included with the source:

[IMG]http://ff2.curvedinfinity.com/wp-content/uploads/2006/11/fractal-screen.png[/IMG]

:)

---

### Post by ZylGadis on 2006-11-03
Great! :)

---

### Post by kopilo on 2006-11-04
> **curvedinfinity said:**
> Chances are the game won't be playable on many ATIs, given their rubish drivers on linux -- I would bet that you could play it on most of the X series ATIs and newer though. I have an ATI Radeon 9200 SE, works fine on my Windows XP partition.

---

### Post by simplyw00x on 2006-11-04
I have a 9200 radeon and it works on linux.

---

### Post by kopilo on 2006-11-04
I'd like to have quicker/sharper turning when slowing down the ship.

EDIT: It'd feel more like flying a plane rather then sking.

---

### Post by curvedinfinity on 2006-11-04
Thats great news then. :) -- And just a request: If anyone has an older card  that plays Finity Flight II well, can they tell me in some way? Like old being GeForce 4 or Radeon 8 series or older. I would expect that this range of cards is where it becomes unplayable, but I haven't actually seen it under 60 fps ever.

---

### Post by curvedinfinity on 2006-11-15
Hey Everyone,
I just gave FF2's website a new look -- please comment!

Here is a link:
[ff2.curvedinfinity.com]("http://ff2.curvedinfinity.com")

And if you didn't catch the last post, a new episode was released a couple days ago.

---

### Post by loell on 2006-11-15
hi cool game, and cool site

any particular reason why the source code is not made available in the download link?

---

### Post by loell on 2006-11-15
ah i see, the license is not gpl

---

### Post by curvedinfinity on 2006-11-15
Despite the fact that I probably won't ever release the game under the GPL, I probably will release the source, as there isn't any reason to hide it. I just don't want those big "1000 FREE GAMES!" websites to put FF2 on their websites without linking to me or anything -- so thats why its currently not available.

---

### Post by loell on 2006-11-15
i totally understand, you seem to be a developer whose got eyes and ears for your users, 

so keep up the good works :)

awesome game :KS

---

### Post by curvedinfinity on 2006-11-15
Haha, I am just as fed up with bloated profiteering software companies as any other linux user. :)

---

### Post by MaximB on 2006-11-15
are you thinking of creating other games ? (not FF ;))

---

### Post by curvedinfinity on 2006-11-15
I'm sure there will be other games, but for at least the next few months, don't expect anything but FF2. :)

---

### Post by MaximB on 2006-11-15
the one type of game that almost doesn't exists in Linux is fighting game - one on one fighting game
Like mortal kombat (yeah we have open mortal, but it sucks) and street fighter.
I wish that this kind of game would be created for Linux.

---

### Post by hoagie on 2006-11-15
Great game, although I can't even get past the first level](*,)  Is it really meant to be hard or am i just stupid?

Just got past the first level, man this game rocks, great work!

---

### Post by curvedinfinity on 2006-11-15
The first level is really hard -- I think a lot of people have had some confusion with the mines, though. If you are trying to shoot them, they can't be destroyed. -- There are also some spoilers that you can find on the site that may help you out. :)

---

### Post by 23nt3x on 2006-11-15
For sound since its open source development why not DL the source files for The Hand That Feeds and Only off of nin.com and incorporate them into the game? Shades of Doom!

The Source files for them can be found in the Current sections Archive on [www.nin.com](www.nin.com)
Its on the 2nd or 3rd page...

The files for THTF are in Garage Band Format for Mac, and the Only files are in a bunch of different formats. All you have to do is convert them to a usable file type.

"You think you're evil; but you're not M00 OMM!" -ohGr Cracker. From the album Welt.... Buy it. It has a bunch of pitch shift secret tracks as does SunnyPsyOp. 

Just for trivia what is a Psi-Op in Military and Intellegence (spy) terms?

---

### Post by curvedinfinity on 2006-11-16
If anyone is interested in the art in Finity Flight II, I am considering releasing it under the LGPL. Read more [here]("http://ff2.curvedinfinity.com/forum/viewtopic.php?id=11").

---

### Post by Mr_HeNtAi on 2006-11-16
Looks like a spiffy little game, I'll have to load it up later today.

---

### Post by curvedinfinity on 2006-11-16
Hehe, it is very spiffy if I do say so myself. -- The next release, which is a side-story as opposed to an episode, I am making for a competition. I started a discussion in ff2's forums to see if anyone had any good gameplay ideas. So if you think of any things you would like added to the game, you know where to look. :) ([ff2.curvedinfinity.com]("http://ff2.curvedinfinity.com"))

---

### Post by minorthreat on 2006-11-16
Very cool game, even if I do suck at it.

Just one comment:  it runs perfectly well if I run it from a console, however, if I open it from Konqueror, I get the grey screen that someone else mentioned earlier.  I don't know what's causing the difference, but just thought I'd mention it.

Thanks!

---

### Post by curvedinfinity on 2006-11-17
Very very odd ... I really don't see where the difference would be. :-? I'll ask around on a support forum somewhere to see if anyone more experienced has some advice.

---

### Post by curvedinfinity on 2006-11-18
Some people have had problems running it from the desktop. Where you running from the desktop or another folder?

---

### Post by curvedinfinity on 2006-11-25
I've done a lot in the last week or so -- I made a major revision to cig-a, updated all of the episodes to fix a few problems people were having, and I also posted a very in-depth backstory as to how the world became the way it is in the game!

They are all worth a read, and they are all on the front page:
[ff2.curvedinfinity.com]("http://ff2.curvedinfinity.com")

:)

---

### Post by Sukarn on 2006-11-26
> **curvedinfinity said:**
> Thats great news then. :) -- And just a request: If anyone has an older card  that plays Finity Flight II well, can they tell me in some way? Like old being GeForce 4 or Radeon 8 series or older. I would expect that this range of cards is where it becomes unplayable, but I haven't actually seen it under 60 fps ever.
I had a GeForce 4 MX 440 (the lowly cards), and the game ran quite smooth on it. There seemed to be no slowdowns.
I dont have it any more though. The motherboard it was integrated in got fried... I got a new motherboard with an integrated via chipset, and since via does not seem well supported on linux, I am getting myself a GeForce 7300GT.

---

### Post by curvedinfinity on 2006-11-26
Haha, thats good news that it runs on a MX 440. 

I'm sure you won't be disappointed with a 7300GT though -- its a good choice. I'm pretty sure it will run Doom3/Quake4 at mid to high settings at reasonable resolutions. :)

---

### Post by loell on 2006-12-03
wow, youv'e gpl'd the source code , :KS

---

### Post by curvedinfinity on 2006-12-04
Drop me a message if you want to help out or just have questions about how it works. :)

---

