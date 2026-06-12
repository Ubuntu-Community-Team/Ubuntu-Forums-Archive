---
title: "Game(s) start then immediately close"
date: 2008-05-31
forum: Gaming &amp; Leisure
---

### Post by oldrocker99 on 2008-05-31
I installed Pingus, and, when I start it, the window open and immediately closes.

I downloaded and installed the Neverwinter Nights Linux version, and the same thing happened, along with a long set of error messages:

ldrocker99@oldrocker99-desktop:~/My Games/nwn$ sudo ./nwn
[sudo] password for oldrocker99: 
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6e9b767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb6e9b8b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb6fe31bd]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xb7d3553d]
#4 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x164) [0xb7d3078c]
#5 ./lib/libSDL-1.2.so.0 [0xb7d32457]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d27f66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7d0a7de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7d0a8dc]
#9 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7bc6450]
#11 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6e9b767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb6e9b81e]
#2 /usr/lib/libX11.so.6 [0xb6fe2518]
#3 /usr/lib/libX11.so.6(XMatchVisualInfo+0x40) [0xb6fd8f70]
#4 ./lib/libSDL-1.2.so.0 [0xb7d3051a]
#5 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x408) [0xb7d30a30]
#6 ./lib/libSDL-1.2.so.0 [0xb7d32457]
#7 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d27f66]
#8 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7d0a7de]
#9 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7d0a8dc]
#10 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#11 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7bc6450]
#12 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6e9b767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb6e9b8b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb6fe31bd]
#3 ./lib/libSDL-1.2.so.0(SDL_XineramaIsActive+0x76) [0xb7d3bb1a]
#4 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x673) [0xb7d30c9b]
#5 ./lib/libSDL-1.2.so.0 [0xb7d32457]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d27f66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7d0a7de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7d0a8dc]
#9 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7bc6450]
#11 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6e9b767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb6e9b81e]
#2 /usr/lib/libX11.so.6 [0xb6fe2518]
#3 /usr/lib/libX11.so.6(XCreateColormap+0x26) [0xb6fb8e76]
#4 ./lib/libSDL-1.2.so.0 [0xb7d32584]
#5 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d27f66]
#6 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7d0a7de]
#7 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7d0a8dc]
#8 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#9 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7bc6450]
#10 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6e9b767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb6e9b8b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb6fe31bd]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeGetGamma+0x9a) [0xb7d3580e]
#4 ./lib/libSDL-1.2.so.0 [0xb7d2ea89]
#5 ./lib/libSDL-1.2.so.0(X11_SaveVidModeGamma+0x36) [0xb7d2eb3a]
#6 ./lib/libSDL-1.2.so.0 [0xb7d3260f]
#7 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d27f66]
#8 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7d0a7de]
#9 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7d0a8dc]
#10 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#11 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7bc6450]
#12 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6e9b767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb6e9b81e]
#2 /usr/lib/libX11.so.6 [0xb6fe2518]
#3 /usr/lib/libX11.so.6(XCreateWindow+0x26) [0xb6fd9616]
#4 ./lib/libSDL-1.2.so.0 [0xb7d31ff3]
#5 ./lib/libSDL-1.2.so.0 [0xb7d32635]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d27f66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7d0a7de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7d0a8dc]
#9 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7bc6450]
#11 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6e9b767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb6e9b8b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb6fe31bd]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xb7d3553d]
#4 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeGetModeLine+0x5b) [0xb7d358e7]
#5 ./lib/libSDL-1.2.so.0 [0xb7d30368]
#6 ./lib/libSDL-1.2.so.0(X11_EnterFullScreen+0x72) [0xb7d31092]
#7 ./lib/libSDL-1.2.so.0 [0xb7d33375]
#8 ./lib/libSDL-1.2.so.0 [0xb7d3352b]
#9 ./lib/libSDL-1.2.so.0(SDL_SetVideoMode+0x1b3) [0xb7d287df]
#10 ./nwmain [0x84d1b4d]
#11 ./nwmain(strftime+0x1dfd) [0x80508b5]
#12 ./nwmain [0x805d896]
#13 ./nwmain [0x805adc0]
#14 ./nwmain [0x8059ae5]
#15 ./nwmain(SDL_SetVideoMode+0x45f) [0x804fb57]
#16 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7bc6450]
#17 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6e9b767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb6e9b81e]
#2 /usr/lib/libX11.so.6 [0xb6fe2518]
#3 /usr/lib/libX11.so.6(XMoveResizeWindow+0x25) [0xb6fb8165]
#4 ./lib/libSDL-1.2.so.0(X11_EnterFullScreen+0xd4) [0xb7d310f4]
#5 ./lib/libSDL-1.2.so.0 [0xb7d33375]
#6 ./lib/libSDL-1.2.so.0 [0xb7d3352b]
#7 ./lib/libSDL-1.2.so.0(SDL_SetVideoMode+0x1b3) [0xb7d287df]
#8 ./nwmain [0x84d1b4d]
#9 ./nwmain(strftime+0x1dfd) [0x80508b5]
#10 ./nwmain [0x805d896]
#11 ./nwmain [0x805adc0]
#12 ./nwmain [0x8059ae5]
#13 ./nwmain(SDL_SetVideoMode+0x45f) [0x804fb57]
#14 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7bc6450]
#15 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
nwmain: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
Aborted


Anyone have any ideas about either of these?:confused:

---

