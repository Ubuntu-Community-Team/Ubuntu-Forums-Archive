---
title: "/usr/bin/ld: cannot find -lG error ??! i'm lost"
date: 2007-04-29
forum: Gaming &amp; Leisure
---

### Post by Vanaheim on 2007-04-29
Hi all, Iv been customizing Ubuntu and learning while doing it, I'm very happy about the way things are improving, so now I'm stepping to the other side and start to customize my retro apps, emulators mostly.

I had Dapper, then re-installed everything and now I'm on Feisty. I think i have all the compile tools installed since i was able to compile a few things already and just a couple of minutes ago i compiled and installed SDL (latest version).

So, since i had already compiled SDL Mame on Dapper and made a backup, i just thought i would use that on Feisty, i made a few changes to a file on the code and tried to compile it but i guet the following error..

Linking mamepm...
/usr/bin/ld: cannot find -lGL
collect2: ld returned 1 exit status
make: *** [mamepm] Error 1

I'm lost here, can anyone help me understand what I'm missing? 
I tried to official SDL mame forums but the site seams to be down temporarily, so, i hope someone of guys might know this specific issue and help me on this ^^

Cheers to all

EDITED:

When i tried to install the dev packages for SDL with synaptic i get this error message:

E: /var/cache/apt/archives/libsdl1.2-dev_1.2.11-7ubuntu1_i386.deb: trying to overwrite `/usr/share/man/man3/SDL_AddTimer.3.gz', which is also in package sdl-devel

I don't know what to do know :(

EDITED (again)

i tried to make a clean compile, now this is what i get with SDL Mame 0114u3

Linking obj/mamepm/file2str...
/usr/bin/ld: cannot find -lXinerama
collect2: ld returned 1 exit status
make: *** [obj/mamepm/file2str] Error 1

i also tried to compile Hazemd (which i was able to compile in Dapper just fine), bow i guet this..

Compiling src/sdl/video.c...
src/sdl/video.c: In function &#8216;sdlvideo_monitor_refresh&#8217;:
src/sdl/video.c:286: error: &#8216;SDL_SysWMinfo&#8217; has no member named &#8216;subsystem&#8217;
src/sdl/video.c:286: error: &#8216;SDL_SYSWM_X11&#8217; undeclared (first use in this function)
src/sdl/video.c:286: error: (Each undeclared identifier is reported only once
src/sdl/video.c:286: error: for each function it appears in.)
src/sdl/video.c:295: warning: implicit declaration of function &#8216;DefaultScreen&#8217;
src/sdl/video.c:295: error: &#8216;SDL_SysWMinfo&#8217; has no member named &#8216;info&#8217;
src/sdl/video.c:297: warning: implicit declaration of function &#8216;DisplayWidth&#8217;
src/sdl/video.c:297: error: &#8216;SDL_SysWMinfo&#8217; has no member named &#8216;info&#8217;
src/sdl/video.c:298: warning: implicit declaration of function &#8216;DisplayHeight&#8217;
src/sdl/video.c:298: error: &#8216;SDL_SysWMinfo&#8217; has no member named &#8216;info&#8217;
make: *** [obj/hazemdpm/sdl/video.o] Error 1

now..this is probably related to SDL right?

I compiled the source (from the their website) and converted the RPM and installed them

still the same errors, then i uninstalled them and installed the libsdl from the repositories and still i get those errors :(

---

### Post by mbradlcu on 2007-05-18
you seem a bit more advanced the me but regarding the ld error you may want to install one of the following packages if you haven't already:
libdmx-dev - X11 Distributed Multihead extension library (development headers)
libdmx1 - X11 Distributed Multihead extension library
libdmx1-dbg - X11 Distributed Multihead library (debug package)
libxcb-xinerama0 - X C Binding, xinerama extension
libxcb-xinerama0-dbg - X C Binding, xinerama extension, debugging symbols
libxcb-xinerama0-dev - X C Binding, xinerama extension, development files
libxinerama-dev - X11 Xinerama extension library (development headers)
libxinerama1 - X11 Xinerama extension library

hope you get it,, sounds like you're up to some cool stuff!

---

