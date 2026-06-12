---
title: "Alien Arena 2009 is OUT!!"
date: 2009-06-19
forum: Gaming &amp; Leisure
---

### Post by MaxIBoy on 2009-06-19
(Copied over the bbcode of the official press release, I didn't write this.) 


[SIZE=2][FONT=Courier New][SIZE=2]It's been over six long months of dedicated, at times daunting, and ultimately triumphant work...and COR Entertainment at last announces the release of Alien Arena 2009! 
 
You've seen the screenshots, the videos, now it is time to face the alien invasion head on, armed to the hilt with disruptors, beamguns, and vaporizors. The amount of improvements to the game engine are staggering. The game comes alive with the full implementation of GLSL per-pixel lighting on all surfaces, OpenAL audio system, and new gameplay features. Optimization was as always, another aspect that we've addressed. No longer does one have to be leary of cranking the settings up, the game plays remarkably faster with the switch to GLSL for per-pixel operations. Alien Arena has transformed into a lean, clean, fragging machine, with stunning visual effects that are usually reserved for commercial titles. This isn't your daddy's Alien Arena - it's not even last year's model, with a host of new and improved maps, sounds and music. 
 
Some of the new features in this release:

[LIST]
[*]GLSL per-pixel lighting on all surfaces.
[*]OpenAL 1.1
[*]Ogg-Vorbis support.
[*]GLSL post process framebuffer effects.
[*]New scoreboards.
[*]New HUD.
[*]Stereo music files.
[*]Seven new maps and two new player characters.
[*]Light volumes.
[*]Voice taunt system.
[*]Doppler sound effects.
[/LIST]
 
For a complete changelog [http://icculus.org/alienarena/changelogs/7.30.txt](http://icculus.org/alienarena/changelogs/7.30.txt)
 
Alien Arena 2009 is open source, free to play, and sets a new standard in freeware FPS gaming. To download the game(windows or linux), or for more information, screenshots and videos, visit [http://red.planetarena.org](http://red.planetarena.org) 
 
[[IMG]http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_15_s.jpg[/IMG]]("http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_15.jpg") [[IMG]http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_1_s.jpg[/IMG]]("http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_1.jpg") [[IMG]http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_9_s.jpg[/IMG]]("http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_9.jpg") [[IMG]http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_4_s.jpg[/IMG]]("http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_4.jpg")[/SIZE][/FONT][/SIZE]

---

### Post by Melcar on 2009-06-19
Oh snap!  Downloading now.

---

### Post by JMiserez on 2009-06-20
I had some problems running the game on Jaunty 64bit. Somehow the game doesn't find the libraries (libXxf86dga.so.1) even though they are installed...

Here is the solution:

---------------------
If you get the following error or a similar one:

**crx: error while loading shared libraries: libXxf86dga.so.1: cannot open shared object file: No such file or directory**

...then you must install it by compiling from source (don't worry, it's easy and fast):
Do the following steps:

0) Download the game and unzip it somewhere (I unzipped it to  /home/joe/games/)

1) Open a terminal to your alienarena2009 folder (I put the game into /home/joe/games/alienarena2009)
```
cd /home/joe/games/alienarena2009
```2) Change to the source directory:
```
cd source
```3) install some libraries and tools you need to compile:
```
sudo apt-get install libvorbis-dev build-essential libcurl4-openssl-dev libopenal-dev fakeroot devscripts debhelper dpatch libsdl1.2-dev libglu1-mesa-dev libgl1-mesa-dev libjpeg62-dev libxxf86vm-dev libxxf86dga-dev libxext-dev libx11-dev
```4) wait until everything is installed

5) now we can compile the game
```
make
```6) and install it (this just replaces the "crx" you downloaded)
```
make install
```7) change to your alienarena2009 folder again
```
cd ..
```8) and run the game!
```
./crx
```--------------------

---

### Post by jenova_skill on 2009-06-20
Thanks for the post on how to install it...... I was having some problems myself. I got so aggravated I deleted it lol.

---

### Post by Irritant on 2009-06-20
Thanks JMiserez for posting those instructions :)

Thanks Max for posting the news, you're fast, hahah.

---

### Post by -grubby on 2009-06-20
Oh man, that looks even sexier than Nexuiz 2.5...
/me goes to download.

EDIT: I set it to the highest settings, and it reminded me of quake 2...

---

### Post by Irritant on 2009-06-20
> **grubby- said:**
> Oh man, that looks even sexier than Nexuiz 2.5...
/me goes to download.

EDIT: I set it to the highest settings, and it reminded me of quake 2...

Eh, Quake 2?  I don't recall quake 2 having per-pixel lighting, shadows, parallax mapping, bumpmapping, specular mapping, textured particles, volumetric shadows, static meshes, etc etc etc.  I know you're entitled to your opinion, but that is an extremely harsh assessment.  What reminds you of Quake 2?

Maybe you're graphics card doesn't support GLSL?

I mean c-mon, look - 

Alien Arena 2009

[[img]http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_15_s.jpg[/img]](http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_15.jpg) 

Quake 2

[[img]http://icculus.org/alienarena/Testpics/quake2_s.jpg[/img]](http://icculus.org/alienarena/Testpics/quake2.jpg)

How could you even make a comparison?  Unless your card does't support GLSL, or something...

---

### Post by spoons on 2009-06-20
I think the engine looks good but work should have been done into higher poly models and textures as they look like they were pulled from 2004.

---

### Post by Irritant on 2009-06-20
> **spoons said:**
> I think the engine looks good but work should have been done into higher poly models and textures as they look like they were pulled from 2004.

Well the effort was made(nearly every model in the game was redone a year ago), but a conscious choice to keep models under 2000 polys was done to keep peformance reasonable.  In a DM game where 10 or more players can be on your screen at once, it's a good idea to keep the polycount down a bit.  So most player models are between 1000-2000 polys, and weapons 500-1000.

Textures are 1024x1024 .jpgs in most cases, done to keep installation size small enough that mags will be more apt to include the game on their cover DVD's.  

I do agree though that the limitations we impose make the game's media look circa 2004 or so.  IMO that's not really such a bad thing though for a game of this type.

---

### Post by mao_dze_dun on 2009-06-20
Thank you for the tips JMiserez. Unfortunately that only half worked for me. I was able to start the game but it opened in a window and part of it was obviously not visible, so... yeah. Btw I'm running a 32bit ubuntu if that is of any consequence. I've been using ubuntu for less than a week and I still try to figure out why the damn thing limits my access to half the stuff :))). Anyway I guess I'm just not doing something right, so I would be really thankful if you issue some "installing aliena arena 2009 on ubuntu for idiots" or something :D

---

### Post by Irritant on 2009-06-20
> **mao_dze_dun said:**
> Thank you for the tips JMiserez. Unfortunately that only half worked for me. I was able to start the game but it opened in a window and part of it was obviously not visible, so... yeah. Btw I'm running a 32bit ubuntu if that is of any consequence. I've been using ubuntu for less than a week and I still try to figure out why the damn thing limits my access to half the stuff :))). Anyway I guess I'm just not doing something right, so I would be really thankful if you issue some "installing aliena arena 2009 on ubuntu for idiots" or something :D

Sounds like you're running the game at an resolution not supported by your xorg.conf?  Try setting the res at your desktop res, then make sure in the vid settings that fullscreen is checked back on.

---

### Post by Melcar on 2009-06-21
Having problems running it on my laptop with the ATI open source drivers.  Attempting to run ./crx simply produces a segfault.  I think it's because the game uses glsl by default and the open drivers don't have support for that.  Is there a way to launch the game without glsl support?

---

### Post by MaxIBoy on 2009-06-21
Just to let everyone know, if you want to run it on 64-bit Linux, you need to recompile it. The pre-built binary is for 32-bit Linux. If anyone would be willing to build a 64-bit binary and upload it, that would be very handy. 


> **Melcar said:**
> Having problems running it on my laptop with the ATI open source drivers.  Attempting to run ./crx simply produces a segfault.  I think it's because the game uses glsl by default and the open drivers don't have support for that.  Is there a way to launch the game without glsl support?The main menu should at least work without glsl. 

Still you can disable it manually by editing the config file. In your home directory, the first time the game is run it should create a folder called .codered. Go into that, there will be a directory called "arena." In that, there will be a file called config.cfg. Edit that with your favorite plaintext editor. Find the line where it says 
```
set gl_glsl_shaders "1"
```
Change "1" to "0" and glsl will be disabled. 

If .codered wasn't created, that means the game crashed very early on in the process.

Generally speaking, the open-source drivers will probably not be able to run the game as well as the proprietary ones, if at all. It's really sad, I wish I could use the open-source drivers, but unfortunately I usually wind up having to install fglrx.

---

### Post by Melcar on 2009-06-21
It wasn't glsl in the end.  Installed some missing dependencies and got the game to run.

:D

[[IMG]http://img196.imageshack.us/img196/1741/alienarena000.jpg[/IMG]](http://img196.imageshack.us/i/alienarena000.jpg/)

[[IMG]http://img196.imageshack.us/img196/6083/alienarena001.jpg[/IMG]](http://img196.imageshack.us/i/alienarena001.jpg/)

[[IMG]http://img3.imageshack.us/img3/6509/alienarena002.jpg[/IMG]](http://img3.imageshack.us/i/alienarena002.jpg/)

Low settings @ 640x480 (2GHz Sempron, 200M IGP, 2GB RAM).  15-30fps most of the time; except when more than two players are on screen, then the performance just craps out.  Water is also a no-no (game turns into a slide show).
To bad I'm not using my old x800gto on my desktop, otherwise I would test it there.  Can't wait for r7xx chips to get 3D accel. with the open drivers and see how they fair on games.

---

### Post by MaxIBoy on 2009-06-21
Try setting r_legacy to "1" in your config file? That may work slightly faster.

---

### Post by mao_dze_dun on 2009-06-21
> **Irritant said:**
> Sounds like you're running the game at an resolution not supported by your xorg.conf?  Try setting the res at your desktop res, then make sure in the vid settings that fullscreen is checked back on.

ahahaha. I feel incredibly stupid. The game was set to windowed mode. I am so used to it being full screen by default in Windows, that I forgot to check the most obvious thing. Thanks a lot mate.

---

### Post by joeelmex on 2009-06-21
I cant get it to work, when I do the make command it gives me 2 Errors.  

I followed the instructions on page 1 of this thread and I am running Ubuntu 64.  I wonder if I have ti recompile it.  As stated 2 post up.  I am new to this anyone mind giving me some more instructions.


This is what I get when I use the Make 

```

client/snd_file.c:30:31: error: vorbis/vorbisfile.h: No such file or directory
client/snd_file.c:223: error: expected declaration specifiers or ‘...’ before ‘ogg_int64_t’
client/snd_file.c: In function ‘ovbfr_seek’:
client/snd_file.c:232: error: ‘offset’ undeclared (first use in this function)
client/snd_file.c:232: error: (Each undeclared identifier is reported only once
client/snd_file.c:232: error: for each function it appears in.)
client/snd_file.c: At top level:
client/snd_file.c:265: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ovbfr_callbacks’
client/snd_file.c: In function ‘ReadVorbisFile’:
client/snd_file.c:276: error: ‘ogg_int64_t’ undeclared (first use in this function)
client/snd_file.c:276: error: expected ‘;’ before ‘samples’
client/snd_file.c:277: error: ‘vorbis_info’ undeclared (first use in this function)
client/snd_file.c:277: error: ‘vi’ undeclared (first use in this function)
client/snd_file.c:278: error: ‘OggVorbis_File’ undeclared (first use in this function)
client/snd_file.c:278: error: expected ‘;’ before ‘vf’
client/snd_file.c:298: error: ‘vf’ undeclared (first use in this function)
client/snd_file.c:298: error: ‘ovbfr_callbacks’ undeclared (first use in this function)
client/snd_file.c:306: error: ‘samples’ undeclared (first use in this function)
client/snd_file.c:343: error: ‘OV_HOLE’ undeclared (first use in this function)
client/snd_file.c:346: error: ‘OV_EBADLINK’ undeclared (first use in this function)
make[1]: *** [release/client/snd_file.o] Error 1
make[1]: Leaving directory `/home/joeelmex/Games/AlienArena/source'
make: *** [build-release] Error 2

```

---

### Post by QCompson on 2009-06-21
> **joeelmex said:**
> I cant get it to work, when I do the make command it gives me 2 Errors.  

I followed the instructions on page 1 of this thread and I am running Ubuntu 64.  I wonder if I have ti recompile it.  As stated 2 post up.  I am new to this anyone mind giving me some more instructions.


This is what I get when I use the Make 

```

client/snd_file.c:30:31: error: vorbis/vorbisfile.h: No such file or directory
client/snd_file.c:223: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;ogg_int64_t&#8217;
client/snd_file.c: In function &#8216;ovbfr_seek&#8217;:
client/snd_file.c:232: error: &#8216;offset&#8217; undeclared (first use in this function)
client/snd_file.c:232: error: (Each undeclared identifier is reported only once
client/snd_file.c:232: error: for each function it appears in.)
client/snd_file.c: At top level:
client/snd_file.c:265: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;ovbfr_callbacks&#8217;
client/snd_file.c: In function &#8216;ReadVorbisFile&#8217;:
client/snd_file.c:276: error: &#8216;ogg_int64_t&#8217; undeclared (first use in this function)
client/snd_file.c:276: error: expected &#8216;;&#8217; before &#8216;samples&#8217;
client/snd_file.c:277: error: &#8216;vorbis_info&#8217; undeclared (first use in this function)
client/snd_file.c:277: error: &#8216;vi&#8217; undeclared (first use in this function)
client/snd_file.c:278: error: &#8216;OggVorbis_File&#8217; undeclared (first use in this function)
client/snd_file.c:278: error: expected &#8216;;&#8217; before &#8216;vf&#8217;
client/snd_file.c:298: error: &#8216;vf&#8217; undeclared (first use in this function)
client/snd_file.c:298: error: &#8216;ovbfr_callbacks&#8217; undeclared (first use in this function)
client/snd_file.c:306: error: &#8216;samples&#8217; undeclared (first use in this function)
client/snd_file.c:343: error: &#8216;OV_HOLE&#8217; undeclared (first use in this function)
client/snd_file.c:346: error: &#8216;OV_EBADLINK&#8217; undeclared (first use in this function)
make[1]: *** [release/client/snd_file.o] Error 1
make[1]: Leaving directory `/home/joeelmex/Games/AlienArena/source'
make: *** [build-release] Error 2

```

I get the same error output.  Not sure which vorbis files we need.  :(

[edit]
It's libvorbis-dev.  

```
sudo apt-get install libvorbis-dev
```

then it compiles fine.

---

### Post by joeelmex on 2009-06-21
I am sure in time someone will post the answer..

---

### Post by QCompson on 2009-06-21
I just did, look at my post above again.  :D

---

### Post by mao_dze_dun on 2009-06-21
Ok guys I have a new problem - the game is quite laggy. I know that my pc is ancient but the previous version was running smooth as hell 99% of the time and this one even with practically all special effects turned off and quality at lowest still lags when there are other players on the screen.
Also for some unknown reason the sound is corrupt. The music and the sounds are skipping badly (even in the menu).

---

### Post by joeelmex on 2009-06-21
> **qcompson said:**
> i just did, look at my post above again.  :d



thank you playing now!!!  :ks:ks

---

### Post by BrowneR on 2009-06-21
Ok so I am trying to run this on Jaunty 32bit.

Firstly I get the following error:
```
error while loading shared libraries: libcurl.so.4: cannot open shared object file: No such file or directory
```

but this is an easy fix:
```
sudo ln -s /usr/lib/libcurl-gnutls.so.4 /usr/lib/libcurl.so.4
```

however now when I try and run the game its segfaulting after sound initialisation :confused:

```

chris@chris-laptop:~/Desktop/alienarena2009$ ./crx 
using /home/chris/.codered/data1/ for writing
using /home/chris/.codered/arena/ for writing
execing default.cfg
couldn't exec config.cfg
Console initialized.

------- sound initialization -------
Segmentation fault

```

---

### Post by Melcar on 2009-06-21
I was getting a segfault at startup too until I installed all this stuff:

```
sudo apt-get install build-essential libcurl4-openssl-dev libopenal-dev fakeroot devscripts debhelper dpatch libsdl1.2-dev libglu1-mesa-dev libgl1-mesa-dev libjpeg62-dev libxxf86vm-dev libxxf86dga-dev libxext-dev libx11-dev
```

My goal was to compile the game following the instructions on the first page, but after I installed all this the game started working.

---

### Post by BrowneR on 2009-06-21
> **Melcar said:**
> I was getting a segfault at startup too until I installed all these stuff:

```
sudo apt-get install build-essential libcurl4-openssl-dev libopenal-dev fakeroot devscripts debhelper dpatch libsdl1.2-dev libglu1-mesa-dev libgl1-mesa-dev libjpeg62-dev libxxf86vm-dev libxxf86dga-dev libxext-dev libx11-dev
```

My goal was to compile the game following the instructions on the first page, but after I installed all this the game started working.


Yep your exactly right. I went through the list and turns out libopenal-dev was the package I required to install. Thanks for that suggestion.

---

### Post by maxol on 2009-06-21
I installed alienarena2009 on my Jaunty 64 system but got a missing libraries error message when I tried to run it.

I installed getlibs as instructed in [this link]("http://ubuntuforums.org/showthread.php?t=474790").

Then I went to my installation folder.

```
cd /usr/local/games/alienarena2009
```

and ran

```
sudo getlibs crx
```

which automatically installed the missing 32 bit libraries for me.

Now the game runs great.

---

### Post by solitaire on 2009-06-21
Hm... I compiled it from source..
But my laptop hangs every time I try to play it. :(
Thinking of giving up on it (even the one form the repo's hangs my laptop) :(

Guess i'm not going to be able to play this ... :(:(

---

### Post by efikkan on 2009-06-21
I just tried quickplay and instant action. The game seems ok and is fun to play. Are the orther players in instant action other players online or AI-players?

---

### Post by MaxIBoy on 2009-06-21
> **mao_dze_dun said:**
> Ok guys I have a new problem - the game is quite laggy. I know that my pc is ancient but the previous version was running smooth as hell 99% of the time and this one even with practically all special effects turned off and quality at lowest still lags when there are other players on the screen.
Also for some unknown reason the sound is corrupt. The music and the sounds are skipping badly (even in the menu).I'm guessing that you have old graphics hardware. 

Try setting "r_legacy" to "1." When the game first runs, it creates a directory called .codered in your home folder. In there will be a directory called "arena." In there is a file called config.cfg. Edit the file, find where it says "r_legacy," and change "0" to "1."

> **efikkan said:**
> I just tried quickplay and instant action. The game seems ok and is fun to play. Are the orther players in instant action other players online or AI-players?In "instant action," you are playing against bots.

---

### Post by dvn7035 on 2009-06-22
Just a quick question will this run on a gma x3100 with our mest up drivers in Jaunty.

---

### Post by toupeiro on 2009-06-22
Ridiculously fun game!

---

### Post by efikkan on 2009-06-22
So I guess it's possible to play COOP over LAN against bots?

---

### Post by Irritant on 2009-06-22
> **efikkan said:**
> So I guess it's possible to play COOP over LAN against bots?

Well you could play teams, and have humans on one team, bots on another on a LAN.

---

### Post by unrater on 2009-06-22
Why we, ubuntu users, don't have .deb package?

The team could put the game in the lauchpad! :D

---

### Post by burnetbj on 2009-06-22
As the previous poster pointed out wheres the deb file ......I promote Open Source all day every day and Linux as well I struggle with linux and get by with support of the Buntu community but this is exactly why people steer away from linux in general

These people spent many hrs building such a beautiful looking game and yet make if hard as all hell to install. i realize i didnt put any effort in and i should help before complaining but i dont have the knowlage to help and trying to install a Linux download like this is silly 

If they are working on a RPM or Deb then they should post that on the download site for us rookies to wait for. 

Having someone go through a install like this is a put off in my point of view but any how long live Open Source

---

### Post by Melcar on 2009-06-22
What can be harder than *./crx*?  Yeah, if you happen to stumble upon dependency issues it can be hell, but that's easy enough to solve; a detailed list of dependencies on the site could alleviate this somewhat.  You also have the option of compiling it yourself (a visible guide on the site or on the forums would be helpful here too).
As for packages, I always believed that it's the responsibility of the distro maintainers to provide packages for their users.  There are also other projects, like *getdeb*, that do a good job at providing ready made packages; maybe it would be better to direct your queries to them instead.

---

### Post by unrater on 2009-06-22
> **Melcar said:**
> What can be harder than *./crx*?  Yeah, if you happen to stumble upon dependency issues it can be hell, but that's easy enough to solve; a detailed list of dependencies on the site could alleviate this somewhat.

Yes, for newbies it's not normal and it's a kind of complicated.

> **Melcar said:**
> You also have the option of compiling it yourself (a visible guide on the site or on the forums would be helpful here too).
For the consumer, who cares about compiling? He only wants the game installed as fast as possible, and, for that, we have the deb packages that should be provided by someone as fast as possible to publicize the software. And, if the developers want to promote the game they need to have some work in this area that is not complicated has programming a game like this.

---

### Post by burnetbj on 2009-06-22
Fare enough, i realize my ignorance is my fault and not the developers. Was just pointing out if the developers really wanted growth in market share they should focus on waiting a day or two to release the software till they had a easy point click package

Also i can buy your Distro should provide the deb or rpm, makes sense to me but why not release the game to the Distro first and then release it at a set date thus bypassing any unwanted frustration on potential new users

Anyhow I guess im done crying now :) will let it go and continue to try and learn how to get this thing going. For some reason after unzipping the file and i try and run those commands provided it tells me it is going to install blah blah, y/n so i pick yes and it wants me to install my 8.10 live .......grrrrr

Done for now need to try and get back to work :)

---

### Post by efikkan on 2009-06-22
> **Irritant said:**
> Well you could play teams, and have humans on one team, bots on another on a LAN. Exactly what I was thinking :) . There are not many good first-person-shooters wich features good bots.

---

### Post by Irritant on 2009-06-22
> **burnetbj said:**
> Also i can buy your Distro should provide the deb or rpm, makes sense to me but why not release the game to the Distro first and then release it at a set date thus bypassing any unwanted frustration on potential new users

That is probably a very good idea.

---

### Post by LoloftheRings on 2009-06-23
This game ran out of the box on Arch Linux, which is far more minimalistic than Ubuntu. I still want to use Ubuntu for gaming, since I get higher framerates.

EDIT: Strange, it runs perfectly, but in game, there is a little window in the middle displaying the game itself, and around that the kills, deaths, minimap and everything else..

---

### Post by Irritant on 2009-06-23
Sounds like you set the screen size to be low - go into vid options and set the slider all the way to the right.

We are going to disable that "feature", was a useless leftover from Q2.

---

### Post by ELD on 2009-06-23
Downloading now to have a little play.

---

### Post by emshains on 2009-06-24
Can I get it working without all the new libraries found in 9.04, if I am running on 8.04 ?

---

### Post by Irritant on 2009-06-24
> **emshains said:**
> Can I get it working without all the new libraries found in 9.04, if I am running on 8.04 ?

It should work fine, even if you have to recompile.  The older dependencies shouldn't matter.

---

### Post by MaxIBoy on 2009-06-24
> **Irritant said:**
> It should work fine, even if you have to recompile.  The older dependencies shouldn't matter.To get it working on 8.04, I needed to download newer versions of OpenAL. I downloaded the Intrepid versions, that worked.

Eventually though, I just upgraded. Now I'm running 9.10.

---

### Post by joeelmex on 2009-06-25
Still no deb for this awesome game?

---

### Post by demonon on 2009-06-25
This game still won't run on Jaunty x64.
Is there a way I can determine what is wrong.
I just cd to the folder and then type ./crx
It says crx is not found.

---

### Post by Irritant on 2009-06-25
> **demonon said:**
> This game still won't run on Jaunty x64.
Is there a way I can determine what is wrong.
I just cd to the folder and then type ./crx
It says crx is not found.

Did you recompile the binaries?

---

### Post by wolterh on 2009-06-25
Well, not to poop the party but, the game is not that awesome. You want some nice alien war game? Play Unreal Tournament 2004. Thats an awesome game. Native on linux and all.

---

### Post by demonon on 2009-06-26
> **Irritant said:**
> Did you recompile the binaries?

Yes, I tried recompiling crx like described in post #3.
I got an error message, let me try to reproduce the error and paste it here.

---

### Post by demonon on 2009-06-26
> **Irritant said:**
> Did you recompile the binaries?

I got it to work, I was missing vorbis packages.

---

### Post by Irritant on 2009-07-02
7.31 will be coming later in the summer, unless we find some critical bugs, and will have alot of new maps that take advantage of the new technologies.

Just finished remaking dm-saucer:

[[img]http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_17_s.jpg[/img]](http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_17.jpg) [[img]http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_18_s.jpg[/img]](http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_18.jpg) [[img]http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_19_s.jpg[/img]](http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_19.jpg) [[img]http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_20_s.jpg[/img]](http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_20.jpg)

---

### Post by Melcar on 2009-07-03
Nice.

---

### Post by uberlube on 2009-08-09
For some reason i get this during the 'make install'

```
cp release/cr* ../
cp release/game.so ../data1/
cp release/game.so ../arena/
cp: cannot create regular file `../arena/': Is a directory
make: *** [install] Error 1

```

any ideas?

---

### Post by Eladon on 2009-08-30
OK, so I finally got this game running per the advice in this thread... only catch is the game won't save any settings!  A game would have to be pretty darn good to spend 30 min setting it up every time I run it!  #-o

When I exit the game, I get:
```
Couldn't write config.cfg.
recursive shutdown

```

---

### Post by Perfect Storm on 2009-08-30
Sounds like you permission issues. Eg. you launched the game with superuser (do) permission.

---

### Post by Brebs on 2009-08-30
> **Eladon said:**
> Couldn't write config.cfg

Use [strace](http://corent.proboards.com/index.cgi?board=rookie&action=display&thread=86&page=2) to see where it is writing.

If it's trying to write somewhere outside of $HOME, then compile the game CORRECTLY, using WITH_DATADIR and WITH_LIBDIR - see the Makefile.

Here's yet another [distro compilation example](http://foo-projects.org/git/?p=lunar/moonbase.git;a=tree;f=games/alienarena). It's farcical how long Ubuntu/Debian [are taking to update](https://bugs.launchpad.net/ubuntu/+source/alien-arena/+bug/279429).

---

### Post by Eladon on 2009-08-30
Thanks Brebs,

Unfortunately I'm a n00b with strace so I imagine it's not working cuz I just don't know how to use it.  I tried the following per your link:
```
strace -e trace=file crx.sdl > alienarena.log 2>&1
```
but alienarena.log just says "strace: crx.sdl: command not found".

Had a look at your other links, and I can tell I am now way over my head.  I don't mind learning, so I encourage you to forward whatever advice you can.  But I can't deny the foreboding feeling that have I signed up for a 120 hour course on rocket science just to play a game?  :(

---

### Post by unzee1236 on 2009-09-06
Just thought I would post what I had to go through to get this runing, the extra stuff I needed 

................................................................

glx.h: No such file or directory 

sudo apt-get install --reinstall mesa-common-dev 

make[1]: *** [release/client/snd_openal.o] Error 1


libopenal-dev is libcurl4-openssl-dev

---------------------------------------
ref_gl/r_image.c:26:21: error: jpeglib.h: No such file or directory
ref_gl/r_image.c:28:20: error: GL/glu.h: No such file or directory



libcurl3-dev

--------------------
ref_gl/r_image.c:28:20: error: GL/glu.h: No such file or directory



 freeglut3-dev

------------------------------
 error: jpeglib.h: No such file or directory


libjpeg62-dev

--------------------------------

unix/gl_glx.c:56:36: error: X11/extensions/xf86dga.h: No such file or directory


x11proto-xf86dga-dev_
--------------------------------------

error: X11/extensions/xf86vmode.h: No such file or directory


libxxf86vm-dev 

----------------------------------------------

 cannot find -lXxf86dga

libxxf86dga-dev

---

### Post by Belgoroth on 2009-09-10
> **JMiserez said:**
> I had some problems running the game on Jaunty 64bit...

**crx: error while loading shared libraries: libXxf86dga.so.1: cannot open shared object file: No such file or directory**

...
I sadly get this error
./crx: error while loading shared libraries: libXxf86dga.so.1: wrong ELF class: ELFCLASS64
any ideas?

---

### Post by realzippy on 2009-09-10
> **Belgoroth said:**
> I sadly get this error
./crx: error while loading shared libraries: libXxf86dga.so.1: wrong ELF class: ELFCLASS64
any ideas?

What is the output from:

**ls /usr/lib | grep libXxf8**

---

### Post by Belgoroth on 2009-09-10
belgoroth@belgoroth-desktop:~$ ls /usr/lib | grep libXxf8
libXxf86dga.a
libXxf86dga.so
 libXxf86dga.so.1
libXxf86dga.so.1
libXxf86dga.so.1.0.0
libXxf86misc.so.1
libXxf86misc.so.1.1.0
libXxf86vm.a
libXxf86vm.so
libXxf86vm.so.1
libXxf86vm.so.1.0.0

---

### Post by realzippy on 2009-09-11
..you have the development files installed?:

libxxf86dga-dev 
libxxf86vm-dev

Found this in another forum:
[I]"I knew perfectly well I was running ubuntu amd64. What puzzles me is that those problems shouldn't arise, as I installed every i386 library and all this 32 bit stuff
docorange

The 32-bit library you need cannot be installed using apt-get because it is not included in the ia32-libs package and nor is it in any of the lib32* packages.

Install getlibs, change to the game directory where crx is located and run
sudo getlibs crx

If you have problems with that you can also use
**sudo getlibs -p libxxf86dga1**     "[/I]


get getlibs here:

[http://frozenfox.freehostia.com/cappy/getlibs-all.deb](http://frozenfox.freehostia.com/cappy/getlibs-all.deb)

---

### Post by Belgoroth on 2009-09-11
Thanks hey! that worked no problem :)

---

### Post by Belgoroth on 2009-09-11
:confused:sadly it does not I get into game and setup is fine but choosing instant action brings up elf class error 
======== CRX Initialized ========

------- Loading game.so -------
LoadLibrary (./arena/game.so): wrong ELF class: ELFCLASS64
********************
ERROR: failed to load game DLL
********************
Master server at 74.63.48.146:27900
Sending shutdown to 74.63.48.146:27900
Master server at 74.63.48.146:27900
Sending shutdown to 74.63.48.146:27900
recursive shutdown
belgoroth@belgoroth-desktop:~/Games/alienarena2009$

---

### Post by realzippy on 2009-09-11
Hm.How did you install alien arena?
Synaptic?

---

### Post by Belgoroth on 2009-09-12
I downloaded from the websight and did the whole make make install option I dont have it on synaptic. I have 6gig ram which is why I believe I need 64bit.  
it does run on my laptop which is Ubuntu studio alternative 8.04 but not enjoyable.

---

### Post by Perfect Storm on 2009-09-12
> **Belgoroth said:**
> I downloaded from the websight and did the whole make make install option I dont have it on synaptic. I have 6gig ram which is why I believe I need 64bit.  
it does run on my laptop which is Ubuntu studio alternative 8.04 but not enjoyable.

I haven't tested this guide since 8.10 - but you could give it a try; [http://gwos.org/doku.php/guides:64bit:alien_arena](http://gwos.org/doku.php/guides:64bit:alien_arena)

---

### Post by realzippy on 2009-09-12
> **Belgoroth said:**
> I downloaded from the websight and did the whole make make install option I dont have it on synaptic. I have 6gig ram which is why I believe I need 64bit.  
it does run on my laptop which is Ubuntu studio alternative 8.04 but not enjoyable.

No alien-arena in synaptic?So check your sources,I just installed it by
synaptic,it is 7.0,maybe not the newest one,but installs all dependencies and libs,so your compiled version should run also.


BTW,if you are interested in playing online,Quake3 now is for free:
Quakelive:
[http://www.quakelive.com/](http://www.quakelive.com/)
if you have nvidia installed,just sign in and play.It runs as fast as installed,there are lots of servers    ...and it looks better than alien-arena.

---

### Post by -_- Joseph -_- on 2009-09-12
omg im gonna dl soon and be playing it and its gonna kick some ***

---

### Post by Jose Catre-Vandis on 2009-09-13
OK, changing r_legacy to 1 sorted out my laggy problems, but some questions:

1. My "gun" is pointing at the floor when I first spawn, how do I point it at the bots/players?

2. Can I set the game up to run on my LAN so we can multiplay without going outside the LAN to an internet game server?

3. If 2 above, can I run the game on my server from a command line, and then access it from clients?

4. Where are there some more detailed instructions on how to play, keyboard commands etc. The Readme.txt is terse to say the least.

5. How do I respawn when I get get killed?

Thanks

---

### Post by Belgoroth on 2009-09-15
> **realzippy said:**
> 


BTW,if you are interested in playing online,Quake3 now is for free:
Quakelive:
[http://www.quakelive.com/](http://www.quakelive.com/)
if you have nvidia installed,just sign in and play.It runs as fast as installed,there are lots of servers    ...and it looks better than alien-arena.
Well not very good at FPS, online gaming`is not usually noob friendly, will see if it likes my 3G connection:)

My mirror didnt have it (university), switched to main repo and got 7, the compiled one also works after that :) thanks

---

### Post by Irritant on 2009-09-15
> **Jose Catre-Vandis said:**
> OK, changing r_legacy to 1 sorted out my laggy problems, but some questions:

1. My "gun" is pointing at the floor when I first spawn, how do I point it at the bots/players?

2. Can I set the game up to run on my LAN so we can multiplay without going outside the LAN to an internet game server?

3. If 2 above, can I run the game on my server from a command line, and then access it from clients?

4. Where are there some more detailed instructions on how to play, keyboard commands etc. The Readme.txt is terse to say the least.

5. How do I respawn when I get get killed?

Thanks

1 - that is not normal, and caused by malformed net packets.

2 - Yes

3 - Yes

4 - [http://alienarena.co.uk/](http://alienarena.co.uk/)

5 - Press fire button.

---

### Post by Jose Catre-Vandis on 2009-09-15
> **Irritant said:**
> 1 - that is not normal, and caused by malformed net packets.

2 - Yes

3 - Yes

4 - [http://alienarena.co.uk/](http://alienarena.co.uk/)

5 - Press fire button.

Thanks Irritant, any ideas on how to sort out Q 1, and I should have added How? to Qs 2 & 3 ;)

---

### Post by swedski on 2009-09-27
Hello 
Did all that and still got the error described running 9.04 x64

---

### Post by shyanel on 2009-10-27
Is anyone familiar with this error?

stu@stu-desktop:~/Desktop/alienarena7_32$ ./crx
./crx: error while loading shared libraries: libjpeg.so.7: cannot open shared object file: No such file or directory

Would really appreciate some help if anyone can shed some light on what's wrong.

I've compiled this as per the instructions on page 1 and everything seemed to go fine.

The "make" and "make install" commands executed okay, but when I type ./crx that's what I get.

Thanks

~Stu

---

### Post by Irritant on 2009-10-27
> **shyanel said:**
> Is anyone familiar with this error?

stu@stu-desktop:~/Desktop/alienarena7_32$ ./crx
./crx: error while loading shared libraries: libjpeg.so.7: cannot open shared object file: No such file or directory

Would really appreciate some help if anyone can shed some light on what's wrong.

I've compiled this as per the instructions on page 1 and everything seemed to go fine.

The "make" and "make install" commands executed okay, but when I type ./crx that's what I get.

Thanks

~Stu

Are you sure it compiled ok?  Check the date of crx, because it should be compiling using the libraries you have, and that is a library that Ubuntu doesn't have yet.

---

### Post by hammeredd on 2009-11-10
i am having the same problem can someone help me?very new to all this been trying to sort problem now for 12 hours straight!!!!!!!!HELP

---

### Post by Melcar on 2009-11-10
The latest Ubuntu ships with libjpeg62, so unless you compile the latest libjpeg on your own, recompiling the AA sources is supposedly the only way of getting it to work.  I have tried following a few guides out there but I always get errors while compiling.  Odd thing is that I can compile previous versions of AA just fine.  Our good friend Artificial Intelligence is looking through the gaming guides, so if anything comes out he will let us know.

---

### Post by Perfect Storm on 2009-11-10
Well, I managed to compile it. But it won't run. I get No error output, nothing in the error logs. Nothing.... 


Melcar, the guide is updated. Try give it a whirl and see if you have more luck than me.

To those who get libjpeg.so.7 error, tried with a symblink?

---

### Post by Irritant on 2009-11-10
AI, what version are you compiling?  There is a known error with anything previous to 7.32 when using the latest Nvidia drivers, this is a bug that is widespread among many id based games.

---

### Post by Perfect Storm on 2009-11-10
> **Irritant said:**
> AI, what version are you compiling?  There is a known error with anything previous to 7.32 when using the latest Nvidia drivers, this is a bug that is widespread among many id based games.

Must be it. I'm running latest nvidia driver (190.42). Is it fixed in the SVN?

---

### Post by Steve60938 on 2009-11-10
I downloaded it tried to run it just as is but it wont, like not even an error just plain wont so i found this and followed the instructions and tried to "makefile" but it gives me this lil nifty bunch of errors:



sudo /usr/local/games/alienarena7_32/source/Makefile /usr/local/games/alienarena7_32/source/Makefile: 8: CC?=gcc: not found
/usr/local/games/alienarena7_32/source/Makefile: 11: OPTIMIZED_CFLAGS?=yes: not found
/usr/local/games/alienarena7_32/source/Makefile: 14: OPTIM_LVL?=2: not found
/usr/local/games/alienarena7_32/source/Makefile: 17: LOCALBASE?=/usr/local: not found
/usr/local/games/alienarena7_32/source/Makefile: 20: X11BASE?=/usr/X11R6: not found
/usr/local/games/alienarena7_32/source/Makefile: 23: BUILD?=ALL: not found
/usr/local/games/alienarena7_32/source/Makefile: 26: WITH_DATADIR?=no: not found
/usr/local/games/alienarena7_32/source/Makefile: 27: WITH_LIBDIR?=no: not found
/usr/local/games/alienarena7_32/source/Makefile: 31: 1.40: not found
/usr/local/games/alienarena7_32/source/Makefile: 33: shell: not found
/usr/local/games/alienarena7_32/source/Makefile: 33: ARCH:=: not found
/usr/local/games/alienarena7_32/source/Makefile: 34: shell: not found
/usr/local/games/alienarena7_32/source/Makefile: 34: OSTYPE:=: not found
/usr/local/games/alienarena7_32/source/Makefile: 36: ./: Permission denied
/usr/local/games/alienarena7_32/source/Makefile: 38: release: not found
/usr/local/games/alienarena7_32/source/Makefile: 39: debug: not found
/usr/local/games/alienarena7_32/source/Makefile: 40: MOUNT_DIR: not found
/usr/local/games/alienarena7_32/source/Makefile: 40: /client: not found
/usr/local/games/alienarena7_32/source/Makefile: 41: MOUNT_DIR: not found
/usr/local/games/alienarena7_32/source/Makefile: 41: /server: not found
/usr/local/games/alienarena7_32/source/Makefile: 42: MOUNT_DIR: not found
/usr/local/games/alienarena7_32/source/Makefile: 42: /ref_gl: not found
/usr/local/games/alienarena7_32/source/Makefile: 43: MOUNT_DIR: not found
/usr/local/games/alienarena7_32/source/Makefile: 43: /qcommon: not found
/usr/local/games/alienarena7_32/source/Makefile: 44: MOUNT_DIR: not found
/usr/local/games/alienarena7_32/source/Makefile: 44: /unix: not found
/usr/local/games/alienarena7_32/source/Makefile: 45: MOUNT_DIR: not found
/usr/local/games/alienarena7_32/source/Makefile: 45: /game: not found
/usr/local/games/alienarena7_32/source/Makefile: 46: MOUNT_DIR: not found
/usr/local/games/alienarena7_32/source/Makefile: 46: /null: not found
/usr/local/games/alienarena7_32/source/Makefile: 47: GAME_DIR: not found
/usr/local/games/alienarena7_32/source/Makefile: 49: Syntax error: word unexpected (expecting ")")

---

### Post by Irritant on 2009-11-11
> **Artificial Intelligence said:**
> Must be it. I'm running latest nvidia driver (190.42). Is it fixed in the SVN?

Yup, was fixed a couple of weeks ago.

---

### Post by RabidWeezle on 2009-11-11
If/When this gets resolved, will the repo be updated with latest?

---

### Post by Perfect Storm on 2009-11-11
> **RabidWeezle said:**
> If/When this gets resolved, will the repo be updated with latest?

The official repo? No.

You might ask playdeb or getdeb when AA gets an official update release with the fixes.

---

### Post by Melcar on 2009-11-11
Playdeb already has a 7.32 package available it seems.

[http://www.playdeb.net/updates/?page=4#alien-arena]("http://www.playdeb.net/updates/?page=4#alien-arena")

---

### Post by Perfect Storm on 2009-11-11
Yep, but the fixes are in the SVN.

---

### Post by Irritant on 2009-11-11
We'll probably be putting out 7.33 in a couple of weeks.  It's alot earlier then we'd like, but because of the bugfixes, as well as issue of the pre-compiled versions using libjpeg7, it's kind of forcing our hand a bit here.

There was also another fix that corrected an FPS problem for some drivers/CPU combos as well, and we also added in our stats and matchmaker in the server browser.  I was hoping to add the in-game IRC client before this release, but that might be asking for trouble, we really need to stabilize the 7.3x series first.  So we are going to give it a couple of weeks, to make sure all is ok, and in the meanwhile I'll probably work on a new map to include, and Emp might be finished up his epic remake of Dm-Zorn by then.

---

### Post by Steve60938 on 2009-11-13
No help for me?

---

### Post by Perfect Storm on 2009-11-13
Try now: [http://gwos.org/doku.php/guides:64bit:alien_arena](http://gwos.org/doku.php/guides:64bit:alien_arena)
The guide have been updated to use SVN version.

---

### Post by raynman on 2009-11-13
[LIST=1]
[*]I followed the guide (64 bit). Every thing works fine as far as compile, but game hangs at sound initialisation.
[/LIST]
still get 

AL lib: oss.c:179: Could not open /dev/dsp: Device or resource busy

Anyone have any ideas on this?

I tried stopping pulseaudio, which works when I run Enemy Territory, but this was no help for Alien Arena. Alien Arena 2007 worked fine, but can't get newer versions to run after successful compile.

Ubuntu 9.10
64 bit

---

### Post by raynman on 2009-11-13
I finally fixed this with info on the alien arena forum.

I created a new file:
[SIZE=2] *~/.alsoftrc*[/SIZE]

and added the entry:
[SIZE=2][FONT=Arial,Helvetica][SIZE=1][FONT=Courier New][SIZE=2][general] 
          drivers = oss[/SIZE][/FONT][/SIZE][/FONT][/SIZE]

now running great on Ubuntu 9.10 on an intel 64 bit laptop.

---

### Post by Dantheman53 on 2009-11-14
> **Artificial Intelligence said:**
> Try now: [http://gwos.org/doku.php/guides:64bit:alien_arena](http://gwos.org/doku.php/guides:64bit:alien_arena)
The guide have been updated to use SVN version.

I installed it using this guide and....

> I finally fixed this with info on the alien arena forum.

I created a new file:
[SIZE=2] *~/.alsoftrc*[/SIZE]

and added the entry:
[SIZE=2][FONT=Arial,Helvetica][SIZE=1][FONT=Courier New][SIZE=2][general] 
          drivers = oss[/SIZE][/FONT][/SIZE][/FONT][/SIZE]

now running great on Ubuntu 9.10 on an intel 64 bit laptop.     That fixed the sound issue. It runs perfect now on my desktop 9.10 64 bit.

Thanks everyone!

---

### Post by DynastyX on 2009-11-26
I'm having troubles with this game, I'm using 32 bit Karmic and I downloaded the game through the software center... I can play in single player mode without any issues, but usually when I try to join a server, the game crashes. I've gotten in server games three or four times, but it's very rare and it usually crashes after a few minutes of playing. Can anyone help?

---

### Post by Melcar on 2009-11-27
Try launching the game in window mode from a terminal.  See what kind of output you get.

---

### Post by DynastyX on 2009-11-27
The last bit of text before it crashes was this,
> 
Server does not have file sound/bots/Mogera.wav.
Server does not have file sound/bots/Ghidora.wav.
Server does not have file sound/bots/Mothra.wav.
Server does not have file sound/bots/Hedora.wav.
Server does not have file sound/weapons/hyprbd1a.wav.
*** buffer overflow detected ***: /usr/lib/games/alien-arena/crx.sdl terminated

There's a bunch of gibberish afterwards but there was nothing that looked important.

---

### Post by DynastyX on 2009-11-27
Bump... Any ideas?

---

### Post by Love2MeetU on 2009-12-08
Alien Arena 7.00 crashes on my PC as well. Can't join a game, can't host a game, can't join any servers. No play time at all. Nada. A great big zero.

I'm using Ubuntu 9.10

---

### Post by Love2MeetU on 2009-12-11
I'm getting this problem near the end


> make: *** No targets specified and no makefile found. Stop.

---

### Post by Love2MeetU on 2009-12-11
Tried again, this time I have a different problem and the game still doesn't start.> 
execing default.cfg
couldn't exec config.cfg
Console initialized.

------- sound initialization -------
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
AL lib: oss.c:179: Could not open /dev/dsp: Device or resource busyThen it just hangs.......
:(

If "bt" is for Bluetooth, well I'm sure that I don't have any Bluetooth devices on my PC.

---

### Post by Love2MeetU on 2009-12-11
> **raynman said:**
> I finally fixed this with info on the alien arena forum.

I created a new file:
[SIZE=2] *~/.alsoftrc*[/SIZE]

and added the entry:
[SIZE=2][FONT=Arial,Helvetica][SIZE=1][FONT=Courier New][SIZE=2][general] 
          drivers = oss[/SIZE][/FONT][/SIZE][/FONT][/SIZE]

now running great on Ubuntu 9.10 on an intel 64 bit laptop.

Maybe this is what I need...BUT where do I put it?

Where does that file go?

---

### Post by Irritant on 2009-12-11
Do you have OpenAL installed?

---

### Post by Love2MeetU on 2009-12-11
> **Irritant said:**
> Do you have OpenAL installed?

I have some related lib files. 
 libopenal1
libopenal-dev

Is that it?

---

### Post by Melcar on 2009-12-11
> **Love2MeetU said:**
> Maybe this is what I need...BUT where do I put it?

Where does that file go?

In your home directory.  It works, as it fixed the faulty sound initialization (the game hangs at start-up).  The only "problem" is that sound is rather weak; had to crack up the volume more than usual to get good sound.

---

### Post by Love2MeetU on 2009-12-12
> **Melcar said:**
> In your home directory.  It works, as it fixed the faulty sound initialization (the game hangs at start-up).  The only "problem" is that sound is rather weak; had to crack up the volume more than usual to get good sound.

So, just to be clear, I create that file with gedit, then paste in that particular line, then put it in my home directory itself and that's all? Is that right? I don't know linux that well, so I have to double-check as everyone seems to be assuming a knowledge of linux that noobies such as I don't have.

Like what does && mean?

---

### Post by Love2MeetU on 2009-12-12
> **Melcar said:**
> In your home directory.  It works, as it fixed the faulty sound initialization (the game hangs at start-up).  The only "problem" is that sound is rather weak; had to crack up the volume more than usual to get good sound.


IT WORKED.

What you said, it fixed the problem and the game is running purrrrrrfect!
:D

---

### Post by yanom on 2009-12-12
> **Love2MeetU said:**
> IT WORKED.

What you said, it fixed the problem and the game is running purrrrrrfect!
:D

making that file fixed my problem to.

---

### Post by Love2MeetU on 2009-12-13
> **Artificial Intelligence said:**
> Try now: [http://gwos.org/doku.php/guides:64bit:alien_arena](http://gwos.org/doku.php/guides:64bit:alien_arena)
The guide have been updated to use SVN version.

My sound for Alien Arena is erratic. Sometimes when I start a game it's fine, other times, there's no sound. When I try this in the guide;
> If the sound fails in Alien Arena, open alacarte and edit Alien Arena, to use ./crx.sdl instead. 
Like this; 
**Command:** sh -c "cd ~/.Games/AlienArena && ./crx.sdl" 
-then the game doesn't start up at all.

---

### Post by Love2MeetU on 2009-12-14
> **Love2MeetU said:**
> My sound for Alien Arena is erratic. Sometimes when I start a game it's fine, other times, there's no sound. When I try this in the guide;

-then the game doesn't start up at all.

Found the problem with the sound, it was "Mumble" interfering with it. **I'd like to fix that, but not sure where the settings are for it.** The problem is that when Mumble starts first, I have sound from Mumble but not from Alien Arena. When Alien Arena starts first, I have sound from the game, but not from Mumble.

Also, I now have ANOTHER problem, but not on my PC.[FONT=Arial][SIZE=1]

[/SIZE][/FONT]  [FONT=Arial][SIZE=1]I just finished loading the latest Alien Arena (from the svn) onto my son's PC but got a bothersome little problem; as soon as the mouse is moved only a moment after spawning, the gun is stuck pointed at the ceiling. Great view of the ceiling in dm-deathray, but it would be nice to be able to aim at something else. I'm sure it's something simple to fix.

Any ideas? For both of these problems?

EDIT; for the problem with the "gun-pointing-at-ceiling", the trick is to put the *set in_dgamouse "0"* in an *config.cfg* file in the *~/.codered/arena* subdirectory, then it works. :) Thanks for the solution that was suggested by stratocaster on the Alien Arena forums.

EDIT - 2 : 
the problem with Mumble sound conflicting with Alien Arena sound has been solved.
Problem solved thanks to advice from Stratocaster on the Alien Arena forums.

The solution is posted here
[http://corent.proboards.com/index.cgi?action=display&board=aatech&thread=4544&page=1](http://corent.proboards.com/index.cgi?action=display&board=aatech&thread=4544&page=1)
[/SIZE][/FONT]

---

### Post by Scott O'Nanski on 2009-12-23
I've got it installed. How do I uninstall it?

---

### Post by Love2MeetU on 2009-12-24
Got another problem on my son's PC with the Alien Arena 2009 install. He has an older computer, Pentium with 1.7ghz, about 1gb of RAM, and 64mb AGP card. The game runs fine as "host", so he's been hosting many games recently and enjoying that, BUT...... he's unable to JOIN any other games. Always the game ends up with a black screen or crashes.

This is very frustrating for him as you can imagine.

Settings are already low, most of the options are off, r_legacy is set to "1" and glsl shaders is set to "0" as advised earlier in this thread.

Btw, neither one of us - with two very different computers - can get Mumble's sound at the same time as Alien Arena 2009. Just to add to the frustrations.

---

### Post by Love2MeetU on 2009-12-24
> **Scott O'Nanski said:**
> I've got it installed. How do I uninstall it?

When I had to, I just deleted the file folders. They're hidden, so you have to click on "view hidden files". You need to delete .codered in your home folder, and then go to the .Games folder to delete the AlienArena folder. You'll also have a AA folder on your desktop most likely, which is easy to delete. For the Menu, just go to System>Preferences>Main Menu>Games and delete the link. Only takes about a minute or two probably.

---

### Post by MaxIBoy on 2009-12-26
> **Love2MeetU said:**
> Got another problem on my son's PC with the Alien Arena 2009 install. He has an older computer, Pentium with 1.7ghz, about 1gb of RAM, and 64mb AGP card. The game runs fine as "host", so he's been hosting many games recently and enjoying that, BUT...... he's unable to JOIN any other games. Always the game ends up with a black screen or crashes.

This is very frustrating for him as you can imagine.

Settings are already low, most of the options are off, r_legacy is set to "1" and glsl shaders is set to "0" as advised earlier in this thread.So the game runs OK as a listen server, and he can join his own servers? Try having him run the game from the terminal, and when it crashes, copy and paste the output of the game into a forum post. You may get better help on the AA forums as well, the developers of the game are always there and ready to help people get it working: [http://corent.proboards.com/index.cgi?](http://corent.proboards.com/index.cgi?)

---

### Post by Scott O'Nanski on 2009-12-26
> **Love2MeetU said:**
> When I had to, I just deleted the file folders. They're hidden, so you have to click on "view hidden files". You need to delete .codered in your home folder, and then go to the .Games folder to delete the AlienArena folder. You'll also have a AA folder on your desktop most likely, which is easy to delete. For the Menu, just go to System>Preferences>Main Menu>Games and delete the link. Only takes about a minute or two probably.

Thanks.

I know there's a proper way to uninstall files that were installed through tars - but this didn't install an uninstall script or whatever Linux guys make that supposed to uninstall their software, but is rarely included or documented.

Maybe I'll ask the guys who made the game.

I have to admit this is one of the many things that upsets me about the OpenSource community. Very poor documentation to enable people to use software "freely". 

If the basic understanding of someone who knows very little about GNU/Linux can comprehend the need for thorough explanation regarding installation/uninstallion proceedures, then I can only conclude the lack thereof is done on purpose.

Why spend years on building something without bothering to take the extra ten minutes to explain the most basic functions of your software?

---

### Post by MaxIBoy on 2009-12-26
If you installed from a .deb package somewhere, remove it using Synaptic. 


Uninstall scripts are usually only necessary for more-complex stuff, like if it put anything in your actual system directories. But this game is entirely self-contained in one folder, plus a .codered folder for each user to store settings and so on. Just delete the .codered folder (for any user who ran the game,) and the main Alien Arena directory, and you're good. 

Actually, here's an uninstaller script for you:
```
#! /bin/bash
curdir=`pwd` #get the name of the current directory
cd .. #change to the parent directory
rm -r $curdir #remove the (formerly) current directory
rm -r ~/.codered #remove the settings files 
```Put it in a text file named "removeaa.sh" in your main AA directory (the one with "crx" in it.) Then "cd" to that directory in a terminal and run these commands:
```
chmod +x removeaa.sh #allow the script to run as a program
./removeaa.sh #run it 
```If anyone actually thinks that's easier than simply deleting the two folders in a file browser, they are free to use this method instead.

---

### Post by nerdy_kid on 2009-12-26
hi all, im getting a buffer overflow.  I downloaded the .deb from playdeb.net, i think the .deb is supposed to be for jaunty, but plenty of jaunty programs work on karmic.  Heres the error:

```

 
using /home/____/.alien-arena/data1/ for writing
using /home/____/.alien-arena/arena/ for writing
execing default.cfg                              
execing config.cfg                               
Console initialized.                             

------- sound initialization -------
sound sampling rate: 44100          
------------------------------------
--------- [Loading Renderer] ---------
ref_gl version: GL 0.01               
Initializing OpenGL display           
...setting fullscreen mode -1: 1280 800
Using XFree86-VidModeExtension Version 2.2
GL_VENDOR: NVIDIA Corporation             
GL_RENDERER: GeForce 8600M GT/PCI/SSE2    
GL_VERSION: 3.2.0 NVIDIA 190.53           
*** buffer overflow detected ***: /usr/lib/games/alien-arena/crx.sdl terminated
======= Backtrace: =========                                                   
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0x507de8]                    
/lib/tls/i686/cmov/libc.so.6[0x506e20]                                         
/lib/tls/i686/cmov/libc.so.6[0x506558]                                         
/lib/tls/i686/cmov/libc.so.6(_IO_default_xsputn+0x9e)[0x49059e]                
/lib/tls/i686/cmov/libc.so.6(_IO_vfprintf+0x384c)[0x46738c]                    
/lib/tls/i686/cmov/libc.so.6(__vsprintf_chk+0xad)[0x50660d]                    
/usr/lib/games/alien-arena/crx.sdl[0x808b753]                                  
======= Memory map: ========                                                   
00110000-00112000 r-xp 00000000 08:01 263956     /usr/lib/libXau.so.6.0.0      
00112000-00113000 r--p 00001000 08:01 263956     /usr/lib/libXau.so.6.0.0      
00113000-00114000 rw-p 00002000 08:01 263956     /usr/lib/libXau.so.6.0.0      
00114000-00115000 r-xp 00000000 08:01 297708     /usr/lib/tls/libnvidia-tls.so.190.53
00115000-00116000 rw-p 00000000 08:01 297708     /usr/lib/tls/libnvidia-tls.so.190.53
00116000-00132000 r-xp 00000000 08:01 411        /lib/libgcc_s.so.1                  
00132000-00133000 r--p 0001b000 08:01 411        /lib/libgcc_s.so.1                  
00133000-00134000 rw-p 0001c000 08:01 411        /lib/libgcc_s.so.1                  
00134000-00136000 r-xp 00000000 08:01 131628     /lib/tls/i686/cmov/libdl-2.10.1.so  
00136000-00137000 r--p 00001000 08:01 131628     /lib/tls/i686/cmov/libdl-2.10.1.so  
00137000-00138000 rw-p 00002000 08:01 131628     /lib/tls/i686/cmov/libdl-2.10.1.so  
00138000-001a6000 r-xp 00000000 08:01 295776     /usr/lib/libGLU.so.1.3.070600       
001a6000-001a7000 r--p 0006e000 08:01 295776     /usr/lib/libGLU.so.1.3.070600       
001a7000-001a8000 rw-p 0006f000 08:01 295776     /usr/lib/libGLU.so.1.3.070600       
001a8000-001e5000 r-xp 00000000 08:01 264137     /usr/lib/libcurl-gnutls.so.4.1.1    
001e5000-001e6000 r--p 0003d000 08:01 264137     /usr/lib/libcurl-gnutls.so.4.1.1    
001e6000-001e7000 rw-p 0003e000 08:01 264137     /usr/lib/libcurl-gnutls.so.4.1.1    
001e7000-001fc000 r-xp 00000000 08:01 131965     /lib/tls/i686/cmov/libpthread-2.10.1.so
001fc000-001fd000 r--p 00014000 08:01 131965     /lib/tls/i686/cmov/libpthread-2.10.1.so
001fd000-001fe000 rw-p 00015000 08:01 131965     /lib/tls/i686/cmov/libpthread-2.10.1.so
001fe000-00200000 rw-p 00000000 00:00 0                                                 
00200000-0020d000 r-xp 00000000 08:01 264689     /usr/lib/liblber-2.4.so.2.5.1          
0020d000-0020e000 r--p 0000c000 08:01 264689     /usr/lib/liblber-2.4.so.2.5.1          
0020e000-0020f000 rw-p 0000d000 08:01 264689     /usr/lib/liblber-2.4.so.2.5.1          
0020f000-00213000 r-xp 00000000 08:01 263967     /usr/lib/libXdmcp.so.6.0.0             
00213000-00214000 rw-p 00003000 08:01 263967     /usr/lib/libXdmcp.so.6.0.0             
00214000-00216000 r-xp 00000000 08:01 1943       /lib/libcom_err.so.2.1                 
00216000-00217000 r--p 00001000 08:01 1943       /lib/libcom_err.so.2.1                 
00217000-00218000 rw-p 00002000 08:01 1943       /lib/libcom_err.so.2.1                 
00218000-00342000 r-xp 00000000 08:01 263952     /usr/lib/libX11.so.6.2.0               
00342000-00343000 ---p 0012a000 08:01 263952     /usr/lib/libX11.so.6.2.0               
00343000-00344000 r--p 0012a000 08:01 263952     /usr/lib/libX11.so.6.2.0               
00344000-00346000 rw-p 0012b000 08:01 263952     /usr/lib/libX11.so.6.2.0               
00346000-00347000 rw-p 00000000 00:00 0                                                 
00347000-0035b000 r-xp 00000000 08:01 556        /lib/libz.so.1.2.3.3                   
0035b000-0035c000 r--p 00013000 08:01 556        /lib/libz.so.1.2.3.3                   
0035c000-0035d000 rw-p 00014000 08:01 556        /lib/libz.so.1.2.3.3                   
0035d000-00364000 r-xp 00000000 08:01 264637     /usr/lib/libkrb5support.so.0.1         
00364000-00365000 r--p 00006000 08:01 264637     /usr/lib/libkrb5support.so.0.1         
00365000-00366000 rw-p 00007000 08:01 264637     /usr/lib/libkrb5support.so.0.1         
00366000-00369000 r-xp 00000000 08:01 460        /lib/libgpg-error.so.0.4.0             
00369000-0036a000 r--p 00002000 08:01 460        /lib/libgpg-error.so.0.4.0             
0036a000-0036b000 rw-p 00003000 08:01 460        /lib/libgpg-error.so.0.4.0             
0036b000-0036d000 rwxp 00000000 00:0f 1586       /dev/zero                              
0036e000-00373000 r-xp 00000000 08:01 264005     /usr/lib/libXxf86dga.so.1.0.0          
00373000-00374000 r--p 00004000 08:01 264005     /usr/lib/libXxf86dga.so.1.0.0          
00374000-00375000 rw-p 00005000 08:01 264005     /usr/lib/libXxf86dga.so.1.0.0          
00375000-003a5000 r-xp 00000000 08:01 264375     /usr/lib/libidn.so.11.5.44             
003a5000-003a6000 ---p 00030000 08:01 264375     /usr/lib/libidn.so.11.5.44             
003a6000-003a7000 r--p 00030000 08:01 264375     /usr/lib/libidn.so.11.5.44             
003a7000-003a8000 rw-p 00031000 08:01 264375     /usr/lib/libidn.so.11.5.44             
003a8000-003ab000 r-xp 00000000 08:01 631        /lib/libuuid.so.1.3.0                  
003ab000-003ac000 r--p 00002000 08:01 631        /lib/libuuid.so.1.3.0                  
003ac000-003ad000 rw-p 00003000 08:01 631        /lib/libuuid.so.1.3.0                  
003ad000-003b2000 r-xp 00000000 08:01 264798     /usr/lib/libogg.so.0.6.0               
003b2000-003b3000 r--p 00004000 08:01 264798     /usr/lib/libogg.so.0.6.0               
003b3000-003b4000 rw-p 00005000 08:01 264798     /usr/lib/libogg.so.0.6.0               
003b9000-003bd000 r-xp 00000000 08:01 270027     /usr/lib/libXxf86vm.so.1.0.0           
003bd000-003be000 r--p 00003000 08:01 270027     /usr/lib/libXxf86vm.so.1.0.0           
003be000-003bf000 rw-p 00004000 08:01 270027     /usr/lib/libXxf86vm.so.1.0.0           
003bf000-00406000 r-xp 00000000 08:01 264694     /usr/lib/libldap_r-2.4.so.2.5.1
00406000-00407000 ---p 00047000 08:01 264694     /usr/lib/libldap_r-2.4.so.2.5.1
00407000-00408000 r--p 00047000 08:01 264694     /usr/lib/libldap_r-2.4.so.2.5.1
00408000-00409000 rw-p 00048000 08:01 264694     /usr/lib/libldap_r-2.4.so.2.5.1
00409000-0040a000 rw-p 00000000 00:00 0
0040a000-00425000 r-xp 00000000 08:01 86         /lib/ld-2.10.1.so
00425000-00426000 r--p 0001a000 08:01 86         /lib/ld-2.10.1.so
00426000-00427000 rw-p 0001b000 08:01 86         /lib/ld-2.10.1.so
00427000-00565000 r-xp 00000000 08:01 131625     /lib/tls/i686/cmov/libc-2.10.1.so
00565000-00567000 r--p 0013e000 08:01 131625     /lib/tls/i686/cmov/libc-2.10.1.so
00567000-00568000 rw-p 00140000 08:01 131625     /lib/tls/i686/cmov/libc-2.10.1.so
00568000-0056b000 rw-p 00000000 00:00 0
0056b000-00596000 r-xp 00000000 08:01 264287     /usr/lib/libgssapi_krb5.so.2.2
00596000-00597000 r--p 0002a000 08:01 264287     /usr/lib/libgssapi_krb5.so.2.2
00597000-00598000 rw-p 0002b000 08:01 264287     /usr/lib/libgssapi_krb5.so.2.2
00598000-005af000 r-xp 00000000 08:01 263874     /usr/lib/libICE.so.6.3.0
005af000-005b0000 r--p 00016000 08:01 263874     /usr/lib/libICE.so.6.3.0
005b0000-005b1000 rw-p 00017000 08:01 263874     /usr/lib/libICE.so.6.3.0
005b1000-005b3000 rw-p 00000000 00:00 0
005b3000-005c3000 r-xp 00000000 08:01 131966     /lib/tls/i686/cmov/libresolv-2.10.1.so
005c3000-005c4000 r--p 00010000 08:01 131966     /lib/tls/i686/cmov/libresolv-2.10.1.so
005c4000-005c5000 rw-p 00011000 08:01 131966     /lib/tls/i686/cmov/libresolv-2.10.1.so
005c5000-005c7000 rw-p 00000000 00:00 0
005c7000-005d7000 r-xp 00000000 08:01 265047     /usr/lib/libtasn1.so.3.1.5
005d7000-005d8000 r--p 0000f000 08:01 265047     /usr/lib/libtasn1.so.3.1.5
005d8000-005d9000 rw-p 00010000 08:01 265047     /usr/lib/libtasn1.so.3.1.5
005da000-00646000 r-xp 00000000 08:01 277937     /usr/lib/libSDL-1.2.so.0.11.2Received signal 6, exiting...

```

*sigh* Nexuiz is way easier to install IMO -- download. run. play. be happy :)  the very size of this thread testifies to my point

---

### Post by Irritant on 2009-12-26
> **Scott O'Nanski said:**
> If the basic understanding of someone who knows very little about GNU/Linux can comprehend the need for thorough explanation regarding installation/uninstallion proceedures, then I can only conclude the lack thereof is done on purpose.

Why spend years on building something without bothering to take the extra ten minutes to explain the most basic functions of your software?

Misguided.  Sorry, but that's the truth.

The devs aren't responsible for the .debs, or any other installation procedures outside of simply unzippping a file.  Which anyone can uninstall simply by deleting the folder they unzipped it into.  

We don't have the time, or the energy to build a game, and worry about the 18 billion flavors/versions of linux and their respective package managers.  We leave that up to the respective communities of Linux flavors to worry about.  I don't mean that to sound offensive, but this is something we just don't have the time for.  We do the best we can just to make sure the game can run on most versions of Linux, and provide the most basic of installation options.

---

### Post by Love2MeetU on 2009-12-27
> **MaxIBoy said:**
> So the game runs OK as a listen server, and he can join his own servers? Try having him run the game from the terminal, and when it crashes, copy and paste the output of the game into a forum post. You may get better help on the AA forums as well, the developers of the game are always there and ready to help people get it working: [http://corent.proboards.com/index.cgi?](http://corent.proboards.com/index.cgi?)

Last part just before the problem comes up

> ...Initializing VBO cache
...GL_ARB_fragment_program not found
...One or more GL_ARB_shader_objects functions were not foundGL_FRAMEBUFFER_COMPLETE_EXT failed, CANNOT use FBO
glGetError() = 0x501


After this, we get sound but only a black screen.

---

### Post by Irritant on 2009-12-27
> **Love2MeetU said:**
> Last part just before the problem comes up



After this, we get sound but only a black screen.

Likely driver issue.  What video card is this?

---

### Post by simple simon on 2010-04-05
How would I play it over LAN? I have Alien Arena on two computers, both connected to my network, and I want to play against my dad who would be on the other computer.

---

### Post by Irritant on 2010-04-05
> **simple simon said:**
> How would I play it over LAN? I have Alien Arena on two computers, both connected to my network, and I want to play against my dad who would be on the other computer.

Just go into the menu, and "host server", give the server a unique name, select the map/modes you want and hit "begin".  You can disable bots, etc in the deathmatch and bot flags submenu.  Then have your dad fire up the game on his computer, click on "join server", and look for your server's name in the list, it should be at the top, or near it.  He can just double click on it to join.

---

### Post by simple simon on 2010-04-06
:)    Thanks, but sometimes it doesn't come up on the list of servers. Any ideas?

---

### Post by Irritant on 2010-04-07
> **simple simon said:**
> :)    Thanks, but sometimes it doesn't come up on the list of servers. Any ideas?

Could be a router/port forwarding issue.  The game's server default port is 27910.

---

### Post by zanto on 2010-10-30
are there any cheats or  guides for this game? i'm an old fogey and i cannot even figure out what to do before i get shot

---

### Post by Irritant on 2010-10-30
Here is a very good guide - [http://alienarena.co.uk/](http://alienarena.co.uk/)

---

