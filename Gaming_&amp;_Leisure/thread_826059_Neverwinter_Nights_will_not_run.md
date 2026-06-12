---
title: "Neverwinter Nights will not run"
date: 2008-06-11
forum: Gaming &amp; Leisure
---

### Post by Kymus on 2008-06-11
I followed the guide posted on the forum here, and everything did as it should and there were no problems. Of course, as luck would have it, when I clicked on the icon, nothing happened. I of course checked to make sure the path was right, and of course nothing happened again. So this time, I tried it in the terminal and here's the nonsense it spewed at me:

> kymus@Shouxing:~/nwn$ ./nwn
NOTICE: NWMovies: Version: 20080308.192336
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
NOTICE: NWMovies: PrePatch3: 168-: eb 58 83 ec 
NOTICE: NWMovies: PostPatch0: b8 00 00 00 00 90 5d c3 
NOTICE: NWMovies: PostPatch1: b8 00 00 00 00 90 5d c3 
NOTICE: NWMovies: PostPatch2: 90 90 90 90 90 83 ec 08 
NOTICE: NWMovies: PostPatch3: 168-: 90 90 83 ec 
NOTICE: NWMovies: PrePatch4: 56 8d 5d e8 53 
NOTICE: NWMovies: PostPatch4: e9 94 c8 ee af 
NOTICE: NWMovies: MoviesPrePatch: 6a 00 53 bf 00 00 00 3f e8 c2 f3 29 00 8b 43 60 8b 10 c7 04 24 00 00 80 3f 57 57 57 50 ff 52 44 83 c4 1c 
NOTICE: NWMovies: MoviesPostPatch: 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 
NOTICE: NWMovies: SDL_WM_GrabInput() address: b7d4f900
NOTICE: NWMovies: (Calculated) SDL_WM_GrabInputRaw() address: b7d4f864
NOTICE: NWMovies: Initialized.
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb79c8767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb79c88b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb7a0d1bd]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xb7d5a53d]
#4 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x164) [0xb7d5578c]
#5 ./lib/libSDL-1.2.so.0 [0xb7d57457]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d4cf66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7d2f7de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7d2f8dc]
#9 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7bea450]
#11 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb79c8767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb79c881e]
#2 /usr/lib/libX11.so.6 [0xb7a0c518]
#3 /usr/lib/libX11.so.6(XMatchVisualInfo+0x40) [0xb7a02f70]
#4 ./lib/libSDL-1.2.so.0 [0xb7d5551a]
#5 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x408) [0xb7d55a30]
#6 ./lib/libSDL-1.2.so.0 [0xb7d57457]
#7 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d4cf66]
#8 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7d2f7de]
#9 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7d2f8dc]
#10 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#11 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7bea450]
#12 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb79c8767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb79c88b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb7a0d1bd]
#3 ./lib/libSDL-1.2.so.0(SDL_XineramaIsActive+0x76) [0xb7d60b1a]
#4 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x673) [0xb7d55c9b]
#5 ./lib/libSDL-1.2.so.0 [0xb7d57457]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d4cf66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7d2f7de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7d2f8dc]
#9 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7bea450]
#11 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb79c8767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb79c881e]
#2 /usr/lib/libX11.so.6 [0xb7a0c518]
#3 /usr/lib/libX11.so.6(XCreateColormap+0x26) [0xb79e2e76]
#4 ./lib/libSDL-1.2.so.0 [0xb7d57584]
#5 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d4cf66]
#6 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7d2f7de]
#7 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7d2f8dc]
#8 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#9 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7bea450]
#10 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb79c8767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb79c88b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb7a0d1bd]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeGetGamma+0x9a) [0xb7d5a80e]
#4 ./lib/libSDL-1.2.so.0 [0xb7d53a89]
#5 ./lib/libSDL-1.2.so.0(X11_SaveVidModeGamma+0x36) [0xb7d53b3a]
#6 ./lib/libSDL-1.2.so.0 [0xb7d5760f]
#7 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d4cf66]
#8 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7d2f7de]
#9 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7d2f8dc]
#10 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#11 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7bea450]
#12 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb79c8767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb79c881e]
#2 /usr/lib/libX11.so.6 [0xb7a0c518]
#3 /usr/lib/libX11.so.6(XCreateWindow+0x26) [0xb7a03616]
#4 ./lib/libSDL-1.2.so.0 [0xb7d56ff3]
#5 ./lib/libSDL-1.2.so.0 [0xb7d57635]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d4cf66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7d2f7de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7d2f8dc]
#9 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7bea450]
#11 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
mcop warning: user defined signal handler found for SIG_PIPE, overriding
Failed to initialize graphics.
nwmain: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
./nwn: line 13: 27724 Aborted                 ./nwmain $@


>_<

---

### Post by eragon100 on 2008-06-11
All you have to do is remove the "libs" directory from the nwn folder. Then it will work. One mouseclick! :popcorn:

---

### Post by Kymus on 2008-06-11
I didn't see a "libs" folder, so I trashed the closest thing (lib). Unfortunately, it still stares at me >_<

---

### Post by eragon100 on 2008-06-11
output?

---

### Post by Kymus on 2008-06-11
1
> kymus@shouxing:~/nwn$ ./nwn
Notice: Nwmovies: Version: 20080308.192336
Notice: Sdl Library Determined To Be: /usr/lib/libsdl-1.2.so.0
Notice: Nwmovies: Patch 0 Address: 0x08076931
Notice: Nwmovies: Patch 1 Address: 0x08076945
Notice: Nwmovies: Patch 2 Address: 0x08159690
Notice: Nwmovies: Patch 3 Address: 0x081596aa
Notice: Nwmovies: Patch 4 Address: 0x08076803
Notice: Nwmovies: Patch 5 Address: 0x08204c55
Notice: Nwmovies: Patch 6 Address: 0x08204c78
Notice: Nwmovies: Prepatch0: 8b 80 48 02 00 00 5d C3 
Notice: Nwmovies: Prepatch1: 8b 80 4c 02 00 00 5d C3 
Notice: Nwmovies: Prepatch2: E8 63 D3 F1 Ff 83 Ec 08 
Notice: Nwmovies: Prepatch3: 168-: Eb 58 83 Ec 
Notice: Nwmovies: Postpatch0: B8 00 00 00 00 90 5d C3 
Notice: Nwmovies: Postpatch1: B8 00 00 00 00 90 5d C3 
Notice: Nwmovies: Postpatch2: 90 90 90 90 90 83 Ec 08 
Notice: Nwmovies: Postpatch3: 168-: 90 90 83 Ec 
Notice: Nwmovies: Prepatch4: 56 8d 5d E8 53 
Notice: Nwmovies: Postpatch4: E9 94 C8 F0 Af 
Notice: Nwmovies: Moviesprepatch: 6a 00 53 Bf 00 00 00 3f E8 C2 F3 29 00 8b 43 60 8b 10 C7 04 24 00 00 80 3f 57 57 57 50 Ff 52 44 83 C4 1c 
Notice: Nwmovies: Moviespostpatch: 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 
Notice: Nwmovies: Sdl_wm_grabinput() Address: B7d55460
Notice: Nwmovies: (calculated) Sdl_wm_grabinputraw() Address: B7d553a0
Notice: Nwmovies: Initialized.
Failed To Initialize Graphics.
./nwn: Line 13:  4899 Segmentation Fault      ./nwmain $@


---

### Post by eragon100 on 2008-06-11
video card?

---

### Post by Kymus on 2008-06-11
ATI Radeon X800 GTO

(as a side note, it seems - from what little I can translate into english there - that it's failing when it's doing something with the movies..... would it possibly make any difference if I "disable" said movies? Would this be a potential easy answer? I dun need 'em)

---

### Post by eragon100 on 2008-06-11
Might be, since the linux version simply DOESN'T HAVE movies, that's why you can read the text somewhere (I forgot where that was) It can't load something that isn't there :lolflag: !

A problem with the movies would be strange with this message it shows tough: "Notice: Nwmovies: Initialized."

Also, do you have the propietary radeon drivers installed?

(and don't you have 60 $ or something for an equally old GeForce, I have a GeForce and it works perfectly, only had to remove the libs folder :popcorn:)

---

### Post by Kymus on 2008-06-11
Well, my recolection isn't fantastic, but, i remember the setup tutorial talking about keeping the movies or letting go of them. Even though I finished the single player campaign... a long time ago, genius me figured "eh, why not just keep them there?" "yanno, just incase?".... How the heck would I go about getting rid of them?

I do have the propriatery drivers installed, yes, but unfortunately, I don't have any cash for a new/different card >_<

---

### Post by eragon100 on 2008-06-11
There are no movies in the linux version, did you install from a windows install? If so, just follow the tutorial on the nwn site for a clean linux installation and see if that works :).

Anyway, I am of to bed, I will check back tomorrow :)

---

### Post by Kymus on 2008-06-11
thanks a lot, I'll try it and report back :)

---

### Post by Kymus on 2008-06-12
a bit of a stall here. I tried looking for Bioware's answer (as you said, eragon), but I had trouble locating it. I found [the original how-to I followed before]("http://ubuntuforums.org/showthread.php?t=113259"). Should I just delete the nwn directory and follow the steps again sans the "NWN with movies" directions?

---

### Post by eragon100 on 2008-06-12
here are the instructions on the bioware website to download everything from the internet and do a clean install (you will need to make a free bioware account, but it doesn't hurt or spam :)) :

[http://nwn.bioware.com/downloads/linuxclient.html]("http://nwn.bioware.com/downloads/linuxclient.html")

Delete the nwn folder, and follow those instructions. When finished, look in the nwn direcory you got now and delete the folder "lib" or "libs"
Then, just run the "nwn" script. It will ask you for a cd-key upon launch, and then you'll be in the main menu and be able to start playing. You won't have movies this way, but it should work :)

---

### Post by Kymus on 2008-06-12
will do; I'll post when I take care of it (hopefully tonight)

---

### Post by Sleaka J on 2008-06-12
Here's a question:

Is there a /texturepacks directory in your Linux nwn directory? Mine didn't install a /texurepacks directory and I think that's what caused the Seg Fault.

---

### Post by Kymus on 2008-06-13
some folks have all the luck.... ugh.

after running ./fixinstall, is seems that I am missing patch.key. I didn't see it in my windows NWN directory (and a search won't produce it either)... the closest I've got is xp2patch.key.

---

### Post by Kymus on 2008-06-13
> **Sleaka J said:**
> Here's a question:

Is there a /texturepacks directory in your Linux nwn directory? Mine didn't install a /texurepacks directory and I think that's what caused the Seg Fault.

Yep, I've got it

---

### Post by eragon100 on 2008-06-13
I didn't run fixinstall when I did a clean install, why did you run it. Is it in the instructions? Anyway, I didn't, and it works fine :)

---

### Post by Kymus on 2008-06-13
here's what nonsense I'm getting this time:

> kymus@Shouxing:~/nwn$ ./nwn
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb79a0767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb79a08b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb79e61bd]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xb7d1e53d]
#4 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x164) [0xb7d1978c]
#5 ./lib/libSDL-1.2.so.0 [0xb7d1b457]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d10f66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7cf37de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7cf38dc]
#9 ./nwmain(SDL_SetVideoMode+0x28d) [0x804f98d]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7baf450]
#11 ./nwmain(AIL_WAV_info+0x31) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb79a0767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb79a081e]
#2 /usr/lib/libX11.so.6 [0xb79e5518]
#3 /usr/lib/libX11.so.6(XMatchVisualInfo+0x40) [0xb79dbf70]
#4 ./lib/libSDL-1.2.so.0 [0xb7d1951a]
#5 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x408) [0xb7d19a30]
#6 ./lib/libSDL-1.2.so.0 [0xb7d1b457]
#7 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d10f66]
#8 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7cf37de]
#9 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7cf38dc]
#10 ./nwmain(SDL_SetVideoMode+0x28d) [0x804f98d]
#11 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7baf450]
#12 ./nwmain(AIL_WAV_info+0x31) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb79a0767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb79a08b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb79e61bd]
#3 ./lib/libSDL-1.2.so.0(SDL_XineramaIsActive+0x76) [0xb7d24b1a]
#4 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x673) [0xb7d19c9b]
#5 ./lib/libSDL-1.2.so.0 [0xb7d1b457]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d10f66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7cf37de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7cf38dc]
#9 ./nwmain(SDL_SetVideoMode+0x28d) [0x804f98d]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7baf450]
#11 ./nwmain(AIL_WAV_info+0x31) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb79a0767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb79a081e]
#2 /usr/lib/libX11.so.6 [0xb79e5518]
#3 /usr/lib/libX11.so.6(XCreateColormap+0x26) [0xb79bbe76]
#4 ./lib/libSDL-1.2.so.0 [0xb7d1b584]
#5 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d10f66]
#6 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7cf37de]
#7 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7cf38dc]
#8 ./nwmain(SDL_SetVideoMode+0x28d) [0x804f98d]
#9 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7baf450]
#10 ./nwmain(AIL_WAV_info+0x31) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb79a0767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb79a08b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb79e61bd]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeGetGamma+0x9a) [0xb7d1e80e]
#4 ./lib/libSDL-1.2.so.0 [0xb7d17a89]
#5 ./lib/libSDL-1.2.so.0(X11_SaveVidModeGamma+0x36) [0xb7d17b3a]
#6 ./lib/libSDL-1.2.so.0 [0xb7d1b60f]
#7 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d10f66]
#8 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7cf37de]
#9 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7cf38dc]
#10 ./nwmain(SDL_SetVideoMode+0x28d) [0x804f98d]
#11 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7baf450]
#12 ./nwmain(AIL_WAV_info+0x31) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb79a0767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb79a081e]
#2 /usr/lib/libX11.so.6 [0xb79e5518]
#3 /usr/lib/libX11.so.6(XCreateWindow+0x26) [0xb79dc616]
#4 ./lib/libSDL-1.2.so.0 [0xb7d1aff3]
#5 ./lib/libSDL-1.2.so.0 [0xb7d1b635]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d10f66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7cf37de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7cf38dc]
#9 ./nwmain(SDL_SetVideoMode+0x28d) [0x804f98d]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7baf450]
#11 ./nwmain(AIL_WAV_info+0x31) [0x804f851]
mcop warning: user defined signal handler found for SIG_PIPE, overriding
Error
nwmain: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
./nwn: line 12:  3151 Aborted                 ./nwmain $@


---

### Post by Sleaka J on 2008-06-13
I had trouble installing NWN until I followed the instructions from [http://nwn.bioware.com/downloads/linuxclient.html](http://nwn.bioware.com/downloads/linuxclient.html) under the part "Installing From An Existing Windows Install" (I installed NWN, XP1 and XP2 under Wine and copied over those directories). That way, you don't get the /lib folder.

I also ran the ./fixinstall and was also missing the patch.key file, but as that only applies to the original install with no expansion and it doesn't make any difference as it ran after I unzipped the 1.68 patch.

Did you start off with a clean directory? You shouldn't have /lib folder errors after installing it that way.

---

### Post by Kymus on 2008-06-13
I deleted the previous NWN folder, then followed Bioware's directions exactly (copied said files and folders, pasted, downloaded the two items, extracted them). 

I deleted the lib folder, and this is what I get now:

> kymus@Shouxing:~/nwn$ ./nwn
Error
./nwn: line 12: 27310 Segmentation fault      ./nwmain $@


---

### Post by Sleaka J on 2008-06-13
Strangely enough, I got a Seg Fault until I used the Bioware "Previous Windows Installation" instructions.

Try installing NWN + XP1 + XP2 + Windows 1.68 patch via Wine and then coping over the files using the other "Windows" way (Saved me from downloading a 1+Gb file). That way worked for me.

---

### Post by Kymus on 2008-06-13
> **Sleaka J said:**
> Strangely enough, I got a Seg Fault until I used the Bioware "Previous Windows Installation" instructions.

Try installing NWN + XP1 + XP2 + Windows 1.68 patch via Wine and then coping over the files using the other "Windows" way (Saved me from downloading a 1+Gb file). That way worked for me.

Will do. May not have time to do it until Monday, but I'll post back here when I've tried it, regardless.

btw, dumb question: What do you mean by XP1 and XP2?

---

### Post by Sleaka J on 2008-06-13
XP1: Expansion Pack 1 - Shadows of Undrentide
XP2: Expansion Pack 2 - Hordes of the Underdark

Of course, you'll only be able to install them if you have them. And make sure you use the correct Windows patch from the Bioware site depending on which expansion packs you have (or not).

---

### Post by Kymus on 2008-06-13
gotcha :)

not a problem; I'm installing with platinum ;)

---

### Post by Sleaka J on 2008-06-13
Keep in mind there is also this thread:

[http://ubuntuforums.org/showthread.php?t=113259](http://ubuntuforums.org/showthread.php?t=113259)

...floating around that deals specifically with the Platinum edition, though I'm not sure how well it would work now (the initial post is a little outdated as it mentions 1.66 as the latest patch).

---

### Post by Kymus on 2008-06-19
Well, I tried installing NWN through wine and that didn't work; it basically locked up when I tried putting in Disc 2. My next step will be to use the tutorial located here on the forums that you linked to (which was the original method I used) except I'm gonna skip the part about the movies. Hopefully that will work.

---

### Post by Sleaka J on 2008-06-24
You can get the movies working using the following thread on the Bioware forums:

[http://nwn.bioware.com/forums/viewtopic.html?topic=629464&forum=72](http://nwn.bioware.com/forums/viewtopic.html?topic=629464&forum=72)

I have the movies working in my NWN installation. There are some little glitches though like the main menu music doesn't play upon first starting, once you've started a game and go back to the main menu, the music does play, but still plays if you view a movie.

---

### Post by Kymus on 2008-06-24
I seemed to have trouble getting the script to read my disc, so I went and tried yet another workaround: i borrowed my girlfriend's copy of diamond edition. The script didn't like the DVD, but this time WINE did! I copied the files over to my nwn folder and things run, it's just rather slow (and right now I'm trying to figure out why, though I think I know). I may poke at it more tomorrow to try to figure out what the current problem is.

---

### Post by Kymus on 2008-06-25
Today I installed things as per the bioware directions and I found that moving around in the menu is a bit faster, but in game, things are still horribly slow. I tried reducing the resolution to 800x600 and I also tried bumping the graphics down as low as they could possibly go and still there was no difference. I even closed Firefox, Skype, KTorrent, and desktop search (all that was running then was Yakuake, Pidgin, and Liferea), and still nothing. :confused::confused::confused:

---

### Post by pofigster on 2008-06-26
For the first problem posted about - there's a really easy fix.

Open the directory that you installed NWN in and open the file nwn (the one you run to play the game) in a text editor.

Find the line:
```
export LD_LIBRARY_PATH=./lib:./miles:$LD_LIBRARY_PATH
```
and delete the ./lib: part so that it looks like:
```
export LD_LIBRARY_PATH=./miles:$LD_LIBRARY_PATH
```

This will solve the problem instantly (as long as you have SDL installed which I know you do with 8.04).

Best of luck!

---

### Post by sir_cheats_a_lot on 2008-07-31
removing the ./lib line didn't work for me sadly.. just caused a segfault, which i didn't have before, along with the 
"Failed to initialize graphics."  message :(.
honestly feel better with all the gibberish  before it tells me it failed to initialize the graphics...I kinda like to have feedback with my errors *shrugs*

only going to give the bottom few lines here:
```
Xlib:  extension "GLX" missing on display ":0.0".
Failed to initialize graphics.
nwmain: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
Aborted

```
using a GeForce 7300GT 512mb agp card by the way.  got the same errors with my ATI Radeon 9200 as well.  kinda at a loss.

---

### Post by Yinepuhotep on 2008-08-15
> **eragon100 said:**
> All you have to do is remove the "libs" directory from the nwn folder. Then it will work. One mouseclick! :popcorn:


I tried that, and got a segfault whenever I try to load the game. :confused:

---

