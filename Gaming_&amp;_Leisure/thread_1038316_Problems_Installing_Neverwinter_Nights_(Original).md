---
title: "Problems Installing Neverwinter Nights (Original)"
date: 2009-01-12
forum: Gaming &amp; Leisure
---

### Post by Phoenix2602 on 2009-01-12
I tried installing the Linux client of NWN (original, no expansions) today.  I followed BioWare's instructions and installed it using the resources downloaded from their site. Whenever I go to run it from terminal using ```
./nwn
``` from the installation directory my screen flashes black and I get the following in terminal:
```
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb6c83891]
#2 /usr/lib/libX11.so.6(_XReply+0x254) [0xb6dce494]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xb7d9853d]
#4 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x164) [0xb7d9378c]
#5 ./lib/libSDL-1.2.so.0 [0xb7d95457]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d8af66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7d6d7de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7d6d8dc]
#9 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7c1a685]
#11 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6c837c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb6c8396e]
#2 /usr/lib/libX11.so.6 [0xb6dcd619]
#3 /usr/lib/libX11.so.6(XMatchVisualInfo+0x40) [0xb6dc3530]
#4 ./lib/libSDL-1.2.so.0 [0xb7d9351a]
#5 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x408) [0xb7d93a30]
#6 ./lib/libSDL-1.2.so.0 [0xb7d95457]
#7 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d8af66]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb6c83891]
#2 /usr/lib/libX11.so.6(_XReply+0x254) [0xb6dce494]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xb7d9853d]
#4 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x164) [0xb7d9378c]
#5 ./lib/libSDL-1.2.so.0 [0xb7d95457]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d8af66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7d6d7de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7d6d8dc]
#9 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7c1a685]
#11 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6c837c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb6c8396e]
#2 /usr/lib/libX11.so.6 [0xb6dcd619]
#3 /usr/lib/libX11.so.6(XMatchVisualInfo+0x40) [0xb6dc3530]
#4 ./lib/libSDL-1.2.so.0 [0xb7d9351a]
#5 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x408) [0xb7d93a30]
#6 ./lib/libSDL-1.2.so.0 [0xb7d95457]
#7 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d8af66]
#8 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7d6d7de]
#9 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7d6d8dc]
#10 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#11 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7c1a685]
#12 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6c837c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb6c83891]
#2 /usr/lib/libX11.so.6(_XReply+0x254) [0xb6dce494]
#3 ./lib/libSDL-1.2.so.0(SDL_XineramaIsActive+0x76) [0xb7d9eb1a]
#4 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x673) [0xb7d93c9b]
#5 ./lib/libSDL-1.2.so.0 [0xb7d95457]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d8af66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7d6d7de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7d6d8dc]
#9 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7c1a685]
#11 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6c837c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb6c8396e]
#2 /usr/lib/libX11.so.6 [0xb6dcd619]
#3 /usr/lib/libX11.so.6(XCreateColormap+0x26) [0xb6da21d6]
#4 ./lib/libSDL-1.2.so.0 [0xb7d95584]
#5 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d8af66]
#6 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7d6d7de]
#7 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7d6d8dc]
#8 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#9 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7c1a685]
#10 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6c837c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb6c83891]
#2 /usr/lib/libX11.so.6(_XReply+0x254) [0xb6dce494]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeGetGamma+0x9a) [0xb7d9880e]
#4 ./lib/libSDL-1.2.so.0 [0xb7d91a89]
#5 ./lib/libSDL-1.2.so.0(X11_SaveVidModeGamma+0x36) [0xb7d91b3a]
#6 ./lib/libSDL-1.2.so.0 [0xb7d9560f]
#7 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d8af66]
#8 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7d6d7de]
#9 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7d6d8dc]
#10 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#11 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7c1a685]
#12 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6c837c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb6c8396e]
#2 /usr/lib/libX11.so.6 [0xb6dcd619]
#3 /usr/lib/libX11.so.6(XCreateWindow+0x26) [0xb6dc3bc6]
#4 ./lib/libSDL-1.2.so.0 [0xb7d94ff3]
#5 ./lib/libSDL-1.2.so.0 [0xb7d95635]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d8af66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7d6d7de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7d6d8dc]
#9 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7c1a685]
#11 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6c837c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb6c83891]
#2 /usr/lib/libX11.so.6(_XReply+0x254) [0xb6dce494]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xb7d9853d]
#4 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeGetModeLine+0x5b) [0xb7d988e7]
#5 ./lib/libSDL-1.2.so.0 [0xb7d93368]
#6 ./lib/libSDL-1.2.so.0(X11_EnterFullScreen+0x72) [0xb7d94092]
#7 ./lib/libSDL-1.2.so.0 [0xb7d96375]
#8 ./lib/libSDL-1.2.so.0 [0xb7d9652b]
#9 ./lib/libSDL-1.2.so.0(SDL_SetVideoMode+0x1b3) [0xb7d8b7df]
#10 ./nwmain [0x84d970d]
#11 ./nwmain(strftime+0x1dfd) [0x80508b5]
#12 ./nwmain [0x805d896]
#13 ./nwmain [0x805adc0]
#14 ./nwmain [0x8059ae5]
#15 ./nwmain(SDL_SetVideoMode+0x45f) [0x804fb57]
#16 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7c1a685]
#17 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6c837c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb6c8396e]
#2 /usr/lib/libX11.so.6 [0xb6dcd619]
#3 /usr/lib/libX11.so.6(XMoveResizeWindow+0x25) [0xb6da1435]
#4 ./lib/libSDL-1.2.so.0(X11_EnterFullScreen+0xd4) [0xb7d940f4]
#5 ./lib/libSDL-1.2.so.0 [0xb7d96375]
#6 ./lib/libSDL-1.2.so.0 [0xb7d9652b]
#7 ./lib/libSDL-1.2.so.0(SDL_SetVideoMode+0x1b3) [0xb7d8b7df]
#8 ./nwmain [0x84d970d]
#9 ./nwmain(strftime+0x1dfd) [0x80508b5]
#10 ./nwmain [0x805d896]
#11 ./nwmain [0x805adc0]
#12 ./nwmain [0x8059ae5]
#13 ./nwmain(SDL_SetVideoMode+0x45f) [0x804fb57]
#14 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7c1a685]
#15 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
nwmain: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
Aborted
#8 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7d6d7de]
#9 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7d6d8dc]
#10 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#11 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7c1a685]
#12 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6c837c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb6c83891]
#2 /usr/lib/libX11.so.6(_XReply+0x254) [0xb6dce494]
#3 ./lib/libSDL-1.2.so.0(SDL_XineramaIsActive+0x76) [0xb7d9eb1a]
#4 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x673) [0xb7d93c9b]
#5 ./lib/libSDL-1.2.so.0 [0xb7d95457]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d8af66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7d6d7de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7d6d8dc]
#9 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7c1a685]
#11 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6c837c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb6c8396e]
#2 /usr/lib/libX11.so.6 [0xb6dcd619]
#3 /usr/lib/libX11.so.6(XCreateColormap+0x26) [0xb6da21d6]
#4 ./lib/libSDL-1.2.so.0 [0xb7d95584]
#5 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d8af66]
#6 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7d6d7de]
#7 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7d6d8dc]
#8 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#9 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7c1a685]
#10 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6c837c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb6c83891]
#2 /usr/lib/libX11.so.6(_XReply+0x254) [0xb6dce494]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeGetGamma+0x9a) [0xb7d9880e]
#4 ./lib/libSDL-1.2.so.0 [0xb7d91a89]
#5 ./lib/libSDL-1.2.so.0(X11_SaveVidModeGamma+0x36) [0xb7d91b3a]
#6 ./lib/libSDL-1.2.so.0 [0xb7d9560f]
#7 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d8af66]
#8 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7d6d7de]
#9 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7d6d8dc]
#10 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#11 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7c1a685]
#12 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6c837c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb6c8396e]
#2 /usr/lib/libX11.so.6 [0xb6dcd619]
#3 /usr/lib/libX11.so.6(XCreateWindow+0x26) [0xb6dc3bc6]
#4 ./lib/libSDL-1.2.so.0 [0xb7d94ff3]
#5 ./lib/libSDL-1.2.so.0 [0xb7d95635]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d8af66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7d6d7de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7d6d8dc]
#9 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7c1a685]
#11 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6c837c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb6c83891]
#2 /usr/lib/libX11.so.6(_XReply+0x254) [0xb6dce494]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xb7d9853d]
#4 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeGetModeLine+0x5b) [0xb7d988e7]
#5 ./lib/libSDL-1.2.so.0 [0xb7d93368]
#6 ./lib/libSDL-1.2.so.0(X11_EnterFullScreen+0x72) [0xb7d94092]
#7 ./lib/libSDL-1.2.so.0 [0xb7d96375]
#8 ./lib/libSDL-1.2.so.0 [0xb7d9652b]
#9 ./lib/libSDL-1.2.so.0(SDL_SetVideoMode+0x1b3) [0xb7d8b7df]
#10 ./nwmain [0x84d970d]
#11 ./nwmain(strftime+0x1dfd) [0x80508b5]
#12 ./nwmain [0x805d896]
#13 ./nwmain [0x805adc0]
#14 ./nwmain [0x8059ae5]
#15 ./nwmain(SDL_SetVideoMode+0x45f) [0x804fb57]
#16 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7c1a685]
#17 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6c837c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb6c8396e]
#2 /usr/lib/libX11.so.6 [0xb6dcd619]
#3 /usr/lib/libX11.so.6(XMoveResizeWindow+0x25) [0xb6da1435]
#4 ./lib/libSDL-1.2.so.0(X11_EnterFullScreen+0xd4) [0xb7d940f4]
#5 ./lib/libSDL-1.2.so.0 [0xb7d96375]
#6 ./lib/libSDL-1.2.so.0 [0xb7d9652b]
#7 ./lib/libSDL-1.2.so.0(SDL_SetVideoMode+0x1b3) [0xb7d8b7df]
#8 ./nwmain [0x84d970d]
#9 ./nwmain(strftime+0x1dfd) [0x80508b5]
#10 ./nwmain [0x805d896]
#11 ./nwmain [0x805adc0]
#12 ./nwmain [0x8059ae5]
#13 ./nwmain(SDL_SetVideoMode+0x45f) [0x804fb57]
#14 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7c1a685]
#15 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
nwmain: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
Aborted
```

Can anyone help?

---

### Post by hikaricore on 2009-01-12
Easy fix:

> Open nwn (in the NWN folder) in a text editor and change:

Code:

export LD_LIBRARY_PATH=./lib:./miles:$LD_LIBRARY_PATH

to

Code:

export LD_LIBRARY_PATH=./miles:$LD_LIBRARY_PATH

*source - [http://www.linuxgrotto.com/2008/11/neverwinter-nights-diamond-on-xubuntu.html](http://www.linuxgrotto.com/2008/11/neverwinter-nights-diamond-on-xubuntu.html)*

---

### Post by Phoenix2602 on 2009-01-13
Thanks! It works perfectly now!

---

