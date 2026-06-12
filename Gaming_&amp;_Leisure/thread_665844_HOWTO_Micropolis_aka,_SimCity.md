---
title: "HOWTO: Micropolis aka, SimCity"
date: 2008-01-12
forum: Gaming &amp; Leisure
---

### Post by petriborg on 2008-01-12
Micropolis is SimCity open sourced for the OLPC XO. It in theory should work Linux in general.


First you'll need the source code from:
[http://www.donhopkins.com/home/micropolis/](http://www.donhopkins.com/home/micropolis/)

Direct link to the code:
```
$wget [http://www.donhopkins.com/home/micropolis/micropolis-activity-source.tgz](http://www.donhopkins.com/home/micropolis/micropolis-activity-source.tgz)

```
Untar the source:
```
$ tar -zxf micropolis-activity-source.tgz
```

Install the compiling base and then some:
```
$ sudo apt-get install libx11-dev libxpm-dev freebsd5-buildutils x11proto-xext-dev libxext-dev
```

Add yacc to your path:
```
$cd /usr/local/bin
$sudo ln -s /usr/lib/freebsd/yacc
```

Compile the code:
```
$cd micropolis-activity/src
$ make && make install
```

Running the game:
Turn off num-lock, there is a bug in Tcl/tk which breaks mouse events when that is on (thanks to Captain Frisbee).
```
$cd micropolis-activity
$./Micropolis 
```


And go play!
At least, hopefully... Its currently work only 'sort of' working for me in Gusty. It will start up and you can click some on the main screen, but the game area doesn't display anything - attached is a picture...

---

### Post by ivotedforkodos on 2008-01-12
Will there be a .deb for this at some point? Will this be incorporated in into Hardy as a new package?

---

### Post by petriborg on 2008-01-12
> **ivotedforkodos said:**
> Will there be a .deb for this at some point? Will this be incorporated in into Hardy as a new package?

Could be, its been released GPL3. That would assume that some of its issues can get ironed out.

---

### Post by InspirationDate on 2008-01-12
I'm having trouble trying to figure out how to run it at 1024 x 768.  It seems to be running at 1152 x 864.  I'm on a laptop so I don't have a lot of options.

Also, I'm able to create a city, but once I'm in, the main window only displays a blank brown screen.  The map appears fine...

Can't wait to get this running :)

---

### Post by pelo8280 on 2008-01-12
> **InspirationDate said:**
> I'm having trouble trying to figure out how to run it at 1024 x 768.  It seems to be running at 1152 x 864.  I'm on a laptop so I don't have a lot of options.

Also, I'm able to create a city, but once I'm in, the main window only displays a blank brown screen.  The map appears fine...

Can't wait to get this running :)

Same here.

---

### Post by cyberix on 2008-01-12
I filed a packaging request...
[https://bugs.launchpad.net/ubuntu/+bug/182455](https://bugs.launchpad.net/ubuntu/+bug/182455)

---

### Post by jonathanhowell on 2008-01-12
I get the same brown screen as the main activity screen. The mini-map shows as if it were rendered at a very low res. No sounds at all.

I'm on Gutsy on a Thinkpad T42.

Here's what's happening on the terminal:
> Starting Micropolis in /home/jonathan/micropolis/micropolis-activity ... 
Welcome to X11 Multi Player Micropolis version 4.0 by Will Wright, Don Hopkins.
Copyright (C) 2002 by Electronic Arts, Maxis. All rights reserved.
sh: Syntax error: Bad fd number
sh: Syntax error: Bad fd number
Adding a player on :0.0 ...
Cool, I found the shared memory extension!
PlaySound Siren
PlaySound Siren
PlaySound Monster
PlaySound Monster
PlaySound HonkHonk-Low
PlaySound HonkHonk-Med
PlaySound Siren
PlaySound Siren
PlaySound HonkHonk-Low
QuitMicropolis


This'll be fun to try and figure out.
- Jonathan

---

### Post by rrusaw on 2008-01-13
The Bad fd number comes from the fact that /bin/sh is not bash on Ubuntu. 

```
sh: Syntax error: Bad fd number
```

---

### Post by hikaricore on 2008-01-13
Should be a simple tweak to the make files and such to substitute in dash right?

---

### Post by Hachi on 2008-01-13
According to this article - [[COLOR="Sienna"]SimCity Source Code Released to the Wild! Let the ports begin...[/COLOR]]("http://weblogs.asp.net/bsimser/archive/2008/01/10/simcity-source-code-released-to-the-wild-let-the-ports-begin.aspx")

> The Micropolis engine can load a SimCity save file and run it, and use the TileEngine to draw it, but you can't actually interact with it or edit the map yet, since the user interface and other views haven't been implemented, just a scrolling zooming view of its tiles.

---

### Post by Sockerdrickan on 2008-01-13
Any screens of this actually running lol

---

### Post by petriborg on 2008-01-13
> **hikaricore said:**
> Should be a simple tweak to the make files and such to substitute in dash right?

The dash thing are for scripts that call /bin/sh in them, but then do bash only operations - the Micropolis program only used bash, but tcl/tk used /bin/sh... 

Trying to figure things out I went and replaced all of the /bin/sh for /bin/dash but that did not solve the problem.

These were the files I tried changing:
src/tclx/ucbsrc/makefile
src/tclx/ossupp/makefile.dvx
src/tclx/ossupp/makefile
src/tclx/tkucbsrc/makefile
src/tclx/src/tclxutil.c
src/tclx/src/makefile
src/tclx/makefile
src/tclx/tksrc/makefile
src/tclx/tclsrc/makefile

But this made no difference that I could find :( I still got the "Bad fd number" problem anyway.

as far as this:
> **Hachi said:**
> According to this article - [[COLOR="Sienna"]SimCity Source Code Released to the Wild! Let the ports begin...[/COLOR]]("http://weblogs.asp.net/bsimser/archive/2008/01/10/simcity-source-code-released-to-the-wild-let-the-ports-begin.aspx")

I thought this was for the Micropolis-core which was a major rewrite of code to C++ and python... Maybe I was mistaken.  :(

---

### Post by Hachi on 2008-01-13
> **petriborg said:**
> I thought this was for the Micropolis-core which was a major rewrite of code to C++ and python... Maybe I was mistaken.  :(

I think you may be right there..

---

### Post by amano on 2008-01-13
> **Tux0r said:**
> Any screens of this actually running lol

Seconded. Can someone running this on Ubuntu please post a screen?

I remember having played this in the earliest nineties on my brave old 286 with EGA graphics.

And please support the package request. Maybe this can be backported even to Gutsy...

---

### Post by petriborg on 2008-01-13
Attached to this post is a screen shot of the intro screen which is far as I can get so far on gusty. I'm not sure how to go about debuging the problems this tcl/tk program has though. If anyone has any tips... :)

I had seen one online else where and a [patch for OSX]("http://rmdir.de/~michael/micropolis_mac-osx.patch") was linked on Slashdot.

I've also poked around the rewrite which is definitely not in any usable state though I can compile it... It seems that the **old version** is supposed to work since it was fixed at least some.

---

### Post by bobbocanfly on 2008-01-13
Fixed ```
sh: Syntax error: Bad fd number
sh: Syntax error: Bad fd number
```

by removing /bin/sh and linking it to bash. Now god knows what will happen next time i boot up but at least thats fixed. Bad news is that it fixes nothing.

Now i get

> bobbo@tiger:~/Code/micropolis-activity$ ./Micropolis
Starting Micropolis in /home/bobbo/Code/micropolis-activity ... 
Welcome to X11 Multi Player Micropolis version 4.0 by Will Wright, Don Hopkins.
Copyright (C) 2002 by Electronic Arts, Maxis. All rights reserved.
Adding a player on :0.0 ...
Cool, I found the shared memory extension!
Micropolis has been terminated by a signal.
Pick a window -- you're leaving!


---

### Post by Crazy Marty on 2008-01-13
The "sh: Syntax error: Bad fd number" errors are from the csh-style file redirection at lines 415 & 416 in "res/micropolis.tcl".

Instead of ">&/dev/null", it should be ">/dev/null 2>&1".

---

### Post by Captain Frisbee on 2008-01-13
If you disable num-lock the game will start properly. Apparently there is a bug with Tk ignoring all mouse-clicks when num-lock is on.

---

### Post by petriborg on 2008-01-13
> **Crazy Marty said:**
> The "sh: Syntax error: Bad fd number" errors are from the csh-style file redirection at lines 415 & 416 in "res/micropolis.tcl".

Instead of ">&/dev/null", it should be ">/dev/null 2>&1".

Yep thats the cause, nice work. I still can't click any of the buttons, its like the mouse events are being forwarded to wherever they go to... Anyone find that piece of code yet?


The section below from res/micropolis.tcl should setup each of the buttons on the main screen, maybe the tcl/tk needs to be told to watch the mouse explicitly somewhere?
```

#   0           1               2               3       4         5   6   7   8         9       10   11       12      13
#   type	id		callback	param	var	  x   y   w   h		normal	over disabled checked checkedover
#   ----------- --------------- --------------- ------- ------- --- --- --- ---         ------- ---- -------- ------- -----------
set ScenarioButtons {
  { button	load		DoLoad		""	""	 70 238 157  90		""	@images/button1hilite.xpm "" }
  { button	generate	DoGenerate	""	""	 62 392 157  90		""	@images/button2hilite.xpm "" }
  { button	quit		DoQuit		""	""	 68 544 157  90		""	@images/button3hilite.xpm "" }
  { button	about		DoAbout		""	""	101 705 157  90		""	@images/button4hilite.xpm "" }
  { checkbox	easy		DoLevel		0	""	982 106 190  70		""	@images/checkbox1hilite.xpm "" @images/checkbox1checked.xpm @images/checkbox1hilitechecked.xpm }
  { checkbox	medium		DoLevel		1	""	982 176 190  70		""	@images/checkbox2hilite.xpm "" @images/checkbox2checked.xpm @images/checkbox2hilitechecked.xpm }
  { checkbox	hard		DoLevel		2	""	982 246 190  70		""	@images/checkbox3hilite.xpm "" @images/checkbox3checked.xpm @images/checkbox3hilitechecked.xpm }
  { button	left		DoLeft		""	""	540 375  50  50		""	@images/lefthilite.xpm @images/leftdisabled.xpm }
  { button	right		DoRight		""	""	841 375  50  50		""	@images/righthilite.xpm @images/rightdisabled.xpm }
  { button	play		DoPlay		""	""	625 376 180  50		""	@images/playhilite.xpm "" }
  { button	scenario1	DoPickScenario	"1"	""	310 451 209 188		""	@images/scenario1hilite.xpm "" }
  { button	scenario2	DoPickScenario	"2"	""	519 451 209 188		""	@images/scenario2hilite.xpm "" }
  { button	scenario3	DoPickScenario	"3"	""	727 450 209 188		""	@images/scenario3hilite.xpm "" }
  { button	scenario4	DoPickScenario	"4"	""	936 450 209 188		""	@images/scenario4hilite.xpm "" }
  { button	scenario5	DoPickScenario	"5"	""	310 639 209 188		""	@images/scenario5hilite.xpm "" }
  { button	scenario6	DoPickScenario	"8"	""	519 639 209 188		""	@images/scenario6hilite.xpm "" }
  { button	scenario7	DoPickScenario	"7"	""	728 638 209 188		""	@images/scenario7hilite.xpm "" }
  { button	scenario8	DoPickScenario	"6"	""	937 638 209 188		""	@images/scenario8hilite.xpm "" }
}

```

---

### Post by petriborg on 2008-01-13
> **Captain Frisbee said:**
> If you disable num-lock the game will start properly. Apparently there is a bug with Tk ignoring all mouse-clicks when num-lock is on.

Thats brilliant! Now - at least for me, no map appears in the main window - here is a screen shot.

---

### Post by Crazy Marty on 2008-01-13
As far as I can tell, the buttons *are* being processed when clicked (at least on my machine).  What isn't happening is getting the main map updated.  I'm not a Tcl/Tk user, so it's all more or less gibberish to me....

Also, for what it's worth, I'm not getting any sound, either.  (Xmms, however, works just fine.  Dell 1420N, if that matters.)

---

### Post by Captain Frisbee on 2008-01-13
If you look at the main menu screen the maps seem to be disabled, they are drawn in a greyed-out style. So could it be something different than the event handling?

---

### Post by petriborg on 2008-01-13
> **Captain Frisbee said:**
> If you look at the main menu screen the maps seem to be disabled, they are drawn in a greyed-out style. So could it be something different than the event handling?

Nope, its not grayed out and they will work, just disable num-lock and the program will start to get mouse events as it should. Its a TK bug. Once you do that you can get into the game but the main display will be blank, if I start one of the maps I can see traffic but still no buildings etc. Looks like a bug in the tile system...

---

### Post by smartboyathome on 2008-01-13
petriborg, could you possibly make your screenshots bigger? It is hard to tell anything from them.

---

### Post by jaktar on 2008-01-13
I'm in the same place as Petriborg.  The right side map doesn't display a thing.  The minimap on the left definately shows there is activity though.

---

### Post by petriborg on 2008-01-13
> **smartboyathome said:**
> petriborg, could you possibly make your screenshots bigger? It is hard to tell anything from them.


Sure thing. I attached a larger screen shot to the first post I made - Figured I should update that for new people that come to the thread. :)

---

### Post by dmb on 2008-01-13
I have the same thing as petriborg, not quite sure whats wrong. Anyone know howto fix that?

---

### Post by Sprite_tm on 2008-01-14
The blank map is a problem with 24-bit display modes. The patch that makes Micropolis OSX-compatible happens to solve that problem too: get it at [http://rmdir.de/~michael/micropolis_mac-osx.patch](http://rmdir.de/~michael/micropolis_mac-osx.patch)

Now if anyone knows why the Micropolis windows are always on the foreground and non-decorated under Fluxbox...

---

### Post by a0peter on 2008-01-14
There is now a package at getdeb, which for me installed and worked without tweaking.

---

### Post by pelo8280 on 2008-01-14
32 bit version: [ftp://ftp-mirror.internap.com/pub/www.getdeb.net/mi/micropolis_0.0.20080114-1~getdeb1_i386.deb](ftp://ftp-mirror.internap.com/pub/www.getdeb.net/mi/micropolis_0.0.20080114-1~getdeb1_i386.deb)

64 bit version: [ftp://ftp-mirror.internap.com/pub/www.getdeb.net/mi/micropolis_0.0.20080114-1~getdeb1_amd64.deb](ftp://ftp-mirror.internap.com/pub/www.getdeb.net/mi/micropolis_0.0.20080114-1~getdeb1_amd64.deb)

It works fine for me, too.  I can build new cities, too; not just open existing ones.

There's still that resolution problem, though - it's running too big vertically for me.  Any ideas to fix that?

---

### Post by rowdog on 2008-01-14
Strange that a Linux release requires the freebsd version of yacc.

I already had yacc and didn't want to replace it with the freebsd version so I edited src/tclx/config.mk

#YACC=yacc
YACC=/usr/lib/freebsd/yacc
#YACC=bison -b y

and no, simply uncommenting the bison line didn't work.

I added the mac patch as mentioned above and now I get...

  Darn, X display ":0" doesn't support the shared memory extension.

...but at least the main map is functional now. All that seems to be missing is sound.

Update: The minimap with the overlays works for navigating the main map but the zone and overlay menus don't work.

---

### Post by Cappy on 2008-01-15
getdeb released a version of this:
[http://www.getdeb.net/app.php?name=Micropolis](http://www.getdeb.net/app.php?name=Micropolis)

Don't know if it is any better than what you guys have been trying to get working.

---

### Post by petriborg on 2008-01-15
> **rowdog said:**
> Strange that a Linux release requires the freebsd version of yacc.

I already had yacc and didn't want to replace it with the freebsd version so I edited src/tclx/config.mk

#YACC=yacc
YACC=/usr/lib/freebsd/yacc
#YACC=bison -b y


Ah, good idea. I'll use that on the HOWTO post later. :-)

> **rowdog said:**
> 
and no, simply uncommenting the bison line didn't work.

I added the mac patch as mentioned above and now I get...

  Darn, X display ":0" doesn't support the shared memory extension.

...but at least the main map is functional now. All that seems to be missing is sound.

Update: The minimap with the overlays works for navigating the main map but the zone and overlay menus don't work.


The memory extension thing comes because the Mac OS X patch adds -w as a default flag to the shell script which disables the memory extension. I believe removing it should change that, though it doesn't really matter.

---

### Post by kingdogbert on 2008-01-15
I've got the brown screen as well. Has anyone else tried loading the scenarios? You can see vehicles (trains, planes, ships, helicopters) moving around. My guess is there's some sort of issue accessing the tile library.. Unfortunately, I'm not a good enough coder to pursue the issue, but I wanted to get this out there in case it helps someone else.

---

### Post by choas on 2008-01-15
I've opened a new terminal (Ctrl Alt F2) and started a new X Session with 
**startx -- :2 -depth 16**
You can switch between X Sessions with Ctrl Alt F7 and Ctrl Alt F9

---

### Post by mister_k81 on 2008-01-15
> **Cappy said:**
> getdeb released a version of this:
[http://www.getdeb.net/app.php?name=Micropolis](http://www.getdeb.net/app.php?name=Micropolis)

Don't know if it is any better than what you guys have been trying to get working.

I just tried the 32 bit deb file and it works for me. Though I'm not getting any sound (does the game even have it?), and I had to turn the number lock key off to get the controls to work. But it works!   

screenshot:

---

### Post by rahimveron on 2008-01-16
Yes that resolution thing is still there. Its way out of my screen. How to change it to 800x600 or 1034x768? Plz help
I have used your link to install it.

---

### Post by dee.dw on 2008-01-19
Did anyone manage to get the source code working properly? I have used the GetDeb source + patch and I still only see a brown background in the game without water or trees.

So what is the difference between "my" build and the build of the GetDeb-maintainer?

Greetings, Dee

---

### Post by steeleyuk on 2008-01-19
Got it working here (from GetDeb). Couple of issues:

Had to disable num key to get a response
No sound though there is an option enable and disable it in the menu.

Also a slight bug, when laying down roads, the cars seem to speed up. Not major, just cosmetic.

I'll post a quick pic of something I threw together in 10 minutes.

[[IMG]http://img502.imageshack.us/img502/4417/micropolisjo2.th.png[/IMG]](http://img502.imageshack.us/my.php?image=micropolisjo2.png)

Game just needs a few additions... hospitals, bus stations, train stations, things like that IMO.

Also, the scenarios are working here. Heres a screenie of the Earthquake one...

[[IMG]http://img503.imageshack.us/img503/9138/screenshotmicropolisconaf9.th.png[/IMG]](http://img503.imageshack.us/my.php?image=screenshotmicropolisconaf9.png)

---

### Post by alanbshepard70 on 2008-01-19
> **rahimveron said:**
> Yes that resolution thing is still there. Its way out of my screen. How to change it to 800x600 or 1034x768? Plz help
I have used your link to install it.

From what I can tell the game doesn't give you this option but I did find a way to scale the game to specific screen resolutions. Although not the most elegant solution I will release a patch for it, unless someone beats me to it.

---

### Post by hockey97 on 2008-01-19
omg wow simcity original how can you have fun with that??

---

### Post by steeleyuk on 2008-01-19
> **hockey97 said:**
> omg wow simcity original how can you have fun with that??

Easy if you know how...:confused:

---

### Post by dee.dw on 2008-01-19
Ah ok, my solution is to use "make install" or start the game with "sim -w". :)

Greetings, Dee

---

### Post by alanbshepard70 on 2008-01-20
I was thinking of making a branded(?) version of the game and I wanted to judge interest and get some creative suggestions on what could be done. My first thoughts were fairly simple and obvious, for booming high end commercial zones those would be Ubuntu HQ and slums would be Microsoft. Instead of little flames for fires I could use little firefox symbols, stuff along that line.

---

### Post by hikaricore on 2008-01-20
> **hockey97 said:**
> omg wow simcity original how can you have fun with that??

It takes patience and an interest in gaming.
You know, there was a time when MMORPGs and FPS style games didn't exist.

In those days titles like King's Quest, Zaxxon, and SimCity were king. :guitar:

---

### Post by desertboy on 2008-01-20
Don't forget space quest 3, astrochicken rocked.

---

### Post by steeleyuk on 2008-01-20
> **hikaricore said:**
> It takes patience and an interest in gaming.

I don't even have any interest in gaming as such. But for SimCity, I make an exception. And theme hospital as well :)

I'll admit I do like simulation games but very rarely play them. May change now that SimCity is around for Linux though...

---

### Post by alanbshepard70 on 2008-01-20
Digging through the source I found a some interesting codes for the game. **[SIZE="6"]Warning[/SIZE]**, **[SIZE="5"]DO NOT[/SIZE]** type these in on any city you care about or haven't saved!!!!!

Just type in the word/letters without the ""
 
```

"fund" - gives you $10,000 if used five times a massive earthquake is triggered
"olpc" - gives you $1,000,000
"fart" - Triggers an earthquake
"nuke" - destroys everything
"stop" - this stops the actions of the following codes
"will" - psychedelic patterns of various items in the game
"bobo" - psychedelic patterns of various items in the game
"boss" - psychedelic patterns of various items in the game
"mack" - psychedelic patterns of various items in the game
"donh" - psychedelic patterns of various items in the game
"patb" - psychedelic patterns of various items in the game
"lucb" - psychedelic patterns of various items in the game

```

For the latest news and cheats for Micropolis go here ->[http://micropolis-forums.org/viewtopic.php?t=4](http://micropolis-forums.org/viewtopic.php?t=4)

---

### Post by Sh@m@n on 2008-01-20
> **alanbshepard70 said:**
> Digging through the source I found a some interesting codes for the game. 


nice catch alan ;)

---

### Post by altonbr on 2008-01-22
Damn... I thought this was SimCity 2000.... :(

Still cool that an old game got GPLed though.

---

### Post by samurailink3 on 2008-01-22
No word on the resolution yet?

---

### Post by altonbr on 2008-01-22
> **samurailink3 said:**
> No word on the resolution yet?

From [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=460674](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=460674)
> Hi,
I have seen you intend to package micropolis. As the released sources
from Don Hopkins do not work on modern X servers and the interface is
designed to be fullscreen (and not resizeable) on OLPC, I have made
some changes to this source to rectify these problems.

You can find my changes at:
[http://git.zerfleddert.de/cgi-bin/gitweb.cgi/micropolis](http://git.zerfleddert.de/cgi-bin/gitweb.cgi/micropolis)
(This git was initialized with the released source .tgz)

You can clone it from:
git://git.zerfleddert.de/micropolis

Regards,
  Michael

---

### Post by steeleyuk on 2008-01-24
Who exactly is managing this project at the moment anyway? Is Don Hopkins going to stay involved or will it just be left up to a community to pick it up and implement new features?

I've started a forum anyway just to get some ideas going. Hopefully somebody who has some good programming skills can get the feature set up to that of SimCity 2000...

---

### Post by arbulus on 2008-01-24
I installed the .deb, but when I launch it, it freezes and doesn't let me do anything.  I launched it from the terminal so I could see the messages.  Here's what it tells me:

```
Starting Micropolis in /usr/share/games/micropolis ... 
Welcome to X11 Multi Player Micropolis version 4.0 by Will Wright, Don Hopkins.
Copyright (C) 2002 by Electronic Arts, Maxis. All rights reserved.
sh: Syntax error: Bad fd number
sh: Syntax error: Bad fd number
Adding a player on :0.0 ...
Darn, X display ":0" doesn't support the shared memory extension.
```

I'm running Gutsy 32 bit with Gnome.

Anyone else encounter this?

---

### Post by Mr Fredrick on 2008-01-24
I get exact same output as arbulus

---

### Post by steeleyuk on 2008-01-25
I get the same output to the terminal but the game works fine.

---

### Post by steeleyuk on 2008-01-25
The latest version available [here]("http://git.zerfleddert.de/cgi-bin/gitweb.cgi/micropolis") will most likely fix the freezing bug.

---

### Post by mr.propre on 2008-01-27
For some reason non of the solution's posted here work.
The closest I get is using .deb files but then I get stuck in the menu.
My nummlock is off because I'm using a laptop. Is there also a windows Binary, I would love to play this game again.

Are there also plans to put it in a little more modern graphics (personal ting in some sort of pixel art look)

---

### Post by steeleyuk on 2008-01-27
I think more modern graphics will come but there's no guarantee when. That said, a new interface is likely to come first...

---

### Post by arbulus on 2008-01-28
> **steeleyuk said:**
> The latest version available [here]("http://git.zerfleddert.de/cgi-bin/gitweb.cgi/micropolis") will most likely fix the freezing bug.


That solved it.

---

### Post by anjilslaire on 2008-02-01
> **steeleyuk said:**
> The latest version available [here]("http://git.zerfleddert.de/cgi-bin/gitweb.cgi/micropolis") will most likely fix the freezing bug.

Link is down. Anybody got a mirror for this version?

---

### Post by alanbshepard70 on 2008-02-01
You can find my custom version of the micropolis source here --> [http://alanbshepard70.googlepages.com/micropolis.html](http://alanbshepard70.googlepages.com/micropolis.html) this includes the most up to date source plus air crashes re-enabled, it also includes several new cheats including one that makes everything free. 

To find other versions check here --> [http://micropolis-forums.org/viewtopic.php?t=5](http://micropolis-forums.org/viewtopic.php?t=5) this site includes many sources of the code plus tips on compiling and installation. 

To track fixes and additions check here --> [http://git.zerfleddert.de/cgi-bin/gitweb.cgi/micropolis](http://git.zerfleddert.de/cgi-bin/gitweb.cgi/micropolis) and a direct link to the patched code is --> [http://git.zerfleddert.de/cgi-bin/gitweb.cgi/micropolis?a=snapshot;h=HEAD;sf=tgz](http://git.zerfleddert.de/cgi-bin/gitweb.cgi/micropolis?a=snapshot;h=HEAD;sf=tgz)

---

### Post by mikerman55 on 2008-02-01
does anyone know how to uninstall micropolis? can't seem to get rid of it.

---

### Post by JNowka on 2008-02-02
How to get rid of Micropolis really depends on if you installed it from source or from a deb file.

If you installed a Micropolis via deb file, you would have to type in "sudo apt-get remove Micropolis"

If you installed Micropolis via from source, all you would have to do is to go to the directory where you compiled the source and installed Micropolis from and type in "sudo make uninstall"

---

### Post by amano on 2008-02-20
> **alanbshepard70 said:**
> You can find my custom version of the micropolis source here --> [http://alanbshepard70.googlepages.com/micropolis.html](http://alanbshepard70.googlepages.com/micropolis.html) this includes the most up to date source plus air crashes re-enabled, it also includes several new cheats including one that makes everything free. 

To find other versions check here --> [http://micropolis-forums.org/viewtopic.php?t=5](http://micropolis-forums.org/viewtopic.php?t=5) this site includes many sources of the code plus tips on compiling and installation. 

To track fixes and additions check here --> [http://git.zerfleddert.de/cgi-bin/gitweb.cgi/micropolis](http://git.zerfleddert.de/cgi-bin/gitweb.cgi/micropolis) and a direct link to the patched code is --> [http://git.zerfleddert.de/cgi-bin/gitweb.cgi/micropolis?a=snapshot;h=HEAD;sf=tgz](http://git.zerfleddert.de/cgi-bin/gitweb.cgi/micropolis?a=snapshot;h=HEAD;sf=tgz)

Thanks! Can you try to convince a MOTU to get this version into the universe repo? Is anybody experienced in packaging and can help?

If prooting a package to the repos fails, can you offer a deb file for Gutsy on your page? That would be convenient for beginners.

Michael Gernoth's fixes should make this game playable on lower resolutions as well. 

EDIT: BTW, his latest fixes are from 8 days ago, thus your version isn't fully up to date anymore (it seems).

---

### Post by alanbshepard70 on 2008-03-05
> **amano said:**
> 
EDIT: BTW, his latest fixes are from 8 days ago, thus your version isn't fully up to date anymore (it seems).

I'm generally able to post the most recent code as it comes out but I was extremely busy that week. The source is now the most current and includes updates and fixes from several different sources.

---

### Post by amano on 2008-03-07
Thanks a lot mate ;) Now we would need some MOTU to get this code packaged and added to the repos...

---

### Post by eragon100 on 2008-03-07
It works perfectly, just no sound :(

---

### Post by eragon100 on 2008-03-07
compiled from source with the guide at the beginning of the thread :)

---

### Post by alanbshepard70 on 2008-03-07
> **amano said:**
> Thanks a lot mate ;) Now we would need some MOTU to get this code packaged and added to the repos...

I appreciate it but a huge shout out and thanks needs to goto Michael Gernoth, he's the one who put in all the work to patch micropolis, adding cheats is simple. 

so.... Thanks Michael Gernoth.

---

### Post by altonbr on 2008-03-07
No .deb yet?

---

### Post by Joeb454 on 2008-03-07
I really want this for my laptop :D I keep checking [getdeb.net]("http://getdeb.net"), but I've not found anything yet :(

---

### Post by alanbshepard70 on 2008-03-07
> **Joeb454 said:**
> I really want this for my laptop :D I keep checking [getdeb.net]("http://getdeb.net"), but I've not found anything yet :(

You can get the micropolis .deb from getdeb here [http://www.getdeb.net/app.php?name=Micropolis](http://www.getdeb.net/app.php?name=Micropolis)

Be aware though that this is an old package that does not include the many fixes since it's release such as working sound, fit screen, full overlay mapping, air disasters re-enabled and many others, most notably the numluck issue that has now been fixed thanks to Michael Gernoth.

---

### Post by hockey97 on 2008-04-07
What I meant bon my early posting.

is that I don't see how you can have fun when there is simcity 3000 and simcity 4  ect.

I love simcity and also theme hospital, I also like airline tycoon. I like interesting tycoon simulation games.

it's just that today why play simcity original when you can play simcity 4 or the new one which I don't like much.

also can someone tell me why they can't  add a weather system??

I have been waiting I even told them during some live chat session they had.

What they told me  that the computer hardware can't handle the load. They said to have so many snow/ rain flakes/drops to drop from the sky takes alot of video proccessing and virtial ram.

---

### Post by samurailink3 on 2008-04-08
Even though I'm a HUGE fan of SimCity 3000, it can't compete with the sheer simplicity of the original Sim City. The point of the release is that this great game can get added life by going open source and being opened up to an entirely new audience. Even though new and 'better' games are released shouldn't stop people from playing older games. Super Mario Bros, System Shock 2, Final Fantasy VII, Zelda A Link to the Past, and countless others are amazing examples of immersion in this form of media. Granted, while none of these are open sourced in any matter, the simplicity or 'aged' status of these games shoudn't stop anyone from playing through what are considered some of gaming's greatest gems.

---

### Post by amano on 2008-04-14
Since compiling Micropolis was a bit of a hassle, I uploaded my compilation result (Hardy, 32 bit)  to Rapidshare: 	[http://rapidshare.com/files/107455743/micropolis.zip.html](http://rapidshare.com/files/107455743/micropolis.zip.html) (about 11 MB)

I used the patched code with the fixes for most of the annoying problems. Just the title screen is too big for most lower resolutions, but there is still no fix for that. Thus you have to move the window with the mouse to see all options.

Have fun. 

If someone has the skills: Please make a deb with the patched code. Only in this way the game can enter the Ubuntu repos at some point...


EDIT: To start the game, simply double-click the "Micropolis" file in the game folder in Nautilus. Or enter the game folder from within the terminal and type " ./Micropolis"

---

### Post by Dark_Rider2k3 on 2008-04-16
Hey!

It works great for me (minus the fact that the screen is HUGE) but I have 1 problem:

when I go to save, I get this message:

Unable to save the city to file named
"/usr/share/games/micropolis/city/firstcity.city".
Permission denied.

I am assuming i need to edit the permissions that the folder has, but I cannot remember how to do it (and /usr is under "root" so I can't change the settings via gui)

---

### Post by Ozor Mox on 2008-04-16
If you run

```
gksudo ./micropolis
```

to start Micropolis as root you should be able to save anywhere.

Or, if you run

```
gksudo nautilus
```

to start the file manager as root, you can modify the permissions of the folder you are talking about.

I saved my city in my home folder though, isn't it easier to do that?

---

### Post by drink on 2008-07-20
[http://ppa.launchpad.net/martin-espinoza/ubuntu/pool/main/m/micropolis/](http://ppa.launchpad.net/martin-espinoza/ubuntu/pool/main/m/micropolis/)

Packages are there for amd64/i386/ipia. Source too of course. Should in theory build anywhere Tcl/Tk builds.

This took me like a day, not sure why it hasn't happened elsewhere yet. I hope I got it right! I haven't tried DOWNLOADING this PPA, but I DID build and install it (on amd64 only but the PPA system builds for all three architectures and obviously it compiled...) so please let me know if it flails on other archs and I'll see if I can do something about it.

I still think "Ubuntero" sounds like a car on the Simpsons, though.

---

### Post by drink on 2008-07-20
Small correction: I have now downloaded and tested on i386 (works.)

What do I need to do to get this into Intrepid?

---

### Post by amano on 2008-11-06
You should file a bug in Launchpad.

BTW, for me the sound (eg. Bulldozer sound etc) is missing in intrepid ibex now. Does that happen to others as well?

---

### Post by hockey97 on 2009-02-08
So when will simcity 4 be released open sourced??? lol

hahaha :p 

I will pass on this. Cause I can't stand the old simcity games. I thought simcity 3000 and simcity 4 are the best ones they ever made.

I just hate how they don't add weather. It really sucks. I mean I want to  see a blizzard in my city and see cars sliding it would be a realistic event.

I do plan to try and make my own simcity down the road. If I do get to start on such a thing I will make a weather system on top of the list.

I just can't belive like 300 people told EA project managers and some programmers  to make a weather system. Then we saw  societies. That messed up the whole series.

The artwork seem too cartoonist. When I saw it on spike TV on E3 and saw the screen shots of  simicty societies I like yelled what the heck is this???

omg they messed up the series. They contracted the work to a 3rd party small company to make the game and this is what they get for doing such  a thing.

I was hoping none buys the game cause I personally thought the game artwork was a piece of crap.

I think simcity 4 and the expansion pack rush hour was the best so far in their series.

Their new game really sucks I would rather play simcity 2000 then the new one.

---

### Post by mister_playboy on 2009-09-15
Just found out about this today!  Thanks to drink for the .deb! :P   I've attached the .svg icon that came with the original binary release... copy it into /usr/share/icons/hicolor/scalable/apps and use it for your Micropolis launcher. :guitar:

---

### Post by rico001 on 2010-10-14
> **amano said:**
> You should file a bug in Launchpad.

BTW, for me the sound (eg. Bulldozer sound etc) is missing in intrepid ibex now. Does that happen to others as well?

Could you also put a request to put a link to the /manual/index.htm in the launch menu, so people will have instructions.
Thanks.

Just FYI, in order to save my game, I had to enable sharing permissions.

---

### Post by milindkrishna1 on 2010-10-31
Hello.. I am new in ubuntu and linux..

I got following message when tried to install compiling base,
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package freebsd5-buildutils is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package freebsd5-buildutils has no installation candidate

Could somebody help me out please?

---

### Post by rico001 on 2011-10-18
> **rico001 said:**
> Could you also put a request to put a link to the /manual/index.htm in the launch menu, so people will have instructions.
Thanks.

Just FYI, in order to save my game, I had to enable sharing permissions.

I found out that games can be saved in the home directory in your username folder

---

