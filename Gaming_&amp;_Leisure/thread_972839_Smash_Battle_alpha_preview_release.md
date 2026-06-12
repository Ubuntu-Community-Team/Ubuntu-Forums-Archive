---
title: "Smash Battle alpha preview release"
date: 2008-11-06
forum: Gaming &amp; Leisure
---

### Post by DemonTPx on 2008-11-06
My friend (Jeroen) and I (Bert) have been working on a game called Smash Battle. It's a two-player fighting game inspired by Mario Battle from Super Mario Bros 3, but with some significant differences. We tried to make this game look and feel like an old 8-bit game.

**How to play**
Smash Battle is a two-player fighting game. The objective is to attack the other player until his healthbar runs out. There are a few ways to damage the other player: You can shoot him (10% damage), bomb him (25% damage), jump on his head (5% damage) or push him into a pit (100% damage).
Players start out with unlimited yellow bullets, 2 red bullets (which do double the damage) and 3 bombs. Some powerups randomly appear in the arena. These could be 25% health, 1 bomb and/or 5 red bullets. You can hold a maximum of 100% healt, 9 bombs and 20 red bullets.


**Features**
[LIST]
[*]Eight characters (which only differ in apperance)
[*]Four stages
[*]Bombs
[*]A few different powerups
[*]Support for keyboard and joypads
[/LIST]

**Video**
[http://www.youtube.com/watch?v=YTEP25zOnJU]("http://www.youtube.com/watch?v=YTEP25zOnJU")

**Download**
The game (binary for ubuntu 8.04/8.10) can be downloaded from [sourceforge]("https://sourceforge.net/project/platformdownload.php?group_id=244367&sel_platform=11747"):
[https://sourceforge.net/project/platformdownload.php?group_id=244367&sel_platform=11747]("https://sourceforge.net/project/platformdownload.php?group_id=244367&sel_platform=11747")
A Windows version and the sourcecode are also availabe.

[COLOR="Red"]Please note that this is an ALPHA version. Do not be suprised if you encounter bugs or anything. This game is fairly playable, but not finished at all.[/COLOR]

[IMG]https://sourceforge.net/dbimage.php?id=193154[/IMG]

**Controls**

It is **highly** recommended that you play this game with two joypads. Keyboard controls are supported, but the keyboard might not work correctly when you press too many buttons at the same time. The controls cannot yet be redefined, unless you change it in the sourcecode (controlschemes can be found and changed in Main.cpp).

_Keyboard Player 1_
W, A, S, D: move left right, duck, jump and control menus
left shift: run
left ctrl: shoot
left alt: bomb
esc: pause

_Keyboard Player 2_
Arrow keys: move left right, duck, jump and control menus
right shift: run
right ctrl: shoot
right alt: bomb
enter: pause

_Playstation controller_
If you happen to have a Playstation to USB converter and two Playstation controllers, then the controls are like this:

D-pad or left analog stick: move left and right, duck, control menu
[]: run
X: jump
R1: bomb
R2: shoot
Start: pause

_Gravis gamepad pro_
D-pad: move left and right, duck, control menu
Blue: run
Green: jump
R1: shoot
R2: bomb
Start: pause

Other joypads will probably also work, but you'll have to find out which button does what for yourself.

[IMG]https://sourceforge.net/dbimage.php?id=193156[/IMG]

**Known bugs**
If you encounter bugs, please report them here: [https://sourceforge.net/tracker/?group_id=244367&atid=1125392]("https://sourceforge.net/tracker/?group_id=244367&atid=1125392")

[LIST]
[*]The Makefile does not contain the file definition for the DoubleDamagePowerUp.cpp and .o files
[*]Fullscreen doesn't work properly on widescreen monitors.
[*]The control schemes cannot be modified in the game.
[*]The joypad controls might not work after you play some matches and return to the menu.
[/LIST]

**Future releases**
Here is a small and incomplete list about what we're planning/hoping to add in the future:

Near future:
[LIST]
[*]Redefine controls
[*]The option to change the rules (how many bullets does each player get? how many bombs? enable health powerups?)
[*]Blue bullets (probably faster, or maybe weaker as a powerdown which you do not want to pickup :) )
[*]A few more arenas, maybe an arena editor
[/LIST]

Far future:
[LIST]
[*]One or more single player modes
[/LIST]

Very far future:
[LIST]
[*]Network multiplayer
[*]Internet mutliplayer
[/LIST]

**License**
The code for Smash Battle is released under GPLv3. The terms and conditions can be found here: [http://www.gnu.org/licenses/gpl.txt]("http://www.gnu.org/licenses/gpl.txt")

The artwork (graphics and sounds) are released under Creative Commons Attribution-Noncommercial-Share Alike 3.0 Unported license. The terms and conditions can be found here: [http://creativecommons.org/licenses/by-nc-sa/3.0/]("http://creativecommons.org/licenses/by-nc-sa/3.0/")

The music (battle.ogg and title.ogg) were composed by NickPerrin and are also under the Attribution-Noncommercial-Share Alike 3.0 Unported license.

**Credits**
Programming - Bert Hekman
Graphics - Jeroen Groeneweg
Sounds - Created with [sfxr]("http://www.cyd.liu.se/~tompe573/hp/project_sfxr.html") by Bert Hekman
Original music - NickPerrin

**About the development**
Smash Battle is written in C++, using Visual Studio 2005 and vim. It is also my very first project in C++, after using PHP, C#, java and python for a while, so expect to encounter some really dirty code when you are going to look through it. It is built upon the SDL, SDL_ttf and SDL_mixer libraries. The graphics were drawn using the GIMP and MS Paint.

---

### Post by grossaffe on 2008-11-06
looks interesting.  any chance we could get a video of the gameplay?

---

### Post by DemonTPx on 2008-11-06
> **grossaffe said:**
> looks interesting.  any chance we could get a video of the gameplay?

[http://www.youtube.com/watch?v=YTEP25zOnJU]("http://www.youtube.com/watch?v=YTEP25zOnJU")

It's not really exciting to see, because I was playing alone. But you'll get the idea.

---

### Post by Ferrat on 2008-11-06
Looks like a great start, haven't looked at the code but sounds like you got a good idea of what to do :) 

keep up the good work=D>

---

### Post by Jim! on 2008-11-06
That is pretty awesome! How long did it take you and what tools did you use to make it? I can't get the game to work on my computer though (8.10). Anyways I watched the video and think it's awesome, good work!

---

### Post by DemonTPx on 2008-11-06
> **Jim! said:**
> That is pretty awesome! How long did it take you and what tools did you use to make it? I can't get the game to work on my computer though (8.10). Anyways I watched the video and think it's awesome, good work!

Thanks :). We've been working on it for almost 2 weeks now.
The tools used are: The SDL library, visual studio, vim, the GIMP, ms paint and sfxr.

It probably doesn't work because you did not install the sdl libraries.

These packages need to be installed:
```
libsdl1.2debian libsdl-ttf2.0-0 libsdl-mixer1.2
```

---

### Post by grossaffe on 2008-11-06
looks interesting.  any plans on making the bomb actually push those in the blast-radius?

---

### Post by DemonTPx on 2008-11-10
> **grossaffe said:**
> looks interesting.  any plans on making the bomb actually push those in the blast-radius?

That is one of the many things we will probably build in :)
It could be awesome if you could bomb someone into a pit :D

---

### Post by grossaffe on 2008-11-10
> **DemonTPx said:**
> That is one of the many things we will probably build in :)
It could be awesome if you could bomb someone into a pit :D

sweet.

also, will it be easy to change the textures? (for example, maybe I want to play as the Mario Bros instead)

---

### Post by rastari on 2008-11-10
i like the sound of it, sounds like a nice fun simple game, games are far too complicated now a days

---

### Post by rastari on 2008-11-10
downloaded with out a problem, the left alt doesn't drop a bomb though i don't know what does on the left side and pressing a lot of buttons at the same time did minimise it although you did say that there would be problems with the keyboard, why did you choose the other characters? freinds of yours or just random?

---

### Post by DemonTPx on 2008-11-13
First off all: Thanks a lot for your replies

> **grossaffe said:**
> sweet.

also, will it be easy to change the textures? (for example, maybe I want to play as the Mario Bros instead)

You should be able to change all textures. They are 24 bit bmp-files and can be found in the gfx-directory.
If you would like to change the names of characters, you would need to change it in the sourcecode (Battle.cpp).

> **rastari said:**
> downloaded with out a problem, the left alt doesn't drop a bomb though i don't know what does on the left side and pressing a lot of buttons at the same time did minimise it although you did say that there would be problems with the keyboard, why did you choose the other characters? freinds of yours or just random?

I mainly tested the game on windows, so I'll go figure out why the left alt doesn't work on linux, soon. But like I also said, I really recommend a joypad with shoulder buttons.

The characters are based on me and my colleagues, which is a lot of fun for us (especially because on of them is gay and ducks in a different way lol! you find out which one that is ;)), but probably not for the rest of the world.
Because of this, I want to make it easier in the future, for users, to create their own characters and sprites.


BTW: Has anyone already played this against someone else? You should try that.. It can be very addictive :D

---

