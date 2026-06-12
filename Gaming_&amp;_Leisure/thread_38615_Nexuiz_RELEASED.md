---
title: "Nexuiz RELEASED"
date: 2005-06-01
forum: Gaming &amp; Leisure
---

### Post by dolny on 2005-06-01
I think this deserves a new thread - Nexuiz.com has been released :D

[http://www.nexuiz.com](http://www.nexuiz.com)

Discuss here :)

---

### Post by fng on 2005-06-01
Certainly gonna test it tonight

---

### Post by gil-galad on 2005-06-01
I am on the torrent!  :razz: 

[http://www.liflg.org/?catid=6&gameid=64](http://www.liflg.org/?catid=6&gameid=64)

---

### Post by senectus on 2005-06-01
For the lazy:
> News

Tuesday May 31th , 2005 - Lee Vermeulen
After many years of development, Nexuiz has been released to the public! Nexuiz is a fast-paced, chaotic, and intense multiplayer first person shooter, focused on providing basic, old style deathmatch. The 1.0 release weighs in at 161MB, and includes 17 maps, 28 playable characters, and 10 music tracks. It is cross-platform, and supports Windows and Linux (x86 and x86_64), with Mac support coming soon (patch to be released in the next few days).

All of Nexuiz is licensed under the GPL, including the core engine, the textures, maps, sounds, and models. It is extremely modder friendly. Because of its GPL license status, it can be included in any Linux distros or packages and is entirely free.

Nexuiz is built on the power of the Darkplaces engine, which is a heavily modified version of the original Quake. Darkplaces features realtime lighting and stencil shadows, bumpmapping, gloss, bloom, and totally rewritten network code that supports up to 64 players on a single server. While quality gameplay was our primary goal, it's graphics technology and artwork allows the game to compete with the current quality of commercial games.

Any online deathmatch fan will instantly feel at home with Nexuiz' weapons and movement style. The fast server browser and quick loading time allows you to jump right into a game at a moments notice and play a quick game.

---

### Post by gil-galad on 2005-06-01
I submitted a story to slashdot.  If you see Nexuiz on slashdot, it might be my handiwork!

---

### Post by equilibrium on 2005-06-01
nice :)

looks like it could be worth downloading, as I love all of the quake series games and am still playing quake3 online  :) 

get bored of stuff like CS etc  :???:

---

### Post by gil-galad on 2005-06-01
Well I have started playing it and it is very good.  Some thoughts:

-gameplay is similar to quake3  :) 
-graphics are generally better than quake3  :-P 
-all the servers are high ping :(

---

### Post by dolny on 2005-06-01
I don't like the lack of originality, most of the models, ping and sys requirements. I like the fact that its totally free. I find it dull and boring after 15minutes. I would prefer a more realistic teamplay type of game but well... its nice that there is another free game for us-> penguins ;)

---

### Post by jdodson on 2005-06-01
first off, i have to say.  HELL YES! this game looks amazing!  i have waited for this for sometime!  1 hour to go to start playing!:)

[QUOTE=gil-galad]Well I have started playing it and it is very good.  Some thoughts:

-gameplay is similar to quake3  :) [/quote]

i love quake3.  i recently bought it for $9.99 and it has risen to be one of my favoriates.

[QUOTE=gil-galad]-graphics are generally better than quake3  :-P [/quote]

thats cool.  then again, i really didnt think quake3's graphics were bad.  i would rather a game be faster than have one zillion polygons rendered in real time with super real effects.  rock on fast games!

[QUOTE=gil-galad]-all the servers are high ping :([/QUOTE]

as the game becomes more and more popular, i imagine more servers will come out of the closet.

---

### Post by gil-galad on 2005-06-01
[QUOTE=dolny]I don't like the lack of originality, most of the models, ping and sys requirements. I like the fact that its totally free. I find it dull and boring after 15minutes. I would prefer a more realistic teamplay type of game but well... its nice that there is another free game for us-> penguins ;)[/QUOTE]
 I think the game is targeted more for people who like quake3 style games.  Most FPS's are not original.  The goal of the project was to make a very decent GPL shooter, and they succeeded.  Nexuiz is the most polished open source game I have seen, and thats awesome.  
   
The game is much faster once you turn off real-time lighting.  :D

---

### Post by fsman on 2005-06-01
I haven't downloaded it yet (just about too).
It looks like a zip file - isn't this for windows.
What needs to be done to install in ubuntu?

---

### Post by gil-galad on 2005-06-01
Take a look at one of my earlier replys, I have a link to linux installers.

---

### Post by equilibrium on 2005-06-01
bah :(

can you only get the linux version via bittorrent?  :( but they host the windows version on http.

 Already a difference between windows and linux versions :-#

---

### Post by equilibrium on 2005-06-01
ah IC on the forums you can use the .zip for linux but need to compile the darkplaces sdl aswell?

[http://www.nexuiz.com/forums/index.php?showtopic=154](http://www.nexuiz.com/forums/index.php?showtopic=154)
> This is a small howto on installing Nexuiz on Linux.

Download the Nexuiz.zip from the website. Also download and install the SDL and the SDL development packages for your distribution.

Open up a terminal and cd to the directory it was downloaded to (normaly your home directory ~)

Once in the directory it was downloaded to type:

unzip Nexuiz.zip
cd Nexuiz/sources/
unzip nexuizenginesourceyyyymmdd.zip
cd darkplaces/
make sdl-release
cp darkplaces-sdl ../../

now cd ../.. and type ./darkplaces-sdl -game nexuiz and there you have it.

also on that thread someone says u just need to set permissions or something  :neutral:  bit confusing tbh  :roll:

> The executable permission where lost during packaging the .zip file.

You have to manually set the execute permissions on the executable files first. You can do this in your favourite desktop environment like KDE or on the console using the "chmod" command.

a "chmod 777 nexuiz-linux-x86-glx" should help a lot

---

### Post by slux on 2005-06-01
chmodding the binaries should be all you need, the zip is a triple-platform release, win32, linux and mac.

Of course if you run into any trouble with the provided ones (or are on non-x86), you can compile.

You don't have to use the torrent if you don't want to for the installer either. [Look here](http://liflg.org/?catid=6&gameid=64).

---

### Post by gil-galad on 2005-06-01
You can get the install file directly here [http://www.liflg.org/?what=dl&catid=6&gameid=64&filename=nexuiz_1.0-english.run](http://www.liflg.org/?what=dl&catid=6&gameid=64&filename=nexuiz_1.0-english.run)

---

### Post by fsman on 2005-06-01
[QUOTE=gil-galad]Take a look at one of my earlier replys, I have a link to linux installers.[/QUOTE]

Do you use the Loki installer? i've never come across this before.
Or do you just sh xxxxx.run

---

### Post by crun on 2005-06-01
Nexuiz ran perfectly for me on Ubuntu with all settings to max, but pretty clunky at work on Windows (maybe worse OpenGL support on the windows Nvidia drivers?)

It's a fantastic looking game, especially for a totally GPL one. Fast and furious, very reminiscent of Quake 3, which in my opinion is a good thing. I hope they add some more game types soon.

---

### Post by jdodson on 2005-06-01
ok to set the record straight....

the file on the sourceforge server "nexuiz.zip" contains the win32 and linux x86/x86_64 files you need to run the game.  all you need to do is run "chmod 755 nexuiz-linux-x86-sdl" or some variant on that name and then ./nexuiz-linux-x86-sdl(or some variant on the name) to run the game.

now the game is a slideshow on my AMD 64 3000+ with a Gig of ram and a nvidida 5700LE+ if you dont turn off "realtime world lights" and the other "realtime lights."  

personally i recompiled the darkplaces engine for kicks.  i saw no noticable speed improvement.

as to the game:

the guns will take a bit to get used to.  there are just so many of them and they are somewhat different from the guns i am used to.  its not a bad thing, however i wish for some guns you could see the projectile as it fires(most guns do this, some do not).

its really cool to shoot a rocket under you and go sky high.  

the LAG IS INCREDIBLE!  i know its mostly people running DSL connections, though even on the dedicated servers, the lag is immense.  i run a 256/256k dsl line here, and have NO problems with unreal-goty, ut2004, quake3, enemy territory or americas army.  i think there is something going on with my machine, or the game.  not sure which, i hope this will be addressed either way.

originality or lack thereof.  i think as the game matures, we will see more game types, such as CTF, etc.  i think this is essential to the games popularity.  however, we already have this awesome example of open source gaming.  it is incredible.

bots.  the game needs them.  hands down, this game needs bots.  i cant stress this enough.  most people play with bots "offline."  the unreal folks realize this is true and are addressing this in the next version of ut2007.  nexuiz "needs" bots for when you have a lan at your house and want to increase the frag counts.  bots, please.

the game is simply incredible.  the graphics are already for "next gen" cards as most people cant run the game without turning off effects.  that is crazy.  the game is very pretty with all the graphics on, it just looks like a slideshow.  mad props to the darkplaces engine and the nexuiz team.  this is the boon to open source FPS gaming we have needed for sometime.

---

### Post by jdodson on 2005-06-01
update on bots: [http://www.nexuiz.com/forums/index.php?showtopic=155](http://www.nexuiz.com/forums/index.php?showtopic=155)

good news:)

---

### Post by 23meg on 2005-06-01
i get a total black screen (except the numbers at the bottom and the crosshair) and stuttering sound when i try to start a game. any ideas on what's going wrong?

---

### Post by fng on 2005-06-01
[QUOTE=jdodson]its really cool to shoot a rocket under you and go sky high.[/QUOTE]

Play Quakeworld or CPMA :)
It happens all the time there.

---

### Post by dolny on 2005-06-01
Well, I still prefer Transfusion ([www.transfusion-game.com](www.transfusion-game.com)) 2vs2 - just have to wait until they fix the netcode ;) 

Anyway I'm happy that such games come out GPL'ed. Maybe somebody will take the two best models (blue and green marine) and make a more interesting mod for it :) Like some objective oriented thing ;)

The most anticipated mod for me is Goldeneye (N64) mod for Source engine. Gonna be switching to WinXP to play it smoothly. Ahh... loved that game on N64. I'll try to buy a N64 copy with Goldeneye :)

---

### Post by equilibrium on 2005-06-02
downloaded it :)

seems to be ok, could develop into something excellent. Be nice if there was a ping dialog / counter both ingame and in the server browser.

I just connected to a server and the lag was stupid, people looked like they were moving at 3fps or something  :-| maybe they need to work on the netcode? some wierd weapons and even wierder movement :).

Might have to try it on LAN

---

### Post by slux on 2005-06-02
I don't know how good the netcode is (it's a fresh implementation so there might be room for improvement) but AFAIK many servers are a little laggy currently since they're not really dedicated or have better connections than a DSL.

Too bad I can't test it since I'm away from my main desktop and The DRI drivers for r100 Radeons don't seem to cut it and the iBook runs out of memory when trying play on Fedora... Fedora seems to be a little memory hungry for some reason anyways... Wish my Hoary CDs would arrive so that could be replaced. :/

---

### Post by dolny on 2005-06-02
Fedora sucks compared to (K)Ubuntu imho. I had it before I switched to Hoary 5.04
It was much more user unfriendly than Ubuntu. Ahh... you'll stay with Ubuntu when you install it, you'll see.

---

### Post by blackbirdXXX on 2005-06-02
When I run the game I get the following informations:
```
blackbird@activetravel:~$ nexuiz -width 1400 -height 1050 -bpp 24
Nexuiz Linux 11:01:54 Jun  1 2005
Trying to load library... "libz.so.1" - loaded.
Compressed files support enabled
Added packfile ./data/data20050531.pk3 (1959 files)
Console initialized.
Playing shareware version.
Initializing client
Trying to load library... "libvorbis.so.0" - loaded.
Trying to load library... "libvorbisfile.so.3" - loaded.
Ogg Vorbis support enabled
couldn't exec config.cfg
couldn't exec autoexec.cfg
0 demo(s) in loop
No demos listed with startdemos
Starting video system
Video: fullscreen 1400x1050x24
Linked against SDL version 1.2.5
Using SDL library version 1.2.5
Unable to load GL driver "(null)": No dynamic GL support in video driver
Desired video mode fail, trying fallbacks...
Video: fullscreen 1400x1050x16
Linked against SDL version 1.2.5
Using SDL library version 1.2.5
Unable to load GL driver "(null)": No dynamic GL support in video driver
Video: fullscreen 640x480x16
Linked against SDL version 1.2.5
Using SDL library version 1.2.5
Unable to load GL driver "(null)": No dynamic GL support in video driver
Video: window 640x480x16
Linked against SDL version 1.2.5
Using SDL library version 1.2.5
Unable to load GL driver "(null)": No dynamic GL support in video driver
Quake Error: Video modes failed
```

What do I have to do?

---

### Post by jdodson on 2005-06-02
[QUOTE=blackbirdXXX]

What do I have to do?[/QUOTE]

did you this?  [http://ubuntuforums.org/showthread.php?t=25723](http://ubuntuforums.org/showthread.php?t=25723)

---

### Post by blackbirdXXX on 2005-06-02
[QUOTE=jdodson]did you this?  [http://ubuntuforums.org/showthread.php?t=25723](http://ubuntuforums.org/showthread.php?t=25723)[/QUOTE]
shure. I can play ut2004 without a problem.

---

### Post by jdodson on 2005-06-02
there is an sdl and glx version.  try both.

if that doesnt work i would recommend going to the nexuiz site for help.  they should know it best.

---

### Post by DJ_Max on 2005-06-02
I'm looking forward to playing this game, but just been too busy. If there are lag issues, whether it's coding, or server problem, hopefully it'll be fixed soon.

---

### Post by gil-galad on 2005-06-02
I think the lag is due to lack of good servers.  There are only a few dedicated, and it looks like they are in several different countries, which could cause plenty of lag.  If you have a decent broadband connection, host it yourself!

---

### Post by equilibrium on 2005-06-02
seemed really laggy for me even on a 100mbit server with 40ms ping  :-? :(

shame really as it could be a good game. Still needs a lot of development tho  :-#

---

### Post by XDevHald on 2005-06-02
(Torrenting now,) let's see what this game is made of ;)

---

### Post by gil-galad on 2005-06-02
Once you find a server with less than 200 ping, it seems fine to me.  The problem is, the servers are usually all over 200 ping.

---

### Post by XDevHald on 2005-06-02
[QUOTE=gil-galad]Once you find a server with less than 200 ping, it seems fine to me. The problem is, the servers are usually all over 200 ping.[/QUOTE]
 Not always a run point on the servers but if you use [http://www.filerush.com/download.php?target=nexuiz.zip]("http://www.filerush.com/download.php?target=nexuiz.zip") then you will be running anywhere from 500 k/bs depending on your connection.

Also, I did read and research on how to install this thing, I torrented it but I am still a little lost on how to run this thing..any suggestions.

[begin=blunt] P.S please do not flame this post with howto's and lame readme files, I'm looking for correct pointers.[end=blunt]

---

### Post by DJ_Max on 2005-06-02
[QUOTE=gil-galad]I think the lag is due to lack of good servers.  There are only a few dedicated, and it looks like they are in several different countries, which could cause plenty of lag.  If you have a decent broadband connection, host it yourself![/QUOTE]
Yeah, I agree, because most new games don't start with good servers. But hosting it on your own broadband connection isn't wise. First, there aren't any decent **home** broadband connections to handle a gameserver. You will need a 100MBit+ line. Which datacenters have.

---

### Post by equilibrium on 2005-06-04
Has anyone noticed the forum for nexuiz is not working?

I can view it but as soon as I post something I get a zero reply and it doesn't work. :(

---

### Post by slux on 2005-06-04
It's been working ok for me. I've replied to a couple of posts today.

---

### Post by equilibrium on 2005-06-04
hmm still getting the same error :(

```
ERROR
The requested URL could not be retrieved

While trying to retrieve the URL: http://www.nexuiz.com/forums/index.php?

The following error was encountered:

    * Zero Sized Reply 
```

only does it when I try to post. I can view the forum ok but just not submit any posts  :neutral:

---

### Post by crane on 2005-06-04
[QUOTE=equilibrium]Has anyone noticed the forum for nexuiz is not working?

I can view it but as soon as I post something I get a zero reply and it doesn't work. :([/QUOTE]
 I had that problem last night!

ASWP has a server set up for this game. Seems to be running OK.

server --> 207.44.248.20:24000

---

### Post by crane on 2005-06-04
[QUOTE=BB]Not always a run point on the servers but if you use [http://www.filerush.com/download.php?target=nexuiz.zip]("http://www.filerush.com/download.php?target=nexuiz.zip") then you will be running anywhere from 500 k/bs depending on your connection.

Also, I did read and research on how to install this thing, I torrented it but I am still a little lost on how to run this thing..any suggestions.

[begin=blunt] P.S please do not flame this post with howto's and lame readme files, I'm looking for correct pointers.[end=blunt][/QUOTE]

Are you referring to running a server or the game itself?

---

### Post by equilibrium on 2005-06-04
hmm very strange, I finally got to post using fast reply.

with the proper reply it just gives the error :( dodgy

---

### Post by tread on 2005-06-04
nice, nice game :D

---

### Post by subterrific on 2005-06-05
I played for about 5 hours today, the game is a lot of fun. If it seems laggy to you, try turning off some of the high-end graphics effects, it is more likely fps lag and not network lag. You can check your ping to a server once you're connected by typing 'ping' in the console. Bring the console down with the ~ key.

If you find any serious bugs, stop by the irc channel #nexuiz on irc.gamesurge.net, the developers are very friendly and seem to be around almost all the time. Be sure to tell them thanks, this game is professional quality and totally GPL. I think it is a major milestone for Linux gaming.

---

### Post by RastaMahata on 2005-06-05
I love the game, but it could be better:

- Have a better menu (I hate when clicks dont work)
- Better sound effects
- Better hud (Well... look at UT2004, thats a fine hud :))
- Better skins (Am I the only one that finds the human models akward?)
- Mic support
- CTF, Team Deathmatch, and why not, some original games. I'm all for old school deathmatch, but ctf is a classic :)
- Bots
- Better network play (Are the servers laggy, or is the net code just buggy?)
- Better flashing effects (Well, I shoot a weapon while running, but the "flash" stays behind..)
- I find weapon skins kinda simple...

I think that it's a great game, but I expect a patch fixing most of these things. Just because a game is GPL'd doesnt mean it can't be better.

---

### Post by slux on 2005-06-06
[QUOTE=RastaMahata]
- Have a better menu (I hate when clicks dont work)
[/QUOTE]

Being worked on, I think it'll be incorporated pretty soon. :)

> - Better sound effects
- Better skins (Am I the only one that finds the human models akward?)

I agree with these points. Hopefully someone will contribute / they'll improve these parts.
> 
- Mic support


I saw it discussed but an app such as TeamSpeak works anyway even if it's not added soon.

> 
- CTF, Team Deathmatch, and why not, some original games. I'm all for old school deathmatch, but ctf is a classic :)

TDM works and there have been a couple of servers running that. Support for at least CTF and Domination is apparently coded but there are no maps yet. Hopefully someone will make those.

> 
- Bots

Going to be in the next patch.

> 
- Better network play (Are the servers laggy, or is the net code just buggy?)


Probably it's mostly laggy servers but I'm sure the netcode will be improved as well.

> 
- Better flashing effects (Well, I shoot a weapon while running, but the "flash" stays behind..)
- I find weapon skins kinda simple...


That's a known bug which will be fixed.

> 
I think that it's a great game, but I expect a patch fixing most of these things. Just because a game is GPL'd doesnt mean it can't be better.

You gotta cut them a little slack though. They're not a big team working on a multi-million dollar budget, they're a small group of people doing this without any compensation in their own free time. Sure, they can still make something as good as or better than those commercial titles but I'd settle even for slightly less. Of course a donation isn't a bad idea if you like what they're done. I'm going to give them the price of a full new game but every little bit helps and probably helps them keep motivated to work on making it even better. :)

---

### Post by nautilus on 2005-06-06
Very cool to see the community pumping out some good, fun games.

Some of the maps are a little glitchy, (like the T tunnel-top one, with little jump-pads at the bottom which, if you "graze" against the wall you get shot back down), and yes, the netcode could really get a makeover (specifically in regards to local preloading of textures and models, or at least passive loading), and I can see some great potential here.

As for the community effort bit... Well...

Hmm, take this lightly, please, but I think a well-initiated community effort could do a bit better, especially on a 'release'.  I see some great stuff coming from the authors here.  As a developer myself, I can relate to how much work went into this stuff.  Now, I believe, details should be addressed, and this could be honed into a great game.

What's with the animations, what's with the low-quality skin avatars, the clunky menu system?  The laggy lead-ins, or is that the hitboxes?  "floating" edges on maps, ones which can even hold you captive?  No particles on weaponsfire of certain weapons?

Sorry, there's no excuse for that.  At the same time, it certainly is a far-cry from Cube, now there's a clunky game.

---

### Post by jdodson on 2005-06-06
stuck thread because i think its that cool.

a bit of info. on the new bots to nexuiz coming real soon! : [http://www.nexuiz.com/forums/index.php?showtopic=301](http://www.nexuiz.com/forums/index.php?showtopic=301)

someone just made a pretty cool map, check it here: [http://www.nexuiz.com/forums/index.php?showtopic=300](http://www.nexuiz.com/forums/index.php?showtopic=300)

---

### Post by DJ_Max on 2005-06-07
[QUOTE=RastaMahata]I love the game, but it could be better:
...
I think that it's a great game, but I expect a patch fixing most of these things. Just because a game is GPL'd doesnt mean it can't be better.[/QUOTE]
Well, thats bugs are going to be found in any game, no matter what license it's under.

---

### Post by negatory on 2005-06-08
For a free open source game I find it very good!I played it for 1 hour and I can't wait to play it more.Sure it's kind of rough on the edges but with the community helping with suggestions I think it could be an excellent game!

Pedro Carrico

PS: It even runs smoothly with cedega  :grin: so nobody can complain about that :wink: !

---

### Post by simonkitch on 2005-06-09
How do I start this game?

---

### Post by Sniffer on 2005-06-09
Great Screenshots no doubt...

Just one question...

Only have online mode..or it has story mode (Offline play)?


want to know before downloading it.

Thks

---

### Post by XDevHald on 2005-06-09
[QUOTE=crane]Are you referring to running a server or the game itself?[/QUOTE]
 No just the game, and thank you for replying back :D

---

### Post by negatory on 2005-06-09
> Originally posted by: simonkitch
How do I start this game 
You have to chmod +x nexuiz-linux-x86_64-glx (or nexuiz-linux-x86-glx if you've got a 32 bits processor)  and then run it as ./nexuiz-linux-x86_64-glx.

Pedro Carrico

---

### Post by negatory on 2005-06-09
> Originally posted by: Sniffer
...
Only have online mode..or it has story mode (Offline play)?
...

Only online mode...but a pretty fast one too...If you liked Quake 3 you'll like this one.

Pedro Carrico

---

### Post by Curlydave on 2005-06-09
I'm more into slower-paced, tactical games myself, eg Natural Selection and Red Orchestra, but I'll give this a try.

---

### Post by ubuntu_demon on 2005-06-09
nexuiz will be in breezy see :

ttp://www.ubuntulinux.org/wiki/UniverseCandidates

I haven't tried this game yet. But I'll request a backport :)

---

### Post by MetalMusicAddict on 2005-06-09
The model in [THIS](http://www.nexuiz.com/public/new/6a.jpg) is TOTALLY Eddie from Iron Maiden. :)

---

### Post by ubuntu_demon on 2005-06-15
allright I've played it! This game rocks! 

I think this is almost as good as q3a. 

The lighting and shadows look better than q3a!

There should be a couple of servers where the Ubuntu community meets (at least 1 in europe for me :-P)

The maps look very good ! (comparable to q3a)

What I would like (to know) is :

-better looking skins
-better looking weapons
-tools and documentation for modders (I'm not a modder but I like urban terror which is a q3a mod)
-crosshair customizing
-a way to show my FPS
-mouse smooth
-better game browser
-punkbuster support

a bit off topic : do you guys know a nice game browser that supports nexuiz / ET / q3a / urban terror ?

---

### Post by slux on 2005-06-16
[QUOTE=demon666_nl]
-better looking skins
-better looking weapons[/QUOTE]

Me too, the weapon skins are being enhanced a bit (mostly adding detail AFAIK) but don't know about the players... Guess it's on the list anyway. Anyone knowing how to skin wanting to give them a hand is welcome I'd imagine.

> 
-tools and documentation for modders (I'm not a modder but I like urban terror which is a q3a mod)


The language for modding is good old QuakeC which has some tutorials focusing on Quake around the net. Some people are talking about Nexuiz specific as well but it's possible to get started with just the Quake ones.

> 
-a way to show my FPS
-mouse smooth

There's a  consoler variable for both, cl_fps for the fps I believe. The mouse stuff I don't touch so I don't remember but look for the different ones or search in the Nexuiz forums. At least the mouse var is also being incorporated in the GUI AFAIK.

> 
-better game browser


The game GUI is getting revamped and there was some discussion about the browser so I'm sure it's on the list :)

> 
-punkbuster support


Doubt that this will be added. It's a GPLed game which means some cheating is extremely hard to weed out (not seen any yet though) but the DP net protocol is mostly server-side which helps. SInce we haven't seen any GPLed FPSes before, this is really an interesting experiment...

> 
a bit off topic : do you guys know a nice game browser that supports nexuiz / ET / q3a / urban terror ?

Try XQF. The CVS version has already added support for Nexuiz and in addition to that it supports pretty much every online FPS known to man.

---

### Post by ubuntu_demon on 2005-06-16
[QUOTE=slux]Me too, the weapon skins are being enhanced a bit (mostly adding detail AFAIK) but don't know about the players... Guess it's on the list anyway. Anyone knowing how to skin wanting to give them a hand is welcome I'd imagine.
[/QUOTE]

I just think they are a bit ugly. Adding more quality will only improve it a little.

[QUOTE=slux]
The language for modding is good old QuakeC which has some tutorials focusing on Quake around the net. Some people are talking about Nexuiz specific as well but it's possible to get started with just the Quake ones.
[/QUOTE]

good

[QUOTE=slux]
There's a  consoler variable for both, cl_fps for the fps I believe. The mouse stuff I don't touch so I don't remember but look for the different ones or search in the Nexuiz forums. At least the mouse var is also being incorporated in the GUI AFAIK.

The game GUI is getting revamped and there was some discussion about the browser so I'm sure it's on the list :)
[/QUOTE]

thnx

[QUOTE=slux]
Doubt that this will be added. It's a GPLed game which means some cheating is extremely hard to weed out (not seen any yet though) but the DP net protocol is mostly server-side which helps. SInce we haven't seen any GPLed FPSes before, this is really an interesting experiment...
[/QUOTE]

maybe they could implement some secuirty measures at the server and in the protocol. 

But in order to prevent cheating we got to have some binary only code that updates a lot ... I think punkbuster is best (if they want to do it)

This game can't be become competetive (clans , clanbase) unless there is some non-open security plugin.

[QUOTE=slux]
Try XQF. The CVS version has already added support for Nexuiz and in addition to that it supports pretty much every online FPS known to man.[/QUOTE]

thnx

edit :

here's their todo list :
[http://savage747.sa.funpic.de/wiki/pmwiki.php?n=Main.Todo](http://savage747.sa.funpic.de/wiki/pmwiki.php?n=Main.Todo)

show fps :
$ showfps 1
increase field of vison to see more :
$ fov 120

I also want to be able to only auto switch weapons when ammo is empty .. otherwise not

---

### Post by RastaMahata on 2005-06-16
wouldnt it be cool if you could play bombing run?
Bombing Run:
"Each level has one ball in the middle of the play field. The objective is to pick up the ball, deliver it to the enemy base and fire it through their goal. You must also defend your own goal to prevent the enemy from scoring. The ball is dropped when a player is killed and can then be picked up by anyone on either team."

This game was first introduced in UT2k3.

---

### Post by slux on 2005-06-17
Yeah, bombing run would be cool and I might have a try at it. I'm currently making a new mode that will probably be reasonably easy to extend into bombing run.

The ability to turn weapon autoswitch is also on the dev team's mind but it's a bit hard to implement currently. I'm sure it'll be available in a future patch anyway but don't expect it in the first one. :P

---

### Post by Omnios on 2005-06-18
wrong thread typo

---

### Post by PaulX on 2005-06-21
it is nice. Quake 3 style it is tasty :-)  ( I always think about food) :)   The problem is the input and poor performance. But it is OK if you disable the fancy lightning stuff. My mouse has lag even offline. I will wait for a new version with some bug fixes and bots because has extreme potential:D

---

