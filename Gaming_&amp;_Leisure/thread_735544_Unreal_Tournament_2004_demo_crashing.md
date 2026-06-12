---
title: "Unreal Tournament 2004 demo crashing"
date: 2008-03-25
forum: Gaming &amp; Leisure
---

### Post by itix on 2008-03-25
I am considering buying the Linux version of UT2004 since it is one of the very few online FPS's I really like (lucky me that someone at epic games ported it to Linux I thought). I had this idea to try out the demo to see how it worked on my computer before I bought the game and of course since it's my luck governing all of this, it crashed. The installation worked flawlessly, and was probably my first ever successful install via the terminal despite numerous previous attempts (terminal + installation + me = catastrophe). However, when I ran it, it crashed almost immediately. I have tried running it as root as well via the terminal and it lasted a couple of seconds longer before crashing, giving me this code:

```

Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7c35767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7c358b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb7c861bd]
#3 ./libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xb7ef742d]
#4 ./libSDL-1.2.so.0(X11_GetVideoModes+0x170) [0xb7ef2428]
#5 ./libSDL-1.2.so.0 [0xb7ef4348]
#6 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7ee9f96]
#7 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7ecc4fe]
#8 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7ecc5fc]
#9 ./ut2004-bin(main+0x507f) [0x8154a2f]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d43450]
#11 ./ut2004-bin(getlogin+0xad) [0x814b121]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7c35767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7c3581e]
#2 /usr/lib/libX11.so.6 [0xb7c85518]
#3 /usr/lib/libX11.so.6(XQueryExtension+0x26) [0xb7c73fe6]
#4 /usr/lib/libX11.so.6(XInitExtension+0x3b) [0xb7c68d4b]
#5 /usr/lib/libXext.so.6(XextAddDisplay+0x53) [0xb7c44443]
#6 ./libSDL-1.2.so.0 [0xb7f3c0e5]
#7 ./libSDL-1.2.so.0(XiGMiscQueryVersion+0x14) [0xb7f3c100]
#8 ./libSDL-1.2.so.0(X11_GetVideoModes+0x3b9) [0xb7ef2671]
#9 ./libSDL-1.2.so.0 [0xb7ef4348]
#10 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7ee9f96]
#11 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7ecc4fe]
#12 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7ecc5fc]
#13 ./ut2004-bin(main+0x507f) [0x8154a2f]
#14 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d43450]
#15 ./ut2004-bin(getlogin+0xad) [0x814b121]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7c35767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7c358b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb7c861bd]
#3 ./libSDL-1.2.so.0(SDL_XineramaIsActive+0x76) [0xb7efda0a]
#4 ./libSDL-1.2.so.0(X11_GetVideoModes+0x857) [0xb7ef2b0f]
#5 ./libSDL-1.2.so.0 [0xb7ef4348]
#6 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7ee9f96]
#7 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7ecc4fe]
#8 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7ecc5fc]
#9 ./ut2004-bin(main+0x507f) [0x8154a2f]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d43450]
#11 ./ut2004-bin(getlogin+0xad) [0x814b121]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7c35767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7c3581e]
#2 /usr/lib/libX11.so.6 [0xb7c85518]
#3 /usr/lib/libX11.so.6(XCreateColormap+0x26) [0xb7c5be76]
#4 ./libSDL-1.2.so.0 [0xb7ef4480]
#5 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7ee9f96]
#6 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7ecc4fe]
#7 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7ecc5fc]
#8 ./ut2004-bin(main+0x507f) [0x8154a2f]
#9 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d43450]
#10 ./ut2004-bin(getlogin+0xad) [0x814b121]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7c35767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7c358b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb7c861bd]
#3 ./libSDL-1.2.so.0(SDL_XF86VidModeGetGamma+0x9a) [0xb7ef76fe]
#4 ./libSDL-1.2.so.0 [0xb7ef0609]
#5 ./libSDL-1.2.so.0(X11_SaveVidModeGamma+0x36) [0xb7ef06ba]
#6 ./libSDL-1.2.so.0 [0xb7ef450b]
#7 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7ee9f96]
#8 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7ecc4fe]
#9 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7ecc5fc]
#10 ./ut2004-bin(main+0x507f) [0x8154a2f]
#11 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d43450]
#12 ./ut2004-bin(getlogin+0xad) [0x814b121]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7c35767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7c3581e]
#2 /usr/lib/libX11.so.6 [0xb7c85518]
#3 /usr/lib/libX11.so.6(XCreateWindow+0x26) [0xb7c7c616]
#4 ./libSDL-1.2.so.0 [0xb7ef3ee9]
#5 ./libSDL-1.2.so.0 [0xb7ef4531]
#6 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7ee9f96]
#7 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7ecc4fe]
#8 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7ecc5fc]
#9 ./ut2004-bin(main+0x507f) [0x8154a2f]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d43450]
#11 ./ut2004-bin(getlogin+0xad) [0x814b121]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7c35767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7c358b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb7c861bd]
#3 ./libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xb7ef742d]
#4 ./libSDL-1.2.so.0(SDL_XF86VidModeGetModeLine+0x5b) [0xb7ef77d7]
#5 ./libSDL-1.2.so.0 [0xb7ef1fa8]
#6 ./libSDL-1.2.so.0(X11_EnterFullScreen+0x72) [0xb7ef2f02]
#7 ./libSDL-1.2.so.0 [0xb7ef51c2]
#8 ./libSDL-1.2.so.0 [0xb7ef541b]
#9 ./libSDL-1.2.so.0(SDL_SetVideoMode+0x1b3) [0xb7eea80f]
#10 ./ut2004-bin(ResizeViewport__12USDLViewportUiiii+0x179) [0x882ca39]
#11 ./ut2004-bin(SetRes__19UOpenGLRenderDeviceP9UViewportiiiii+0x202) [0x8832402]
#12 ./ut2004-bin(TryRenderDevice__12USDLViewportPCwiii+0x181) [0x882c655]
#13 ./ut2004-bin(OpenWindow__12USDLViewportUliiiii+0x1e6) [0x882b38a]
#14 ./ut2004-bin(Init__11UGameEngine+0x14b5) [0x8261ad5]
#15 ./ut2004-bin(__strtod_internal+0x4da6) [0x814f2fa]
#16 ./ut2004-bin(main+0x6019) [0x81559c9]
#17 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d43450]
#18 ./ut2004-bin(getlogin+0xad) [0x814b121]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7c35767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7c3581e]
#2 /usr/lib/libX11.so.6 [0xb7c85518]
#3 /usr/lib/libX11.so.6(XMoveResizeWindow+0x25) [0xb7c5b165]
#4 ./libSDL-1.2.so.0(X11_EnterFullScreen+0xca) [0xb7ef2f5a]
#5 ./libSDL-1.2.so.0 [0xb7ef51c2]
#6 ./libSDL-1.2.so.0 [0xb7ef541b]
#7 ./libSDL-1.2.so.0(SDL_SetVideoMode+0x1b3) [0xb7eea80f]
#8 ./ut2004-bin(ResizeViewport__12USDLViewportUiiii+0x179) [0x882ca39]
#9 ./ut2004-bin(SetRes__19UOpenGLRenderDeviceP9UViewportiiiii+0x202) [0x8832402]
#10 ./ut2004-bin(TryRenderDevice__12USDLViewportPCwiii+0x181) [0x882c655]
#11 ./ut2004-bin(OpenWindow__12USDLViewportUliiiii+0x1e6) [0x882b38a]
#12 ./ut2004-bin(Init__11UGameEngine+0x14b5) [0x8261ad5]
#13 ./ut2004-bin(__strtod_internal+0x4da6) [0x814f2fa]
#14 ./ut2004-bin(main+0x6019) [0x81559c9]
#15 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d43450]
#16 ./ut2004-bin(getlogin+0xad) [0x814b121]
ut2004-bin: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
Signal: SIGIOT [iot trap]
Aborting.


Crash information will be saved to your logfile.
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7c35767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7c3581e]
#2 /usr/lib/libX11.so.6 [0xb7c85518]
#3 /usr/lib/libX11.so.6(XFreeCursor+0x25) [0xb7c618f5]
#4 ./libSDL-1.2.so.0(X11_FreeWMCursor+0x40) [0xb7ef3254]
#5 ./libSDL-1.2.so.0(SDL_FreeCursor+0x85) [0xb7ee6435]
#6 ./libSDL-1.2.so.0(SDL_CursorQuit+0x63) [0xb7ee5f87]
#7 ./libSDL-1.2.so.0(SDL_VideoQuit+0x43) [0xb7eeb8e3]
#8 ./libSDL-1.2.so.0(SDL_QuitSubSystem+0x8b) [0xb7ecc6b7]
#9 ./ut2004-bin [0x8829fa4]
#10 /lib/tls/i686/cmov/libc.so.6(exit+0xd4) [0xb7d5af74]
#11 ./ut2004-bin [0x869e544]
#12 [0xb7f8d420]
#13 /lib/tls/i686/cmov/libc.so.6(abort+0x101) [0xb7d598f1]
#14 /lib/tls/i686/cmov/libc.so.6(__assert_fail+0xee) [0xb7d510ee]
#15 /usr/lib/libX11.so.6 [0xb7c85324]
#16 /usr/lib/libX11.so.6 [0xb7c854fd]
#17 /usr/lib/libX11.so.6(XWarpPointer+0x25) [0xb7c7c3e5]
#18 ./libSDL-1.2.so.0 [0xb7ef215f]
#19 ./libSDL-1.2.so.0(X11_ResizeFullScreen+0x67) [0xb7ef2d1f]
ut2004-bin: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.

```

---

### Post by Lord Illidan on 2008-03-25
First of all, can you give us some more information about your system?

32 bit or 64 bit? ATi or Nvidia?

---

### Post by pieisgood4589 on 2008-03-25
After reading the code, your error is in this line-
```
Signal: SIGIOT [iot trap]
```

[http://www.unrealadmin.org/forums/showthread.php?t=12432](http://www.unrealadmin.org/forums/showthread.php?t=12432) <--That's a website for help on the issue. When all else fails, Google helps:popcorn:

---

### Post by itix on 2008-03-25
I should have thought of that.

ACER aspire 3610 with the following specs:
Processor: Intel Celeron M @ 1,5 ghz (single core)
GFX-card: Intel 910/915 chipset, and I think it has 128 mb memory.
1 gb RAM
soundcard unknown

It's definitely a 32 bit system since it started it's life running xp and too much ut2004 ;)

---

### Post by Lord Illidan on 2008-03-25
How are you starting Unreal Tournament? I remember on mine I had to go in the System folder.

```
cd ~/software/games/ut2004/System
./ut2004-bin
```

---

### Post by itix on 2008-03-26
Didn't help. It was the same procedure all over again.

I'm going to read through that massive thread *pieisgood4589* posted after eating breakfast.

I installed mine where It suggested that I should. Therefore I had to install it as root as well. Would this affect anything?
Mine is in _/usr/local/games/ut2004demo_

---

