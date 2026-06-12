---
title: "[SOLVED] neverwinter nights not working on hardy"
date: 2008-05-05
forum: Gaming &amp; Leisure
---

### Post by eragon100 on 2008-05-05
Hi guys!

I followed the normal install procedure:

1. download linux client resources (1.2 GB)

2. download linux client binaries (5.7 MB)

3. extract both

4. copy and paste the contents of the binaries folder into the resources folder, allowing all overwrites/merges etc.

5. double-click nwn in game folder and selecting run

Nothing happened. It worked perfectly this way in both feisty (ubuntu ultimate 1.4 gamers edition) and gutsy.

When I run it from the terminal I get:

eragon@Asgard:~/Desktop/games/nwn$ ./nwn
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6eb5767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb6eb58b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb6ffd1bd]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xb7d4f53d]
#4 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x164) [0xb7d4a78c]
#5 ./lib/libSDL-1.2.so.0 [0xb7d4c457]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d41f66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7d247de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7d248dc]
#9 ./nwmain(SDL_SetVideoMode+0x28d) [0x804f98d]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7be0450]
#11 ./nwmain(AIL_WAV_info+0x31) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6eb5767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb6eb581e]
#2 /usr/lib/libX11.so.6 [0xb6ffc518]
#3 /usr/lib/libX11.so.6(XMatchVisualInfo+0x40) [0xb6ff2f70]
#4 ./lib/libSDL-1.2.so.0 [0xb7d4a51a]
#5 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x408) [0xb7d4aa30]
#6 ./lib/libSDL-1.2.so.0 [0xb7d4c457]
#7 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d41f66]
#8 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7d247de]
#9 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7d248dc]
#10 ./nwmain(SDL_SetVideoMode+0x28d) [0x804f98d]
#11 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7be0450]
#12 ./nwmain(AIL_WAV_info+0x31) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6eb5767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb6eb58b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb6ffd1bd]
#3 ./lib/libSDL-1.2.so.0(SDL_XineramaIsActive+0x76) [0xb7d55b1a]
#4 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x673) [0xb7d4ac9b]
#5 ./lib/libSDL-1.2.so.0 [0xb7d4c457]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d41f66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7d247de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7d248dc]
#9 ./nwmain(SDL_SetVideoMode+0x28d) [0x804f98d]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7be0450]
#11 ./nwmain(AIL_WAV_info+0x31) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6eb5767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb6eb581e]
#2 /usr/lib/libX11.so.6 [0xb6ffc518]
#3 /usr/lib/libX11.so.6(XCreateColormap+0x26) [0xb6fd2e76]
#4 ./lib/libSDL-1.2.so.0 [0xb7d4c584]
#5 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d41f66]
#6 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7d247de]
#7 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7d248dc]
#8 ./nwmain(SDL_SetVideoMode+0x28d) [0x804f98d]
#9 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7be0450]
#10 ./nwmain(AIL_WAV_info+0x31) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6eb5767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb6eb58b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb6ffd1bd]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeGetGamma+0x9a) [0xb7d4f80e]
#4 ./lib/libSDL-1.2.so.0 [0xb7d48a89]
#5 ./lib/libSDL-1.2.so.0(X11_SaveVidModeGamma+0x36) [0xb7d48b3a]
#6 ./lib/libSDL-1.2.so.0 [0xb7d4c60f]
#7 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d41f66]
#8 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7d247de]
#9 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7d248dc]
#10 ./nwmain(SDL_SetVideoMode+0x28d) [0x804f98d]
#11 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7be0450]
#12 ./nwmain(AIL_WAV_info+0x31) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6eb5767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb6eb581e]
#2 /usr/lib/libX11.so.6 [0xb6ffc518]
#3 /usr/lib/libX11.so.6(XCreateWindow+0x26) [0xb6ff3616]
#4 ./lib/libSDL-1.2.so.0 [0xb7d4bff3]
#5 ./lib/libSDL-1.2.so.0 [0xb7d4c635]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d41f66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7d247de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7d248dc]
#9 ./nwmain(SDL_SetVideoMode+0x28d) [0x804f98d]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7be0450]
#11 ./nwmain(AIL_WAV_info+0x31) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6eb5767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb6eb58b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb6ffd1bd]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xb7d4f53d]
#4 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeGetModeLine+0x5b) [0xb7d4f8e7]
#5 ./lib/libSDL-1.2.so.0 [0xb7d4a368]
#6 ./lib/libSDL-1.2.so.0(X11_EnterFullScreen+0x72) [0xb7d4b092]
#7 ./lib/libSDL-1.2.so.0 [0xb7d4d375]
#8 ./lib/libSDL-1.2.so.0 [0xb7d4d52b]
#9 ./lib/libSDL-1.2.so.0(SDL_SetVideoMode+0x1b3) [0xb7d427df]
#10 ./nwmain [0x843733a]
#11 ./nwmain(strftime+0x1b55) [0x8050625]
#12 ./nwmain [0x805b20e]
#13 ./nwmain [0x8058d68]
#14 ./nwmain [0x8057cb4]
#15 ./nwmain(SDL_SetVideoMode+0x305) [0x804fa05]
#16 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7be0450]
#17 ./nwmain(AIL_WAV_info+0x31) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6eb5767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb6eb581e]
#2 /usr/lib/libX11.so.6 [0xb6ffc518]
#3 /usr/lib/libX11.so.6(XMoveResizeWindow+0x25) [0xb6fd2165]
#4 ./lib/libSDL-1.2.so.0(X11_EnterFullScreen+0xd4) [0xb7d4b0f4]
#5 ./lib/libSDL-1.2.so.0 [0xb7d4d375]
#6 ./lib/libSDL-1.2.so.0 [0xb7d4d52b]
#7 ./lib/libSDL-1.2.so.0(SDL_SetVideoMode+0x1b3) [0xb7d427df]
#8 ./nwmain [0x843733a]
#9 ./nwmain(strftime+0x1b55) [0x8050625]
#10 ./nwmain [0x805b20e]
#11 ./nwmain [0x8058d68]
#12 ./nwmain [0x8057cb4]
#13 ./nwmain(SDL_SetVideoMode+0x305) [0x804fa05]
#14 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7be0450]
#15 ./nwmain(AIL_WAV_info+0x31) [0x804f851]
nwmain: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
./nwn: line 12: 10363 Aborted                 ./nwmain $@
eragon@Asgard:~/Desktop/games/nwn$ 

WTF :confused::confused::(

Help :confused:

---

### Post by Perfect Storm on 2008-05-05
Open nwn with a text editor and change line 10 to;

**export LD_LIBRARY_PATH=:./miles:$LD_LIBRARY_PATH **

[http://gaming.gwos.org/doku.php/guides:64bit:nwn](http://gaming.gwos.org/doku.php/guides:64bit:nwn)

---

### Post by eragon100 on 2008-05-05
please mark as solved, I thought up it might have something to do with the libraries it ships and removed the lib folder from the nwn directory. Working perfectly :)

---

### Post by Spartnova on 2008-05-06
Worked for me too.  I had a working install of NWN on 7.10, but after upgrading to 8.04, NWN would not load.  I followed the instructions posted here and it now works fine!  Thanks!

---

### Post by oldrocker99 on 2008-06-18
> **Spartnova said:**
> Worked for me too.  I had a working install of NWN on 7.10, but after upgrading to 8.04, NWN would not load.  I followed the instructions posted here and it now works fine!  Thanks!

I changed the line, and this time a whole black screen came up for about 400 milliseconds, and quit. The terminal says it's a segmentation fault. Now what?

:guitar:

---

### Post by svenpikk on 2008-07-22
I installed neverwinter nights and followed every thing said above. But when I start it i see the videos and when it gets to main menu it closes and thats it...what should i do, i'm running Ubuntu Hardy Heron.

---

