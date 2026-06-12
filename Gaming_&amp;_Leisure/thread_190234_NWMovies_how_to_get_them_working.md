---
title: "NWMovies how to get them working"
date: 2006-06-06
forum: Gaming &amp; Leisure
---

### Post by hellfire_bg on 2006-06-06
For the last several hours i`ve been trying to get NWMovies (this is a user made addon that allows the play of Neverwinter Nights` movies inside the linux client) working with no success. The errorr message i get is:
> ./nwmovies.pl AtariLogo >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: AtariLogo: Tue Jun  6 08:47:09 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/AtariLogo.bik
1149572831.546112: BinkLib: SDL_PRELOAD Initialized
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave
NOTICE: NWMovies.pl finished playing: AtariLogo: Tue Jun  6 08:47:13 2006
./nwmovies.pl BiowareLogo >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: BiowareLogo: Tue Jun  6 08:47:14 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/BiowareLogo.bik
1149572834.579726: BinkLib: SDL_PRELOAD Initialized
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave
NOTICE: NWMovies.pl finished playing: BiowareLogo: Tue Jun  6 08:47:14 2006
./nwmovies.pl WotcLogo >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: WotcLogo: Tue Jun  6 08:47:14 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/WOTCLogo.bik
1149572835.037499: BinkLib: SDL_PRELOAD Initialized
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave
NOTICE: NWMovies.pl finished playing: WotcLogo: Tue Jun  6 08:47:15 2006
./nwmovies.pl fge_logo_black >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: fge_logo_black: Tue Jun  6 08:47:15 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/fge_logo_black.bik
1149572835.614518: BinkLib: SDL_PRELOAD Initialized
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave
NOTICE: NWMovies.pl finished playing: fge_logo_black: Tue Jun  6 08:47:15 2006
./nwmovies.pl NWNIntro >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: NWNIntro: Tue Jun  6 08:47:16 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/NWNintro.bik
1149572836.095388: BinkLib: SDL_PRELOAD Initialized
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave
NOTICE: NWMovies.pl finished playing: NWNIntro: Tue Jun  6 08:47:16 2006
./nwmovies.pl Prelude >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: Prelude: Tue Jun  6 08:47:24 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/prelude.bik
1149572844.647864: BinkLib: SDL_PRELOAD Initialized
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave
NOTICE: NWMovies.pl finished playing: Prelude: Tue Jun  6 08:47:24 2006

Any idea what should i do? The most annoying thing is that several months ago i easily managed to get them working but i don`t remember what i did to get them working and on which distribution it was (it was either on gentoo or on ubuntu 5.10).

---

### Post by edm00se on 2006-08-19
I'm pretty sure that the forum user leech knows how to. I think he said he was going to post a howto thread on it, though I've been waiting for it for a while and haven't seen it yet. ;)

---

### Post by mlind on 2006-08-19
This is probably libSDL related thingy. I've built [patched libSDL]("http://home.woh.rr.com/nwmovies/libsdl.html") soname for which has fullscreen toggling patches included.

It's for Dapper (and alsa version I guess).
[http://ubuntuforums.org/showpost.php?p=1364547&postcount=103](http://ubuntuforums.org/showpost.php?p=1364547&postcount=103)

Related thread from bioware forums
[http://nwn.bioware.com/forums/viewtopic.html?topic=490407&forum=72](http://nwn.bioware.com/forums/viewtopic.html?topic=490407&forum=72)

---

### Post by leech on 2006-08-19
Yeah, and I apologize for that, I've been just busy doing stuff.  I'll give it a run.  At one point the guy who wrote the installer that I have in the how to had discussed with me having the NWmovies and NWmouse installed by the installer, but his website has dropped from the face of the planet.

I'll get to work on it today.

Leech

---

### Post by leech on 2006-08-19
I added to the How-To for adding the Movies in.  Unfortunately I can't really test it, since  don't have Dapper installed on my system right now (updated to Edgy).

I attached the nwmovies.so that I just built (it looks like he updated the script not too long ago, so maybe there is a fix in there for you.)

Leech

---

### Post by edm00se on 2006-08-19
I'll give it a go and see what I can find.

---

### Post by edm00se on 2006-08-19
Hit a snag. Filed a [bug report]("https://launchpad.net/distros/ubuntu/+source/libsdl1.2/+bug/56939") on it. When attempting to install libsdl1.2-dev it gives me some dependency issues.

When trying to install libsdl1.2-dev
> libsdl1.2-dev: Depends: libartsc0-dev but it is not going to be installed

Trying to install libartsc0-dev:
> libartsc0-dev: Depends: libglib2.0-dev but it is not going to be installed

Trying to install libglib2.0-dev:
> libglib2.0-dev: Depends: libglib2.0-0 (= 2.10.2-1ubuntu3) but 2.10.3-0ubuntu1 is to be installed

Wasn't even able to force it (with -f, gave same errors).

---

### Post by leech on 2006-08-19
Odd, I wonder if they screwed up the Dapper packages, is that what you're running?  libglib2.0-dev 2.10.3 is the one that is in Edgy.

Leech

---

### Post by mlind on 2006-08-19
I'm able to install libsl1.2-dev on Dapper. You probably got something messed up with custom packages or missing repository from sources.list

```

$ sudo aptitude install libsdl1.2-dev
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  libaa1-dev libartsc0-dev libasound2-dev libaudio-dev libesd0-dev
  libgl1-mesa-dev libglu1-mesa-dev libice-dev libslang2-dev libsm-dev
  libx11-dev libxau-dev libxdmcp-dev libxext-dev libxi-dev mesa-common-dev
  x11proto-core-dev x11proto-input-dev x11proto-kb-dev x11proto-xext-dev
The following NEW packages will be installed:
  libaa1-dev libartsc0-dev libasound2-dev libaudio-dev libaudiofile-dev
  libesd0-dev libgl1-mesa-dev libglib2.0-dev libglu1-mesa-dev libice-dev
  libncurses5-dev libsdl1.2-dev libslang2-dev libsm-dev libx11-dev
  libxau-dev libxdmcp-dev libxext-dev libxi-dev libxt-dev mesa-common-dev
  x11proto-core-dev x11proto-input-dev x11proto-kb-dev x11proto-xext-dev
0 packages upgraded, 25 newly installed, 0 to remove and 0 not upgraded.
Need to get 6851kB of archives. After unpacking 27,9MB will be used.
Do you want to continue? [Y/n/?]

```

---

### Post by edm00se on 2006-08-19
> **mlind said:**
> I'm able to install libsl1.2-dev on Dapper. You probably got something messed up with custom packages or missing repository from sources.list

```

$ sudo aptitude install libsdl1.2-dev

```

Interestingly enough, I tried using aptitude in place of apt-get (which all my previous attempts had been) and it magically fixed all my problems. Is there any reason that should happen?

I should finish verifying the howto with movies upon my return to my apartment tonight.

---

### Post by mlind on 2006-08-19
> **edm00se said:**
> Interestingly enough, I tried using aptitude in place of apt-get (which all my previous attempts had been) and it magically fixed all my problems. Is there any reason that should happen?


Dunno. Sometimes apt-get gets confused like that and aptitude wants to install more packages than necessary. 
Or there could have been pending updates on a repository, so that dependencies were incomplete for short period.

---

### Post by edm00se on 2006-08-20
Well, whichever the case, ```
sudo aptitude install libsdl1.2-dev
``` worked just fine.

  I finished the rest of the instructions according to the howto and while it seemed like it would have worked, I still don't get the videos to play in-game.

  Here's my terminal output when I try to play:
```

eric@RabbitHole:/usr/local/games/nwn$ ./nwn
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
NOTICE: NWMovies: PostPatch4: e9 88 d5 f5 af
NOTICE: NWMovies: MoviesPrePatch: 6a 00 53 bf 00 00 00 3f e8 c2 f3 29 00 8b 43 60 8b 10 c7 04 24 00 00 80 3f 57 57 57 50 ff 52 44 83 c4 1c
NOTICE: NWMovies: MoviesPostPatch: 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90
NOTICE: NWMovies: SDL_WM_GrabInput() address: b7dd4900
NOTICE: NWMovies: (Calculated) SDL_WM_GrabInputRaw() address: b7dd4864
NOTICE: NWMovies: Initialized.
mcop warning: user defined signal handler found for SIG_PIPE, overriding


```

  I had been experiencing problems with not being able to run NWN prior to updating my video driver properly to NVIDIA's driver version 1.0-8762. I use an AGP 8x GeForce FX5200. The game did not run prior to my updating to the appropriate NVIDIA driver. Before my fiddling with the bink player settings, the game ran, as it does now, without the in-game movies.
  My version of Neverwinter Nights is the Diamon release, which I installed from DVD via the install script per leech's Howto.

  The only thing I believe I am missing is that while the Howto instructs to download three files: 1- installer script, 2- nwmovies-latest.tar.gz, and 3- BinkLinuxPlayer.zip.

  The Howto does not cover what to do with the BinkLInuxPlayer.zip file. I know it's kind of nitpicky, but it's 2:37 am right now for me, I can't seem to figure out what to do with it. Leech, help me out here buddy. I'm guessing the BinkPlayer has to be installed somehwere.

---

### Post by leech on 2006-08-20
My bad.  I think I actually was writing that at about the same time you posted last.

I'll fix it.

All I had to do was unzip it into the nwn main folder.  nwmovies picks it up from there.  I did a fresh install the other day of it in Edgy and with the exception of the dash vs. bash thing (I mention that at the bottom of the howto) it worked the same as it does in Dapper.  

Leech

---

### Post by edm00se on 2006-08-20
It's in the nwn directory and once more, it gives the same output as my last post:

  ```

eric@RabbitHole:/usr/local/games/nwn$ ./nwn
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
NOTICE: NWMovies: PostPatch4: e9 88 e5 ea af
NOTICE: NWMovies: MoviesPrePatch: 6a 00 53 bf 00 00 00 3f e8 c2 f3 29 00 8b 43 60 8b 10 c7 04 24 00 00 80 3f 57 57 57 50 ff 52 44 83 c4 1c
NOTICE: NWMovies: MoviesPostPatch: 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90
NOTICE: NWMovies: SDL_WM_GrabInput() address: b7d25900
NOTICE: NWMovies: (Calculated) SDL_WM_GrabInputRaw() address: b7d25864
NOTICE: NWMovies: Initialized.
mcop warning: user defined signal handler found for SIG_PIPE, overriding


```

  Anyone know what that mcop warning means?

---

### Post by mlind on 2006-08-20
> **edm00se said:**
> Anyone know what that mcop warning means?

I think that message is coming from arts plugin. Are you using original NWN's libSDL ? If you are, try to remove ./lib from LD_LIBRARY_PATH that's defined on **nwn** script.

Dapper has libsdl plugin for Alsa installed.

---

### Post by edm00se on 2006-08-20
Yes, I was using the SDL that came with it. I took a look in the nwn script, saw what you were talking about and removed the "./lib" from the LD_LIBRARY_PATH.

  On the first run, got the following output:
```

eric@RabbitHole:/usr/local/games/nwn$ ./nwn
NOTICE: NWMovies: Version: 20060113.161108
NOTICE: SDL Library determined to be: /usr/lib/libSDL-1.2.so.0
WARNING: NWMovies: INI recalculation required: 7734576:7734576 1146250588:1146250588 408104:405239 1146250588:1050522574
WARNING: NWMovies: SDL_WM_GrabInputRaw() not visible.  Looking for it the hard way.
WARNING: NWMovies: This may not work.
NOTICE: NWMovies: (crumb) Entry point determined: 0xc440
NOTICE: NWMovies: (crumb) Located address: 000361f0
NOTICE: NWMovies: (cookie) Entry point determined: 0x7830
NOTICE: NWMovies: (cookie) Searching executable: 28
NOTICE: NWMovies: (cookie) Cookie location: 0x1ac07a
NOTICE: NWMovies: (cookie) Searching executable: 29
NOTICE: NWMovies: (cookie) Call Location #1: 000270f8
NOTICE: NWMovies: (cookie) Call Location #2: 0002710c
NOTICE: NWMovies: (cookie) Call Location #3: 00026fc8
NOTICE: NWMovies: (cookie) Searching executable: 16
NOTICE: NWMovies: (cookie) Searching executable: 02
NOTICE: NWMovies: (cookie) Searching executable: 02
NOTICE: NWMovies: (cookie) Searching executable: 18
NOTICE: NWMovies: (cookie) Searching executable: 02
NOTICE: NWMovies: (movies) Searching executable: 28
NOTICE: NWMovies: (movies) Searching executable: 30
NOTICE: NWMovies: (movies) Cookie start_location: 0x1b5425
NOTICE: NWMovies: (movies) Searching executable: 30
NOTICE: NWMovies: (movies) Cookie end_location: 0x1b5448
NOTICE: NWMovies: (cookie) Recalculated calls 0: 08076931
NOTICE: NWMovies: (cookie) Recalculated calls 1: 08076945
NOTICE: NWMovies: (cookie) Recalculated calls 2: 08159690
NOTICE: NWMovies: (cookie) Recalculated calls 3: 081596aa
NOTICE: NWMovies: (cookie) Recalculated calls 4: 08076803
NOTICE: NWMovies: (movies) Recalculated calls 5: 08204c55
NOTICE: NWMovies: (movies) Recalculated calls 6: 08204c78
NOTICE: NWMovies: INI File written: Now exiting.  This is perfectly normal!
NOTICE: Your next run of NWN should be complete, and include movies.

```

  So, running the second time, got no videos again. Here's the output:
```

eric@RabbitHole:/usr/local/games/nwn$ ./nwn
NOTICE: NWMovies: Version: 20060113.161108
NOTICE: SDL Library determined to be: /usr/lib/libSDL-1.2.so.0
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
NOTICE: NWMovies: PostPatch4: e9 88 b5 f4 af
NOTICE: NWMovies: MoviesPrePatch: 6a 00 53 bf 00 00 00 3f e8 c2 f3 29 00 8b 43 60 8b 10 c7 04 24 00 00 80 3f 57 57 57 50 ff 52 44 83 c4 1c
NOTICE: NWMovies: MoviesPostPatch: 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90
NOTICE: NWMovies: SDL_WM_GrabInput() address: b7db029f
NOTICE: NWMovies: (Calculated) SDL_WM_GrabInputRaw() address: b7db01f0
NOTICE: NWMovies: Initialized.

```

  Seeing how there was a presumption on what libSDL to use, looking in /usr/lib/ my options appear to be:
[LIST=1]
[*]libSDL-1.2.so.0
[*]libSDL-1.2.so.0.7.2
[*]libSDL.a
[*]libSDL.la
[*]libSDLmain.a
[*]libSDL.so
[/LIST]

  At least, that's what I get when I hit tab for $ls /usr/lib/libSDL
Should I specify a different libSDL in the nwn script?

---

### Post by edm00se on 2006-08-21
It somehow feels like I made some headway, but it's about 4am here, and I'm not really much further. Okay, here's what I've got:

  I was reading through the nwmovies.README.softmix.txt that comes in the nwmovies dir. In it, the author talks about what seems to be a recurring problem with the distributed libSDL from Bioware, in which a symbol required by NWMovies is not visible. What he says to look for is the following, inside the output from the nwn script:

```

WARNING: NWMovies: SDL_WM_GrabInputRaw() not visible. Looking for it the hard way.
WARNING: NWMovies: This may not work.

```

  Each time I run nwn, regardless of whether I have it point to the Bioware provided libSDL-1.2.so.0 or letting it find my machine's libSDL-1.2.so.0.7.2 from /usr/lib/ (or whichever it picks from removing ./lib in the nwn script), I get that very error.

  According to the README, I'm supposed to compile the new version (at the time of its writing, 1.2.7) of libSDL-1.2 from source, with a slight adjustment to the src/video/SDL_video.c to remove the static reference from:

```

static SDL_GrabMode SDL_WM_GrabInputRaw(SDL_GrabMode mode)

```


  I did this with the currently available link from libsdl.org which the download is version 1.2.11. Once it's configured (with --enable-alsa) and made, the instructions appear to say to copy over the newly made libSDL-1.2.so.0.7.0 (I imagine there'd be an 11 in there in place of 7). I cannot find the file anywhere.

  Having no luck, I went back, downloaded the 1.2.7 source, and tried again to find the same thing. So, I'm either too tired to function properly and am missing the file I need to copy over in place of libSDL-1.2.so.0, or something is amiss.

---

### Post by mlind on 2006-08-21
If you compiled modified libSDL from source package, place it on nwn/lib and make sure nwn/lib/libSDL-1.2.so.0 symlink points to this new file.

---

### Post by leech on 2006-08-21
In my How To I did specify to use the one for ubuntu.  /usr/lib/libSDL.so.0 what you could do is, if Kubuntu has the libSDL for Arts, just install the one for alsa with sudo apt-get install libsdl1.2debian-alsa.  You could also try libsdl1.2debian-all (which I think has all the interfaces compiled in).  

Leech

---

### Post by edm00se on 2006-08-21
I've installed libSDL1.2debian-alsa and when I remove ./lib from the nwn script, it finds libSDL on my system, which I'm guessing is that one. I get the same results, which is why I tried compiling from source in the first place.

  I tried the same after having installed libSDL1.2debian-all, but after I got the same, switched back to the -alsa package.

  As for making a sym link to the new file I compiled, what the heck am I supposed to consider _the file_? I can't seem to find it. In the build dir, this is what I got:

```

eric@RabbitHole:~/Desktop/SDL-1.2.11$ ls build
libSDL.la          SDL_error.lo         SDL_nullevents.lo   SDL_video.lo
libSDLmain.a       SDL_error.o          SDL_nullevents.o    SDL_video.o
SDL_active.lo      SDL_esdaudio.lo      SDL_nullmouse.lo    SDL_wave.lo
SDL_active.o       SDL_esdaudio.o       SDL_nullmouse.o     SDL_wave.o
SDL_alsa_audio.lo  SDL_events.lo        SDL_nullvideo.lo    SDL_x11dga.lo
SDL_alsa_audio.o   SDL_events.o         SDL_nullvideo.o     SDL_x11dga.o
SDL_artsaudio.lo   SDL_expose.lo        SDL.o               SDL_x11dyn.lo
SDL_artsaudio.o    SDL_expose.o         SDL_pixels.lo       SDL_x11dyn.o
SDL_audiocvt.lo    SDL_fatal.lo         SDL_pixels.o        SDL_x11events.lo
SDL_audiocvt.o     SDL_fatal.o          SDL_qsort.lo        SDL_x11events.o
SDL_audiodev.lo    SDL_fb3dfx.lo        SDL_qsort.o         SDL_x11gamma.lo
SDL_audiodev.o     SDL_fb3dfx.o         SDL_quit.lo         SDL_x11gamma.o
SDL_audio.lo       SDL_fbelo.lo         SDL_quit.o          SDL_x11gl.lo
SDL_audio.o        SDL_fbelo.o          SDL_resize.lo       SDL_x11gl.o
SDL_blit_0.lo      SDL_fbevents.lo      SDL_resize.o        SDL_x11image.lo
SDL_blit_0.o       SDL_fbevents.o       SDL_RLEaccel.lo     SDL_x11image.o
SDL_blit_1.lo      SDL_fbmatrox.lo      SDL_RLEaccel.o      SDL_x11modes.lo
SDL_blit_1.o       SDL_fbmatrox.o       SDL_rwops.lo        SDL_x11modes.o
SDL_blit_A.lo      SDL_fbmouse.lo       SDL_rwops.o         SDL_x11mouse.lo
SDL_blit_A.o       SDL_fbmouse.o        SDL_stdlib.lo       SDL_x11mouse.o
SDL_blit.lo        SDL_fbriva.lo        SDL_stdlib.o        SDL_x11video.lo
SDL_blit_N.lo      SDL_fbriva.o         SDL_stretch.lo      SDL_x11video.o
SDL_blit_N.o       SDL_fbvideo.lo       SDL_stretch.o       SDL_x11wm.lo
SDL_blit.o         SDL_fbvideo.o        SDL_string.lo       SDL_x11wm.o
SDL_bmp.lo         SDL_gamma.lo         SDL_string.o        SDL_x11yuv.lo
SDL_bmp.o          SDL_gamma.o          SDL_surface.lo      SDL_x11yuv.o
SDL_cdrom.lo       SDL_getenv.lo        SDL_surface.o       SDL_yuv.lo
SDL_cdrom.o        SDL_getenv.o         SDL_syscdrom.lo     SDL_yuv_mmx.lo
SDL_cpuinfo.lo     SDL_iconv.lo         SDL_syscdrom.o      SDL_yuv_mmx.o
SDL_cpuinfo.o      SDL_iconv.o          SDL_syscond.lo      SDL_yuv.o
SDL_cursor.lo      SDL_joystick.lo      SDL_syscond.o       SDL_yuv_sw.lo
SDL_cursor.o       SDL_joystick.o       SDL_sysjoystick.lo  SDL_yuv_sw.o
SDL_dgaevents.lo   SDL_keyboard.lo      SDL_sysjoystick.o   XF86DGA2.lo
SDL_dgaevents.o    SDL_keyboard.o       SDL_sysloadso.lo    XF86DGA2.o
SDL_dgamouse.lo    SDL.lo               SDL_sysloadso.o     XF86DGA.lo
SDL_dgamouse.o     SDL_malloc.lo        SDL_sysmutex.lo     XF86DGA.o
SDL_dgavideo.lo    SDL_malloc.o         SDL_sysmutex.o      XF86VMode.lo
SDL_dgavideo.o     SDL_mixer.lo         SDL_syssem.lo       XF86VMode.o
SDL_diskaudio.lo   SDL_mixer_m68k.lo    SDL_syssem.o        Xinerama.lo
SDL_diskaudio.o    SDL_mixer_m68k.o     SDL_systhread.lo    Xinerama.o
SDL_dmaaudio.lo    SDL_mixer_MMX.lo     SDL_systhread.o     xme.lo
SDL_dmaaudio.o     SDL_mixer_MMX.o      SDL_systimer.lo     xme.o
SDL_dspaudio.lo    SDL_mixer_MMX_VC.lo  SDL_systimer.o      Xv.lo
SDL_dspaudio.o     SDL_mixer_MMX_VC.o   SDL_thread.lo       Xv.o
SDL_dummyaudio.lo  SDL_mixer.o          SDL_thread.o
SDL_dummyaudio.o   SDL_mouse.lo         SDL_timer.lo
SDL_dummy_main.o   SDL_mouse.o          SDL_timer.o

```

  The README I cited earlier says to copy it from the src/.libs dir, but the .libs dir is non-existant for me.

---

### Post by mlind on 2006-08-21
Try like this
```

mkdir -p ~/tmp/libsdl
cd /tmp/libsdl
apt-get source libsdl1.2=1.2.9-0.0ubuntu2

#install all build dependencies, including **fakeroot**.
#you probably have those already installed.

cd libsdl1.2-1.2.9
fakeroot debian/rules install
cd debian/tmp/usr/lib
ls -la

```

You should find compiled libSDL-1.2.so.0.7.2, copy this to nwn/lib directory and correct libSDL-1.2.so.0 symlink to this new file.

You need to have Ubuntu **main** source repository enabled
```

deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

```

---

### Post by edm00se on 2006-08-21
Gave it a go. After installing the source, compiling, and copying over the newly made libSDL-1.2.so.0.7.2 and creating the sym link, ran the nwn script (made sure it pointed to the ./lib folder). It found the link, used it, did the setup thing. On the next run, same thing happened. Heard the *ding noise that the game makes when there are no movies, and went straight to the main menu.

  I did notice that it didn't give the "this might not work" error on the first run. So that's something at least. Any thoughts guys?

---

### Post by leech on 2006-08-22
Wait, so now that you have libsdl1.2debian-alsa and you have libsdl1.2-dev installed.  Try doing a fresh install of nwn.  Copy out your saves and your modules directory first, of course.  Then just remove the nwn folder and start fresh.

Also it could be that somewhere we're missing a SDL library.  

Leech

---

### Post by leech on 2006-08-22
My assumptions were correct.  You're missing a sdl library.  I installed nwn fresh on my somewhat fresh install of Debian unstable and while the nwmovies appeared to work, no movies were played (just like you said, it binged then went to the nwn main screen.)

What I did was installed wormux, which depended on several sdl libraries.  Not sure exactly which one (probably is in the nwmovies.log file actually) but it is one of libsdl-gfx1.2-4, libsdl-image1.2, libsdl-mixer1.2, libsdl-net1.2, libsdl-ttf2.0-0 and libsdl1.2debian.

You could just install wormux, or just ```
sudo apt-get install libsdl-gfx1.2-4 libsdl-mixer1.2
```

Let me know if that works (or even better, install them one at a time and let me know which one works so I can add it to the How To.)

Leech

Edit: Looks like it actually only needs the gfx and mixer libraries.

---

### Post by edm00se on 2006-08-23
I completly removed my installation of NWN and did a clean install. I made sure I had the libraries installed and went for another try. As strange as it is, I still get the same results. The game starts, it bings, and then I get the menu.

[EDIT]
I made sure I had the libraries installed by installing wormux.

---

### Post by edm00se on 2006-08-24
You said you've gotten this working? I really can't think of what would be left, at this point.

---

### Post by leech on 2006-08-24
Please post your nwmovies.log file, we'll see what we can come up with.

Leech

---

### Post by edm00se on 2006-08-24
```

eric@RabbitHole:/usr/local/games/nwn$ cat nwmovies.log
./nwmovies.pl AtariLogo >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: AtariLogo: Wed Aug 23 01:27:22 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/AtariLogo.bik
NOTICE: NWMovies.pl finished playing: AtariLogo: Wed Aug 23 01:27:22 2006
./nwmovies.pl BiowareLogo >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: BiowareLogo: Wed Aug 23 01:27:22 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/BiowareLogo.bik
NOTICE: NWMovies.pl finished playing: BiowareLogo: Wed Aug 23 01:27:22 2006
./nwmovies.pl WotcLogo >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: WotcLogo: Wed Aug 23 01:27:22 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/WOTCLogo.bik
NOTICE: NWMovies.pl finished playing: WotcLogo: Wed Aug 23 01:27:22 2006
./nwmovies.pl fge_logo_black >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: fge_logo_black: Wed Aug 23 01:27:22 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/fge_logo_black.bik
NOTICE: NWMovies.pl finished playing: fge_logo_black: Wed Aug 23 01:27:22 2006
./nwmovies.pl NWNIntro >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: NWNIntro: Wed Aug 23 01:27:22 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/NWNintro.bik
NOTICE: NWMovies.pl finished playing: NWNIntro: Wed Aug 23 01:27:22 2006
./nwmovies.pl Prelude >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: Prelude: Wed Aug 23 01:27:29 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/prelude.bik
NOTICE: NWMovies.pl finished playing: Prelude: Wed Aug 23 01:27:29 2006
./nwmovies.pl AtariLogo >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: AtariLogo: Wed Aug 23 01:28:33 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/AtariLogo.bik
NOTICE: NWMovies.pl finished playing: AtariLogo: Wed Aug 23 01:28:33 2006
./nwmovies.pl BiowareLogo >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: BiowareLogo: Wed Aug 23 01:28:33 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/BiowareLogo.bik
NOTICE: NWMovies.pl finished playing: BiowareLogo: Wed Aug 23 01:28:33 2006
./nwmovies.pl WotcLogo >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: WotcLogo: Wed Aug 23 01:28:33 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/WOTCLogo.bik
NOTICE: NWMovies.pl finished playing: WotcLogo: Wed Aug 23 01:28:33 2006
./nwmovies.pl fge_logo_black >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: fge_logo_black: Wed Aug 23 01:28:33 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/fge_logo_black.bik
NOTICE: NWMovies.pl finished playing: fge_logo_black: Wed Aug 23 01:28:33 2006
./nwmovies.pl NWNIntro >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: NWNIntro: Wed Aug 23 01:28:34 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/NWNintro.bik
NOTICE: NWMovies.pl finished playing: NWNIntro: Wed Aug 23 01:28:34 2006
./nwmovies.pl AtariLogo >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: AtariLogo: Wed Aug 23 01:29:37 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/AtariLogo.bik
NOTICE: NWMovies.pl finished playing: AtariLogo: Wed Aug 23 01:29:37 2006
./nwmovies.pl BiowareLogo >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: BiowareLogo: Wed Aug 23 01:29:37 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/BiowareLogo.bik
NOTICE: NWMovies.pl finished playing: BiowareLogo: Wed Aug 23 01:29:37 2006
./nwmovies.pl WotcLogo >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: WotcLogo: Wed Aug 23 01:29:37 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/WOTCLogo.bik
NOTICE: NWMovies.pl finished playing: WotcLogo: Wed Aug 23 01:29:37 2006
./nwmovies.pl fge_logo_black >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: fge_logo_black: Wed Aug 23 01:29:37 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/fge_logo_black.bik
NOTICE: NWMovies.pl finished playing: fge_logo_black: Wed Aug 23 01:29:37 2006
./nwmovies.pl NWNIntro >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: NWNIntro: Wed Aug 23 01:29:37 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/NWNintro.bik
NOTICE: NWMovies.pl finished playing: NWNIntro: Wed Aug 23 01:29:38 2006
./nwmovies.pl AtariLogo >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: AtariLogo: Wed Aug 23 23:58:31 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/AtariLogo.bik
NOTICE: NWMovies.pl finished playing: AtariLogo: Wed Aug 23 23:58:31 2006
./nwmovies.pl BiowareLogo >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: BiowareLogo: Wed Aug 23 23:58:31 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/BiowareLogo.bik
NOTICE: NWMovies.pl finished playing: BiowareLogo: Wed Aug 23 23:58:31 2006
./nwmovies.pl WotcLogo >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: WotcLogo: Wed Aug 23 23:58:31 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/WOTCLogo.bik
NOTICE: NWMovies.pl finished playing: WotcLogo: Wed Aug 23 23:58:31 2006
./nwmovies.pl fge_logo_black >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: fge_logo_black: Wed Aug 23 23:58:32 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/fge_logo_black.bik
NOTICE: NWMovies.pl finished playing: fge_logo_black: Wed Aug 23 23:58:32 2006
./nwmovies.pl NWNIntro >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: NWNIntro: Wed Aug 23 23:58:32 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/NWNintro.bik
NOTICE: NWMovies.pl finished playing: NWNIntro: Wed Aug 23 23:58:32 2006
./nwmovies.pl AtariLogo >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: AtariLogo: Thu Aug 24 00:39:48 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/AtariLogo.bik
NOTICE: NWMovies.pl finished playing: AtariLogo: Thu Aug 24 00:39:48 2006
./nwmovies.pl BiowareLogo >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: BiowareLogo: Thu Aug 24 00:39:48 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/BiowareLogo.bik
NOTICE: NWMovies.pl finished playing: BiowareLogo: Thu Aug 24 00:39:48 2006
./nwmovies.pl WotcLogo >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: WotcLogo: Thu Aug 24 00:39:48 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/WOTCLogo.bik
NOTICE: NWMovies.pl finished playing: WotcLogo: Thu Aug 24 00:39:49 2006
./nwmovies.pl fge_logo_black >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: fge_logo_black: Thu Aug 24 00:39:49 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/fge_logo_black.bik
NOTICE: NWMovies.pl finished playing: fge_logo_black: Thu Aug 24 00:39:49 2006
./nwmovies.pl NWNIntro >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: NWNIntro: Thu Aug 24 00:39:49 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/NWNintro.bik
NOTICE: NWMovies.pl finished playing: NWNIntro: Thu Aug 24 00:39:49 2006
./nwmovies.pl AtariLogo >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: AtariLogo: Thu Aug 24 00:40:40 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/AtariLogo.bik
NOTICE: NWMovies.pl finished playing: AtariLogo: Thu Aug 24 00:40:41 2006
./nwmovies.pl BiowareLogo >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: BiowareLogo: Thu Aug 24 00:40:41 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/BiowareLogo.bik
NOTICE: NWMovies.pl finished playing: BiowareLogo: Thu Aug 24 00:40:41 2006
./nwmovies.pl WotcLogo >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: WotcLogo: Thu Aug 24 00:40:41 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/WOTCLogo.bik
NOTICE: NWMovies.pl finished playing: WotcLogo: Thu Aug 24 00:40:41 2006
./nwmovies.pl fge_logo_black >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: fge_logo_black: Thu Aug 24 00:40:41 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/fge_logo_black.bik
NOTICE: NWMovies.pl finished playing: fge_logo_black: Thu Aug 24 00:40:41 2006
./nwmovies.pl NWNIntro >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: NWNIntro: Thu Aug 24 00:40:41 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/NWNintro.bik
NOTICE: NWMovies.pl finished playing: NWNIntro: Thu Aug 24 00:40:41 2006
./nwmovies.pl AtariLogo >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: AtariLogo: Thu Aug 24 11:11:03 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/AtariLogo.bik
NOTICE: NWMovies.pl finished playing: AtariLogo: Thu Aug 24 11:11:03 2006
./nwmovies.pl BiowareLogo >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: BiowareLogo: Thu Aug 24 11:11:03 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/BiowareLogo.bik
NOTICE: NWMovies.pl finished playing: BiowareLogo: Thu Aug 24 11:11:03 2006
./nwmovies.pl WotcLogo >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: WotcLogo: Thu Aug 24 11:11:03 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/WOTCLogo.bik
NOTICE: NWMovies.pl finished playing: WotcLogo: Thu Aug 24 11:11:03 2006
./nwmovies.pl fge_logo_black >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: fge_logo_black: Thu Aug 24 11:11:03 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/fge_logo_black.bik
NOTICE: NWMovies.pl finished playing: fge_logo_black: Thu Aug 24 11:11:03 2006
./nwmovies.pl NWNIntro >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: NWNIntro: Thu Aug 24 11:11:03 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/NWNintro.bik
NOTICE: NWMovies.pl finished playing: NWNIntro: Thu Aug 24 11:11:03 2006

```

It looks like it at least thinks it's actually playing them, though it doesn't do anything visually, just the bing and straight to menu.

---

### Post by leech on 2006-08-24
Interesting.  Yeah, the log looks fine.  Try this.

Go into your nwn directory and run ./BinkPlayer movies/AtariLogo.bik

Let's see if we can track down where the problem is.  Maybe it's BinkPlayer that is having the issues.  

Leech

---

### Post by edm00se on 2006-08-24
I was just about to post this, anywho, I am able to play movies by executing BinkPlayer from command line. I can get AtariLogo and all the other game videos to play.

---

### Post by leech on 2006-08-24
Did you end up using the libsdl from ubuntu or from nwn?

Leech

---

### Post by edm00se on 2006-08-24
I did some digging on the nwn.bioware.com site. Found [a thread]("http://nwn.bioware.com/forums/viewtopic.html?topic=490407&forum=72") which seemed very similar. I double checked and yes, I recently started getting the glibc errors after NWMovies initializes:

```

NOTICE: NWMovies: Initialized.
*** glibc detected *** double free or corruption (out): 0x080a13f8 ***
*** glibc detected *** double free or corruption (out): 0x080a13f8 ***
*** glibc detected *** double free or corruption (out): 0x080a13f8 ***
*** glibc detected *** double free or corruption (out): 0x080a13f8 ***
*** glibc detected *** double free or corruption (out): 0x080a13f8 ***

```

They suggested using the failsafe option in gdm(/kdm/xdm).

[EDIT]
The failsafe didn't work for me, either.

---

### Post by edm00se on 2006-08-24
> **leech said:**
> Did you end up using the libsdl from ubuntu or from nwn?

Leech

The one from ubuntu.

---

### Post by edm00se on 2006-08-24
Okay, I tried executing the following:

```

eric@RabbitHole:/usr/local/games/nwn$ nwmovies/nwmovies.pl movies/AtariLogo.bik NOTICE: NWMovies.pl playing: movies/AtariLogo.bik: Thu Aug 24 18:24:17 2006
ERROR: NWMovies.pl: Missing movie file: movies/AtariLogo.bik
NOTICE: NWMovies.pl finished playing: movies/AtariLogo.bik: Thu Aug 24 18:24:17 2006

```

Shouldn't that play the same (or close to it) as if I viewed a video straight through the BinkPlayer?

---

### Post by leech on 2006-08-24
Yeah, except for it should be 

nwmovies/nwmovies.pl ../movies

---

### Post by leech on 2006-08-24
Yeah, one would think so.  I just tried the same thing and it gave me the same error.  

Not sure why it's not working for you.  It's working fine on my end, following the same steps as I've set forth.  What we need is another person who has tried this and either failed or gotten it to work so we can see what is going wrong.

Leech

---

### Post by edm00se on 2006-08-24
> **leech said:**
> What we need is another person who has tried this and either failed or gotten it to work so we can see what is going wrong.

Leech

I can agree to that.

---

### Post by SpEcIeS on 2006-09-25
When I apply the movies I can only view them either with the BinkPlayer separatly or with NWN in windowed mode. When in windowed mode I cannot discontinue the video, such as the ATARI Logo, to continue. Also, the vidoes are played in a separate window, which holds the mouse hostage within the confines of the windowed NWN. If in Fullscreen mode nothing appears and I am left with a black screen. The cursor, which is hardware enabled, is also present.

Is this how videos play in linux for NWN? I must be missing something.

Other than the above, sound works with video and it seems to work well, using BinkPlayer.

---

### Post by edm00se on 2006-09-25
Sounds like you're in the same boat as myself. Leech, we got another one.

---

### Post by edm00se on 2006-09-28
It sounds like you're experiencing exactly the same syptoms I am with it.

---

### Post by benhall on 2006-10-19
Also having the same problems. Interestingly the problem might reside in Binklib.so, but I don't have a fix. You can watch movies using nwmovies.pl with 

> ./nwmovies.pl AtariLogo

Except that when I do it, all the colours are wrong (but the movie plays). If you remove (or comment out) the line

> $ENV{"LD_PRELOAD"} = $ENV{"LD_PRELOAD"} . ":./nwmovies/binklib.so"; 

then the above command plays the video normally, but in a window. Then running nwn gives movie sound, but no movie video (which is a little annoying).

---

### Post by MrBlond83 on 2006-10-19
My problem is different, after installing NWMovies, I can view movies in the game but they have no sound at all, and when starting the game the menu has no background music but has button click sounds. Funnily, inside the game the background music works fine, and if I go back from the game to the main menu the music works too.

When I view movies directly with Bink or with nwmovies.so, the sound works flawlessly. So it really just puzzles me. Of cours without NWMovies the main menu has background music and everything is normal.

Anyone has an idea on how to fix this?

---

### Post by edm00se on 2006-10-25
Talk about strange stuff. What kind of video card and driver are you guys using? I'm running a Radeon 5200 FX with NVIDIA's 8762 driver.

---

### Post by MrBlond83 on 2006-10-25
Radeon with NVIDIA driver? :/

---

### Post by SpEcIeS on 2006-10-25
> **edm00se said:**
> Talk about strange stuff. What kind of video card and driver are you guys using? I'm running a _Radeon 5200 FX_ with _NVIDIA's 8762_ driver.
Surely there is this is a typo. :confused: ATI card with NVIDIA drivers. <???> :D

---

### Post by edm00se on 2006-10-25
> **SpEcIeS said:**
> Surely there is this is a typo. :confused: ATI card with NVIDIA drivers. <???> :D

Holy quacamole. Can't believe I did that. It's a GeForce FX 5200. Wow, definitely not an ATI card.

---

### Post by Kashirigi on 2006-10-30
Well, you're not alone. I'm having the exact same problem. In case anyone's wondering, I have an nVidia N6800 card. And I'm using the dapper nVidia drivers. . .

---

### Post by tenshi-no-shi on 2007-03-08
I am having the same problem as well, annoys me to no end, I am going to try in failsafe mode now.

Edit: In failsafe mode it has the same problem, augh.

Edit #2: I got it to work with the dapper libSDL that someone posted earlier in this thread and using that to replace the one provided by bioware, but the sound is off, it keeps on cutting in and out, I think this is because it's for dapper and I am running edge. I have tried building the package myself based on the instructions from the nwmovies site, but with no luck, but that was the 1.2.11 version, I will try it with the 1.2.9 version and see if I can get it to work.

---

### Post by leech on 2007-04-11
I'm stuck in the same thing now, can't seem to get the movies to work on my laptop (they still work fine on my Desktop).  I also noticed on my laptop that if I leave ./lib in the nwn scripts path, that my sound is choppy, once I remove that it works.  On my Desktop system, if I remove the ./lib my movies stop working.

Talk about annoying.

Leech

---

### Post by Mazehero55 on 2007-05-23
um so is there any news on how to fix this yet???

I'm having the same thing only there's a few differences. And something really really odd.

in my log I get the error:

> can't create mcop directory


And for the thing really really odd. I tried to make a link once by right clicking on nwn and ran that and all the videos ran flawlessly but then the game had no sound whatsoever and was unbearably slow. But it was just that once and now I just get the *ding* at the begining still. Talk about confusing

---

