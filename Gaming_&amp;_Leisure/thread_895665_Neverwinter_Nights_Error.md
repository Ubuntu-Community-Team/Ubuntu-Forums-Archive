---
title: "Neverwinter Nights Error"
date: 2008-08-20
forum: Gaming &amp; Leisure
---

### Post by dennismoore1 on 2008-08-20
I followed the instructions on the Neverwinter Nights website.  Here is what my terminal looks like.

username@computer:~$ cd nwn
username@computer:~/nwn$ ./nwn
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb70e8767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb70e88b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb72301bd]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xb7cf353d]
#4 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x164) [0xb7cee78c]
#5 ./lib/libSDL-1.2.so.0 [0xb7cf0457]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7ce5f66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7cc87de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7cc88dc]
#9 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7b84450]
#11 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb70e8767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb70e881e]
#2 /usr/lib/libX11.so.6 [0xb722f518]
#3 /usr/lib/libX11.so.6(XMatchVisualInfo+0x40) [0xb7225f70]
#4 ./lib/libSDL-1.2.so.0 [0xb7cee51a]
#5 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x408) [0xb7ceea30]
#6 ./lib/libSDL-1.2.so.0 [0xb7cf0457]
#7 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7ce5f66]
#8 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7cc87de]
#9 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7cc88dc]
#10 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#11 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7b84450]
#12 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb70e8767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb70e88b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb72301bd]
#3 ./lib/libSDL-1.2.so.0(SDL_XineramaIsActive+0x76) [0xb7cf9b1a]
#4 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x673) [0xb7ceec9b]
#5 ./lib/libSDL-1.2.so.0 [0xb7cf0457]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7ce5f66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7cc87de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7cc88dc]
#9 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7b84450]
#11 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb70e8767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb70e881e]
#2 /usr/lib/libX11.so.6 [0xb722f518]
#3 /usr/lib/libX11.so.6(XCreateColormap+0x26) [0xb7205e76]
#4 ./lib/libSDL-1.2.so.0 [0xb7cf0584]
#5 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7ce5f66]
#6 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7cc87de]
#7 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7cc88dc]
#8 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#9 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7b84450]
#10 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb70e8767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb70e88b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb72301bd]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeGetGamma+0x9a) [0xb7cf380e]
#4 ./lib/libSDL-1.2.so.0 [0xb7ceca89]
#5 ./lib/libSDL-1.2.so.0(X11_SaveVidModeGamma+0x36) [0xb7cecb3a]
#6 ./lib/libSDL-1.2.so.0 [0xb7cf060f]
#7 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7ce5f66]
#8 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7cc87de]
#9 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7cc88dc]
#10 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#11 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7b84450]
#12 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb70e8767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb70e881e]
#2 /usr/lib/libX11.so.6 [0xb722f518]
#3 /usr/lib/libX11.so.6(XCreateWindow+0x26) [0xb7226616]
#4 ./lib/libSDL-1.2.so.0 [0xb7cefff3]
#5 ./lib/libSDL-1.2.so.0 [0xb7cf0635]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7ce5f66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7cc87de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7cc88dc]
#9 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7b84450]
#11 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb70e8767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb70e88b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb72301bd]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xb7cf353d]
#4 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeGetModeLine+0x5b) [0xb7cf38e7]
#5 ./lib/libSDL-1.2.so.0 [0xb7cee368]
#6 ./lib/libSDL-1.2.so.0(X11_EnterFullScreen+0x72) [0xb7cef092]
#7 ./lib/libSDL-1.2.so.0 [0xb7cf1375]
#8 ./lib/libSDL-1.2.so.0 [0xb7cf152b]
#9 ./lib/libSDL-1.2.so.0(SDL_SetVideoMode+0x1b3) [0xb7ce67df]
#10 ./nwmain [0x847e1da]
#11 ./nwmain(strftime+0x1de9) [0x80508a1]
#12 ./nwmain [0x805c3b3]
#13 ./nwmain [0x8059e24]
#14 ./nwmain [0x8058c1d]
#15 ./nwmain(SDL_SetVideoMode+0x45f) [0x804fb57]
#16 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7b84450]
#17 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb70e8767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb70e881e]
#2 /usr/lib/libX11.so.6 [0xb722f518]
#3 /usr/lib/libX11.so.6(XMoveResizeWindow+0x25) [0xb7205165]
#4 ./lib/libSDL-1.2.so.0(X11_EnterFullScreen+0xd4) [0xb7cef0f4]
#5 ./lib/libSDL-1.2.so.0 [0xb7cf1375]
#6 ./lib/libSDL-1.2.so.0 [0xb7cf152b]
#7 ./lib/libSDL-1.2.so.0(SDL_SetVideoMode+0x1b3) [0xb7ce67df]
#8 ./nwmain [0x847e1da]
#9 ./nwmain(strftime+0x1de9) [0x80508a1]
#10 ./nwmain [0x805c3b3]
#11 ./nwmain [0x8059e24]
#12 ./nwmain [0x8058c1d]
#13 ./nwmain(SDL_SetVideoMode+0x45f) [0x804fb57]
#14 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7b84450]
#15 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
nwmain: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
Aborted
username@computer:~/nwn$ 

What does all this nonsense mean?
Thanks in Advance.

---

### Post by eragon100 on 2008-08-20
It means you have to remove the lib (or libs, not sure about the s) folder from the nwn directory, then it should work :wink:

---

### Post by dennismoore1 on 2008-08-20
got thanks man it works perfetly!

---

### Post by eragon100 on 2008-08-20
you're welcome :popcorn:

---

