---
title: "Smash Battle: Multiplayer platform shooter (with .deb installer)"
date: 2011-03-08
forum: Gaming &amp; Leisure
---

### Post by DemonTPx on 2011-03-08
[CENTER][IMG]http://smashbattle.condor.tv/wp-content/gallery/smash-battle/title.png[/IMG][/CENTER]

**Smash Battle** is a multiplayer (2 to 4) fighting game. The objective is to attack the other player until his healthbar runs out. There are a few ways to damage the other player.

Bullets: 2 damage points
Red bullets: 4 damage points
Blue bullets: instant kill
Bombs/Airstrike: 3-5 damage points per bomb (depends on character)
Laser: 5 damage points
Headstomp: 1-3 damage points (depends on character weight)
Push in a pit: instant kill (heavy characters push harder)

Players start out with unlimited (yellow) bullets and three bombs. Other powerups (eg healt, shield, airstrike, laser) appear at random while playing.

[CENTER][IMG]http://smashbattle.condor.tv/wp-content/gallery/smash-battle/gp2.png[/IMG][/CENTER]

**Download**
Click on any of the links to download Smash Battle:
[DEB installer for Ubuntu/Debian]("http://sourceforge.net/projects/smashbattle/files/smashbattle/beta-110224/battle_110308svn-2_i386.deb/download") (Latest SVN version, has an extra random powerup)
[Source code]("http://sourceforge.net/projects/smashbattle/files/smashbattle/beta-110224/smashbattle-110224-src.zip/download") (needs libsdl1.2-dev and libsdl-mixer1.2-dev)
[Windows installer]("http://sourceforge.net/projects/smashbattle/files/smashbattle/beta-110224/smashbattle-110224.exe/download")

Alternatively you could add this line to /etc/apt/sources.list:
```
deb http://repository.condor.tv lucid main
```

And run:
```
sudo apt-get update
sudo apt-get install battle
```

**Features**
[LIST]
[*]Mayhem for up to 4 players
[*]16 different levels in 4 different styles
[*]Retro 8-bit style graphics, sounds, music and gameplay
[*]A lot of awesome powerups like the laser and airstrike
[/LIST]

**More about Smash Battle**
Check out our website: [http://smashbattle.condor.tv](http://smashbattle.condor.tv) or [follow Smash Battle on facebook]("http://www.facebook.com/pages/Smash-Battle/183341475040243").
Some old videos of us playing with three players can be found here: [http://smashbattle.condor.tv/video/](http://smashbattle.condor.tv/video/)

**License**
The code for Smash Battle is released under GPLv3. The terms and conditions can be found here: [http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

The artwork (graphics and sounds) are released under Creative Commons Attribution-Noncommercial-Share Alike 3.0 Unported license. The terms and conditions can be found here: [http://creativecommons.org/licenses/by-nc-sa/3.0/](http://creativecommons.org/licenses/by-nc-sa/3.0/)

The music was composed by NickPerrin and are also under the Attribution-Noncommercial-Share Alike 3.0 Unported license.

**Credits**
Programming - Bert Hekman
Graphics - Jeroen Groeneweg
Sounds - Created with sfxr by Bert Hekman
Original music - NickPerrin

**About the development**
Smash Battle is written in C++, using Visual Studio 2005 and vim. It is also my very first project in C++, after using PHP, C#, java and python for a while, so expect to encounter some really dirty code when you are going to look through it. It is built upon the SDL, SDL_ttf and SDL_mixer libraries. The graphics were drawn using the GIMP and MS Paint.

[CENTER][IMG]http://smashbattle.condor.tv/wp-content/gallery/smash-battle/gp3.png[/IMG][/CENTER]

---

