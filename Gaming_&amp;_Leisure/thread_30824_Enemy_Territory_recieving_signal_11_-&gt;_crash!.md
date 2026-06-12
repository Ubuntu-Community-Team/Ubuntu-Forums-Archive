---
title: "Enemy Territory recieving signal 11 -&gt; crash!"
date: 2005-04-30
forum: Gaming &amp; Leisure
---

### Post by Dracontopes on 2005-04-30
This is what I get when running et from console:

chris@chris:~ $ et
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/chris/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

>>> CUT <<<

LOADING... clients
[skipnotify]^2*** You have been authorized "referee" status ***
Type: ^3ref^7 (by itself) for a list of referee commands.
CL_InitCGame: 14.54 seconds
Com_TouchMemory: 0 msec
[skipnotify]4hp^7 entered the game
4hp^7 has joined the Allied team^7!
==== ShutdownGame ====
Sys_LoadDll(/home/chris/.etwolf/etmain/qagame.mp.i386.so)...
Sys_LoadDll(/home/chris/.etwolf/etmain/qagame.mp.i386.so) failed:
"/home/chris/.etwolf/etmain/qagame.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/qagame.mp.i386.so)... ok
Sys_LoadDll(qagame) found **vmMain** at  0xa1b8eb90
Sys_LoadDll(qagame) succeeded!
------- Game Initialization -------
gamename: etmain
gamedate: Mar 10 2005
Not logging to disk.
Enable spawning!
Disable spawning!
0 teams with 0 entities
-----------------------------------
Setting MOTD...
Setting Allied autospawn to Abandoned Villa
Setting Axis autospawn to Forward Bunker
[skipnotify]4hp^7 entered the game
[skipnotify]^1FIGHT!
Received signal 11, exiting...
Shutdown tty console
wwwwwwwchris@chris:~ $

What is wrong here?
3d accel. is enabled. (ATI r9700pro)
The crashes appear random, but mostly within 10 minutes.

---

### Post by mreiki on 2005-06-01
i'm having the exact same problem ... :S

---

### Post by Birgit on 2007-06-21
add
       "+set r_allowSoftwareGL 1"

Helped me out.
But with me it didn't even start at the first place so I didn't had crashes after 10 minutes or so. 
Good luck !

---

### Post by Rafty on 2007-06-22
are you running 2.60 or 2.60b? if you run 2.60b, downgrade to 2.60 for testing.

_or maybe note this:_
[quote="De@thByBl@st"]This just in:

You _might_ get some positive results by upgrading your libelf (use the source Luke), it has help in a few cases I have come across recently and I have noticed that some distros use a ridiculously old version.

About:
libelf lets you read, modify or create ELF files in an architecture-independent way. The library takes care of size and endian issues. For example, you can process a file for SPARC processors on an Intel-based system. This library is a clean-room rewrite of the System V Release 4 library, and is supposed to be source code compatible with it. It was meant primarily for porting SVR4 applications to other operating systems, but can also be used as the basis for new applications (and as a light-weight alternative to libbfd).

Web page	[http://www.mr511.de/software/](http://www.mr511.de/software/)
Source tarball	[http://www.mr511.de/software/libelf-0.8.9.tar.gz](http://www.mr511.de/software/libelf-0.8.9.tar.gz)
Source information	[http://www.mr511.de/software/](http://www.mr511.de/software/)


As always, let us know if it helped you.[/quote]

good luck ;)

---

### Post by asipi on 2007-06-23
signal 11 is SIGSEGV = segmentation fault what could caused by improper libs and/or driver (video driver suspected)
if you are using 3D desktop like beryl, turn it off. if you are using screensaver, turn it off.
use stable libs (I mean do not install development cvs versions). upgrade ET to 2.60b, and upgrade your video driver to the latest. if you have a vhance, try an nvidia videocard because nvidia rocks on linux, it is better than under win (no flame plz, I tested on the same konfig)

IMO your problem comes from the opengl screensavers.

---

