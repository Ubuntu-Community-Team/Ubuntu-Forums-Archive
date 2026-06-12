---
title: "ZSnes wont start - SDL_CloseAudio?.."
date: 2007-05-12
forum: Gaming &amp; Leisure
---

### Post by MikeReiner on 2007-05-12
:(
```

mike@solution:~/zsnes_1_51/src$ ./autogen.sh
Generating build information using aclocal and autoconf...
/usr/share/aclocal/smpeg.m4:13: warning: underquoted definition of AM_PATH_SMPEG
/usr/share/aclocal/smpeg.m4:13:   run info '(automake)Extending aclocal'
/usr/share/aclocal/smpeg.m4:13:   or see http://sources.redhat.com/automake/automake.html#Extending-aclocal
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for nasm... nasm
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.2.0... yes
checking for zlib - version >= 1.2.3... yes
checking for libpng - version >= 1.2.0... yes
checking if you want the zsnes debugger... yes
checking for initscr in -lcurses... no
checking for initscr in -lncurses... no
checking for initscr in -lpdcurses... no
configure: error: A curses library is required to use the debugger


```




===============old
After installing zsnes through ubuntu's package manager, trying to run it gives me:

```
ZSNES v1.42 (c) 1997-2005, ZSNES Team

Be sure to check http://www.zsnes.com/ for the latest version.
Please report crashes to zsnes-devel@lists.sourceforge.net.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE' thoroughly before doing so.

Use ZSNES -? for command line definitions.

MMX support found and enabled.

zsnes: symbol lookup error: zsnes: undefined symbol: SDL_CloseAudio

```

i'm running
ubuntu 7.04 feisty just incase you wanna know.

Also, another quick question to you other linux guys, would using a real sound card as opposed to onboard stop some of the terrible sound issues that games on linux have at times?

---

### Post by MikeReiner on 2007-05-21
Bump.. come on guys... :\

---

### Post by BoyOfDestiny on 2007-05-21
> **MikeReiner said:**
> After installing zsnes through ubuntu's package manager, trying to run it gives me:

```
ZSNES v1.42 (c) 1997-2005, ZSNES Team

Be sure to check http://www.zsnes.com/ for the latest version.
Please report crashes to zsnes-devel@lists.sourceforge.net.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE' thoroughly before doing so.

Use ZSNES -? for command line definitions.

MMX support found and enabled.

zsnes: symbol lookup error: zsnes: undefined symbol: SDL_CloseAudio

```

i'm running
ubuntu 7.04 feisty just incase you wanna know.

Also, another quick question to you other linux guys, would using a real sound card as opposed to onboard stop some of the terrible sound issues that games on linux have at times?

Hmm does it still happen if you disable esound? It's under system -> preferences -> Sound -> Enable sound mixing (I run with it unchecked) and do a reboot (or pkill esd)

As for zsnes, I use 1.51, here is a deb I made the "debian way" (and a little before feisty went gold)

[http://www.safaribans.com/ubuntu/dists/feisty/main/binary-i386/zsnes_1.51-1_i386.deb](http://www.safaribans.com/ubuntu/dists/feisty/main/binary-i386/zsnes_1.51-1_i386.deb)

As for crappy sound, my laptop has an onboard intel soundcard. I've found setting games etc to use 48000hz frequency solved my sound issues. 

Good luck :)

---

### Post by MikeReiner on 2007-05-21
I'm afraid that didn't work. :\

I asked the same question here a while ago:
[http://board.zsnes.com/phpBB2/viewtopic.php?t=10103](http://board.zsnes.com/phpBB2/viewtopic.php?t=10103)

The developer said that my SDL version may be 'too' new.. anyway I could test that theory?

speaking of which, what version are you using?

---

### Post by BoyOfDestiny on 2007-05-21
> **MikeReiner said:**
> I'm afraid that didn't work. :\

I asked the same question here a while ago:
[http://board.zsnes.com/phpBB2/viewtopic.php?t=10103](http://board.zsnes.com/phpBB2/viewtopic.php?t=10103)

The developer said that my SDL version may be 'too' new.. anyway I could test that theory?

speaking of which, what version are you using?

I'm using Feisty as well. With zsnes 1.51. So we have the same verison of SDL etc... It's probably Ubuntu's old zsnes package that is having trouble...

Would you like to give compiling zsnes a try?

[www.zsnes.com](www.zsnes.com)

Download the Linux verison, extract it in the home folder (or wherever, but for this example it should end up in /home/yourusername/zsnes_1_51

from a terminal (I'm guessing you have universe repo enabled)

Paste this in
*sudo apt-get install build-essential nasm autoconf automake libsdl1.2-dev zlib1g-dev libpng12-dev mesa-common-dev libao-dev *

I think that's all you should need to build it (not sure as I installed the dependencies for building zsnes almost a year ago... It's basically a one time thing here)

then get to the directory where you extracted zsnes ( /home/yourusername/zsnes_1_51)
*cd zsnes_1_51/src*

then
*./autogen.sh*

Hopefully no errors

then type

*make*

After it's done

*sudo make install*

Then enjoy zsnes 1.51

---

### Post by MikeReiner on 2007-05-22
:(
```

mike@solution:~/zsnes_1_51/src$ ./autogen.sh
Generating build information using aclocal and autoconf...
/usr/share/aclocal/smpeg.m4:13: warning: underquoted definition of AM_PATH_SMPEG
/usr/share/aclocal/smpeg.m4:13:   run info '(automake)Extending aclocal'
/usr/share/aclocal/smpeg.m4:13:   or see http://sources.redhat.com/automake/automake.html#Extending-aclocal
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for nasm... nasm
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.2.0... yes
checking for zlib - version >= 1.2.3... yes
checking for libpng - version >= 1.2.0... yes
checking if you want the zsnes debugger... yes
checking for initscr in -lcurses... no
checking for initscr in -lncurses... no
checking for initscr in -lpdcurses... no
configure: error: A curses library is required to use the debugger


```

---

### Post by MikeReiner on 2007-05-22
update: I disabled the debugger, so the lack of curses doesn't matter.. so i started compiling.. and why am I not surprised.. *more* problems...

code: part that actually matters...
```
linux/audio.o: In function `DeinitSound':
audio.c:(.text+0xc4): undefined reference to `SDL_CloseAudio'
linux/audio.o: In function `InitSound':
audio.c:(.text+0x117): undefined reference to `SDL_CloseAudio'
audio.c:(.text+0x1a8): undefined reference to `SDL_OpenAudio'
audio.c:(.text+0x1b8): undefined reference to `SDL_PauseAudio'
audio.c:(.text+0x20d): undefined reference to `SDL_CloseAudio'
linux/audio.o: In function `SoundWrite_sdl':
audio.c:(.text+0x2fa): undefined reference to `SDL_LockAudio'
audio.c:(.text+0x3d9): undefined reference to `SDL_UnlockAudio'
collect2: ld returned 1 exit status
make: *** [main] Error 1

```

---

### Post by BoyOfDestiny on 2007-05-23
> **MikeReiner said:**
> update: I disabled the debugger, so the lack of curses doesn't matter.. so i started compiling.. and why am I not surprised.. *more* problems...

code: part that actually matters...
```
linux/audio.o: In function `DeinitSound':
audio.c:(.text+0xc4): undefined reference to `SDL_CloseAudio'
linux/audio.o: In function `InitSound':
audio.c:(.text+0x117): undefined reference to `SDL_CloseAudio'
audio.c:(.text+0x1a8): undefined reference to `SDL_OpenAudio'
audio.c:(.text+0x1b8): undefined reference to `SDL_PauseAudio'
audio.c:(.text+0x20d): undefined reference to `SDL_CloseAudio'
linux/audio.o: In function `SoundWrite_sdl':
audio.c:(.text+0x2fa): undefined reference to `SDL_LockAudio'
audio.c:(.text+0x3d9): undefined reference to `SDL_UnlockAudio'
collect2: ld returned 1 exit status
make: *** [main] Error 1

```

I'm really at a loss here...

try installing

libsdl-sound1.2-dev
libsdl1.2debian-alsa
libsdl-mixer1.2-dev

Hope that does it... I'm sure it can work. We have the exact same software here...

---

### Post by MikeReiner on 2007-05-23
Same result. :(

---

### Post by MikeReiner on 2007-05-27
*bump* 

*whistles tetris theme*

---

### Post by BoyOfDestiny on 2007-05-28
> **MikeReiner said:**
> *bump* 

*whistles tetris theme*

No one else seems to have encountered this I guess... Ok here is everything with sdl in it that I have installed...
(in screen cap)

Do you have anything like a .asoundrc sitting in your home folder?

Do any other SDL based software have sound issues?

Hope this helps...

Output of ./autogen.sh for me
```

./autogen.sh
Generating build information using aclocal and autoconf...
/usr/share/aclocal/soundtouch.m4:29: warning: underquoted definition of AM_PATH_SOUNDTOUCH
/usr/share/aclocal/soundtouch.m4:29:   run info '(automake)Extending aclocal'
/usr/share/aclocal/soundtouch.m4:29:   or see http://sources.redhat.com/automake/automake.html#Extending-aclocal
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for nasm... nasm
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.2.0... yes
checking for zlib - version >= 1.2.3... yes
checking for libpng - version >= 1.2.0... yes
checking if you want the zsnes debugger... yes
checking for initscr in -lcurses... yes
checking for initscr in -lncurses... yes
checking for initscr in -lpdcurses... no
checking if you want libao support... no
checking how to run the C preprocessor... gcc -E
checking for X... libraries , headers 
checking for glGetError in -lGL... yes
checking for OpenGL... yes
checking for JMA support... yes
checking for cpu info... found
checking if you want gdb friendly executable... no
checking which cpu architecture to optimize for... pentium-m
checking if you want crazy optimizations... no
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking whether sys/types.h defines makedev... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged


ZSNES v1.51

SDL support                   Version 1.2.11
NASM support                  NASM version 0.98.38 compiled on Jun 27 2005
zlib support                  Version 1.2.3
PNG support                   Yes, version 1.2.15beta5
OpenGL support                Yes
JMA support                   Yes
ZSNES debugger                Enabled

The binary will be installed in /usr/local/bin


```

---

### Post by MikeReiner on 2007-05-28
Well OBVIOUSLY I broke something here. I just installed all of those packages, and the error didn't change at all. This is seriously pissing me off.

edit: oh and no, .asound or anything like that.

---

### Post by BoyOfDestiny on 2007-05-29
> **MikeReiner said:**
> Well OBVIOUSLY I broke something here. I just installed all of those packages, and the error didn't change at all. This is seriously pissing me off.

edit: oh and no, .asound or anything like that.

Yeah I can imagine how annoying this must be...
Hmm, could it be hardware?

Ok here is one more idea. 
Do you have a feisty live cd? Try popping it in, enable the repos, and install zsnes 1.42 (or whatever the repo version is) do you encounter the error still? 
If so I'd say just file a bug report... I've never encountered this bug... I've been running Ubuntu with zsnes since day 1...

Sorry I couldn't be of more help. 
Good luck.

EDIT: One other thing, can you launch zsnes (as in it runs without sound) and change the sound settings? Maybe one of them works?
shown when I launch zsnes
Audio Opened.
Driver: Simple DirectMedia Layer output
Channels: 2
Rate: 48000

---

### Post by fdmille on 2008-02-16
I had the same curses library error and this solved the problem for me (Gutsy):

In Synaptic Package Manager, install Lib32ncurses5 and Lib32ncurses5-dev.

---

