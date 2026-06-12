---
title: "[SOLVED] Doom 1 problems"
date: 2007-10-13
forum: Gaming &amp; Leisure
---

### Post by TidusBlade on 2007-10-13
I tried installing Doom 1 through WINE, but it doesn't work too well, not truly fullscreen and sound is a bit delayed. I then tried with Cedega, It installed flawlessly, but when I open it, theres no sound and freezes after about 10 seconds of play :( BTW I installed from the Collector's Edition.
Any help would be appreciated ^_^

---

### Post by DoktorSeven on 2007-10-13
Go grab a native DOOM port, there is no reason to have to run DOOM through Wine/Cedega/DOSbox.  You just need the WAD file(s) from the DOOM install CD (or the install itself on your HD).

Doomsday is quite good, and a simple frontend is [here](http://gdoomsday.sf.net).

---

### Post by Dark Aspect on 2007-10-13
Hi

I am in the same boat I have 64-bit Ubuntu so Doomsday does not work and PRBoom hangs up....Any other ideas for a port,I don't like lxldoom becuase I can't get it in full screen.Does ZDoom work with 64-bit?

---

### Post by DoktorSeven on 2007-10-13
I don't know if any of them can be successfully built in a 64-bit environment (I don't have a 64-bit system to test).  You can always download zdoom's source and give compiling a try.

---

### Post by Dark Aspect on 2007-10-14
> **DoktorSeven said:**
> I don't know if any of them can be successfully built in a 64-bit environment (I don't have a 64-bit system to test).  You can always download zdoom's source and give compiling a try.

Right....After I downloaded and installed what I believe to be all of the dependences I receive this error:

> Compiling sc_man.cpp:                                                 [ERROR]  
g++ -fno-rtti -pipe -Wall -Wno-unused -fno-strict-aliasing -O2 -fomit-frame-pointer -MMD -DHAVE_FILELENGTH -D__forceinline=inline -Izlib -IFLAC -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -Dstricmp=strcasecmp -Dstrnicmp=strncasecmp -DNEED_STRUPR -Isrc/ -Isrc/g_doom/ -Isrc/g_heretic/ -Isrc/g_hexen/ -Isrc/g_raven/ -Isrc/g_shared/ -Isrc/g_strife/ -Isrc/oplsynth/ -Isrc/sound/ -Isrc/sdl/ -Isrc/textures/ -DUSEASM=1 -DNDEBUG -o releaseobj/sc_man.o -c src/sc_man.cpp
================================================================================src/sc_man_scanner.re: In function &#8216;bool SC_GetString()&#8217;:
src/sc_man_scanner.re:144: error: no matching function for call to &#8216;MIN(long int, int)&#8217;
make: *** [releaseobj/sc_man.o] Error 1


Ideas?,I have never complied ZDoom before on Linux and I have heard of it being difficult.Could the above error be related to running a 64-bit OS?

---

### Post by TidusBlade on 2007-10-14
> **DoktorSeven said:**
> Go grab a native DOOM port, there is no reason to have to run DOOM through Wine/Cedega/DOSbox.  You just need the WAD file(s) from the DOOM install CD (or the install itself on your HD).

Doomsday is quite good, and a simple frontend is [here](http://gdoomsday.sf.net).
Never knew there was a native port :) Thanx!

---

### Post by FredB on 2007-10-14
Doom 1 ? Knee Deep in Dead ? How many hours on it ;)

My preferred port is also Zdoom.

---

### Post by hikaricore on 2007-10-14
I can't say for sure if it's 64bit compatible, but Doomsday has always been my favorite: [http://www.doomsdayhq.com/](http://www.doomsdayhq.com/)
As well as not being too difficult to compile it supports 3d models to bring new life to good old Doom.

---

### Post by superdif on 2008-02-29
Sorry if I resume an old thread, but I have the same problem on Kubuntu 7.10 64 bits.

The thread is marked as SOLVED, but the solution is not clear (at least to me). :confused:

---

### Post by TidusBlade on 2008-03-01
Yeah, I marked it as solved since I found a solution elsewhere. 
Sorry if I cant link to it, found it back in October...
But you can just use one of those native DOOM ports ;)

---

### Post by superdif on 2008-03-01
Ok then. I'll keep trying several ports.

Thanks. :)

---

### Post by UK-Wobbie on 2008-03-01
I got DOOM 1 and 2 working in Wine and it worked OK!
But you may need to play about with the size of the screen and put it as full screen!

And for music you need [timidity]("apt://timidity") to play the midi files :)

---

### Post by grossaffe on 2008-03-29
I've found EDGE (Enhanced Doom Gaming Engine) to be a useable Doom engine for Gutsy 64-bit.  My favorite Total Conversion, the GoldeneyeTC, was written for EDGE (it was written for zdoom as well, but the EDGE version is far superior in features)

On the other hand, i would like to get zdoom working because there are some pwads that only work with that that i would like to get to run.

---

### Post by hessiess on 2008-03-29
> **grossaffe said:**
> I've found EDGE (Enhanced Doom Gaming Engine) to be a useable Doom engine for Gutsy 64-bit.  My favorite Total Conversion, the GoldeneyeTC, was written for EDGE (it was written for zdoom as well, but the EDGE version is far superior in features)

On the other hand, i would like to get zdoom working because there are some pwads that only work with that that i would like to get to run.

zdoom works on wine if you don't want to compile

---

### Post by grossaffe on 2008-03-30
> **hessiess said:**
> zdoom works on wine if you don't want to compile

yeah, but how do you get pwads working with it since you can't drag 'n drop in linux?

also, i found it to be a bit buggy in wine.

---

### Post by disturbedite on 2008-03-31
Skulltag is by far the best 2D version of doom available.  there is a native linux version & there is even an ubuntu download on the download page.  (no compiling required).
i beta test it & its great.

---

### Post by hessiess on 2008-03-31
> **grossaffe said:**
> yeah, but how do you get pwads working with it since you can't drag 'n drop in linux?

also, i found it to be a bit buggy in wine.

i just dropped doom1.wad into the directory after unziping and it just worked. the graphics are abit glitchy but its playable

---

### Post by grossaffe on 2008-03-31
> **hessiess said:**
> i just dropped doom1.wad into the directory after unziping and it just worked. the graphics are abit glitchy but its playable

no, that's the Iwad, pwads are the mods for doom.  if i just want to play doom straight up, i use EDGE.  I'll also use it with whatever pwads are made for it through the terminal.  but some pwads were made specifically for zdoom and do not work with EDGE.

---

