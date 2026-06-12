---
title: "anyone want to test my game?"
date: 2011-01-19
forum: Gaming &amp; Leisure
---

### Post by _Dan on 2011-01-19
Hello!

Anyone? It's so easy to get Windows testers for a game, but Linux, not so much.

It's a kind of block-pushing 3D puzzle game. But some of the later levels are hopefully quite challenging and should require a great deal of thought :) 

I'm afraid it's an attempt at commercial/shareware too... I hope that's ok.

I'm mainly interested in bug reports at this time (i.e. does it even run on your system!?), most of the gameplay is fixed for now (though any general opinions are certainly welcome too!) I've had an occasional problem myself where the game will freeze when entering full screen mode (switching to a different virtual terminal then returning seems to fix it.) but I'm not sure how common this is.

Here's a few screenshots:
[[img]http://garnetgames.com/puzzlemoppet/screens/balloons_and_boxes_small.png[/img]](http://garnetgames.com/puzzlemoppet/screens/balloons_and_boxes.png)   [[img]http://garnetgames.com/puzzlemoppet/screens/confusion_small.png[/img]](http://garnetgames.com/puzzlemoppet/screens/confusion.png)  [[img]http://garnetgames.com/puzzlemoppet/screens/up_and_down_small.png[/img]](http://garnetgames.com/puzzlemoppet/screens/up_and_down.png)

Anyway, if you are interested in testing, you can download it here:
[http://download.garnetgames.com/PuzzleMoppetTrial.tar.gz](http://download.garnetgames.com/PuzzleMoppetTrial.tar.gz)

Or see more info on the website: [http://garnetgames.com](http://garnetgames.com)

---

### Post by ronnielsen1 on 2011-01-19
> ron@desktop:~/Downloads/PuzzleGameTrialVersion/bin$ ./PuzzleGame.linux
Changing directory to .
Litha Game Engine
Logging to ./Puzzle Moppet.log
Arg: ./PuzzleGame.linux
Irrlicht says: Irrlicht Engine version 1.6.1
Irrlicht says: Linux 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 i686
Irrlicht says: Starting fullscreen mode...
failed to create drawable
X Error of failed request:  BadDrawable (invalid Pixmap or Window parameter)
  Major opcode of failed request:  55 (X_CreateGC)
  Resource id in failed request:  0x4600003
  Serial number of failed request:  45
  Current serial number in output stream:  47
ron@desktop:~/Downloads/PuzzleGameTrialVersion/bin$ 


The config file worked but I couldn't get the game to work

---

### Post by R33D3M33R on 2011-01-19
The game runs on Ubuntu 10.04 and Kubuntu 10.10, but the FPS are pretty low. It works in fullscreen and in windowed mode. Both computers have ATI Radeon HD 4xxx, dualcore CPU and 2 GB of RAM, Ati Catalyst installed. I liked the game, the puzzles are quite tough :).

The only thing bothering me was the intro as nothing was happening for quite some time and there was no response when pressing keys.I thought the game got somehow stuck. A better indication that something is happening would be nice.

---

### Post by TenPlus1 on 2011-01-19
Game works pretty well on my Xubuntu 10.10 setup using nvidia gfx :)

Plays well and some interesting puzzles :) thx

---

### Post by TenPlus1 on 2011-01-19
Game works pretty well on my Xubuntu 10.10 setup using nvidia gfx :)

Plays well and some interesting puzzles :) thx

---

### Post by nerdy_kid on 2011-01-19
Works here.

Kubuntu Maverick, NVIDIA Geforce 8600M.

---

### Post by nerdy_kid on 2011-01-19
Works here.  Low FPS though, but it could be because my laptop is doing some other stuff too.

Kubuntu Maverick, NVIDIA Geforce 8600M.

---

### Post by Simian Man on 2011-01-19
I only played with it a little bit because my work computer is too slow for 3D games, but it ran pretty well and is really fun.  I will try it some more when I get home.

> **_Dan said:**
> I'm afraid it's an attempt at commercial/shareware too... I hope that's ok.
Definitely.  Linux needs quality commercial games much more than underdeveloped open source ones :).

> **_Dan said:**
> 
I've had an occasional problem myself where the game will freeze when entering full screen mode (switching to a different virtual terminal then returning seems to fix it.) but I'm not sure how common this is.
I think that is a problem with running Irrlicht on Linux - which I notice you are using.  IIRC the isWindowActive function would sometimes return false in fullscreen when it should return true.

---

### Post by _Dan on 2011-01-19
@ronnielsen1,
The config app uses software rendering while the game itself uses OpenGL. Do other hardware accelerated apps work for you?

@R33D3M33R,
Thanks :) The puzzles in the demo are the easy ones :P 

Other people have mentioned that about the intro, maybe I should decrease the time. Or maybe I could just make the character fall if a key is pressed.

---

### Post by Simian Man on 2011-01-19
I only played with it a little bit because my work computer is too slow for 3D games, but it ran pretty well and is really fun.  I will try it some more when I get home.

> **_Dan said:**
> I'm afraid it's an attempt at commercial/shareware too... I hope that's ok.
Definitely.  Linux needs quality commercial games much more than underdeveloped open source ones :).

> **_Dan said:**
> 
I've had an occasional problem myself where the game will freeze when entering full screen mode (switching to a different virtual terminal then returning seems to fix it.) but I'm not sure how common this is.
I think that is a problem with running Irrlicht on Linux - which I notice you are using.  IIRC the isWindowActive function would sometimes return false in fullscreen when it should return true.

---

### Post by _Dan on 2011-01-19
@ronnielsen1,
The config app uses software rendering while the game itself uses OpenGL. Do other hardware accelerated apps work for you?

@R33D3M33R,
Thanks :) The puzzles in the demo are the easy ones :P 

Other people have mentioned that about the intro, maybe I should decrease the time. Or maybe I could just make the character fall if a key is pressed.

---

### Post by _Dan on 2011-01-19
@ronnielsen1,
The config app uses software rendering while the game itself uses OpenGL. Do other hardware accelerated apps work for you?

@R33D3M33R,
Thanks :) The puzzles in the demo are the easy ones :P 

Other people have mentioned that about the intro, maybe I should decrease the time. Or maybe I could just make the character fall if a key is pressed.

---

### Post by _Dan on 2011-01-19
argh, sorry for the multiple posts. They weren't showing up then they all appeared at once :S 

Thanks guys. My unoptimal shader code is probably to blame for any low FPS.. ;) You can disable post processing in the config app which should speed it up quite a bit.

@Simian Man, thanks for the Irrlicht tip!

---

### Post by ronnielsen1 on 2011-01-19
> @ronnielsen1,
The config app uses software rendering while the game itself uses OpenGL. Do other hardware accelerated apps work for you?


Yeah, I figured that out after I posted. I suffer from a Dell Ubuntu bug with integrated Intel graphics
> 00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)

that can't be turned off in BIOS. I thought I had it figured out by putting a newer Nvidia card but I never could get it right. The integraded card would always mess with the graphics. I finally just pulled the Nvidia card and let the Intel have it. I haven't messed with getting drivers for it installed.

---

### Post by R33D3M33R on 2011-01-19
> **_Dan said:**
> @ronnielsen1,
The config app uses software rendering while the game itself uses OpenGL. Do other hardware accelerated apps work for you?

@R33D3M33R,
Thanks :) The puzzles in the demo are the easy ones :P 

Other people have mentioned that about the intro, maybe I should decrease the time. Or maybe I could just make the character fall if a key is pressed.

I think it's better if the character would fall at keypress. I would also ask if a "go one step back" will be integrated? This should work only if the character didn't fall off the platform.

---

### Post by R33D3M33R on 2011-01-19
> **_Dan said:**
> @ronnielsen1,
The config app uses software rendering while the game itself uses OpenGL. Do other hardware accelerated apps work for you?

@R33D3M33R,
Thanks :) The puzzles in the demo are the easy ones :P 

Other people have mentioned that about the intro, maybe I should decrease the time. Or maybe I could just make the character fall if a key is pressed.

I think it's better if the character would fall at keypress. I would also ask if a "go one step back" will be integrated? This should work only if the character didn't fall off the platform.

---

### Post by ronnielsen1 on 2011-01-19
> @ronnielsen1,
The config app uses software rendering while the game itself uses OpenGL. Do other hardware accelerated apps work for you?


Yeah, I figured that out after I posted. I suffer from a Dell Ubuntu bug with integrated Intel graphics
> 00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)

that can't be turned off in BIOS. I thought I had it figured out by putting a newer Nvidia card but I never could get it right. The integraded card would always mess with the graphics. I finally just pulled the Nvidia card and let the Intel have it. I haven't messed with getting drivers for it installed.

---

### Post by ronnielsen1 on 2011-01-19
> @ronnielsen1,
The config app uses software rendering while the game itself uses OpenGL. Do other hardware accelerated apps work for you?


Yeah, I figured that out after I posted. I suffer from a Dell Ubuntu bug with integrated Intel graphics
> 00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)

that can't be turned off in BIOS. I thought I had it figured out by putting a newer Nvidia card but I never could get it right. The integraded card would always mess with the graphics. I finally just pulled the Nvidia card and let the Intel have it. I haven't messed with getting drivers for it installed.

---

### Post by R33D3M33R on 2011-01-19
> **_Dan said:**
> @ronnielsen1,
The config app uses software rendering while the game itself uses OpenGL. Do other hardware accelerated apps work for you?

@R33D3M33R,
Thanks :smile: The puzzles in the demo are the easy ones :razz: 

Other people have mentioned that about the intro, maybe I should  decrease the time. Or maybe I could just make the character fall if a  key is pressed.

I think it's better if the character would fall at keypress. I would  also ask if a "go one step back" will be integrated? This should work  only if the character didn't fall off the platform.

---

### Post by ronnielsen1 on 2011-01-19
> @ronnielsen1,
The config app uses software rendering while the game itself uses OpenGL. Do other hardware accelerated apps work for you?


Yeah, I figured that out after I posted. I suffer from a Dell Ubuntu bug with integrated Intel graphics
> 00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)

that can't be turned off in BIOS. I thought I had it figured out by putting a newer Nvidia card but I never could get it right. The integraded card would always mess with the graphics. I finally just pulled the Nvidia card and let the Intel have it. I haven't messed with getting drivers for it installed.

---

### Post by ronnielsen1 on 2011-01-19
> @ronnielsen1,
The config app uses software rendering while the game itself uses OpenGL. Do other hardware accelerated apps work for you?


Yeah, I figured that out after I posted. I suffer from a Dell Ubuntu bug with integrated Intel graphics
> 00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)

that  can't be turned off in BIOS. I thought I had it figured out by putting a  newer Nvidia card but I never could get it right. The integraded card  would always mess with the graphics. I finally just pulled the Nvidia  card and let the Intel have it. I haven't messed with getting drivers  for it installed.

---

### Post by DMKryl on 2011-01-19
> **R33D3M33R said:**
> I think it's better if the character would fall at keypress. I would  also ask if a "go one step back" will be integrated? This should work  only if the character didn't fall off the platform.

^this, played the demo, get frustrated when i fell from mistake, works fine in acer 4738z ubuntu maverick, button to cut the intro.

---

### Post by DMKryl on 2011-01-19
> **R33D3M33R said:**
> I think it's better if the character would fall at keypress. I would  also ask if a "go one step back" will be integrated? This should work  only if the character didn't fall off the platform.

^this, played the demo, get frustrated when i fell from mistake, works fine in acer 4738z ubuntu maverick, button to cut the intro.

---

### Post by _Dan on 2011-01-19
@ronnielsen1,
Ok, thanks for clearing that up!

I'll certainly consider an "undo" function, it might be pretty tricky to implement though. Thanks for the suggestion.

---

### Post by DMKryl on 2011-01-19
> **R33D3M33R said:**
> I think it's better if the character would fall at keypress. I would  also ask if a "go one step back" will be integrated? This should work  only if the character didn't fall off the platform.

^this, played the demo, get frustrated when i fell from mistake, works fine in acer 4738z ubuntu maverick, button to cut the intro.

---

### Post by vedster on 2011-01-19
CPU: Intel i5-430M @ 2.66GHZ
GPU: Intel HD Graphics (Integrated)
RAM: 4GB
Ubuntu Build: 10.10

Performance was great even with just an integrated GPU. Great news considering most low-mid end laptops are being built with this card.

There was however, a glitch. 
After falling off the cliff, if one holds the up and right arrow key  simultaneously BEFORE the character respawns, the character will glide  over the ground and it's legs will not go through the walk cycle. This happens in all levels.

I have posted a video of this happening here (private video, won't appear in searches): [http://www.youtube.com/watch?v=afMcy8-YvuE](http://www.youtube.com/watch?v=afMcy8-YvuE)

Hope I helped!
Will edit this post if I find other glitches.

---

### Post by _Dan on 2011-01-20
Ha. Thanks for reporting this :-)

---

### Post by quids on 2011-01-21
Works fine with Nvidia 9800 set at 1920x1080 resolution

Only played a couple of levels

---

### Post by _Dan on 2011-02-17
Thanks quids!

Just a little update, the game now has a simple menu system + level selector.

[[img]http://garnetgames.com/puzzlemoppet/screens/titlescreen_small.png[/img]](http://garnetgames.com/puzzlemoppet/screens/titlescreen.png)

Also, I've replaced most of the trial levels with some new - and harder ones - with more block types that previously were only in the full version.

I guess this is in response to people saying the original was too short and too easy. So if you thought that, please try this new version :)

Download: [http://download.garnetgames.com/PuzzleMoppetTrial.tar.gz](http://download.garnetgames.com/PuzzleMoppetTrial.tar.gz)

Also, if anyone has general feedback about the game that would be interesting. Since at the moment, it's not selling :(
(though I only released it in a few places while it's still in beta)...

But I want to know, what puts it below other games? Is it the lack of a map system? Just generally not polished or fun enough?

---

### Post by MaxIBoy on 2011-02-19
It appears to be working OK here, but with one apparent bug that I noticed. In the two attached screenshots, I've reached situations where I cannot push the blocks into the lifter beams, even though there does not appear to be anything blocking them.

---

### Post by _Dan on 2011-02-19
Thanks for testing!

Oddly enough, that isn't a bug but a feature... :S the lifter things are supposed to be solid, so you have to raise the blocks up a level to push them into the beams.

(as you see at the start of that level - the first block you push across a bridge made from two other blocks to get it into the beam).

That behaviour isn't really something I can change this late, after I made the puzzles relying on it... I wonder how I can make it more obvious that you are not supposed to be able to do that?!

---

### Post by R33D3M33R on 2011-02-19
This is not a bug. Keep in mind that the beam lift's are 1 block/box high.

---

### Post by gerowen on 2011-02-19
> **_Dan said:**
> Thanks quids!

Just a little update, the game now has a simple menu system + level selector.

[[img]http://garnetgames.com/puzzlemoppet/screens/titlescreen_small.png[/img]](http://garnetgames.com/puzzlemoppet/screens/titlescreen.png)

Also, I've replaced most of the trial levels with some new - and harder ones - with more block types that previously were only in the full version.

I guess this is in response to people saying the original was too short and too easy. So if you thought that, please try this new version :)

Download: [http://download.garnetgames.com/PuzzleMoppetTrial.tar.gz](http://download.garnetgames.com/PuzzleMoppetTrial.tar.gz)

Also, if anyone has general feedback about the game that would be interesting. Since at the moment, it's not selling :(
(though I only released it in a few places while it's still in beta)...

But I want to know, what puts it below other games? Is it the lack of a map system? Just generally not polished or fun enough?

Have you thought about seeing if Canonical would put it up in the Software Center?  They advertise games and stuff that cost money so it could be an easy way to get some advertising out there, and an easy way to publish updates to those who have already paid.  I just got the trial version and it seems pretty cool.

---

### Post by _Dan on 2011-02-19
That's a very interesting idea, thanks! I think I'm still on the Ubuntu version before paid apps were added to the software centre, guess I now have a reason to upgrade and see this :)

I'll probably wait until I've done some more improvements though before I look into that.

Currently working on: Undo system! I just got a basic undo working, and it was easier than I expected :)

---

### Post by ubun2geek on 2011-02-19
Sure! I'll try as soon as I am out of tty1 mode. If you want to help, please move to this post:
[http://ubuntuforums.org/showthread.php?t=1690561](http://ubuntuforums.org/showthread.php?t=1690561)

---

### Post by DrAcid on 2011-02-19
> **_Dan said:**
> Thanks quids!

Just a little update, the game now has a simple menu system + level selector.

[[img]http://garnetgames.com/puzzlemoppet/screens/titlescreen_small.png[/img]](http://garnetgames.com/puzzlemoppet/screens/titlescreen.png)

Also, I've replaced most of the trial levels with some new - and harder ones - with more block types that previously were only in the full version.

I guess this is in response to people saying the original was too short and too easy. So if you thought that, please try this new version :)

Download: [http://download.garnetgames.com/PuzzleMoppetTrial.tar.gz](http://download.garnetgames.com/PuzzleMoppetTrial.tar.gz)

Also, if anyone has general feedback about the game that would be interesting. Since at the moment, it's not selling :(
(though I only released it in a few places while it's still in beta)...

But I want to know, what puts it below other games? Is it the lack of a map system? Just generally not polished or fun enough?

Thank You for developing game for Linux as well! ):P
I have gladly tested the build You have provided on my Ubuntu 10.10 x32 with all latest updates & x.Org(latest??) from xorg-edgers ppa. My video is Intel GMA HD(which absolutely sucks btw! :( ).
The game runs SMOOTHLY. it has crashed only once when I've tried to reset the first level(several times.) the error returned was: (I have pressed DEL several times before crash)
```
save path: /home/dracid/.Puzzle Moppet/puzzlegame.save
Loading level... (tutorial_lifts.lev)
Level::Level: ../projects/Puzzle/trial_levels/levels/tutorial_lifts.lev
Restarting current level...
Removing level.
Level::~Level
*** WARNING at World.cpp:155:RemoveTransformable: Specified transformable was not found.
Loading level... (tutorial_lifts.lev)
Level::Level: ../projects/Puzzle/trial_levels/levels/tutorial_lifts.lev
Restarting current level...
Removing level.
Level::~Level
*** WARNING at World.cpp:155:RemoveTransformable: Specified transformable was not found.
Loading level... (tutorial_lifts.lev)
Level::Level: ../projects/Puzzle/trial_levels/levels/tutorial_lifts.lev
Restarting current level...
Removing level.
Level::~Level
*** WARNING at World.cpp:155:RemoveTransformable: Specified transformable was not found.
Loading level... (tutorial_lifts.lev)
Level::Level: ../projects/Puzzle/trial_levels/levels/tutorial_lifts.lev
Restarting current level...
Removing level.
Level::~Level
*** WARNING at World.cpp:155:RemoveTransformable: Specified transformable was not found.
Loading level... (tutorial_lifts.lev)
Level::Level: ../projects/Puzzle/trial_levels/levels/tutorial_lifts.lev
Segmentation fault

```


**I also include my HP laptop specs (hardinfo) in the attachment as a zipped HTML file.**

My terminal output for the game(no crashes):
```
dracid@acid-top:~/PuzzleGameTrialVersion/bin$ ./PuzzleGame.linux 
Changing directory to .
Litha Game Engine
Logging to ./Puzzle Moppet.log
Settings path: /home/dracid/.Puzzle Moppet/Puzzle Moppet.ini
Arg: ./PuzzleGame.linux
Irrlicht says: Irrlicht Engine version 1.6.1
Irrlicht says: Linux 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:48 UTC 2011 i686
Irrlicht says: Starting fullscreen mode...
Irrlicht says: Using renderer: OpenGL 2.1
Irrlicht says: Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20100330 DEVELOPMENT x86/MMX/SSE2: Tungsten Graphics, Inc
Irrlicht says: OpenGL driver version is 1.2 or better.
Irrlicht says: GLSL version: 1.2
*** THIS IS THE TRIAL VERSION ***
New shader instance, material ID is 24
AddEffect {512,384}.
Success!
Actual effect RTT size is {512,384}.
New shader instance, material ID is 25
AddEffect {512,384}.
Success!
Actual effect RTT size is {512,384}.
New shader instance, material ID is 26
AddEffect {512,384}.
Success!
Actual effect RTT size is {512,384}.
Preloading media...
Irrlicht says: Could not load mesh, because file could not be opened: : sea.b3d
Irrlicht says: Could not load mesh, because file could not be opened: : land.irrmesh
Irrlicht says: Could not load mesh, because file could not be opened: : cliff.irrmesh
Irrlicht says: Could not open file of texture: watersand.png
Irrlicht says: Could not open file of texture: water.png
Irrlicht says: Could not open file of texture: watersand_add.png
Irrlicht says: Could not open file of texture: skies/Set 26/final_6.png
Irrlicht says: Could not open file of texture: skies/Set 26/final_5.png
Irrlicht says: Could not open file of texture: skies/Set 26/final_1.png
Irrlicht says: Could not open file of texture: skies/Set 26/final_3.png
Irrlicht says: Could not open file of texture: skies/Set 26/final_2.png
Irrlicht says: Could not open file of texture: skies/Set 26/final_4.png
*** WARNING at OpenALSoundSystem.cpp:59:GetOpenALBuffer: Could not create buffer from file (../projects/Puzzle/media/sfx/sea.wav)
OpenALSoundSystem error: I/O error
*** WARNING at OpenALSoundSystem.cpp:165:PreloadSound: Could not get buffer (../projects/Puzzle/media/sfx/sea.wav)
Finished preloading!
Entering start screen...
Identified level: intro.lev
Identified level: first.lev
Identified level: tutorial_lifts.lev
Identified level: concept_level.lev
Identified level: alittlebridge.lev
Identified level: icy_intro.lev
Identified level: splody.lev
Identified level: simple_aha.lev
Identified level: balloonacy.lev
Identified level: balloon_dispenser.lev
save path: /home/dracid/.Puzzle Moppet/puzzlegame.save
Found a valid next level...
(have completed level splody.lev so will continue on next level, simple_aha.lev)
Identified level: intro.lev
Identified level: first.lev
Identified level: tutorial_lifts.lev
Identified level: concept_level.lev
Identified level: alittlebridge.lev
Identified level: icy_intro.lev
Identified level: splody.lev
Identified level: simple_aha.lev
Identified level: balloonacy.lev
Identified level: balloon_dispenser.lev
furthest save path: /home/dracid/.Puzzle Moppet/puzzlegame.save.furthest
Identified level: intro.lev
Identified level: first.lev
Identified level: tutorial_lifts.lev
Identified level: concept_level.lev
Identified level: alittlebridge.lev
Identified level: icy_intro.lev
Identified level: splody.lev
Identified level: simple_aha.lev
Identified level: balloonacy.lev
Identified level: balloon_dispenser.lev
furthest save path: /home/dracid/.Puzzle Moppet/puzzlegame.save.furthest
Found a valid next level...
(have completed level splody.lev so will continue on next level, simple_aha.lev)
Level::Level: ../projects/Puzzle/trial_levels/levels/simple_aha.lev
New shader instance, material ID is 27
New shader instance, material ID is 28
New shader instance, material ID is 29
save path: /home/dracid/.Puzzle Moppet/puzzlegame.save
Game save exists, will show continue game option.
Exiting from start screen... (exit clicked)
furthest save path: /home/dracid/.Puzzle Moppet/puzzlegame.save.furthest
Level::~Level
*** WARNING at World.cpp:155:RemoveTransformable: Specified transformable was not found.
AL lib: ALc.c:1420: alcDestroyContext(): deleting 3 Source(s)
Litha Engine appears to have shut down successfully.
Opening web page: http://www.garnetgames.com/puzzlemoppet/getfullversion/?reached=splody.lev
Found xdg-open with path: /usr/bin/xdg-open
Running process: /usr/bin/xdg-open
Arg: http://www.garnetgames.com/puzzlemoppet/getfullversion/?reached=splody.lev

```

I have an info about a bug: I haven't run the config utility at first, so I missed the option to play on my native resolution - 1280x800. I've played on 1024x768; after I've quit the game the resolution hadn't returned to my native one. I had to manually reset screen using Ubuntu's utilities.
It would be nice to see this fixed...
Also, IMHO, lifts have annoying sound - I was stuck on the "little bridge" level for a bit. Eventually sound drove me crazy. :P
It's not TOO bad though. It started bothering me after only 10 minutes...


Well, that's all I've got for You today, folks! If You need help testing - I'll gladly provide.

I wish You the best luck! ;)


P.S.(How can I view my current FPS?)
P.P.S.(Oh, and "A Little Bridge" level is quite hard comparing to the upcoming ones... :P Should it be the other way?)

---

### Post by gerowen on 2011-02-19
One suggestion to avoid confusion with the lifts in "A Little Bridge" (this is referencing a comment you made earlier in this topic) is you cuold surround the first level of the lift with some sort of wall, but leave the tops open so players could see that they need to get the blocks over top of the lifts for them to work, since the walls are stopping them from pushing them straight in like they did in the level prior.

---

### Post by _Dan on 2011-02-20
@OpenOffice.org, sorry I haven't a clue about your problem... I'm not a Linux guru by any stretch.

@DrAcid, hmm that crash is odd... :( 

Those "RemoveTransformable" warning lines aren't actually a problem and can be ignored, so I'm not sure what this might be.  I'm here hammering away at Delete and it's just refusing to crash.

If you know gdb you could always run it through that... :)

or run
ulimit -c unlimited
before running the game, and maybe it'll generate a core dump file when it crashes, but I'm not too sure if I compiled it correctly for that.

I'll hopefully add resolution settings into the main game rather than just in a separate app. I will add sfx volume settings too.

I'll look into the resolution bug. I think maybe that only happens when it has crashed?

Thanks for the detailed report!

@gerowen, that's a good idea, thanks.

---

### Post by gerowen on 2011-02-21
The delete crash never occurred on my laptop, but on my desktop machine which also runs Ubuntu 10.10 64bit does crash randomly when you press the delete key.  Sometimes it resets the level as expected, other times the game closes altogether.  I'll try running it from the terminal and see what kind of output I get.

---

### Post by MaxIBoy on 2011-02-24
> **_Dan said:**
> Thanks for testing!

Oddly enough, that isn't a bug but a feature... :S the lifter things are supposed to be solid, so you have to raise the blocks up a level to push them into the beams.

(as you see at the start of that level - the first block you push across a bridge made from two other blocks to get it into the beam).

That behaviour isn't really something I can change this late, after I made the puzzles relying on it... I wonder how I can make it more obvious that you are not supposed to be able to do that?!
I'd suggest an artwork tweak. It would have been more obvious if it was a solid block with a "beam nozzle" or portal-looking thing at the top with the beam coming out. That would have made it clear to me personally, but then again no one else seemed to have a problem with it, so maybe I was just being stupid. :)

---

### Post by cbennett a7xftw on 2011-02-25
yeah sure looks good

---

### Post by lolligelol on 2011-02-25
works quite well for me, love the game!
only the intro bothers me a little bit, but i have no mayor problems!
:)

---

### Post by _Dan on 2011-02-26
[quote=MaxIBoy]I'd suggest an artwork tweak. It would have been more obvious if it was a solid block with a "beam nozzle" or portal-looking thing at the top with the beam coming out. That would have made it clear to me personally, but then again no one else seemed to have a problem with it, so maybe I was just being stupid. :)[/quote]
hmm! well, I'll add it on my list of things to consider anyway :) 

[quote=lolligelol]only the intro bothers me a little bit, but i have no mayor problems![/quote]

So how does it bother you? ;) 

I guess it's a little too simple is it?

---

### Post by DrAcid on 2011-02-26
Yeah, a little work on the intro would be great! ;)

---

### Post by _Dan on 2011-03-26
Hello, another little update :) I think I'm close now to what I'll call "complete".

- tutorial across the first few levels
- undo function! (also saves just before you fall off the world)
- level ratings (can you get a "Perfect" score hmm?)
- options menu (with volume control and other things)
- other minor things: bug fixes, optimisations (should run significantly faster now), more character animations...

[[img]http://xzist.org/temp/puzzlegame/tutorial_small.png[/img]](http://xzist.org/temp/puzzlegame/tutorial.png)

Download: [PuzzleMoppetTrial.tar.gz](http://download.garnetgames.com/PuzzleMoppetTrial.tar.gz)

---

### Post by _Dan on 2011-04-04
Another update...

I've now added grid based movement:

[[img]http://xzist.org/temp/puzzlegame/glyph_small.png[/img]](http://xzist.org/temp/puzzlegame/glyph.png)

Download: [PuzzleMoppetTrial.tar.gz](http://download.garnetgames.com/PuzzleMoppetTrial.tar.gz)

(so the character sticks to the invisible grid. The glyph on the ground shows the current movement direction).

I'd love to hear any opinions on the grid based movement... I'm not sure whether I should enable it by default or not...

Well, anyway, if you're lucky this will be my last update ;)
(though I still have a few minor things left I might do)

---

### Post by ahood on 2011-10-08
Hello

I obtained this game during a download free day some time ago. I launch it with the following command.

> sh ./PuzzleGame

I receive the following error message.

> Syntax error: "(" unexpected (expecting ")")

:confused:

Any help will be greatly appreciated.

---

### Post by juancarlospaco on 2011-10-08
> **ahood said:**
> 
sh ./puzzlegame


no

> 
./puzzlegame


yes

:P

---

### Post by Shazaam on 2011-10-09
Hey _Dan, fun game.
A few minor things (probably my fault):
1. Nothing shows in the Applications/Games list.
2. This...
```
Querying current desktop resolution...
Cached original resolution: 1600x900
Irrlicht says: Irrlicht Engine version 1.6.1
Irrlicht says: Linux 2.6.32-34-generic #77-Ubuntu SMP Tue Sep 13 19:40:53 UTC 2011 i686
Irrlicht says: Using renderer: OpenGL 2.1.2
Irrlicht says: GeForce 6600 GT/AGP/SSE/3DNOW!: NVIDIA Corporation
Irrlicht says: OpenGL driver version is 1.2 or better.
Irrlicht says: GLSL version: 1.2
Fullscreen: 0
VSync: 1
Max render FPS: 60.0
Shader level set to 1 (high)
*** THIS IS THE TRIAL VERSION ***
Shader level set to 0 (low)
New shader instance, material ID is 24
Preloading media...
Irrlicht says: Could not load mesh, because file could not be opened: : sea.b3d
Irrlicht says: Could not load mesh, because file could not be opened: : land.irrmesh
Irrlicht says: Could not load mesh, because file could not be opened: : cliff.irrmesh
Irrlicht says: Could not open file of texture: watersand.png
Irrlicht says: Could not open file of texture: water.png
Irrlicht says: Could not open file of texture: watersand_add.png
Irrlicht says: Could not open file of texture: skies/Set 26/final_6.png
Irrlicht says: Could not open file of texture: skies/Set 26/final_5.png
Irrlicht says: Could not open file of texture: skies/Set 26/final_1.png
Irrlicht says: Could not open file of texture: skies/Set 26/final_3.png
Irrlicht says: Could not open file of texture: skies/Set 26/final_2.png
Irrlicht says: Could not open file of texture: skies/Set 26/final_4.png
*** WARNING at OpenALSoundSystem.cpp:148:GetOpenALBuffer: Ogg loading failed: ../projects/Puzzle/media/sfx/sea.ogg
*** WARNING at OpenALSoundSystem.cpp:169:PreloadSound: Could not get buffer (../projects/Puzzle/media/sfx/sea.ogg)
Finished preloading!
```
To run the game (without making a launcher myself) I have to drill down to the /puzzlemoppet/bin folder and click PuzzleGame. Not a problem as the game runs fine on my system-
Ubuntu Lucid, AMD Athlon XP3200.

---

