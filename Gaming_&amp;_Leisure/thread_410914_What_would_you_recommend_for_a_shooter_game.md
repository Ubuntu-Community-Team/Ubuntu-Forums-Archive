---
title: "What would you recommend for a shooter game"
date: 2007-04-16
forum: Gaming &amp; Leisure
---

### Post by Dan_472 on 2007-04-16
Hello

What would you recommend for a shooter game (similar to Operation Flashpoint...which I'm still trying to get working  [http://ubuntuforums.org/showthread.php?t=409513](http://ubuntuforums.org/showthread.php?t=409513)  ).  Something that will run natively in Linux (Ubuntu 6.06) or works well in wine?

Thank you

---

### Post by Tanoku on 2007-04-16
In my humble opinion, Wolfenstein: Enemy Territory is one of the best online FPSs ever made. EVARRRR.

Runs native on Linux, and it's free. Direct download: [http://www.3dgamers.com/dlselect/games/wolfensteinet/et-linux-2.60.x86.run.html](http://www.3dgamers.com/dlselect/games/wolfensteinet/et-linux-2.60.x86.run.html)

...And when it comes to running fine on Wine, all of Steam's games have golden or platinium ratings on the Wine AppDB. Both Counter-Strike: Source and Day of Defeat: Source are awesome, yet they have some serious hardware requirements. If your computer isn't that new, you can also use Steam to play old games on the HL1 engine, such as the original Counter Strike or Day of Defeat, or the more-than-awesome Team Fortress Classic.

All these games from Steam are commercial: You must pay for them. Their homepage is [www.steampowered.com](www.steampowered.com)

---

### Post by smartbei on 2007-04-16
I recently downloaded Nexuiz and Sauerbraten - two shooter games that run natively on Linux. Nexuiz is somewhat lik Unreal Tournament, while Sauerbraten is similar to doom in principle, though the graphics, etc. are much better obviously. Search Google to find - shouldn't be too hard.

---

### Post by noerrorsfound on 2007-04-16
[http://infiltration.sentrystudios.net/](http://infiltration.sentrystudios.net/)
It requires the original version of Unreal Tournament from 1999.

Infiltration Mod is even more realistic than Operation Flashpoint, but it doesn't have a single player campaign. It's mainly meant to be played online but you can play with bots also. The online community is kind of small but there are usually some players online.

---

### Post by rolando2424 on 2007-04-16
I know of Tremulous and Open Arena.

Tremulous, it's a online-only FPS, with a bit of RTS on it.

And Open Arena is a Quake 3 Arena clone.

---

### Post by Phenax on 2007-04-16
Alien Arena, World of Padman, Warsow..

---

### Post by justin whitaker on 2007-04-16
OFP does not run, AFAIK, on any version of WINE. Please, please prove me wrong. I love that game!

Good open source FPS titles are pretty much listed here, and most are in the Quake vein:

Nexuiz
Tremulous
Warsow
Open Arena

UT2004 runs natively, and you can get many of the mods for that game to run. Not that many realism mods, but there are some good Counterstrike type things you can try. There is a nice Tactical Ops mod that is intriguing. 

UT's Infiltration Mod can be made to run, as noted. I have not tried, and I have no idea if any servers still exist. That might be something worth pursuing, if no servers are left. 

As noted, many Steam titles can be made to run on Wine, Cedega, and Crossover office.

---

### Post by crimsontide on 2007-04-16
Urban Terror ........[http://www.urbanterror.net/news.php](http://www.urbanterror.net/news.php)

---

### Post by RomeReactor on 2007-04-16
I second [Alien Arena 2007]("http://red.planetarena.org/")!

---

### Post by TheTruth34 on 2007-04-16
medal of honor:allied assault is a good shooter game, so is soldier of fortune 2

---

### Post by desicratn on 2007-04-17
I would second Urban terror.This is my new favorite FPS.Lots of action, cool guns and you have to stop yourself from bleeding to death. A+.

-Sauerbraten -Doom with sweeter graphics
-Open Arena -Very smooth lots of fun.
-Half life1 on wine, a classic.
-Nexius, its good but Open arena plays alot smoother and faster.
-Legends-FPS with jump jets, kinda fun but...<shrug>
-Penumbra Overture: While it isnt out for Linux just yet and it isnt a FPS per se, the demo for this  first person puzzle game is awesome and the game looks like it will kick ***.

I havent tried Enemy territory yet but I am downloading it now so....
I love FPS games and thought I was going to have to dual boot into XP to get my fix but the more I do in Ubuntu the more I want to just  reclaim my "otherwise occupied" hard drive space back from XP.
:guitar:

---

### Post by surfjdh on 2007-04-17
if you want fast paced, ut-style then get nexiuz, its really fun, make sure to run the sdl version and not glx ; its forked up for some reason
if you want dark, bf style then get wolfenstein e-t, and for a cs 1.6 feel get True Combat:Elite mod for W:E-T

---

### Post by mrazster on 2007-04-17
Urban Terror by far...!!!!!!!!...if it's a multiplayer game you are looking for.
Otherwise wine+Call of Duty....

---

### Post by hobieone on 2007-04-17
the two native one i enjoy quite a bit  is unreal tournament 2004 and recently world of padman which is a little on the goofy side but alot of fun!

---

### Post by FoolsGold on 2007-04-17
Urban Terror also gets my vote.

---

### Post by fakie_flip on 2007-04-17
> **RomeReactor said:**
> I second [Alien Arena 2007]("http://red.planetarena.org/")!

How did you install that game?

---

### Post by Mateo on 2007-04-17
I wouldn't recommend Wolfenstein.  Every time I've played it, it's required 50-80 megabyte downloads of maps and such.

---

### Post by RomeReactor on 2007-04-17
Hi flakie. I don't have it installed at the moment, so I'm downloading the new version (v6.04); however, when I last installed it I don't recall coming across any problems. We'll see with this one.

Also, there's a .deb package on [GetDeb]("http://www.getdeb.net/search.php?keywords=alien+arena&op=").

---

### Post by RomeReactor on 2007-04-18
If anyone is having trouble with the sound in Alien Arena 2007 (downloaded from one of the mirrors offered on [their site]("http://red.planetarena.org/")), the solution is to open the **AlienArena** file inside the **alienarena2007** folder

```
gedit /PATH/TO/alienarena2007/AlienArena
```

and changing this line

```
./crx.$acmd +set game arena $*
```

adding **sdl.** after **crx.**, so the file looks like this

```
#!/bin/sh
  
acmd=`uname -m`

./crx.**sdl.**$acmd +set game arena $*
exit $?
```

Don't overlook the periods. Granted the sound in the menu is crackly, but it sounds better during gameplay.

To run the game, open a terminal and change to the alienarena2007 directory; in my case it would be

```
cd /home/sho/.games/alienarena2007
```

and then

```
./AlienArena
```

To make a launcher in "Applications-->Games" right-click on the menu and select "Edit Menus"; add a new entry under "Games", enter **Alien Arena 2007** as the name (or whatever you like) and on the "Command" section, enter

```
sh -c "/PATH/TO/alienarena2007 && ./AlienArena"
```

To add the icon, press the icon button and navigate to the alienarena2007 folder and use the one that's there (alienarena.xpm). I hope this helps you.

**EDIT**: Sorry for not making a new thread and barging in here with this.

---

### Post by Matt Yun on 2007-04-18
Well, a thread that mentions both Enemy Territory and Urban Terror must also have [True Combat: Elite]("http://www.truecombatelite.net/") (TC:E), a contemporary specops/terrorist tactical mod of Enemy Territory.

TC:E features ironsight aiming (no crosshairs unless you're scoped), realistic movement (no bunny jumping), and modern firearms.  Downside is that it is online only; there is no significant bot support.  Personally, I think the gameplay is way better than Counterstrike.

There is a native Linux binary (download the 0.49b version), but alas, the source is not open or Free.

Some config tips:  if you're running older hardware (I've got a R250 series ATI Radeon 9250), then set the colour depth to 16-bit instead of 24-bit, in both the game and in your X session.  Also, make sure you set the "wallmarks" (ie. bullet marks) game option to "No".

I've also tried [Infiltration]("http://infiltration.sentrystudios.net/") (Unreal Tournament 1999 mod) and [Strikeforce]("http://www.strikeforcegame.com/") (Unreal Tournament 2004 mod).   Both are urban tactical shooters, like Counterstrike.  Both can be played with their respective native Linux Unreal Tournament editions, with bot support for single-player gaming.  

Strikeforce had an unplayable framerate on my aging hardware, so I can't comment further on it.

Infiltration played quite well, but the graphics and movement were less fluid than TC:E.  However, apparently the tactical depth of Infiltration potentially exceeds any other tactical shooter:  see this amazing [review]("http://dslyecxi.com/botg_infiltration.html") for a full description and video of some of the possibilities.  One of the weapons mods (called "mutators" in Unreal) includes the XM-29 "Sabre" Objective Individual Combat Weapon (OICW), complete with 20mm grenade launcher and hi-tech sights!  Despite this, however, I still stick with TC:E because I don't have the time to learn Infiltration.

---

### Post by dumbo on 2007-04-18
It's not that similar to OF (even remotely), but there's also 'savage' (or 'SFE' as it's now become).

It's a quirky RTS/FPS/RPG which is unlike anything else I've played.  I'm not sure how active it is today...

[http://www.newerth.com/smf/index.php/topic,259.0.html](http://www.newerth.com/smf/index.php/topic,259.0.html)

[Savage 2 win/linux is rather heavily delayed, but hopefully will be released/beta'ed this year somewhen]

---

### Post by fakie_flip on 2007-04-18
> **Mateo said:**
> I wouldn't recommend Wolfenstein.  Every time I've played it, it's required 50-80 megabyte downloads of maps and such.

Once you find a server with good ping that you like, add it to your favorites, and next time when you join that same server again you shouldn't have to download the files anymore because you will have them already. However if the files are starting to consume too much disk space, you can delete them from .etwolf in your home folder or you can delete the entire directory and let it get recreated on its own.

---

### Post by fakie_flip on 2007-04-18
Sauerbraten is a great game. I was addicted to it for a while, but now I am trying new games that were mentioned in this thread. I love playing Sauerbraten with instagib, and a new version of Sauerbraten was released just a few days ago that includes new sounds, maps, and improvements to existing maps. I started to play Open Arena last night and really like that one. When I get home, I am going to download Alien Arena 2007. My computer is starting to become full of FPS games. I like them, but I want to have some other types of games too. What other good games are there besides first person shooters? I think I have 10 or more FPS games in Ubuntu now, and I'd like to get some other types of games. These are the games I have already.

Frozen Bubble
Armagetron Advanced
Planet Penguin Racer
Neverball

FPS games
Unreal Tournament 2004
Sauerbraten and Cube
Wolfenstein Enemy Territory
Return to the Castle Wolfenstein
Alien Arena 2007 (downloading)
World of Padman
Nexuiz
Urban Terror

I downloaded a few others that were mentioned in this thread but haven't tried them yet.

---

### Post by justin whitaker on 2007-04-18
I just downloaded Open Arena after hearing the review on The Linux Action Show....it's pretty good. I thought I had gotten past the whole Quake Arena thing, ended up running maps for 2 hours. 






And getting my butt kicked. :(

---

### Post by barmazal on 2007-04-19
Im playing Cup now with my Enemy Territory team, cool game.

Warsaw is nice but still bit buggy and Sauerbraten is really good for Linux game

Nexuiz im about to try once i get it to work

---

### Post by dan171717 on 2007-04-19
tremulous is my fav it is cool u can be a alein and a human 


i like garrys mod but u need halflife2

---

### Post by TheBeasty on 2007-04-19
Wolfenstein:enemy territory is da best or u could download cedega and install cs

---

### Post by bluehue on 2007-04-19
Native: Quake/Doom series.
Wine: Deus Ex ([http://appdb.winehq.org/appview.php?iVersionId=3775](http://appdb.winehq.org/appview.php?iVersionId=3775)) and S.T.A.L.K.E.R. ([http://appdb.winehq.org/appview.php?iVersionId=7377](http://appdb.winehq.org/appview.php?iVersionId=7377))

---

