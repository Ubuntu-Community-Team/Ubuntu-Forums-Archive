---
title: "Compiling XMAME 0.97"
date: 2005-07-14
forum: Gaming &amp; Leisure
---

### Post by oshi on 2005-07-14
Okay, I know there are a lot of topics on this subject and I have read every one of them.

I am a novice at linux, I have only been using Ubuntu for a few months.

My question is how do I compile xmame 0.97?

I am trying to compile the source to include new rom data for more recent games. (hope this is okay to say here :))

Anyway  have made all the changes needed to the files that needed to be edited and I have no clue on how to compile.

I assume I just run "make" in a terminal or something like that? 

When I do run "make" it says:

```
make: *** No targets specified and no makefile found.  Stop.
```

Can anyone pelase help me? Thanks a lot for any help.

And again sorry for beating a dead horse. :)

---

### Post by BoyOfDestiny on 2005-07-14
mame .98 is out, hopefully advmame and xmame will catch up soon =)  (and I wouldn't worry about mentioning rom data... just don't say where to get the 11-12 gigs of it ;) )... 

Anyway, go to synaptic and make sure you have build-essential. Also, I recommend getting automake, autogen, and checkinstall as well... I'm not sure if necessary but I dl'd the xmame-dev package (if memory serves). 

I forgot if it comes with an autogen... if so try ./autogen.sh
./configure
make

if there is anything reported missing just grab it from synaptic. After it's nice and compiled, either do a make install or checkinstall. The latter will make a nice .deb file for you. If you choose that route, dpkg -i nameofyour.deb

After that you should be all set, I wanted a cross platform gui too... so I downloaded advance menu (which should work with xmame and not just advmame)

[http://advancemame.sourceforge.net/index.html](http://advancemame.sourceforge.net/index.html)

Good luck,

BoyOfDestiny

---

### Post by oshi on 2005-07-14
I have the build-essentials, automake, autogen, and checkinstall.

xmame doesn't come with an autogen or configure script. 

in the root dir theres a "makefile.unix" "makefile.mame" & a "makefile.mes"

---

### Post by BoyOfDestiny on 2005-07-14
Ah... now I remember why I use advancemame. [http://advancemame.sourceforge.net/download.html](http://advancemame.sourceforge.net/download.html)

Trust me, it's better than xmame, and for some reason alt+enter made it fullscreen without any tweaking.

Although I guess this isn't really the solution... has anyone compiled xmame successfully?

---

### Post by oshi on 2005-07-14
[QUOTE=BoyOfDestiny]Ah... now I remember why I use advancemame. [http://advancemame.sourceforge.net/download.html](http://advancemame.sourceforge.net/download.html)

Trust me, it's better than xmame, and for some reason alt+enter made it fullscreen without any tweaking.

Although I guess this isn't really the solution... has anyone compiled xmame successfully?[/QUOTE]
 I'll give AdvMAME a shot. I'm not sure if the same rules apply to adding new games for it. But I assume it's the same.

---

### Post by oshi on 2005-07-15
Okay I figured I'd just use the same topic.

When I try to make AdvanceSCAN it spits this out at the end:

```
make  all-am
make[1]: Entering directory `/home/oshi/downloads/source/advancescan-1.13'
g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -DUSE_LSB -DUSE_ERROR_SILENT -c -o scan.o scan.cc
g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -DUSE_LSB -DUSE_ERROR_SILENT -c -o rom.o rom.cc
g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -DUSE_LSB -DUSE_ERROR_SILENT -c -o disk.o disk.cc
g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -DUSE_LSB -DUSE_ERROR_SILENT -c -o sample.o sample.cc
g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -DUSE_LSB -DUSE_ERROR_SILENT -c -o conf.o conf.cc
g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -DUSE_LSB -DUSE_ERROR_SILENT -c -o data.o data.cc
g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -DUSE_LSB -DUSE_ERROR_SILENT -c -o token.o token.cc
gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -DUSE_LSB -DUSE_ERROR_SILENT -c strcov.c
g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -DUSE_LSB -DUSE_ERROR_SILENT -c -o file.o file.cc
g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -DUSE_LSB -DUSE_ERROR_SILENT -c -o ziprom.o ziprom.cc
g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -DUSE_LSB -DUSE_ERROR_SILENT -c -o game.o game.cc
g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -DUSE_LSB -DUSE_ERROR_SILENT -c -o gameinfo.o gameinfo.cc
g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -DUSE_LSB -DUSE_ERROR_SILENT -c -o gamexml.o gamexml.cc
g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -DUSE_LSB -DUSE_ERROR_SILENT -c -o zip.o zip.cc
g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -DUSE_LSB -DUSE_ERROR_SILENT -c -o output.o output.cc
g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -DUSE_LSB -DUSE_ERROR_SILENT -c -o analyze.o analyze.cc
g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -DUSE_LSB -DUSE_ERROR_SILENT -c -o siglock.o siglock.cc
gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -DUSE_LSB -DUSE_ERROR_SILENT -c getopt.c
gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -DUSE_LSB -DUSE_ERROR_SILENT -c snprintf.c
gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -DUSE_LSB -DUSE_ERROR_SILENT -c -o readinfo.o `test -f 'lib/readinfo.c' | | echo './'`lib/readinfo.c
gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -DUSE_LSB -DUSE_ERROR_SILENT -c -o xmlrole.o `test -f 'expat/xmlrole.c' | | echo './'`expat/xmlrole.c
gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -DUSE_LSB -DUSE_ERROR_SILENT -c -o xmlparse.o `test -f 'expat/xmlparse.c'  || echo './'`expat/xmlparse.c
gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -DUSE_LSB -DUSE_ERROR_SILENT -c -o xmltok.o `test -f 'expat/xmltok.c' || echo './'`expat/xmltok.c
g++  -g -O2 -DUSE_LSB -DUSE_ERROR_SILENT   -o advscan  scan.o rom.o disk.o sample.o conf.o data.o token.o strcov.o f ile.o ziprom.o game.o gameinfo.o gamexml.o zip.o output.o analyze.o siglock.o getopt.o snprintf.o readinfo.o xmlrole .o xmlparse.o xmltok.o  -lz
g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -DUSE_LSB -DUSE_ERROR_SILENT -c -o diff.o diff.cc
g++  -g -O2 -DUSE_LSB -DUSE_ERROR_SILENT   -o advdiff  diff.o rom.o disk.o sample.o data.o strcov.o file.o ziprom.o game.o gameinfo.o gamexml.o zip.o siglock.o getopt.o snprintf.o readinfo.o xmlrole.o xmlparse.o xmltok.o  -lz
make[1]: *** No rule to make target `expat/COPYING', needed by `all-am'.  Stop.
make[1]: Leaving directory `/home/oshi/downloads/source/advancescan-1.13'
make: *** [all] Error 2

```

Also when running "advmame gametitle" it tells me:

```
AdvanceMAME - Copyright (C) 1999-2003 by Andrea Mazzoleni
MAME - Copyright (C) 1997-2003 by Nicola Salmoria and the MAME Team
Unable to initialize the video driver. The errors are:
fb: Unsupported in X.
```

It also says the same thing while running advmenu.

Clues?

---

### Post by BoyOfDestiny on 2005-07-15
hmm bizzare, worked out of the box for me. I guess make sure you have the SDL dev files... Did you do anything besides 

 ./configure 
make 
make install or checkinstall

As for running the games, before I installed advance menu, I would right click on my rom set (mine are zipped) and do an open with advmame.

---

### Post by oshi on 2005-07-15
I don't think I have the SDL dev files. Is there a deb package around?

after 'make install' i ran advmame gametitle from a terminal and it gave me that error.

---

### Post by UKer on 2005-07-15
I had no problems compiling xmame. I just edited the makefile.unix and the only changes I made were to enable opengl (you need the x-window-system-dev package if you do this) and the joystick, and I think I needed to install an xml parser (libxml-parser-perl) and libncurses5-dev packages, and it build fine just by running 'make'. If you want an easy GUI you also need the latest beta of gxmame, I use 0.35beta2 (the latest stable version isn't compatible with 0.97), you need the gtk and gnome dev files for this I think.

When setting up gxmame I chose the binary for xmame (/usr/local/bin/xmame.x11) and enabling opengl made it run very well in fullscreen (even for games like Cruisin' USA).

You can also get preview screenshots and icons for gxmame from [http://www.classicgaming.com/mame32qa/](http://www.classicgaming.com/mame32qa/) - these make choosing games much easier as you can see what they look like.

---

### Post by BoyOfDestiny on 2005-07-16
So advmame built properly after make? I notice in what you pasted there was "make all -am"... And yes, there should be some package with sdl dev... but if it was able to build... should work...

As for gxmame, it looks like the last release was in 2003, and mame 35 beta 2 is from 1999 (mame doesn't even use that old naming convention)... 

Which is why I choose advance menu, many new games, and very trivial to set up (just play with the .rc file)

---

### Post by McQuaid on 2005-07-17
Hey, I myself gave up on xmame and went the advmame route.  I don't really like the frontend much, and found the mucking with the cfg files annoying but got everything working in the end.  I should have made notes but didn't so just looking through my advmame.rc file to notice some of the things i did.

First thing, pressing alt enter for fullscreen annoyed the heck out of me.  I wanted fullscreen by default which should be trivial.

the first thing I tried was changing device_video_output to fullscreen.  Which seemed to work but was definitely not the same as using alt enter.  The pixel's looked stretched in a weird way and there was a definite performance hit.  Then I read about changing device_video_output to overlay and I had great fullscreen by default.  I say 'great fullscreen' because it wasn't the same as indicating fullscreen nor pressing alt enter.  It was using the hardware overlay and the reason I liked this was that it would stretch the image of the game so that there would be no borders.  This is a feature on the directx side of things in windows but sdl has no such feature.  Thats why in most emus in linux you'll get borders as most arcade games/consoles used irregular resolutions but in the end were meant to be displayed on a 4:3 screen.  Advancemame does this by having it's own stretching of the image (but what seems to be only enabled with overlay as indicated above).  By default it's done through this option in the config: device_video_overlaysize 1024.  If you res is higher than 1024 change appropriately.  The downside to this is the scanlines option doesn't look right on this.  Well, with nvidia cards anyways as nvidia cards apply a filter to 2d stuff using hardware overlay.  It can actually make games look nicer, like say rygar, but a game with really low res like pac man might look kinda smudged.  As this is in hardware this problem exists on the windows side as well.  I found a site that talked about hacking in weird resolutions so that you'd have each res available for all the types of games.  From what I've read this is totally safe to do, just not sure if it's ok on the linux side but might give it a shot.

But before trying the above try doing this to deal with your x11 problem.  In the same config change device_video to sdl.  I can't remember if I changed that but I believe I did from x11.  

Here's my outstanding issues/gripes.  I don't want to display all the mame games.  I'd like to display a list of my favourites.  Advmenu seems to have some rating scheme but I couldn't figure it out.  Also, I thought since advmenu is really meant for a cabinet and to be worked by a joystick I thought I'd enable it.  I changed device_joystick none to auto and advmenu would wig out.  It would just keep moving left until the game selection cursor was all the way to the top.  But that exact same setting has my joystick working in the advmame file.  Well, the one issue I have is my start/select buttons are not recognised while within an advmame game.  I usually like to set start to pause.  This is with a psx game pad hooked up to the lpt port.  All buttons work in all other games in linux except advmame, but a minor gripe I guess. 

 And if I prefer to use alt enter for fullscreen for games where I'd prefer scanlines it would be nice to figure out the config equivilent if anyone knows that.  Also that brings me to that last thing on advmame.  Some games I'd run at desktop res, some higher/lower (like asteroids, I used to run at a higher res to help aleviate stairstepping effects for vector graphics, that is until the emulation of the sound in asteroids, now it needs a 2 gig rig to run, I wish someone maintained a patch to apply so samples would be used if present).  As it is I don't see any way of setting per game video/audio configs.  I was looking for the cfg directory that's usually standard for mame keeping each games specific settings but advmame doesn't use that.  Instead, if you change button mapping assignments it appends them to advmame.rc file which I find kinda clunky.  I wonder why they would drop the cfg dir when they did the first port.  Just limits flexibility as far as I can see.  

Ok way too much, hopefully someone found it useful.  Btw, a lot of my once working roms are no longer working as I hadn't updated mame in ages.  I might have to grab redumps but I know mame scan programs can get some working again with just renaming.  Is there a good rom scanning util in linux? preferably something with a gui.

---

### Post by Mosey on 2005-12-17
I'm getting the same error after building and while attempting a first run:

AdvanceMENU - Copyright (C) 1999-2004 by Andrea Mazzoleni
Unable to initialize the video driver. The errors are:
fb: Unsupported in X.

Any ideas on this?

---

### Post by anil_robo on 2005-12-21
I downloaded, compiled and installed Gxmame successfully. Gxmame is a Gtk frontend for xmame. I had an old CD of some mame ROMs lying around. I copied the roms to the hard drive, and tried to load them with Gxmame. It audited them fine - saying that they were correct. But it never showed the games in the list to run :(

I know the game ROM is good. GXMame also knows that the roms are correct. But how do I launch them? :(

---

### Post by dobbymoodge on 2005-12-29
[QUOTE=Mosey]I'm getting the same error after building and while attempting a first run:

AdvanceMENU - Copyright (C) 1999-2004 by Andrea Mazzoleni
Unable to initialize the video driver. The errors are:
fb: Unsupported in X.

Any ideas on this?[/QUOTE]

Make sure that you have libsdl-dev installed.  Something like ```
sudo apt-get install libsdl1.2-dev
``` ought to do the trick, or use synaptic.  I also installed a bunch of other sdl-dev packages just to be sure.

I still haven't gotten joystick support working; advj works fine, but I can't get the actual emulator to detect the joystick.

---

