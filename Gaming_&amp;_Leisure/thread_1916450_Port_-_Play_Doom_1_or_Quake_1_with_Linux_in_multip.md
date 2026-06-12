---
title: "Port - Play Doom 1 or Quake 1 with Linux in multiplayer?"
date: 2012-01-28
forum: Gaming &amp; Leisure
---

### Post by honeybear on 2012-01-28
Hi, I would like to know if it is possible to  Play Doom 1 or Quake 1 with Linux in multiplayer? thank you.

I have heard of possible ports

---

### Post by honeybear on 2012-01-28
I would like to try prboom doom 1 classic. However there is no IWAD into the 1.9 final version. One cannot find doom shareware :( 

[http://www.doomworld.com/classicdoom/info/shareware.php](http://www.doomworld.com/classicdoom/info/shareware.php)

If you try harmony shareware: you get 
[http://files.drdteam.org/index.php/files/download/64952/harmony.zip](http://files.drdteam.org/index.php/files/download/64952/harmony.zip)

> 

 ls -lhtrah harm1.wad 
-rw-rw-rw- 1 josh josh 56M Dec 10  2009 harm1.wad


 prboom -iwad harm1.wad 

prboom v2.5.0 ([http://prboom.sourceforge.net/](http://prboom.sourceforge.net/))
I_SetAffinityMask: manual affinity mask is 1
M_LoadDefaults: Load system defaults.
 default file: /home/josh/.prboom/prboom.cfg
 found harm1.wad
IWAD found: harm1.wad
CheckIWAD: IWAD tag harm1.wad not present




---

### Post by dmn_clown on 2012-01-28
> **honeybear said:**
> I would like to try prboom doom 1 classic. However there is no IWAD into the 1.9 final version. One cannot find doom shareware

So buy ultimate doom:

[http://store.steampowered.com/app/2280/](http://store.steampowered.com/app/2280/)

$10 for Doom, Doom 2, and Final Doom.

---

### Post by honeybear on 2012-01-28
> **dmn_clown said:**
> So buy ultimate doom:

[http://store.steampowered.com/app/2280/](http://store.steampowered.com/app/2280/)

$10 for Doom, Doom 2, and Final Doom.

PRBOOM is made so that it supports the shareware and you can find freeprboom into the deb.

I would like to play custom MAPs... for deathmatch with a friend. There are a lot here: [http://www.doomworld.com/idgames/](http://www.doomworld.com/idgames/)


ubuntu has a package:
[http://pkgs.org/ubuntu-10.10/ubuntu-multiverse-i386/doom-wad-shareware_1.9-1.1_all.deb](http://pkgs.org/ubuntu-10.10/ubuntu-multiverse-i386/doom-wad-shareware_1.9-1.1_all.deb)


no idea how to play users WAD... :( 
[http://www.doomwadstation.com/mega/index.html](http://www.doomwadstation.com/mega/index.html)

for instance, prboom -iwad  TE.WAD  , is not working ...:( 

Do you eventually know a ubuntu wiki for prboom?



I have just found that you cannot play custom wads with prboom

That's pitty. Those are the only wads that it states that could eventually work...
 Supported WADs

    * doom2f.wad
    * doom2.wad
    * plutonia.wad
    * tnt.wad
    * doom.wad
    * doom1.wad
    * doomu.wad
    * freedoom.wad 

Well, forget to use prboom to play cool maps :(

---

### Post by disturbedite on 2012-01-28
Use Skulltag. IMO it's the best doom source port. It has the most options & has some of the most extensive multiplayer: [http://www.skulltag.com/](http://www.skulltag.com/)

---

### Post by honeybear on 2012-01-28
> **disturbedite said:**
> Use Skulltag. IMO it's the best doom source port. It has the most options & has some of the most extensive multiplayer: [http://www.skulltag.com/](http://www.skulltag.com/)

thank you !

(too bad, not into my repos.)  

32-bits: [http://www.skulltag.com/download/files/release/st-v098d_linux-x86.tar.bz2](http://www.skulltag.com/download/files/release/st-v098d_linux-x86.tar.bz2)

I gotta try to fix that issue
>  ./skulltag
./skulltag: error while loading shared libraries: libfmodex-4.24.16.so: cannot open shared object file: No such file or directory


It is far far better than 10 years of prboom. Tell me why linux is not capable to make so decent games ... :(
wow [http://www.skulltag.com/img/screenshots/DOOM0155.jpg](http://www.skulltag.com/img/screenshots/DOOM0155.jpg)

no lib
> 
$ ls /usr/lib/libf
libfaac.so.0            libfakekey.so.0.0.1     libfltk_forms.so.1.1    libfluidsynth.so.1.3.0  libform.so.5            libfreetype.so.6.6.0    libfuse.so.2            
libfaac.so.0.0.0        libfam.so.0             libfltk_gl.so.1.1       libfontconfig.so.1      libform.so.5.7          libfribidi.so.0         libfuse.so.2.8.4        
libfaad.so.2            libfam.so.0.0.0         libfltk_images.so.1.1   libfontconfig.so.1.4.4  libformw.so.5           libfribidi.so.0.3.1     libfusion-1.2.so.9      
libfaad.so.2.0.0        libffi.so.5             libfltk.so.1.1          libfontenc.so.1         libformw.so.5.7         libfsplib.so.0          libfusion-1.2.so.9.0.1  
libfakekey.so.0         libffi.so.5.0.10        libfluidsynth.so.1      libfontenc.so.1.0.0     libfreetype.so.6        libfsplib.so.0.0.0


I give up ... [http://ubuntuforums.org/showthread.php?t=807259](http://ubuntuforums.org/showthread.php?t=807259)
seems that no one really know how to make it work

maybe here: 
[http://www.fmod.org/index.php/release/version/fmodapi42416linux.tar.gz](http://www.fmod.org/index.php/release/version/fmodapi42416linux.tar.gz)




> #  cp libfmodex-4.24.16.so /usr/lib/ ; cp libsnes_spc.so  /usr/lib/





> ./skulltag
Skulltag v0.98d - SVN revision 3021 - SDL version
Compiled on Nov  6 2010

M_LoadDefaults: Load system defaults.
Removing ZDoomGL settings...
Cannot find a game IWAD (doom.wad, doom2.wad, heretic.wad, etc.).
Did you install Skulltag properly? You can do either of the following:

1. Place one or more of these wads in the same directory as Skulltag.
2. Edit your skulltag-username.ini and add the directories of your iwads
to the list beneath [IWADSearch.Directories]



it seems that it can run it but I would like to use the doom1 shareware and other custom maps. Seems not so much possible :(

---

### Post by Brebs on 2012-01-29
For Quake 1, I'd recommend [DarkPlaces](http://icculus.org/twilight/darkplaces/) - works great in multiplayer.

---

### Post by honeybear on 2012-01-29
> **Brebs said:**
> For Quake 1, I'd recommend [DarkPlaces](http://icculus.org/twilight/darkplaces/) - works great in multiplayer.

Cool. thanks
[http://icculus.org/twilight/darkplaces/screenshots.html](http://icculus.org/twilight/darkplaces/screenshots.html)


a again nothing in the repos: :(
```
 apt-cache search dark place
gpe-othello - othello board game for GPE
tome - A single-player, text-based, dungeon simulation game.
```


it seesm that the last version is this one:
[http://icculus.org/twilight/darkplaces/files/darkplacesmod20080808.zip](http://icculus.org/twilight/darkplaces/files/darkplacesmod20080808.zip)

man, again a dead project :(

---

### Post by blueshead on 2012-01-29
Also if you like Quake.. Try Quake Live.. It's free and works in Linux

[http://www.quakelive.com]("http://www.quakelive.com")

My tag is "swampy"

---

### Post by HolgerB on 2012-01-29
@honeybear:

> man, again a dead project Dead ? Well...then this is the dawn of the Dead....:confused:

If young padawan checks out their webpage at...
[http://icculus.org/twilight/darkplaces/](http://icculus.org/twilight/darkplaces/)

...he will find out that the latest version was released on 2011-06-26. Since then was no release but for now they only release if there are any bugfixes.

You might want to check some videos on the tube:

Superduper Quake mod sporting darkplaces:
[http://www.youtube.com/watch?v=5hXZCASWxmo](http://www.youtube.com/watch?v=5hXZCASWxmo)

Kleshik - a cool Coop mod:
[http://www.youtube.com/watch?v=-j5-Q5AirXQ](http://www.youtube.com/watch?v=-j5-Q5AirXQ)

IMO Darkplaces is by far the best Quake revamp this world has seen. Plus it supports Rygels Highres texture pack.

---

### Post by honeybear on 2012-01-29
> **HolgerB said:**
> @honeybear:

Dead ? Well...then this is the dawn of the Dead....:confused:

If young padawan checks out their webpage at...
[http://icculus.org/twilight/darkplaces/](http://icculus.org/twilight/darkplaces/)

...he will find out that the latest version was released on 2011-06-26. Since then was no release but for now they only release if there are any bugfixes.

You might want to check some videos on the tube:

Superduper Quake mod sporting darkplaces:
[http://www.youtube.com/watch?v=5hXZCASWxmo](http://www.youtube.com/watch?v=5hXZCASWxmo)

Kleshik - a cool Coop mod:
[http://www.youtube.com/watch?v=-j5-Q5AirXQ](http://www.youtube.com/watch?v=-j5-Q5AirXQ)

IMO Darkplaces is by far the best Quake revamp this world has seen. Plus it supports Rygels Highres texture pack.

Thanks. Soy Indeed padawam

I was into files, [http://icculus.org/twilight/darkplaces/files/](http://icculus.org/twilight/darkplaces/files/)
I got it : [http://icculus.org/twilight/darkplaces/files/darkplacesengineautobuild.zip](http://icculus.org/twilight/darkplaces/files/darkplacesengineautobuild.zip)

The youtube video is amazing. wow. even better then nexuiz. 

What an amazing youtube, really. I hope that we can get this soon for ubuntu into the apt-get.

For when, we can get the program into our repositories? Somthg official? 


still watching the video. Kinda gore a bit. can you turn off the blood for young players?

---

### Post by HolgerB on 2012-01-29
Hey honeybear,

I am afraid that Darkplaces will never be part of the standard repos as it relies heavy on commercial files.
In other word you need at least the commercial Quake pak files. For Kleshik you also need the mission packs as well or you will experience missing models.

So unless you bought Q1 plus mission packs back in the old days (like me) or bought them from Steam as part of the Quake bundle released lately (as well like me :)) you are out off luck. Superduper Quake to some extent might work with Q1 shareware pak files as well but I never tried. Kleshik is really great and can scare the hell out of you if you play late in the night with lights turned off and headphones turned loud :)

For Q1 I am afraid there is no gore level. May be one can disable gibs via console commands ?

I am not shure...

HTH,
H.

---

### Post by honeybear on 2012-01-30
> **HolgerB said:**
> Hey honeybear,

I am afraid that Darkplaces will never be part of the standard repos as it relies heavy on commercial files.
In other word you need at least the commercial Quake pak files. For Kleshik you also need the mission packs as well or you will experience missing models.

So unless you bought Q1 plus mission packs back in the old days (like me) or bought them from Steam as part of the Quake bundle released lately (as well like me :)) you are out off luck. Superduper Quake to some extent might work with Q1 shareware pak files as well but I never tried. Kleshik is really great and can scare the hell out of you if you play late in the night with lights turned off and headphones turned loud :)

For Q1 I am afraid there is no gore level. May be one can disable gibs via console commands ?

I am not shure...

HTH,
H.

too bad. but look there are too several clone port of doom, and they could be into repositories. 

Could be cool to disable over the console, for larger public

I hope that one day those developments will get more free-quake I releases. It was a hit

---

### Post by ranger77 on 2012-02-03
have you ever tried to run DOOM, Quake1 or similar games in DosBox emulator? I think the will work just fine, i've personally tested DOOM 2, Chasm- the rift and some other old games stuff; they worked fine with no problems, maybe except for some sound effects. 
I did not tested multiplayer gaming, but as far as i know they should be working....and the games can be found on the internet.... archved .exe files or something like that.
I guess you can give them a try..;)

---

### Post by HolgerB on 2012-02-03
Doom, Doom2, Heretic, Chasm, Eradicator and so on...

All those DOS games (even the newer ones like Redneck Rampage) will run nicely on a fast, modern machine.

You can check out some of my videos on Youtube on that topic:
Chasm:
[http://www.youtube.com/watch?v=cbSaZNTdrNA](http://www.youtube.com/watch?v=cbSaZNTdrNA)

Buildgames:
[http://www.youtube.com/watch?v=e8wZAbCLFQ4](http://www.youtube.com/watch?v=e8wZAbCLFQ4)

Even Quake1 will run nicely but under DOSBox you have no 3D acceleration. Doom will stick to its native 320x200.
You will loose all features you have when playing those modern ports (Skulltag for Doom, Darkplaces for Quake).
Plus you will need a much more beefy machine for playing Quake inside DOSBox in VGA res compared to running natively in Darkplaces with OpenGL acceleration. Things might change if we get better hardware acceleration inside DOSBox but for now DOSBox "only" is a replacement to run those games from the area when 486DX40 were around and a Pentium 133 was a real performance beast

---

### Post by VicViper on 2012-02-04
Quake 1 Multiplayer: [http://ezquake.sourceforge.net/]("http://ezquake.sourceforge.net/")

---

### Post by mastablasta on 2012-02-06
I used to run zdoom on windows, i am sure it works just as fine in linux:
[http://en.wikipedia.org/wiki/Doom_source_port](http://en.wikipedia.org/wiki/Doom_source_port)

---

### Post by Brebs on 2012-02-06
Darkplaces has *many* options, which you can tweak. I actually prefer lots of blood, so use:
```
cl_stainmaps 1
cl_particles_blood 1
cl_particles_blood_alpha 1
cl_particles_blood_bloodhack 1
cl_particles_quality 7
```
Darkplaces can work with the shareware Quake 1 data - run it with *-game demo*

---

### Post by honeybear on 2012-02-06
> **Brebs said:**
> Darkplaces has *many* options, which you can tweak. I actually prefer lots of blood, so use:
```
cl_stainmaps 1
cl_particles_blood 1
cl_particles_blood_alpha 1
cl_particles_blood_bloodhack 1
cl_particles_quality 7
```
Darkplaces can work with the shareware Quake 1 data - run it with *-game demo*

thank you

Would you know if there is a loky bash script that installs it from deb or tar.gz on the net?

bash loki-play-quake.sh ?

---

### Post by HolgerB on 2012-02-07
> **honeybear said:**
> thank you

Would you know if there is a loky bash script that installs it from deb or tar.gz on the net?

bash loki-play-quake.sh ?
Heya honeybear,

why would one want to have a bash script to install a tar.gz ?
Or more specific for a zip file (as the darkplaces engine comes).

Simply do a tar xvf (for tar.gz) or unzip (for zip files) followed by the name of the downloaded file and you are set. This will install the included files to directory you are currently in.

For the rest (e.g. setting up dp with Quake) you simply have to grab the pak-files from an existing install and copy them over. I used DOSBox to install the original quake and grabbed the pak files from there.

Personally I am a big fan of games being self-contained with all required libs and files inside a zip, tar, rar, whatever. I am not in urgent need of a deb for any program available. Esp. since I also like to try out other distribs as well.

HTH,
H.

---

