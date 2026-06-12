---
title: "UT-goty problem xlib.lock"
date: 2008-03-11
forum: Gaming &amp; Leisure
---

### Post by Dax0r on 2008-03-11
I have experienced this error with ut-goty:


> [OpenGL
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  42 (X_SetInputFocus)
  Serial number of failed request:  85
  Current serial number in output stream:  86
Signal: SIGSEGV [segmentation fault]
Aborting.
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb77f3767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb77f381e]
#2 /usr/lib/libX11.so.6 [0xb7845e08]
#3 /usr/lib/libX11.so.6(XFreeCursor+0x25) [0xb78228b5]
#4 ./libSDL-1.1.so.0(X11_FreeWMCursor+0x40) [0xb7a78944]
#5 ./libSDL-1.1.so.0(SDL_FreeCursor+0x7e) [0xb7a6d316]
#6 ./libSDL-1.1.so.0(SDL_CursorQuit+0x65) [0xb7a6ce89]
#7 ./libSDL-1.1.so.0(SDL_VideoQuit+0x43) [0xb7a720f3]
#8 ./libSDL-1.1.so.0(SDL_QuitSubSystem+0x8b) [0xb7a54a87]
#9 ./libSDL-1.1.so.0(SDL_Quit+0x1f) [0xb7a54ae3]
#10 ./Core.so(HandleSignal__9__Contexti+0xc9) [0xb7b82e01]
ut-bin: xcb_xlib.c:73: xcb_xlib_lock: Assertion `!c->xlib.lock' failed.


i have experienced the same error with java (azureus,ecc) and I fixed with 

# sed -i 's/XINERAMA/FAKEEXTN/g' /opt/java/jre/lib/i386/xawt/libmawt.so


I've tryed 
LIBXCB_ALLOW_SLOPPY_LOCK=true ut
with no results...

Any ideas???

---

