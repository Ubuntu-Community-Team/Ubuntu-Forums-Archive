---
title: "[SOLVED] Urban Terror"
date: 2008-09-29
forum: Gaming &amp; Leisure
---

### Post by Forbees on 2008-09-29
so i looked, and this game looks sweet, but there isn't a .deb, (that has seeders at least)

so i looked up how to do it manually, but it didn't seem to work :(

i had trouble finding a post with step by step instuctions, so i went here
[https://answers.launchpad.net/ubuntu/+source/hal/+question/24505](https://answers.launchpad.net/ubuntu/+source/hal/+question/24505)

and it didn't seem to have problems installing, but when i tried to run it i get > bash: /usr/local/games/UrbanTerror/Linux/UrbanTerror/ioUrbanTerror.x86_64: cannot execute binary file

heres my terminal operations incase it helps

```

forbees@forbees-desktop:~$ sudo mkdir /usr/local/games/UrbanTerror
[sudo] password for forbees: 
forbees@forbees-desktop:~$ sudo unzip -d /usr/local/games/UrbanTerror/Linux UrbanTerror_41_FULL.zip
Archive:  UrbanTerror_41_FULL.zip
   creating: /usr/local/games/UrbanTerror/Linux/UrbanTerror/
  inflating: /usr/local/games/UrbanTerror/Linux/UrbanTerror/ioUrbanTerror Source.url  
   creating: /usr/local/games/UrbanTerror/Linux/UrbanTerror/ioUrbanTerror.app/
   creating: /usr/local/games/UrbanTerror/Linux/UrbanTerror/ioUrbanTerror.app/Contents/
  inflating: /usr/local/games/UrbanTerror/Linux/UrbanTerror/ioUrbanTerror.app/Contents/Info.plist  
   creating: /usr/local/games/UrbanTerror/Linux/UrbanTerror/ioUrbanTerror.app/Contents/MacOS/
   creating: /usr/local/games/UrbanTerror/Linux/UrbanTerror/ioUrbanTerror.app/Contents/MacOS/baseq3/
  inflating: /usr/local/games/UrbanTerror/Linux/UrbanTerror/ioUrbanTerror.app/Contents/MacOS/ioUrbanTerror.ub  
  inflating: /usr/local/games/UrbanTerror/Linux/UrbanTerror/ioUrbanTerror.app/Contents/MacOS/libSDL-1.2.0.dylib  
   creating: /usr/local/games/UrbanTerror/Linux/UrbanTerror/ioUrbanTerror.app/Contents/MacOS/missionpack/
 extracting: /usr/local/games/UrbanTerror/Linux/UrbanTerror/ioUrbanTerror.app/Contents/PkgInfo  
   creating: /usr/local/games/UrbanTerror/Linux/UrbanTerror/ioUrbanTerror.app/Contents/Resources/
  inflating: /usr/local/games/UrbanTerror/Linux/UrbanTerror/ioUrbanTerror.app/Contents/Resources/iourbanterror.icns  
  inflating: /usr/local/games/UrbanTerror/Linux/UrbanTerror/ioUrbanTerror.exe  
  inflating: /usr/local/games/UrbanTerror/Linux/UrbanTerror/ioUrbanTerror.i386  
  inflating: /usr/local/games/UrbanTerror/Linux/UrbanTerror/ioUrbanTerror.x86_64  
  inflating: /usr/local/games/UrbanTerror/Linux/UrbanTerror/ioUrbanTerror_COPYING.txt  
  inflating: /usr/local/games/UrbanTerror/Linux/UrbanTerror/ioUrbanTerror_id-readme.txt  
  inflating: /usr/local/games/UrbanTerror/Linux/UrbanTerror/ioUrbanTerror_Logitech_Game_Recognition.reg  
  inflating: /usr/local/games/UrbanTerror/Linux/UrbanTerror/ioUrbanTerror_README.txt  
  inflating: /usr/local/games/UrbanTerror/Linux/UrbanTerror/ioUrTded.exe  
  inflating: /usr/local/games/UrbanTerror/Linux/UrbanTerror/ioUrTded.i386  
  inflating: /usr/local/games/UrbanTerror/Linux/UrbanTerror/ioUrTded.x86_64  
   creating: /usr/local/games/UrbanTerror/Linux/UrbanTerror/q3ut4/
  inflating: /usr/local/games/UrbanTerror/Linux/UrbanTerror/q3ut4/autoexec.cfg  
   creating: /usr/local/games/UrbanTerror/Linux/UrbanTerror/q3ut4/demos/
  inflating: /usr/local/games/UrbanTerror/Linux/UrbanTerror/q3ut4/demos/tutorial.dm_68  
 extracting: /usr/local/games/UrbanTerror/Linux/UrbanTerror/q3ut4/description.txt  
  inflating: /usr/local/games/UrbanTerror/Linux/UrbanTerror/q3ut4/mapcycle.txt  
  inflating: /usr/local/games/UrbanTerror/Linux/UrbanTerror/q3ut4/q3ut.ico  
  inflating: /usr/local/games/UrbanTerror/Linux/UrbanTerror/q3ut4/QIIIA Game Source (SDK) License.doc  
  inflating: /usr/local/games/UrbanTerror/Linux/UrbanTerror/q3ut4/readme41.txt  
   creating: /usr/local/games/UrbanTerror/Linux/UrbanTerror/q3ut4/screenshots/
  inflating: /usr/local/games/UrbanTerror/Linux/UrbanTerror/q3ut4/screenshots/shot0000.jpg  
  inflating: /usr/local/games/UrbanTerror/Linux/UrbanTerror/q3ut4/server.cfg  
  inflating: /usr/local/games/UrbanTerror/Linux/UrbanTerror/q3ut4/Urban Terror on the Web.url  
  inflating: /usr/local/games/UrbanTerror/Linux/UrbanTerror/q3ut4/zpak000.pk3  
  inflating: /usr/local/games/UrbanTerror/Linux/UrbanTerror/q3ut4/zpak000_assets.pk3  
forbees@forbees-desktop:~$ sudo chmod +x /usr/local/games/UrbanTerror/Linux/UrbanTerror/ioUrbanTerror.x86_64
forbees@forbees-desktop:~$ /usr/local/games/UrbanTerror/Linux/UrbanTerror/ioUrbanTerror.x86_64
bash: /usr/local/games/UrbanTerror/Linux/UrbanTerror/ioUrbanTerror.x86_64: cannot execute binary file

```

---

### Post by mindoms on 2008-09-29
Are you running ubuntu 64-bit on an 64-bit Computer?
if not, then this might help:
```
sudo chmod +x /usr/local/games/UrbanTerror/Linux/UrbanTerror/ioUrbanTerror.i386 
/usr/local/games/UrbanTerror/Linux/UrbanTerror/ioUrbanTerror.i386 
```

---

### Post by Perfect Storm on 2008-09-29
Guide (64-bit): [http://gaming.gwos.org/doku.php/guides:64bit:urban_terror](http://gaming.gwos.org/doku.php/guides:64bit:urban_terror)

---

### Post by Bios Element on 2008-09-29
Or you could just get it off [http://www.playdeb.net/](http://www.playdeb.net/) and do things the easier way... And get a deb.

---

### Post by Forbees on 2008-09-29
> **mindoms said:**
> Are you running ubuntu 64-bit on an 64-bit Computer?
if not, then this might help:
```
sudo chmod +x /usr/local/games/UrbanTerror/Linux/UrbanTerror/ioUrbanTerror.i386 
/usr/local/games/UrbanTerror/Linux/UrbanTerror/ioUrbanTerror.i386 
```

wow . . . . no i'm using 32 bit lol . .  .. that was newbish of me >,< if this doesn't work i suppose i'll get a deb from the site Bios Element posted . . . . when i google searched for a .deb all i found where dead torrents for it

---

### Post by EvilMarshmallow on 2008-09-29
Just thought I'd chime in to tell you it's worth the hassle.  It's a pretty fun game.  Good luck on the installation.

---

### Post by Forbees on 2008-09-29
well i got it installed . . . . but i'm having a window problem, it seems that "avant window navigater" is trying to still display while the game is, so i jump from fullscreen, to like a window screen with no mouse every few seconds . . . . i seem to get this with other fullscreen games too

know how to fix??

---

### Post by Twitch6000 on 2008-09-29
> **Forbees said:**
> well i got it installed . . . . but i'm having a window problem, it seems that "avant window navigater" is trying to still display while the game is, so i jump from fullscreen, to like a window screen with no mouse every few seconds . . . . i seem to get this with other fullscreen games too

know how to fix??

Make it autohide.

---

### Post by Perfect Storm on 2008-09-29
> **Forbees said:**
> well i got it installed . . . . but i'm having a window problem, it seems that "avant window navigater" is trying to still display while the game is, so i jump from fullscreen, to like a window screen with no mouse every few seconds . . . . i seem to get this with other fullscreen games too

know how to fix??

Disable compiz.

---

### Post by Forbees on 2008-09-29
> **Twitch6000 said:**
> Make it autohide.

:( that didn't help, it still pops up trying to show through, since it is active with Urban Terror

also my upper task bar is showing . . . since it gets stuck in like a window mode

heres a pic, so you know what i'm dealing with, it gets an occasional quick black flash, but i think i just need to adjust the refresh rate to fix that . . . it just wont stay in fullscreen and give me mouse controls :(

[IMG]http://i33.tinypic.com/2ajs4g0.png[/IMG]

---

### Post by Forbees on 2008-09-29
i found out that if i Alt-Tab to force urban terror in focus it regains fullscreen mode

but heres the catch, as soon as i stop moving the mouse it goes back into it's weird thing

i found out that mid game, when i stop moving the mouse and i go back to the wierd window mode i still have keyboard controls, just no mouse controls

---

### Post by mindoms on 2008-09-29
I dont think its related to awn
to rule it out, just close it before you start the game.
right-click on one side of the bar, choose close, obviously

as a quick work around i'd suggest to start the game in windowed mode. usually there is a parameter for this for the command line. try 
```
/path/to/game --help
```
to see the available options

hth, stefan

---

### Post by Forbees on 2008-09-29
well i fixed itself!!!

very happy to play

it reminds me much of counterstrike . . . which is the only reason i still have a windows partition . . . well that and lightscribe, havent gotten that to work yet in linux


i think soon i will have no need for windows lol

---

### Post by noerrorsfound on 2008-09-29
Congratulations! Counter-Strike (version 1.6) runs fine on Linux using Wine. Counter-Strike: Source may be what you're talking about and that runs in Wine as well, but I don't get nearly as good performance compared to Windows even with all settings on minimum. It's playable, though, and the only limitations are not being able to use your microphone in-game (you can hear other people speak fine, though) and not being able to use the in-game Steam Community feature.

---

### Post by Forbees on 2008-09-29
> **noerrorsfound said:**
> Congratulations! Counter-Strike (version 1.6) runs fine on Linux using Wine. Counter-Strike: Source may be what you're talking about and that runs in Wine as well, but I don't get nearly as good performance compared to Windows even with all settings on minimum. It's playable, though, and the only limitations are not being able to use your microphone in-game (you can hear other people speak fine, though) and not being able to use the in-game Steam Community feature.

i tried playing scorce through steam and crossover and it had epic video failure .. . .

walls started sprouting from my arm and than it stalled the whole system >,<

so this will work when i'm to lazy to switch OS's

---

### Post by roycerm2 on 2008-10-01
i was having graphical problems and it was resolved by turning the screen saver off.

---

### Post by Forbees on 2008-10-01
NEW PROBLEM!!!!

now after playing for about 10min it jumps into a windowed mode (about 1/4 the screen) and i loose all controle, but still in-game

i can't alt-f4 i can't ctrl-alt-del 

only way i can get out is with ctrl-alt-backspace

any ideas whats going on??

---

### Post by eragon100 on 2008-10-01
As AI said. Disable desktop effects, it should solve all your problems :wink:

---

### Post by Forbees on 2008-10-01
so i have to goto advanced desktop effects settings and unclick every single box when i want to play? :(

---

### Post by Perfect Storm on 2008-10-01
Install fusion-icon and set it up to auto-start in sessions, or make a script to disable compiz when starting the game.

---

### Post by Forbees on 2008-10-01
> **Artificial Intelligence said:**
> Install fusion-icon and set it up to auto-start in sessions, or make a script to disable compiz when starting the game.

how might i do said script?

---

### Post by Perfect Storm on 2008-10-01
Example;

```
nano Launch-Urban-Terror.sh
```

add:

[b]#!/bin/bash

metacity --replace &

<command to execute Urban Terror>

compiz --replace & [/b]


Save [ctrl] + [o] and exit [ctrl] + [x].

```
chmod +x Launch-Urban-Terror.sh
```

---

### Post by MaxIBoy on 2008-10-01
Actually, the Windows installer under WINE also installs the native Linux and Darwin versions.

---

### Post by Forbees on 2008-10-01
> **Artificial Intelligence said:**
> Example;

```
nano Launch-Urban-Terror.sh
```

add:

[b]#!/bin/bash

metacity --replace &

<command to execute Urban Terror>

compiz --replace & [/b]


Save [ctrl] + [o] and exit [ctrl] + [x].

```
chmod +x Launch-Urban-Terror.sh
```




now when i join a sever i'm constantly "waiting for players"

eventhough the sever is almost full  i walk around the map unable to do anything >,<

---

### Post by Perfect Storm on 2008-10-01
Try this instead, then; [http://ubuntuforums.org/showthread.php?t=867562&highlight=game+compiz](http://ubuntuforums.org/showthread.php?t=867562&highlight=game+compiz)

---

### Post by Forbees on 2008-10-02
now i can't play at all . . . . i removed the script to attempt to go back to normal game-play with my limited like 10 min but i still get "waiting for players"

i join a game, i get like the last input from another user

"bob fell on his own granade"
than noone is there
shows i'm the only player in the map, waiting for other players to join


i've lost my amazing game and i've only had it a few days :( :( :'(

---

### Post by Perfect Storm on 2008-10-02
Then reverse the changes, you made.

---

### Post by Forbees on 2008-10-02
> **Artificial Intelligence said:**
> Then reverse the changes, you made.




 . . . . . i did . . . . . .

---

### Post by Perfect Storm on 2008-10-02
I think some thing else is wrong. The stuff doesn't touch the game itself. Only compiz.

---

### Post by Forbees on 2008-10-02
seems to be fine as of this morning . . .  i didn't reboot or anything

idk it likes to hate me than love me?

---

### Post by Northsider on 2008-10-05
> **Forbees said:**
> NEW PROBLEM!!!!

now after playing for about 10min it jumps into a windowed mode (about 1/4 the screen) and i loose all controle, but still in-game

i can't alt-f4 i can't ctrl-alt-del 

only way i can get out is with ctrl-alt-backspace

any ideas whats going on??

Not to beat the dead horse, but I get this as well and it's quite annoying.  I lose ALL mouse/keyboard control and I have to force shutdown.:(

Does disabling compiz really help with this problem?  Seems tedious...why can't *any* game I try in linux work properly?

---

### Post by Perfect Storm on 2008-10-05
Well it helps me in other games (like quakewars), so I'm 99% sure.

---

### Post by Forbees on 2008-10-05
i ended up getting the script in properly, but it didn't help >,<

---

### Post by WitchCraft on 2008-12-09
pkill compiz

or in it's much simpler form:
```

kill `ps -ef | grep "compiz" | sed '/grep/d;s/^ *[^ ]*//;s/^\s*//g;s/\([0-9]*\).*/\1/'`

```

or in it's simpler form:
```

kill `ps -e | grep "compiz" |sed 's/^\s*//g;s/\([0-9]*\).*/\1/'`

```

or in the trivial form:

```

kill `pgrep compiz`

```


Greez

/name "  ALL"

---

### Post by maddog46113 on 2008-12-10
```
sudo apt-get install fusion-icon
```

then go to system -> preferences -> sessions
click add 

```

Name: Fusion Icon
Command: fusion-icon

```

Now the fusion icon will start automatically when you start up your computer... just right click on it select window manager put it on metacity when your gaming and compiz when your not. Should be more simple for you.

---

