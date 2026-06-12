---
title: "nwn movies in 9.10"
date: 2009-11-17
forum: Gaming &amp; Leisure
---

### Post by Naegling23 on 2009-11-17
I've been trying to get the movies to work in nwn, they used to work, way back in the day, but no longer.  
Anyway, if I had the comment in the nwn script to initialize the movies, the game wouldnt launch.  So I followed some of the latest guides on getting the movies working, downloaded the latest nwnmovies.  Long story short, I can launch the game, the movies tab is available, and I can click on any of the movies, but nothing happens when I do.

here is my terminal output if it helps shed some light on the situation:
pangolin@ubuntu:~/nwn$ ./nwn
NOTICE: NWMovies(./nwmain): Version: 20090223.080954
NOTICE: Looking up symbols in libSDL.....
NOTICE: NWMovies: using libSDL via direct dlopen()
NOTICE: SDL Library determined to be: ./lib/libSDL-1.2.so.0
NOTICE: NWMovies: SDL_WM_GrabInput() address: f7523900
NOTICE: NWMovies: SDL_GetVideoSurface() address: f7521048
NOTICE: NWMovies: SDL_WM_ToggleFullScreen() address: f75239e8
NOTICE: NWMovies: SDL_PollEvent() address: f753d51c
NOTICE: NWMovies: SDL_WM_IconifyWindow() address: f75239a8
NOTICE: NWMovies: Patch 0 Address: 0x08077a9d
NOTICE: NWMovies: Patch 1 Address: 0x08077ab1
NOTICE: NWMovies: Patch 2 Address: 0x0815b5f7
NOTICE: NWMovies: Patch 3 Address: 0x0815b611
NOTICE: NWMovies: Patch 4 Address: 0x0807796f
NOTICE: NWMovies: Patch 5 Address: 0x08207835
NOTICE: NWMovies: Patch 6 Address: 0x08207858
NOTICE: NWMovies: PrePatch0: 8b 80 78 02 00 00 5d c3 
NOTICE: NWMovies: PrePatch1: 8b 80 7c 02 00 00 5d c3 
NOTICE: NWMovies: PrePatch2: e8 68 c5 f1 ff 83 ec 08 
NOTICE: NWMovies: PrePatch3: 169+: eb 59 90 83 
NOTICE: NWMovies: PostPatch0: b8 00 00 00 00 90 5d c3 
NOTICE: NWMovies: PostPatch1: b8 00 00 00 00 90 5d c3 
NOTICE: NWMovies: PostPatch2: 90 90 90 90 90 83 ec 08 
NOTICE: NWMovies: PostPatch3: 169+: 90 90 90 83 
NOTICE: NWMovies: PrePatch4: 56 8d 5d e8 53 
NOTICE: NWMovies: PostPatch4: e9 20 64 6e ef 
NOTICE: NWMovies: MoviesPrePatch: 6a 00 53 bf 00 00 00 3f e8 72 4f 2a 00 8b 43 60 8b 10 c7 04 24 00 00 80 3f 57 57 57 50 ff 52 44 83 c4 1c 
NOTICE: NWMovies: MoviesPostPatch: 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 
NOTICE: NWMovies: Initialized.
NOTICE: SDL_WM_GrabInput(QUERY) called..
NOTICE: SDL_WM_GrabInput(OFF) called..
pangolin@ubuntu:~/nwn$ 

any help here?

---

