---
title: "[SOLVED] Problem with Neverwinter Nights game"
date: 2008-12-09
forum: Gaming &amp; Leisure
---

### Post by kinngg on 2008-12-09
So i followed the instructions 

Install Linux binaries.
      i) Dowload Linux NWN binaries, for links see 
         [http://nwn.bioware.com/downloads/linuxclient.html](http://nwn.bioware.com/downloads/linuxclient.html)
     ii) Extract the archive into your nwn directory
    iii) Run ./fixinstall from your nwn directory.

III) Download game resources:
   1) Download NWN 1.29 game resources
      See [http://nwn.bioware.com/downloads/linuxclient.html](http://nwn.bioware.com/downloads/linuxclient.html)

   2) Extract game resources to desired location.

   3) Download Linux NWN binaries and language files 
      See [http://nwn.bioware.com/downloads/linuxclient.html](http://nwn.bioware.com/downloads/linuxclient.html)

   4) Extract these archives into the nwn directory created in step (2)


To run Neverwinter Nights, run ./nwn or ./dmclient from your nwn directory 
to run the player client or DM client respectively.

But everytime i try to run ./nwn or ./dmclient it opens a window for a very short period like half a second before disappearing again. Whats the problem with this game?

---

### Post by kinngg on 2008-12-09
and when i run it in my terminal i get this message 


chilin@chilin-laptop:~/Desktop/nwn$ sudo ./nwn
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6d187c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb6d18891]
#2 /usr/lib/libX11.so.6(_XReply+0x254) [0xb6e63494]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xb7df653d]
#4 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x164) [0xb7df178c]
#5 ./lib/libSDL-1.2.so.0 [0xb7df3457]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7de8f66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7dcb7de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7dcb8dc]
#9 ./nwmain(SDL_SetVideoMode+0x28d) [0x804f98d]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7c78685]
#11 ./nwmain(AIL_WAV_info+0x31) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6d187c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb6d1896e]
#2 /usr/lib/libX11.so.6 [0xb6e62619]
#3 /usr/lib/libX11.so.6(XMatchVisualInfo+0x40) [0xb6e58530]
#4 ./lib/libSDL-1.2.so.0 [0xb7df151a]
#5 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x408) [0xb7df1a30]
#6 ./lib/libSDL-1.2.so.0 [0xb7df3457]
#7 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7de8f66]
#8 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7dcb7de]
#9 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7dcb8dc]
#10 ./nwmain(SDL_SetVideoMode+0x28d) [0x804f98d]
#11 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7c78685]
#12 ./nwmain(AIL_WAV_info+0x31) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6d187c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb6d18891]
#2 /usr/lib/libX11.so.6(_XReply+0x254) [0xb6e63494]
#3 ./lib/libSDL-1.2.so.0(SDL_XineramaIsActive+0x76) [0xb7dfcb1a]
#4 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x673) [0xb7df1c9b]
#5 ./lib/libSDL-1.2.so.0 [0xb7df3457]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7de8f66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7dcb7de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7dcb8dc]
#9 ./nwmain(SDL_SetVideoMode+0x28d) [0x804f98d]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7c78685]
#11 ./nwmain(AIL_WAV_info+0x31) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6d187c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb6d1896e]
#2 /usr/lib/libX11.so.6 [0xb6e62619]
#3 /usr/lib/libX11.so.6(XCreateColormap+0x26) [0xb6e371d6]
#4 ./lib/libSDL-1.2.so.0 [0xb7df3584]
#5 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7de8f66]
#6 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7dcb7de]
#7 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7dcb8dc]
#8 ./nwmain(SDL_SetVideoMode+0x28d) [0x804f98d]
#9 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7c78685]
#10 ./nwmain(AIL_WAV_info+0x31) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6d187c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb6d18891]
#2 /usr/lib/libX11.so.6(_XReply+0x254) [0xb6e63494]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeGetGamma+0x9a) [0xb7df680e]
#4 ./lib/libSDL-1.2.so.0 [0xb7defa89]
#5 ./lib/libSDL-1.2.so.0(X11_SaveVidModeGamma+0x36) [0xb7defb3a]
#6 ./lib/libSDL-1.2.so.0 [0xb7df360f]
#7 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7de8f66]
#8 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7dcb7de]
#9 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7dcb8dc]
#10 ./nwmain(SDL_SetVideoMode+0x28d) [0x804f98d]
#11 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7c78685]
#12 ./nwmain(AIL_WAV_info+0x31) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6d187c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb6d1896e]
#2 /usr/lib/libX11.so.6 [0xb6e62619]
#3 /usr/lib/libX11.so.6(XCreateWindow+0x26) [0xb6e58bc6]
#4 ./lib/libSDL-1.2.so.0 [0xb7df2ff3]
#5 ./lib/libSDL-1.2.so.0 [0xb7df3635]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7de8f66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7dcb7de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7dcb8dc]
#9 ./nwmain(SDL_SetVideoMode+0x28d) [0x804f98d]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7c78685]
#11 ./nwmain(AIL_WAV_info+0x31) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6d187c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb6d18891]
#2 /usr/lib/libX11.so.6(_XReply+0x254) [0xb6e63494]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xb7df653d]
#4 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeGetModeLine+0x5b) [0xb7df68e7]
#5 ./lib/libSDL-1.2.so.0 [0xb7df1368]
#6 ./lib/libSDL-1.2.so.0(X11_EnterFullScreen+0x72) [0xb7df2092]
#7 ./lib/libSDL-1.2.so.0 [0xb7df4375]
#8 ./lib/libSDL-1.2.so.0 [0xb7df452b]
#9 ./lib/libSDL-1.2.so.0(SDL_SetVideoMode+0x1b3) [0xb7de97df]
#10 ./nwmain [0x843733a]
#11 ./nwmain(strftime+0x1b55) [0x8050625]
#12 ./nwmain [0x805b20e]
#13 ./nwmain [0x8058d68]
#14 ./nwmain [0x8057cb4]
#15 ./nwmain(SDL_SetVideoMode+0x305) [0x804fa05]
#16 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7c78685]
#17 ./nwmain(AIL_WAV_info+0x31) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6d187c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb6d1896e]
#2 /usr/lib/libX11.so.6 [0xb6e62619]
#3 /usr/lib/libX11.so.6(XMoveResizeWindow+0x25) [0xb6e36435]
#4 ./lib/libSDL-1.2.so.0(X11_EnterFullScreen+0xd4) [0xb7df20f4]
#5 ./lib/libSDL-1.2.so.0 [0xb7df4375]
#6 ./lib/libSDL-1.2.so.0 [0xb7df452b]
#7 ./lib/libSDL-1.2.so.0(SDL_SetVideoMode+0x1b3) [0xb7de97df]
#8 ./nwmain [0x843733a]
#9 ./nwmain(strftime+0x1b55) [0x8050625]
#10 ./nwmain [0x805b20e]
#11 ./nwmain [0x8058d68]
#12 ./nwmain [0x8057cb4]
#13 ./nwmain(SDL_SetVideoMode+0x305) [0x804fa05]
#14 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7c78685]
#15 ./nwmain(AIL_WAV_info+0x31) [0x804f851]
nwmain: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
Aborted

---

### Post by Perfect Storm on 2008-12-09
Edit nwn file with a text editor.

Change line 10 so it looks like this:

export LD_LIBRARY_PATH=:./miles:$LD_LIBRARY_PATH

---

### Post by kinngg on 2008-12-09
Thank you so much it worked :)

---

