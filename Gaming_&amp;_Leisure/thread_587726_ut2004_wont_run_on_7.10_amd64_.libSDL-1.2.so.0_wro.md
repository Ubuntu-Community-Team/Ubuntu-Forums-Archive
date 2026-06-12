---
title: "ut2004 wont run on 7.10 amd64 ./libSDL-1.2.so.0: wrong ELF class: ELFCLASS64"
date: 2007-10-23
forum: Gaming &amp; Leisure
---

### Post by spoonie on 2007-10-23
hi all 

Ive installed ut2004 and updated it to 3355 but it wont run :(

I was getting this error./ut2004-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

but that one is fixed but now I get this error about sdl 
./ut2004-bin: error while loading shared libraries: ./libSDL-1.2.so.0: wrong ELF class: ELFCLASS64

Ive installed 32bit libraries (sudo apt-get install ia32-libs*) but still no goodI, Ive downloaded i386 deb of sdl but it wont let me install it because Im running 64 build Ive modified the ut2004 startup script so it points to the amd64 binary.  

anyone had the same issue 

thanks all

---

### Post by johannes on 2007-10-24
You probably just need to start it with the correct binary, ut2004-bin-linux-amd64.

e.g.
cd ut2004/System
./ut2004-bin-linux-amd64

---

### Post by otac0n on 2007-10-25
Same problem. (Except, I'm at 3369)

This indeed worked for me. :)

You can edit the /usr/local/games/ut2004/ut2004 file to point to the ut2004-bin-linux-amd64 instead of ut2004-bin

---

### Post by [MD5]Hash on 2007-10-25
I'm going to bump this thread, not sure how old it is, but I'm having an issue running the UT2004 demo for the x64 build of the game, and I've been scouring the interwebs for hours looking for a solution, and I'm not having much luck...

Here's where I stand, I've downloaded the x64 version of the game and successfully installed the game, if it makes any difference whatsoever, I installed it on a secondary partition I use for storing larger games and backup files, so if this is a possible issue, please feel free to let me know.

I'm also using the 64 bit build of Ubuntu 7.10, again, if this plays any role in resolving this problem.

When I try to run the game, I get the following error:

./ut2004-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory


I've tried using 'sudo apt-get install ia32-libs*" to see if that would fix any of this, and still I get the above error message.  Any advice?


Edit: Okay, I found the package I needed to install, and got it installed.  The game now runs, but I'm having a new issue...

The game runs insanely fast, everything in the game runs faster than normal, the menus, the actual gameplay itself is like 180% of normal.

---

### Post by alexuntu on 2007-10-26
Similar problem here,

I installed ut2004 fine on ubuntu 7.10 then when i tried running it i get that same error everyone stated before:

./ut2004-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

I exported LD_LIBRARY_PATH to /usr/lib32 where this file is located but i now started getting the error:

./ut2004-bin: error while loading shared libraries: libstdc++.so.5: wrong ELF class: ELFCLASS32

Does anyone have any idea how to solve this one? I noticed some of you spoke aboutut a file '2004-bin-linux-amd64' but after checking my install dir i don't seem to find that binary there.

Any Ideas? Thanks in advance for the help

Edit:
 I've managed to get this going, i installed the 3369 patch then tried running the original ut2004-bin (not the one from the patch) it complained that libSDL-1.2.so.0 was wrong ELF class: ELFCLASS64 so i simply created a local link to /usr/lib32/libSDL-1.2-so.0 and voilá it all worked perfectly.

Hope this helps others with the same problem.


Alex

---

