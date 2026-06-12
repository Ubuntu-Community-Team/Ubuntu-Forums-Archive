---
title: "Neverwinter Nights Movies"
date: 2006-11-16
forum: Gaming &amp; Leisure
---

### Post by JNowka on 2006-11-16
I have followed the howto by leech, and done everything by the book.  My problem is that everytime I play the game, the movies are not even played in game.  I have looked at the nwmovies.log file and it says that the movies are being successfully played.  I have used the command line to play the movies so the player works.  I have even deleted the # in front of the mplayer and plaympeg lines in the nwmovies.pl.  Nothing seems to work.  I don't see the Atarii Logo, the Bioware logo, the movies under the Movies section.  Can anyone help me?

---

### Post by leech on 2006-11-16
Post your nwmovies.log and maybe there is something I (or anyone else) can see in it that is causing the issue.

Are you using BinkPlayer to watch the movies?

Leech

---

### Post by JNowka on 2006-11-18
Sorry about the delay.  Had some things happen that pulled me away from the computer for a day.  Here is the zipped nwmovies.log.

*edit*
Yes I am using BinkPlayer to play the movies.

---

### Post by JNowka on 2006-11-18
Here is what I got when I ran the game from the command line

NOTICE: NWMovies: Version: 20060113.161108
NOTICE: SDL Library determined to be: /usr/lib/libSDL-1.2.so.0
NOTICE: NWMovies: Patch 0 Address: 0x08076939
NOTICE: NWMovies: Patch 1 Address: 0x0807694d
NOTICE: NWMovies: Patch 2 Address: 0x0815973c
NOTICE: NWMovies: Patch 3 Address: 0x08159756
NOTICE: NWMovies: Patch 4 Address: 0x0807680b
NOTICE: NWMovies: Patch 5 Address: 0x08204e41
NOTICE: NWMovies: Patch 6 Address: 0x08204e64
NOTICE: NWMovies: PrePatch0: 8b 80 48 02 00 00 5d c3
NOTICE: NWMovies: PrePatch1: 8b 80 4c 02 00 00 5d c3
NOTICE: NWMovies: PrePatch2: e8 bf d2 f1 ff 83 ec 08
NOTICE: NWMovies: PrePatch3: eb 58 83 ec
NOTICE: NWMovies: PostPatch0: b8 00 00 00 00 90 5d c3
NOTICE: NWMovies: PostPatch1: b8 00 00 00 00 90 5d c3
NOTICE: NWMovies: PostPatch2: 90 90 90 90 90 83 ec 08
NOTICE: NWMovies: PostPatch3: 90 90 83 ec
NOTICE: NWMovies: PrePatch4: 56 8d 5d e8 53
NOTICE: NWMovies: PostPatch4: e9 80 75 ee af
NOTICE: NWMovies: MoviesPrePatch: 6a 00 53 bf 00 00 00 3f e8 ae fd 29 00 8b 43 60 8b 10 c7 04 24 00 00 80 3f 57 57 57 50 ff 52 44 83 c4 1c
NOTICE: NWMovies: MoviesPostPatch: 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90
NOTICE: NWMovies: SDL_WM_GrabInput() address: b7d4229f
NOTICE: NWMovies: (Calculated) SDL_WM_GrabInputRaw() address: b7d421f0
NOTICE: NWMovies: Initialized.
*** glibc detected *** double free or corruption (out): 0x080acf60 ***
*** glibc detected *** double free or corruption (out): 0x080acf60 ***
*** glibc detected *** double free or corruption (out): 0x080acf60 ***
*** glibc detected *** double free or corruption (out): 0x080acf60 ***
*** glibc detected *** double free or corruption (out): 0x080acf60 ***
*** glibc detected *** double free or corruption (out): 0x080acf60 ***

---

### Post by leech on 2006-11-18
From the log, it looks like you're missing the libSDL_Gfx.so file.  You can fix this by installing libsdl-gfx1.2-dev

There is a way to compile the nwmovies to use the SDL library that comes with Neverwinter Nights, but I've always used the one that is installed with that package.

Leech

---

### Post by JNowka on 2006-11-18
Ok I have downloaded the libSDL_gfx driver and it didn't work.  So I reinstalled all my libSDL drivers that were installed and it didn't work.  So i deleted the .so files for the nwmovies and reinstalled and it didn't work.  So I have deleted the old log file and ran it again so you get a fresh look at things.

nwmovies.log
> ./nwmovies.pl AtariLogo >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: AtariLogo: Sat Nov 18 12:40:39 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/AtariLogo.bik
1163882439.989248: BinkLib: SDL_PRELOAD Initialized
NOTICE: NWMovies.pl finished playing: AtariLogo: Sat Nov 18 12:40:40 2006
./nwmovies.pl BiowareLogo >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: BiowareLogo: Sat Nov 18 12:40:40 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/BiowareLogo.bik
1163882440.219789: BinkLib: SDL_PRELOAD Initialized
NOTICE: NWMovies.pl finished playing: BiowareLogo: Sat Nov 18 12:40:40 2006
./nwmovies.pl WotcLogo >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: WotcLogo: Sat Nov 18 12:40:40 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/WOTCLogo.bik
1163882440.447561: BinkLib: SDL_PRELOAD Initialized
NOTICE: NWMovies.pl finished playing: WotcLogo: Sat Nov 18 12:40:40 2006
./nwmovies.pl fge_logo_black >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: fge_logo_black: Sat Nov 18 12:40:40 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/fge_logo_black.bik
1163882440.678318: BinkLib: SDL_PRELOAD Initialized
NOTICE: NWMovies.pl finished playing: fge_logo_black: Sat Nov 18 12:40:40 2006
./nwmovies.pl NWNIntro >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: NWNIntro: Sat Nov 18 12:40:40 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/NWNintro.bik
1163882440.906756: BinkLib: SDL_PRELOAD Initialized
NOTICE: NWMovies.pl finished playing: NWNIntro: Sat Nov 18 12:40:41 2006

nwn run script.
> #!/bin/sh

# This script runs Neverwinter Nights from the current directory

export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0

# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
export LD_LIBRARY_PATH=./lib:./miles:$LD_LIBRARY_PATH
export LD_PRELOAD=./nwmovies.so

./nwmain $@


Out put to terminal when ran from terminal.
> NOTICE: NWMovies: Version: 20060113.161108
NOTICE: SDL Library determined to be: ./lib/libSDL-1.2.so.0
NOTICE: NWMovies: Patch 0 Address: 0x08076939
NOTICE: NWMovies: Patch 1 Address: 0x0807694d
NOTICE: NWMovies: Patch 2 Address: 0x0815973c
NOTICE: NWMovies: Patch 3 Address: 0x08159756
NOTICE: NWMovies: Patch 4 Address: 0x0807680b
NOTICE: NWMovies: Patch 5 Address: 0x08204e41
NOTICE: NWMovies: Patch 6 Address: 0x08204e64
NOTICE: NWMovies: PrePatch0: 8b 80 48 02 00 00 5d c3
NOTICE: NWMovies: PrePatch1: 8b 80 4c 02 00 00 5d c3
NOTICE: NWMovies: PrePatch2: e8 bf d2 f1 ff 83 ec 08
NOTICE: NWMovies: PrePatch3: eb 58 83 ec
NOTICE: NWMovies: PostPatch0: b8 00 00 00 00 90 5d c3
NOTICE: NWMovies: PostPatch1: b8 00 00 00 00 90 5d c3
NOTICE: NWMovies: PostPatch2: 90 90 90 90 90 83 ec 08
NOTICE: NWMovies: PostPatch3: 90 90 83 ec
NOTICE: NWMovies: PrePatch4: 56 8d 5d e8 53
NOTICE: NWMovies: PostPatch4: e9 80 35 e9 af
NOTICE: NWMovies: MoviesPrePatch: 6a 00 53 bf 00 00 00 3f e8 ae fd 29 00 8b 43 60 8b 10 c7 04 24 00 00 80 3f 57 57 57 50 ff 52 44 83 c4 1c
NOTICE: NWMovies: MoviesPostPatch: 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90
NOTICE: NWMovies: SDL_WM_GrabInput() address: b7d00900
NOTICE: NWMovies: (Calculated) SDL_WM_GrabInputRaw() address: b7d00864
NOTICE: NWMovies: Initialized.
*** glibc detected *** double free or corruption (out): 0x0809e330 ***
*** glibc detected *** double free or corruption (out): 0x0809e330 ***
*** glibc detected *** double free or corruption (out): 0x0809e330 ***
*** glibc detected *** double free or corruption (out): 0x0809e330 ***
*** glibc detected *** double free or corruption (out): 0x0809e330 ***



I hope this helps.

---

### Post by JNowka on 2006-11-18
I have just noticed that if I run the game and try to play 1 movie from the movies tab I get 6 of the glibc detected errors on exit.  when I try to play none I only get 5.

---

### Post by Harleen on 2006-11-18
Have you compiled nwmovies using the libSDL provided by nwn? This could cause your problem, as the binkplayer requires the libSDL_Gfx from your system, which itself needs the Ubuntu-libSDL. When nwmovies loads the other library, than binkplayer will also use the "bioware"-library. And this line shows, that you are loading the bioware-library:
```
NOTICE: SDL Library determined to be: ./lib/libSDL-1.2.so.0
```
Try removing the ./lib from the LD_LIBRARY_PATH variable in your nwn startup script, so your system's libSDL is used.

If this sounds, as if I'm knowing what I'm talking about: I don't. I'm using mplayer for playback and am just wild guessing.

---

### Post by JNowka on 2006-11-18
Actually that line is caused by a setting in the nwn run script.  I have also changed that so that it is using the library from /usr/lib.  And still I have the problem.  Here is what everything currently looks like.

nwmovies.log
> ./nwmovies.pl AtariLogo >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: AtariLogo: Sat Nov 18 16:17:16 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/AtariLogo.bik
1163895437.043125: BinkLib: SDL_PRELOAD Initialized
NOTICE: NWMovies.pl finished playing: AtariLogo: Sat Nov 18 16:17:17 2006
./nwmovies.pl BiowareLogo >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: BiowareLogo: Sat Nov 18 16:17:17 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/BiowareLogo.bik
1163895437.406687: BinkLib: SDL_PRELOAD Initialized
NOTICE: NWMovies.pl finished playing: BiowareLogo: Sat Nov 18 16:17:17 2006
./nwmovies.pl WotcLogo >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: WotcLogo: Sat Nov 18 16:17:17 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/WOTCLogo.bik
1163895437.764593: BinkLib: SDL_PRELOAD Initialized
NOTICE: NWMovies.pl finished playing: WotcLogo: Sat Nov 18 16:17:17 2006
./nwmovies.pl fge_logo_black >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: fge_logo_black: Sat Nov 18 16:17:18 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/fge_logo_black.bik
1163895438.129554: BinkLib: SDL_PRELOAD Initialized
NOTICE: NWMovies.pl finished playing: fge_logo_black: Sat Nov 18 16:17:18 2006
./nwmovies.pl NWNIntro >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: NWNIntro: Sat Nov 18 16:17:18 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/NWNintro.bik
1163895438.488821: BinkLib: SDL_PRELOAD Initialized
NOTICE: NWMovies.pl finished playing: NWNIntro: Sat Nov 18 16:17:18 2006
nwn run script
> #!/bin/sh

# This script runs Neverwinter Nights from the current directory

export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0

# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
export LD_LIBRARY_PATH=./miles:$LD_LIBRARY_PATH
export LD_PRELOAD=/usr/local/games/nwn/nwmovies/nwmovies.so

./nwmain $@


Output to terminal when ran from terminal.
> NOTICE: NWMovies: Version: 20060113.161108
NOTICE: SDL Library determined to be: /usr/lib/libSDL-1.2.so.0
NOTICE: NWMovies: Patch 0 Address: 0x08076939
NOTICE: NWMovies: Patch 1 Address: 0x0807694d
NOTICE: NWMovies: Patch 2 Address: 0x0815973c
NOTICE: NWMovies: Patch 3 Address: 0x08159756
NOTICE: NWMovies: Patch 4 Address: 0x0807680b
NOTICE: NWMovies: Patch 5 Address: 0x08204e41
NOTICE: NWMovies: Patch 6 Address: 0x08204e64
NOTICE: NWMovies: PrePatch0: 8b 80 48 02 00 00 5d c3
NOTICE: NWMovies: PrePatch1: 8b 80 4c 02 00 00 5d c3
NOTICE: NWMovies: PrePatch2: e8 bf d2 f1 ff 83 ec 08
NOTICE: NWMovies: PrePatch3: eb 58 83 ec
NOTICE: NWMovies: PostPatch0: b8 00 00 00 00 90 5d c3
NOTICE: NWMovies: PostPatch1: b8 00 00 00 00 90 5d c3
NOTICE: NWMovies: PostPatch2: 90 90 90 90 90 83 ec 08
NOTICE: NWMovies: PostPatch3: 90 90 83 ec
NOTICE: NWMovies: PrePatch4: 56 8d 5d e8 53
NOTICE: NWMovies: PostPatch4: e9 80 05 f6 af
NOTICE: NWMovies: MoviesPrePatch: 6a 00 53 bf 00 00 00 3f e8 ae fd 29 00 8b 43 60 8b 10 c7 04 24 00 00 80 3f 57 57 57 50 ff 52 44 83 c4 1c
NOTICE: NWMovies: MoviesPostPatch: 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90
NOTICE: NWMovies: SDL_WM_GrabInput() address: b7dba29f
NOTICE: NWMovies: (Calculated) SDL_WM_GrabInputRaw() address: b7dba1f0
NOTICE: NWMovies: Initialized.
*** glibc detected *** double free or corruption (out): 0x080acf60 ***
*** glibc detected *** double free or corruption (out): 0x080acf60 ***
*** glibc detected *** double free or corruption (out): 0x080acf60 ***
*** glibc detected *** double free or corruption (out): 0x080acf60 ***
*** glibc detected *** double free or corruption (out): 0x080acf60 ***


---

### Post by JNowka on 2006-11-18
I found that the following command will work when run from the command line.  It is found in the nwmovies.log file.
> ./nwmovies.pl AtariLogo >> nwmovies.log 2>&1Everytime I do run it from the command line I get the following message after it gets done running.

> NOTICE: NWMovies.pl playing: AtariLogo: Sat Nov 18 16:43:59 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/AtariLogo.bik
1163897039.071197: BinkLib: SDL_PRELOAD Initialized
open /dev/sequencer: No such file or directory
NOTICE: NWMovies.pl finished playing: AtariLogo: Sat Nov 18 16:44:03 2006I have a feeling that the problem may be the fact that it cant find the /dev/sequencer.

Does anyone know how to make it avalible for Dapper?

Another thing is that the movies is choppy like this.  But with just using BinkPlayer it isn't.

---

### Post by leech on 2006-11-19
Try ```
sudo modprobe snd_seq_oss
```

My log looks like ```

./nwmovies.pl AtariLogo >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: AtariLogo: Sun Nov 19 08:14:46 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/AtariLogo.bik
1163949286.796244: BinkLib: SDL_PRELOAD Initialized
NOTICE: NWMovies.pl finished playing: AtariLogo: Sun Nov 19 08:14:51 2006
./nwmovies.pl BiowareLogo >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: BiowareLogo: Sun Nov 19 08:14:51 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/BiowareLogo.bik
1163949291.873573: BinkLib: SDL_PRELOAD Initialized
NOTICE: NWMovies.pl finished playing: BiowareLogo: Sun Nov 19 08:14:54 2006
./nwmovies.pl WotcLogo >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: WotcLogo: Sun Nov 19 08:14:54 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/WOTCLogo.bik
1163949294.162631: BinkLib: SDL_PRELOAD Initialized
NOTICE: NWMovies.pl finished playing: WotcLogo: Sun Nov 19 08:14:55 2006
./nwmovies.pl fge_logo_black >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: fge_logo_black: Sun Nov 19 08:14:55 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/fge_logo_black.bik
1163949295.496041: BinkLib: SDL_PRELOAD Initialized
NOTICE: NWMovies.pl finished playing: fge_logo_black: Sun Nov 19 08:14:57 2006
./nwmovies.pl NWNIntro >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: NWNIntro: Sun Nov 19 08:14:57 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/NWNintro.bik
1163949297.361903: BinkLib: SDL_PRELOAD Initialized
NOTICE: NWMovies.pl finished playing: NWNIntro: Sun Nov 19 08:14:58 2006

```

If Harleen were correct, I don't think mine should work (since I had built nwmovies with the system libraries, yet the LD_Path is set to ./lib.  I just tried removing it and running it again and my movies did not play.

So add that back in so that your nwn script looks like mine.  Not entirely sure why that would be the case, since the script itself says to remove ./lib.

Leech

---

### Post by JNowka on 2006-11-19
Ok I tried the sudo modprobe snd_seq_oss and it just basically quit out.

> jeremy@Linux:~$ sudo modprobe snd_seq_oss
Password:
jeremy@Linux:~$ sudo modprobe snd_seq_oss
jeremy@Linux:~$

---

### Post by leech on 2006-11-19
Yeah, that's what it's supposed to do, you should now have a /dev/sequencer.  List the output of ```
sudo lsmod |grep seq
```

Did the other change work?  Adding ./lib back into the nwn script?

Leech

---

### Post by JNowka on 2006-11-20
When I used the command I received this:
> jeremy@Linux:~$ sudo lsmod |grep seq
Password:
snd_seq_device          8716  1 snd_rawmidi
snd                    55268  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_pcm,snd_timer
jeremy@Linux:~$


As for adding ./lib back in the nwn script, no it didn't work.  It wouldn't play the movies either when I had it in there.  But I did add the ./lib in.

---

### Post by JNowka on 2006-11-20
Ok, last attempt.  This is what installing the nwmovies looks like.

> jeremy@Linux:/usr/local/games/nwn$ ./nwmovies_install.pl /usr/lib/libSDL-1.2.so.0
NOTICE: NWMovies: Executing: gcc -Wall -Inwmovies/libdis -g -fPIC -shared -Wl,-soname,libdisasm.so nwmovies/libdis/libdis.c nwmovies/libdis/i386.c -o nwmovies/libdis/libdisasm.so
NOTICE: NWMovies: Executing: gcc -Wall -shared -g -Wl,-soname,binklib.so nwmovies/binklib.c -o nwmovies/binklib.so /usr/lib/libSDL-1.2.so.0 -ldl -lelf  -lm
NOTICE: NWMovies: Executing: gcc -Wall -shared -g -DSDLLIB=\"/usr/lib/libSDL-1.2.so.0\" -I/usr/include/libelf -Inwmovies/libdis -o nwmovies/nwmovies.so nwmovies/nwmovies.c nwmovies/nwmovies_lookup.c nwmovies/nwmovies_cookie.c nwmovies/nwmovies_crumb.c nwmovies/nwmovies_link.S /usr/lib/libSDL-1.2.so.0 -ldl -lelf
NOTICE: NWMovies: Please check for errors above
NOTICE: NWMovies: nwmovies executable built. Please modify your nwn startup command to
NOTICE: NWMovies: set LD_PRELOAD to 'nwmovies.so', before executing nwmain.
jeremy@Linux:/usr/local/games/nwn$


---

### Post by leech on 2006-11-20
The only other difference I can see in your set up is that you installed to /usr/local/games/nwn instead of your user's home directory.

Leech

---

### Post by JNowka on 2006-11-21
> **leech said:**
> The only other difference I can see in your set up is that you installed to /usr/local/games/nwn instead of your user's home directory.

Leech

I prefer to install it there so all users of the computer can play it.  Do you think it would work if I used a symbolic link to link the directory to my home directory?

---

