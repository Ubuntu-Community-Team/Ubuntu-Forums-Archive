---
title: "ut2004 demo is crashing in ubuntu 8.04"
date: 2008-09-23
forum: Gaming &amp; Leisure
---

### Post by jakonj on 2008-09-23
Hello. I have ut2k4 demo (build 3120) and i played it a lot in ubuntu 7.10. However in 8.04 there are errors. I can see ut splash logo when i try to start game ant that is it. Game is installed in ~/programi/ut2004-demo

Here is the terminal output when i try to start ut2k4 demo:
```
krak@ubuntu: ut2004demo
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7bdc767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7bdc8b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb7c2c1bd]
#3 ./libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xb7e9e42d]
#4 ./libSDL-1.2.so.0(X11_GetVideoModes+0x170) [0xb7e99428]
#5 ./libSDL-1.2.so.0 [0xb7e9b348]
#6 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7e90f96]
#7 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7e734fe]
#8 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7e735fc]
#9 ./ut2004-bin(main+0x507f) [0x8154a2f]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7cea450]
#11 ./ut2004-bin(getlogin+0xad) [0x814b121]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7bdc767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7bdc81e]
#2 /usr/lib/libX11.so.6 [0xb7c2b518]
#3 /usr/lib/libX11.so.6(XQueryExtension+0x26) [0xb7c19fe6]
#4 /usr/lib/libX11.so.6(XInitExtension+0x3b) [0xb7c0ed4b]
#5 /usr/lib/libXext.so.6(XextAddDisplay+0x53) [0xb7bea443]
#6 ./libSDL-1.2.so.0 [0xb7ee30e5]
#7 ./libSDL-1.2.so.0(XiGMiscQueryVersion+0x14) [0xb7ee3100]
#8 ./libSDL-1.2.so.0(X11_GetVideoModes+0x3b9) [0xb7e99671]
#9 ./libSDL-1.2.so.0 [0xb7e9b348]
#10 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7e90f96]
#11 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7e734fe]
#12 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7e735fc]
#13 ./ut2004-bin(main+0x507f) [0x8154a2f]
#14 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7cea450]
#15 ./ut2004-bin(getlogin+0xad) [0x814b121]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7bdc767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7bdc8b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb7c2c1bd]
#3 ./libSDL-1.2.so.0(SDL_XineramaIsActive+0x76) [0xb7ea4a0a]
#4 ./libSDL-1.2.so.0(X11_GetVideoModes+0x857) [0xb7e99b0f]
#5 ./libSDL-1.2.so.0 [0xb7e9b348]
#6 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7e90f96]
#7 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7e734fe]
#8 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7e735fc]
#9 ./ut2004-bin(main+0x507f) [0x8154a2f]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7cea450]
#11 ./ut2004-bin(getlogin+0xad) [0x814b121]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7bdc767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7bdc81e]
#2 /usr/lib/libX11.so.6 [0xb7c2b518]
#3 /usr/lib/libX11.so.6(XCreateColormap+0x26) [0xb7c01e76]
#4 ./libSDL-1.2.so.0 [0xb7e9b480]
#5 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7e90f96]
#6 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7e734fe]
#7 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7e735fc]
#8 ./ut2004-bin(main+0x507f) [0x8154a2f]
#9 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7cea450]
#10 ./ut2004-bin(getlogin+0xad) [0x814b121]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7bdc767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7bdc8b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb7c2c1bd]
#3 ./libSDL-1.2.so.0(SDL_XF86VidModeGetGamma+0x9a) [0xb7e9e6fe]
#4 ./libSDL-1.2.so.0 [0xb7e97609]
#5 ./libSDL-1.2.so.0(X11_SaveVidModeGamma+0x36) [0xb7e976ba]
#6 ./libSDL-1.2.so.0 [0xb7e9b50b]
#7 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7e90f96]
#8 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7e734fe]
#9 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7e735fc]
#10 ./ut2004-bin(main+0x507f) [0x8154a2f]
#11 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7cea450]
#12 ./ut2004-bin(getlogin+0xad) [0x814b121]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7bdc767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7bdc81e]
#2 /usr/lib/libX11.so.6 [0xb7c2b518]
#3 /usr/lib/libX11.so.6(XCreateWindow+0x26) [0xb7c22616]
#4 ./libSDL-1.2.so.0 [0xb7e9aee9]
#5 ./libSDL-1.2.so.0 [0xb7e9b531]
#6 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7e90f96]
#7 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7e734fe]
#8 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7e735fc]
#9 ./ut2004-bin(main+0x507f) [0x8154a2f]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7cea450]
#11 ./ut2004-bin(getlogin+0xad) [0x814b121]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7bdc767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7bdc8b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb7c2c1bd]
#3 ./libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xb7e9e42d]
#4 ./libSDL-1.2.so.0(SDL_XF86VidModeGetModeLine+0x5b) [0xb7e9e7d7]
#5 ./libSDL-1.2.so.0 [0xb7e98fa8]
#6 ./libSDL-1.2.so.0(X11_EnterFullScreen+0x72) [0xb7e99f02]
#7 ./libSDL-1.2.so.0 [0xb7e9c1c2]
#8 ./libSDL-1.2.so.0 [0xb7e9c41b]
#9 ./libSDL-1.2.so.0(SDL_SetVideoMode+0x1b3) [0xb7e9180f]
#10 ./ut2004-bin(ResizeViewport__12USDLViewportUiiii+0x179) [0x882ca39]
#11 ./ut2004-bin(SetRes__19UOpenGLRenderDeviceP9UViewportiiiii+0x202) [0x8832402]
#12 ./ut2004-bin(TryRenderDevice__12USDLViewportPCwiii+0x181) [0x882c655]
#13 ./ut2004-bin(OpenWindow__12USDLViewportUliiiii+0x1e6) [0x882b38a]
#14 ./ut2004-bin(Init__11UGameEngine+0x14b5) [0x8261ad5]
#15 ./ut2004-bin(__strtod_internal+0x4da6) [0x814f2fa]
#16 ./ut2004-bin(main+0x6019) [0x81559c9]
#17 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7cea450]
#18 ./ut2004-bin(getlogin+0xad) [0x814b121]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7bdc767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7bdc81e]
#2 /usr/lib/libX11.so.6 [0xb7c2b518]
#3 /usr/lib/libX11.so.6(XMoveResizeWindow+0x25) [0xb7c01165]
#4 ./libSDL-1.2.so.0(X11_EnterFullScreen+0xca) [0xb7e99f5a]
#5 ./libSDL-1.2.so.0 [0xb7e9c1c2]
#6 ./libSDL-1.2.so.0 [0xb7e9c41b]
#7 ./libSDL-1.2.so.0(SDL_SetVideoMode+0x1b3) [0xb7e9180f]
#8 ./ut2004-bin(ResizeViewport__12USDLViewportUiiii+0x179) [0x882ca39]
#9 ./ut2004-bin(SetRes__19UOpenGLRenderDeviceP9UViewportiiiii+0x202) [0x8832402]
#10 ./ut2004-bin(TryRenderDevice__12USDLViewportPCwiii+0x181) [0x882c655]
#11 ./ut2004-bin(OpenWindow__12USDLViewportUliiiii+0x1e6) [0x882b38a]
#12 ./ut2004-bin(Init__11UGameEngine+0x14b5) [0x8261ad5]
#13 ./ut2004-bin(__strtod_internal+0x4da6) [0x814f2fa]
#14 ./ut2004-bin(main+0x6019) [0x81559c9]
#15 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7cea450]
#16 ./ut2004-bin(getlogin+0xad) [0x814b121]
ut2004-bin: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
Signal: SIGIOT [iot trap]
Aborting.


Crash information will be saved to your logfile.
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7bdc767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7bdc81e]
#2 /usr/lib/libX11.so.6 [0xb7c2b518]
#3 /usr/lib/libX11.so.6(XFreeCursor+0x25) [0xb7c078f5]
#4 ./libSDL-1.2.so.0(X11_FreeWMCursor+0x40) [0xb7e9a254]
#5 ./libSDL-1.2.so.0(SDL_FreeCursor+0x85) [0xb7e8d435]
#6 ./libSDL-1.2.so.0(SDL_CursorQuit+0x63) [0xb7e8cf87]
#7 ./libSDL-1.2.so.0(SDL_VideoQuit+0x43) [0xb7e928e3]
#8 ./libSDL-1.2.so.0(SDL_QuitSubSystem+0x8b) [0xb7e736b7]
#9 ./ut2004-bin [0x8829fa4]
#10 /lib/tls/i686/cmov/libc.so.6(exit+0xd4) [0xb7d02084]
#11 ./ut2004-bin [0x869e544]
#12 [0xb7f31420]
#13 /lib/tls/i686/cmov/libc.so.6(abort+0x101) [0xb7d00a01]
#14 /lib/tls/i686/cmov/libc.so.6(__assert_fail+0xee) [0xb7cf810e]
#15 /usr/lib/libX11.so.6 [0xb7c2b324]
#16 /usr/lib/libX11.so.6 [0xb7c2b4fd]
#17 /usr/lib/libX11.so.6(XWarpPointer+0x25) [0xb7c223e5]
#18 ./libSDL-1.2.so.0 [0xb7e9915f]
#19 ./libSDL-1.2.so.0(X11_ResizeFullScreen+0x67) [0xb7e99d1f]
ut2004-bin: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
krak@ubuntu: 

```

I have all sdl libs like i had on ubuntu 7.10 (mixer, net and libsdl1.2-debian-all). What could be the problem?

---

### Post by msskr on 2008-10-21
Im having the same problem however, on a previous install of Hardy I had no problem with this or any other games.  Locking Assertion Failure seems to be a huge problem with many things I get into lately.  Anyone have anything?!

---

### Post by lavinog on 2008-12-20
are the libSDL-1.2.so.0 libs in the ut2004/System folder symbolicly linked to the  /usr/lib/libSDL-1.2.so.0

---

### Post by chrishutt on 2009-01-02
Hi

Ive just got mine working by deleting libSDL-1.2.so.0 from the System directory (actually i renamed it but you could just delete it) so the game uses the system one instead.

---

