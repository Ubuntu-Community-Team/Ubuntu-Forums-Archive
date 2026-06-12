---
title: "movie problems with Neverwinter Nights"
date: 2006-12-21
forum: Gaming &amp; Leisure
---

### Post by ceno-byte on 2006-12-21
first off i must say this is a great HOWTO guid for installing Neverwinter Nights thnxs very much Leech. I followed it but i ran into a problem when i tried to install the movies i followed everything in the guide but when i go to run NWN from the terminal i get this error " ERROR: ld.so: object './nwmovies.so' from LD_PRELOAD cannot be preloaded: ignored. "

here is my nwn script :

#!/bin/sh

# This script runs Neverwinter Nights from the current directory

export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0

# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
export LD_LIBRARY_PATH=./lib:./miles:$LD_LIBRARY_PATH
export LD_PRELOAD=./nwmovies.so
./nwmain $@

is there something i did wrong im not really sure what to do from here if it helps im running ubuntu 6.10

besides this little snag everything else works perfectly :)

---

### Post by ceno-byte on 2006-12-21
bump

---

### Post by leech on 2006-12-21
I would check to make sure that the nwmovies.so compiled properly.  The one it's trying to load is actually just a link to nwn/nwmovies/nwmovies.so make sure that it's there.  If it isn't, try just running the nwmovies_install.pl again and post the output here.

Leech

---

### Post by ceno-byte on 2006-12-22
ok i reinstalled the movie script here is the first output i got 

steve@steve:~/NWN$ ./nwmovies_install.pl /usr/lib/libSDL-1.2.so.0
NOTICE: NWMovies: Executing: gcc -Wall -Inwmovies/libdis -g -fPIC -shared -Wl,-soname,libdisasm.so nwmovies/libdis/libdis.c nwmovies/libdis/i386.c -o nwmovies/libdis/libdisasm.so
NOTICE: NWMovies: Executing: gcc -Wall -shared -g -Wl,-soname,binklib.so nwmovies/binklib.c -o nwmovies/binklib.so /usr/lib/libSDL-1.2.so.0 -ldl -lelf  -lm
NOTICE: NWMovies: Executing: gcc -Wall -shared -g -DSDLLIB=\"/usr/lib/libSDL-1.2.so.0\" -I/usr/include/libelf -Inwmovies/libdis -o nwmovies/nwmovies.so nwmovies/nwmovies.c nwmovies/nwmovies_lookup.c nwmovies/nwmovies_cookie.c nwmovies/nwmovies_crumb.c nwmovies/nwmovies_link.S /usr/lib/libSDL-1.2.so.0 -ldl -lelf 
NOTICE: NWMovies: Please check for errors above
NOTICE: NWMovies: nwmovies executable built. Please modify your nwn startup command to
NOTICE: NWMovies: set LD_PRELOAD to 'nwmovies.so', before executing nwmain.

here is the second output i got after running nwn

steve@steve:~/NWN$ ./nwn
NOTICE: NWMovies: Version: 20060113.161108
NOTICE: SDL Library determined to be: ./lib/libSDL-1.2.so.0
NOTICE: NWMovies: Patch 0 Address: 0x08076931
NOTICE: NWMovies: Patch 1 Address: 0x08076945
NOTICE: NWMovies: Patch 2 Address: 0x08159690
NOTICE: NWMovies: Patch 3 Address: 0x081596aa
NOTICE: NWMovies: Patch 4 Address: 0x08076803
NOTICE: NWMovies: Patch 5 Address: 0x08204c55
NOTICE: NWMovies: Patch 6 Address: 0x08204c78
NOTICE: NWMovies: PrePatch0: 8b 80 48 02 00 00 5d c3 
NOTICE: NWMovies: PrePatch1: 8b 80 4c 02 00 00 5d c3 
NOTICE: NWMovies: PrePatch2: e8 63 d3 f1 ff 83 ec 08 
NOTICE: NWMovies: PrePatch3: eb 58 83 ec 
NOTICE: NWMovies: PostPatch0: b8 00 00 00 00 90 5d c3 
NOTICE: NWMovies: PostPatch1: b8 00 00 00 00 90 5d c3 
NOTICE: NWMovies: PostPatch2: 90 90 90 90 90 83 ec 08 
NOTICE: NWMovies: PostPatch3: 90 90 83 ec 
NOTICE: NWMovies: PrePatch4: 56 8d 5d e8 53 
NOTICE: NWMovies: PostPatch4: e9 0c c1 e8 af 
NOTICE: NWMovies: MoviesPrePatch: 6a 00 53 bf 00 00 00 3f e8 c2 f3 29 00 8b 43 60 8b 10 c7 04 24 00 00 80 3f 57 57 57 50 ff 52 44 83 c4 1c 
NOTICE: NWMovies: MoviesPostPatch: 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 
NOTICE: NWMovies: SDL_WM_GrabInput() address: b7cf9900
NOTICE: NWMovies: (Calculated) SDL_WM_GrabInputRaw() address: b7cf9864
NOTICE: NWMovies: Initialized.

now i have the option for the movies but when i click on them (example prelude for NWN campaign) nothing happens. i even tried Ctrl + Alt + Backspace to restart my session and still no luck :( so close to fixing this any more suggestions Leech it would be greatly appreciated.

---

### Post by leech on 2006-12-22
Well let's test first to see if BinkPlayer is working.  From your nwn directory;

```
./BinkPlayer movies/NWNintro.bik
```

Leech

---

### Post by ceno-byte on 2006-12-22
i ran "./BinkPlayer movies/NWNintro.bik" first it said permission denied so i changed binkplayer to  allow executing of this program then i ran "./BinkPlayer movies/NWNintro.bik" again now it plays movies fine with that code but if i run NWN and try to play the movies in the game they still wont play.

---

### Post by leech on 2006-12-23
What does your nwmovies.log file say?

Leech

---

### Post by ceno-byte on 2006-12-23
ok here is what i attached my nwmovies.log file bcause its to much to post

---

### Post by leech on 2006-12-24
Install libsdl-gfx1.2-dev with 'sudo apt-get install libsdl-gfx1.2-dev'

According to your log, you're missing the libSDL_gfx.so file.  The weird thing is that it isn't giving that error at the beginning of the log, but afterwards (probably when you fixed the permissions on BinkPlayer, but now BinkPlayer can't find it.)

Hopefully this works for you.

Leech

---

### Post by ceno-byte on 2006-12-24
ok Leech i used the code "sudo apt-get install libsdl-gfx1.2-dev" and installed with no problem. so i started Neverwinter Nights and the movies still dont work. ive attached the terminal output of what it says when i try to play a movie hopefully from that you might know what to do next.

---

### Post by ceno-byte on 2006-12-26
Bump

---

### Post by ceno-byte on 2006-12-29
bump

---

