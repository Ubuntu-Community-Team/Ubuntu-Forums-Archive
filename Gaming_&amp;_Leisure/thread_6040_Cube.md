---
title: "Cube"
date: 2004-11-24
forum: Gaming &amp; Leisure
---

### Post by unikum on 2004-11-24
How to install and get it working? I dont get it  :cry: 

I unpacked it to ~/home/unikum/

---

### Post by jdong on 2004-11-24
What the heck is cube?

---

### Post by unikum on 2004-11-24
A game.

[http://www.cubeengine.com/](http://www.cubeengine.com/)

---

### Post by jdong on 2004-11-24
Thanks. Download right now. It's a source tarball, so most likely it'll be a *make; make install* ordeal.
 
 Let me check that first!

---

### Post by jdong on 2004-11-24
nope -- it's a binary release.... Here we go:
 
 1. Move cube to /opt: [b]sudo mv ~/cube /opt
 [/b]2. Edit **/opt/cube/cube_unix**.
     Line 2: CUBE_DIR=/opt/cube
 3. Link over: [b] sudo ln -s /opt/cube/cube_unix /usr/local/bin/cube
 [/b]4. Execute: **cube**
 
 Enjoy!
 P.S. it really looks cool! testing right now!

---

### Post by plasmo on 2004-11-24
for cube i think youll also need the lib sdl
which can be installed from apt

---

### Post by franx on 2004-12-01
jdong, I downloaded and extracted Cube to /home/franx and then followed your directions, but when I typed in "cube" to launch, I got this:

franx@ubuntu:~ $ cube
/opt/cube/bin_unix/ppc_linux_client: error while loading shared
libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No
such file or directory
franx@ubuntu:~ $

Any advice on what I'm doing wrong?

Fran

---

### Post by HungSquirrel on 2004-12-01
[QUOTE=franx]jdong, I downloaded and extracted Cube to /home/franx and then followed your directions, but when I typed in "cube" to launch, I got this:

franx@ubuntu:~ $ cube
/opt/cube/bin_unix/ppc_linux_client: error while loading shared
libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No
such file or directory
franx@ubuntu:~ $

Any advice on what I'm doing wrong?

Fran[/QUOTE]
 *sudo apt-get install libstdc++5* ought to do the trick.

---

### Post by regeya on 2004-12-01
[QUOTE=jdong]What the heck is cube?[/QUOTE]

Man, I was about to post a witty "hey, why not apt-get search for it" then did it myself.  No Cube!  I must have been thinking back to my Gentoo days, where an emerge -s would have given me the info.  Huh.  :)

---

### Post by franx on 2004-12-01
hung squirrel, did as you suggested.  now I get this:

franx@ubuntu:~ $ cube
/opt/cube/bin_unix/ppc_linux_client: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

Sorry to be a pest, but I've played this game in OSX and it's quite good.  Would really love to run it under Ubuntu.

Fran

---

### Post by p!=f on 2004-12-01
[QUOTE=franx]
franx@ubuntu:~ $ cube
/opt/cube/bin_unix/ppc_linux_client: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
Fran[/QUOTE]
```

sudo apt-get install libstdc++2.10-glibc2.2 libsdl-{image,mixer}1.2

```

---

### Post by IAmNotPhillip on 2004-12-04
Ok. I am able to get this game to run, but only at unplayable levels (ie: 5 FPS). My computer may not be the best, but I certainly have played more graphically demanding games faster than this. Maybe it's because I'm using integrated graphics? I'm not sure, I'm still fairly new to Linux.

Also, whenever I use the command Cube from the /opt/cube directory, it starts fine. But when I try to start it from anywhere else, it always says
```
phillip@ubuntu:~ $ cube
/usr/local/bin/cube: line 39: /home/phillip/bin_unix/linux_client: No such file or directory
/usr/local/bin/cube: line 39: exec: /home/phillip/bin_unix/linux_client: cannot execute: No such file or directory
phillip@ubuntu:~ $
```

---

### Post by jdong on 2004-12-04
You MUST edit the /usr/local/bin/cube file, there's variables in there holding bogus pathnames!!

---

### Post by IAmNotPhillip on 2004-12-05
I actually already did that...I just accidently had a typo.
Stupid me >.<

Anyway, now that's fixed, any ideas on my framerate issues?

---

### Post by TravisNewman on 2004-12-05
Have you tried other 3d games? It could be because your graphics driver isn't installed. If you have an nvidia or ati onboard card, there are howtos in the HOWTO section for installing those. Most likely, however, you'll have an intel card, and I've never touched those so I dunno what to do to get those drivers set up

---

### Post by IAmNotPhillip on 2004-12-05
I have tried Tribes2 via cedega, but I wasn't sure if that was because of my system, or because I haven't tweaked cedega correctly. All i know is under Windows, I am able to play it just fine. Just not under Ubuntu.

It's an integrated intel card.

Oh well, not too much of a loss. I planed on getting a better PC either this, or next month anyway. I can't wait until then. :)

---

### Post by shimon on 2005-02-03
[QUOTE=panickedthumb]however, you'll have an intel card, and I've never touched those so I dunno what to do to get those drivers set up[/QUOTE]

Intel has been the nice guys and GPL'd there drivers =D>

---

### Post by Tonio on 2005-02-04
No problems, works...*
But how changing the  resolution of the game... i'm always in 800*600 :(

---

### Post by kleeman on 2005-02-04
I run at 1600x1200 as follows:

./cube_unix -w1600 -h1200

---

### Post by Tonio on 2005-02-04
Yep, works!! :)

Thanx!! :) :)

---

### Post by soulglo83 on 2005-03-12
I recently unpacked the cube_2004_5_22.tar.gz file to my opt/ folder, meaning cube was situated in /opt/cube. i then edited the cube_unix file and updated it with the correct path. after linking the file and executing, i observed the program open then close quickly and dump me back at bash. floating point error of some sort, either way i have failed to find an answer. below is what was waiting for me in bash after the execution command line.

init: sdl
init: net
init: world
game mode is ffa/default
init: video: sdl
init: video: mode
disabling TCL support
init: video: misc
init: gl
init: basetex
init: sound
sound init failed (SDL_mixer): No available audio device
init: cfg
could not read "servers.cfg"
init: localconnect
init: mainloop
read map packages/base/metl3.cgz (254 milliseconds)
Cyclops by metlslime
game mode is ffa/default
Fatal signal: Floating Point Exception (SDL Parachute Deployed)

*EDIT* I had forgotten to include that in the event it was an issue w/ the soundcard being tied up, i killed all esd and artsd prior to execution, still same error output.

*EDIT* Can run game now, edited autoexec.cfg and gave sound and music 0 values.

---

### Post by buellman on 2005-03-12
[QUOTE=kleeman]I run at 1600x1200 as follows:

./cube_unix -w1600 -h1200[/QUOTE]

you can edit the cube_unix file and go to the last line and edit like:

exec ${CUBE_DIR}/bin_unix/${MACHINE_PREFIX}${SYSTEM_PREFIX}client -w1600 -h1200 $*

for all guys with ati-cards:
go to [http://sourceforge.net/project/showfiles.php?group_id=91993](http://sourceforge.net/project/showfiles.php?group_id=91993)
and download cube_2004_06_06_linux_client_ATI_workaround.zip and follow the instructions. it solves a problem in cube with ati-cards. 

hope that helps.

greets. buellman

---

### Post by Kemotaha on 2005-03-12
So quick question then,  How is it as a game?

What game is it most like?  I don't have time to try it right now but I am always up for a new game that is fun.

---

### Post by buellman on 2005-03-13
[QUOTE=Kemotaha]So quick question then,  How is it as a game?

What game is it most like?  I don't have time to try it right now but I am always up for a new game that is fun.[/QUOTE]

hi!

if you ask me: its the best game in the universe  :razz:  its a pretty "simple" ego-shooter that reminds of quake. surely it has not the best graphics but online it rocks like hell. just pure clean fun.
maybe you want to look at some screenshots?
[http://cubeengine.com/](http://cubeengine.com/)

hope to see you guys online for a little match  :smile: 

greets. buellman

---

### Post by Kemotaha on 2005-03-13
Sounds good.  I will jump on it after april 20th.  That's when I am done with finals and graduated.  Yeah!!!!!

More time for fun.

---

### Post by ivai on 2005-03-26
Hi, just installed ubuntu on my powerbook g4 with 1.5ghz proc.  Trying to install Cube, have it in the /opt folder, have edited cube_unix, and am getting the following error:

```

ivai@ubuntu:~ $ cube
/opt/cube/bin_unix/ppc_linux_client: error while loading shared libraries: libSDL_image-1.2.so.0: cannot open shared object file: No such file or directory
ivai@ubuntu:~ $

```

thanks in advance...

---

### Post by kleeman on 2005-03-26
You need to use synaptic to install libsdl-image1.2 dude! Missing libraries like this nearly always mean missing packages with similar names!

---

### Post by ivai on 2005-03-26
When I search in synaptic for "sdl" all it comes back with is:

libsdl1.2debian
libsdl1.2debian-oss
libsdl1.2-dev
libsdl-mixer1.2
libsdl-mixer1.2-dev


The first three are installed and up to date.

---

### Post by kleeman on 2005-03-26
Sounds as if you don't have the universe apt repository enabled.

---

### Post by kleeman on 2005-03-26
Have a look in /etc/apt/sources.list. There is a comment on how to enable universe

---

### Post by ivai on 2005-03-26
Thanks for the tip :)

---

### Post by ivai on 2005-03-26
Grr... I've installed sdl_image1.2, but now i'm getting the same error that was posted earlier --

```
ivai@ubuntu:/etc/apt $ cube
/opt/cube/bin_unix/ppc_linux_client: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
ivai@ubuntu:/etc/apt $

```

And when I run the suggested command, i get the following as if libstdc++2.10 isn't there:

```

ivai@ubuntu:/etc/apt $ sudo apt-get install libstdc++2.10-glibc2.2 libsdl-{image,mixer}1.2
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package libstdc++2.10-glibc2.2
ivai@ubuntu:/etc/apt $

```

Thanks in advance.. I'm definitely used to portage and not apt

---

### Post by kleeman on 2005-03-26
Can you see it (libstdc++2.10-glibc2.2) in synaptic?  It is visible on my i386 system with universe enabled.

---

### Post by vamos on 2005-04-15
[QUOTE=jdong]nope -- it's a binary release.... Here we go:
 
 1. Move cube to /opt: [b]sudo mv ~/cube /opt
 [/b]2. Edit **/opt/cube/cube_unix**.
     Line 2: CUBE_DIR=/opt/cube
 3. Link over: [b] sudo ln -s /opt/cube/cube_unix /usr/local/bin/cube
 [/b]4. Execute: **cube**
 
 Enjoy!
 P.S. it really looks cool! testing right now![/QUOTE]


uuhm.... im sooooo noobie with linux...

you downloaded it right...
then unpacked it to some home-dir?

because if I do **sudo mv ~/cube /opt**
it says 'mv: cannot stat `/root/cube': Onbekend bestand of map'
does the extracted cube-game has to be in the root?
remember...I'm newbie to the bone so please be clear :))
thanks in advance _O_ 
(for so far I love ubuntu btw)

---

### Post by vamos on 2005-04-15
[QUOTE=HungSquirrel]*sudo apt-get install libstdc++5* ought to do the trick.[/QUOTE]


this didnt work for me either...
it said:

> 
root@vamos:/opt/cube # sudo apt-get install libstdc++5

Pakketlijsten worden ingelezen... Klaar  (pakket list being read)

Boom van vereisten wordt opgebouwd... Klaar (tree of demands build)

libstdc++5 is reeds de nieuwste versie. (newest version)
0 pakketten opgewaardeerd, 0 nieuwe pakketten geïnstalleerd, 0 verwijderen en 0 niet opgewaardeerd.  (nothing removed installed or updated)

root@vamos:/opt/cube # cube
./bin_unix/linux_client: error while loading shared libraries: libSDL_image-1.2.so.0: cannot open shared object file: No such file or directory


---

### Post by vamos on 2005-04-15
yay it works now.... only with a lousy 25fps but it has to be possible to fix that too %)
i'll look around a bit

---

### Post by ploum on 2005-04-17
Here's a cube package for Ubuntu Hoary (done by a friend)


[http://pr.fritalk.com/bmp/cube_20040522-4_i386.deb](http://pr.fritalk.com/bmp/cube_20040522-4_i386.deb)

---

### Post by jkndrkn on 2005-06-26
Has anyone here had any problems getting sound to work upon install?
All sound events on my computer work properly except for Cube.

---

### Post by minimidgy on 2005-07-06
here is what I get:

```
~$ cube
init: sdl
init: net
init: world
game mode is ffa/default
init: video: sdl
init: video: mode
init: video: misc
init: gl
init: basetex
init: sound
sound init failed (SDL_mixer): No available audio device
init: cfg
could not read "servers.cfg"
init: localconnect
init: mainloop
read map packages/base/metl3.cgz (236 milliseconds)
Cyclops by metlslime
game mode is ffa/default
Fatal signal: Floating Point Exception (SDL Parachute Deployed)
```

---

### Post by Ramon on 2005-07-10
Sorry for the bump.

this is mine error : /usr/local/bin/cube: line 39: /home/ramon/bin_unix/linux_client: Onbekend bestand of map
/usr/local/bin/cube: line 39: exec: /home/ramon/bin_unix/linux_client: cannot execute: Onbekend bestand of map


annyone ??

---

### Post by georgey on 2006-02-06
Hi, I have installed Cube on Breezy, got my ATI card to work but have no sound. All other aps have sound ok. Any thoughts anyone? I have read some posts discussing sound devices not being released, but haven't found a solution I can understand. 

Thanks 

George:-k

---

### Post by inovermyheadd on 2006-03-15
ok so I was lazy, and I just unpacked cube without entering the terminal...so now I have this folder and the cube_unix sh file or whatever...and when I click on it...the game works and it is great!

I would like to somehow put it under games in my applications...how do I go about doing that?

---

