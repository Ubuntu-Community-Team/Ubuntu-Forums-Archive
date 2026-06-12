---
title: "Why are Games so Hard to Install ?"
date: 2010-01-06
forum: Gaming &amp; Leisure
---

### Post by Rodney9 on 2010-01-06
Why are Games so Hard to Install ?

I have tried Edge, Skulltag and VaVoom, they all give me errors.
I have searched this forum and the net,
I have made symbolic links and followed other arcane directions, goodness knows what I am doing to the system..

Why in this day and age do we have to run games from a terminal ?

> vavoom -iwaddir doom.wad nothing happens

> /Edge-1.34$ ./edge134 
./edge134: error while loading shared libraries: libGLEW.so.1.5: cannot open shared object file: No such file or directory

I have used " $ sudo ln -s /usr/local/lib/libGLEW.so.1.5 /usr/local/lib/libGLEW.so.1.5 "


> ~/skulltag$ ./skulltag
Skulltag v0.98a - SVN revision 2485M - SDL version
Compiled on Oct 24 2009

M_LoadDefaults: Load system defaults.
W_Init: Init WADfiles.
 adding /home/puss/skulltag/skulltag.pk3 (453 files)
 adding /home/puss/skulltag/skulltag.wad (2306 lumps)
 adding ./doom.wad (2306 lumps)
I_Init: Setting up machine state.
CPU Vendor ID: GenuineIntel
  Name: Intel(R) Core(TM)2 Duo CPU E8400 @ 3.00GHz
  Family 6, Model 23, Stepping 10
  Features: MMX SSE SSE2 SSE3 SSSE3 SSE4.1
I_InitSound: Initializing FMOD
 IError! You are using an old version of FMOD (4.24.04).
 IThis program requires version 4.24.16
GSound init failed. Using nosound.
V_Init: allocate screen.
S_Init: Setting up sound.
ST_Init: Init startup screen.
P_Init: Checking cmd-line parameters...
G_ParseMapInfo: Load map definitions.
S_InitData: Load sound definitions.
Texman.Init: Init texture manager.
ParseTeamInfo: Load team definitions.
LoadActors: Load actor definitions.
R_Init: Init Doom refresh subsystem.
DecalLibrary: Load decals.
M_Init: Init miscellaneous info.
P_Init: Init Playloop state.
ANIMDEFS: Can't find bluelava
Script error, "skulltag.pk3:animdefs.txt" line 300:
Unknown texture bluelava

No idea


I just want to play a improved single player version of Doom easily

Rodney

---

### Post by phreakyo on 2010-01-06
I can't help much but to offer a bit a of empathy, as I think we've all had problems getting games to run perfectly on our various systems. 

A small thing about symbolic links. The command you used helps nothing. If libglew is not there, a link from something that isnt there to begin with wont change anything. You are missing a package which contains that library.

I think apt-cache search is the search function for ubuntu.

apt-cache search libglew or something similar.

---

### Post by Dark Aspect on 2010-01-06
use [prboom]("http://packages.ubuntu.com/karmic/prboom").

---

### Post by Perfect Storm on 2010-01-06
> **Rodney9 said:**
> Why are Games so Hard to Install ?

I have tried Edge, Skulltag and VaVoom, they all give me errors.
I have searched this forum and the net,
I have made symbolic links and followed other arcane directions, goodness knows what I am doing to the system..

Why in this day and age do we have to run games from a terminal ?

 nothing happens



I have used " $ sudo ln -s /usr/local/lib/libGLEW.so.1.5 /usr/local/lib/libGLEW.so.1.5 "




No idea


I just want to play a improved single player version of Doom easily

Rodney

The lib it says that are missing are libglew. In most cases .so files in ubuntu are stored in /usr/lib

But first make sure to install libglew;
```
sudo apt-get install libglew1.5
```

---

### Post by sakuramboo on 2010-01-07
[http://www.playdeb.net/software/Vavoom](http://www.playdeb.net/software/Vavoom)

Really, just click the "Install this now" link and it's installed. Then, you get your little icon under Applications->Games. Couldn't really be any more simple.

---

### Post by Rodney9 on 2010-01-08
> **sakuramboo said:**
> [http://www.playdeb.net/software/Vavoom](http://www.playdeb.net/software/Vavoom)

Really, just click the "Install this now" link and it's installed. Then, you get your little icon under Applications->Games. Couldn't really be any more simple.

> In order to play Doom, an ID software game, the original Doom datafiles are needed.

Click Accept, to download the shareware version of the Doom datafiles, which can be freely downloaded from the internet.

If you posess the registered version you can use that instead, by using the following command: "vavoom -iwaddir <dir>". Where <dir> is a directory containing the datafiles of the registered version.

Please click Accept to allow access to the internet to download the necessary datafiles.

This is what I get when I click the VaVoom Doom Icon.
 
I have put the Ulimate Doom wad in my home and desktop as well as /user/share/games/vavoom/basev/doom/

---

### Post by sakuramboo on 2010-01-11
> **Rodney9 said:**
> This is what I get when I click the VaVoom Doom Icon.
 
I have put the Ulimate Doom wad in my home and desktop as well as /user/share/games/vavoom/basev/doom/I just have to put it in my home directory. But, that is, if I want ultimate doom (same with heretic), but the engine is installed with a few clicks.

---

### Post by zakshdw on 2010-06-10
agreed iv been to hell and back trying to get doom working on ubuntu (no pun intended) but it just wont work! its so annoying :mad:

---

### Post by sakuramboo on 2010-06-10
The package from playdeb has autodownloader place the wad files in ~/.vavoom. That is where you place the wad files.

[~]$ ls .vavoom/
basev  doom-shareware  heretic-shareware
[~]$ ls .vavoom/doom-shareware/
doom1.wad  doom1.wad.orig

---

### Post by Eonfge on 2010-06-14
He, I can't help that many others because I'm a noob as well, but this time I got a fair change helping you:
[URL="http://skulltag.net/wiki/Installation_for_Ubuntu"]
Skulltag[/URL] website

[Ubuntu Tread]("http://ubuntuforums.org/showthread.php?t=1410889")

[Original Tread]("http://skulltag.net/forum/viewtopic.php?p=293947#p293947")

I'm not sure, but it might only work on 32bit. Their has been issues with 64bit systems before, but I can't confirm it.

[I]ps. Dont make such 'deceptive' titles... 

"Installing Doom Classic on Ubuntu 10.04" is a lot better for archiving. It's also way more community friendly because people then instantly know the situation.
[/I]

---

### Post by perspectoff on 2010-08-14
I personally like the quick, simple Skulltag instructions at

Ubuntuguide: [http://ubuntuguide.org/wiki/Ubuntu:All#Skulltag](http://ubuntuguide.org/wiki/Ubuntu:All#Skulltag)

Kubuntuguide: [http://kubuntuguide.org/All#Skulltag](http://kubuntuguide.org/All#Skulltag)

---

