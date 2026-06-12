---
title: "ut2004 demo"
date: 2009-03-30
forum: Gaming &amp; Leisure
---

### Post by wolfyking2 on 2009-03-30
I installed the ut2004 demo fine, and it seems like the game starts up good, it shows the little screen then goes to the black one.  But ti stays black.  I have an intel card (bad, I know!) but is there some way to configure the graphics without getting into the game?  Because I really wanna play this game!

---

### Post by wolfyking2 on 2009-03-30
nvm, got it working

---

### Post by wolfyking2 on 2009-03-31
darn, I uninstalled the demo, because of space, but then i realized i didn't need to, so i installed again, and when i run the script to run the game, the little box with all the advertisements comes up really quick and goes back down.  why is this?  I saw the output and i think it said it couldn't find game.game.gameengine or something, which makes me suspicous.  The installation went fine, so I don't see what's wrong!  (it was working the first time i installed it.

---

### Post by wingnux on 2009-03-31
Run it trough the terminal and post the output here, without this infe we can't help you.

---

### Post by wolfyking2 on 2009-03-31
heh, fixed it again, just had to delete some file from the hidden folders

---

### Post by wolfyking2 on 2009-06-03
Just downloaded the demo again, and gives me this error.

```
user@ubuntu:~$ '/home/user/ut2004demo/System/ut2004-bin' 



: 

Exiting due to error
user@ubuntu:~$ 

```

and this error when I use the script (last error I used ut2004-bin)

```
user@ubuntu:~$ '/home/user/ut2004demo/ut2004demo' 
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7be3767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7be38b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb7c341bd]
#3 ./libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xb7ea542d]
#4 ./libSDL-1.2.so.0(X11_GetVideoModes+0x170) [0xb7ea0428]
#5 ./libSDL-1.2.so.0 [0xb7ea2348]
#6 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7e97f96]
#7 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7e7a4fe]
#8 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7e7a5fc]
#9 ./ut2004-bin(main+0x507f) [0x8154a2f]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7cf1450]
#11 ./ut2004-bin(getlogin+0xad) [0x814b121]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7be3767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7be381e]
#2 /usr/lib/libX11.so.6 [0xb7c33518]
#3 /usr/lib/libX11.so.6(XQueryExtension+0x26) [0xb7c21fe6]
#4 /usr/lib/libX11.so.6(XInitExtension+0x3b) [0xb7c16d4b]
#5 /usr/lib/libXext.so.6(XextAddDisplay+0x53) [0xb7bf2443]
#6 ./libSDL-1.2.so.0 [0xb7eea0e5]
#7 ./libSDL-1.2.so.0(XiGMiscQueryVersion+0x14) [0xb7eea100]
#8 ./libSDL-1.2.so.0(X11_GetVideoModes+0x3b9) [0xb7ea0671]
#9 ./libSDL-1.2.so.0 [0xb7ea2348]
#10 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7e97f96]
#11 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7e7a4fe]
#12 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7e7a5fc]
#13 ./ut2004-bin(main+0x507f) [0x8154a2f]
#14 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7cf1450]
#15 ./ut2004-bin(getlogin+0xad) [0x814b121]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7be3767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7be38b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb7c341bd]
#3 ./libSDL-1.2.so.0(SDL_XineramaIsActive+0x76) [0xb7eaba0a]
#4 ./libSDL-1.2.so.0(X11_GetVideoModes+0x857) [0xb7ea0b0f]
#5 ./libSDL-1.2.so.0 [0xb7ea2348]
#6 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7e97f96]
#7 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7e7a4fe]
#8 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7e7a5fc]
#9 ./ut2004-bin(main+0x507f) [0x8154a2f]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7cf1450]
#11 ./ut2004-bin(getlogin+0xad) [0x814b121]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7be3767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7be381e]
#2 /usr/lib/libX11.so.6 [0xb7c33518]
#3 /usr/lib/libX11.so.6(XCreateColormap+0x26) [0xb7c09e76]
#4 ./libSDL-1.2.so.0 [0xb7ea2480]
#5 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7e97f96]
#6 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7e7a4fe]
#7 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7e7a5fc]
#8 ./ut2004-bin(main+0x507f) [0x8154a2f]
#9 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7cf1450]
#10 ./ut2004-bin(getlogin+0xad) [0x814b121]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7be3767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7be38b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb7c341bd]
#3 ./libSDL-1.2.so.0(SDL_XF86VidModeGetGamma+0x9a) [0xb7ea56fe]
#4 ./libSDL-1.2.so.0 [0xb7e9e609]
#5 ./libSDL-1.2.so.0(X11_SaveVidModeGamma+0x36) [0xb7e9e6ba]
#6 ./libSDL-1.2.so.0 [0xb7ea250b]
#7 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7e97f96]
#8 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7e7a4fe]
#9 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7e7a5fc]
#10 ./ut2004-bin(main+0x507f) [0x8154a2f]
#11 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7cf1450]
#12 ./ut2004-bin(getlogin+0xad) [0x814b121]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7be3767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7be381e]
#2 /usr/lib/libX11.so.6 [0xb7c33518]
#3 /usr/lib/libX11.so.6(XCreateWindow+0x26) [0xb7c2a616]
#4 ./libSDL-1.2.so.0 [0xb7ea1ee9]
#5 ./libSDL-1.2.so.0 [0xb7ea2531]
#6 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7e97f96]
#7 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7e7a4fe]
#8 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7e7a5fc]
#9 ./ut2004-bin(main+0x507f) [0x8154a2f]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7cf1450]
#11 ./ut2004-bin(getlogin+0xad) [0x814b121]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7be3767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7be38b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb7c341bd]
#3 ./libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xb7ea542d]
#4 ./libSDL-1.2.so.0(SDL_XF86VidModeGetModeLine+0x5b) [0xb7ea57d7]
#5 ./libSDL-1.2.so.0 [0xb7e9ffa8]
#6 ./libSDL-1.2.so.0(X11_EnterFullScreen+0x72) [0xb7ea0f02]
#7 ./libSDL-1.2.so.0 [0xb7ea31c2]
#8 ./libSDL-1.2.so.0 [0xb7ea341b]
#9 ./libSDL-1.2.so.0(SDL_SetVideoMode+0x1b3) [0xb7e9880f]
#10 ./ut2004-bin(ResizeViewport__12USDLViewportUiiii+0x179) [0x882ca39]
#11 ./ut2004-bin(SetRes__19UOpenGLRenderDeviceP9UViewportiiiii+0x202) [0x8832402]
#12 ./ut2004-bin(TryRenderDevice__12USDLViewportPCwiii+0x181) [0x882c655]
#13 ./ut2004-bin(OpenWindow__12USDLViewportUliiiii+0x1e6) [0x882b38a]
#14 ./ut2004-bin(Init__11UGameEngine+0x14b5) [0x8261ad5]
#15 ./ut2004-bin(__strtod_internal+0x4da6) [0x814f2fa]
#16 ./ut2004-bin(main+0x6019) [0x81559c9]
#17 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7cf1450]
#18 ./ut2004-bin(getlogin+0xad) [0x814b121]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7be3767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7be381e]
#2 /usr/lib/libX11.so.6 [0xb7c33518]
#3 /usr/lib/libX11.so.6(XMoveResizeWindow+0x25) [0xb7c09165]
#4 ./libSDL-1.2.so.0(X11_EnterFullScreen+0xca) [0xb7ea0f5a]
#5 ./libSDL-1.2.so.0 [0xb7ea31c2]
#6 ./libSDL-1.2.so.0 [0xb7ea341b]
#7 ./libSDL-1.2.so.0(SDL_SetVideoMode+0x1b3) [0xb7e9880f]
#8 ./ut2004-bin(ResizeViewport__12USDLViewportUiiii+0x179) [0x882ca39]
#9 ./ut2004-bin(SetRes__19UOpenGLRenderDeviceP9UViewportiiiii+0x202) [0x8832402]
#10 ./ut2004-bin(TryRenderDevice__12USDLViewportPCwiii+0x181) [0x882c655]
#11 ./ut2004-bin(OpenWindow__12USDLViewportUliiiii+0x1e6) [0x882b38a]
#12 ./ut2004-bin(Init__11UGameEngine+0x14b5) [0x8261ad5]
#13 ./ut2004-bin(__strtod_internal+0x4da6) [0x814f2fa]
#14 ./ut2004-bin(main+0x6019) [0x81559c9]
#15 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7cf1450]
#16 ./ut2004-bin(getlogin+0xad) [0x814b121]
ut2004-bin: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
Signal: SIGIOT [iot trap]
Aborting.


Crash information will be saved to your logfile.
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7be3767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7be381e]
#2 /usr/lib/libX11.so.6 [0xb7c33518]
#3 /usr/lib/libX11.so.6(XFreeCursor+0x25) [0xb7c0f8f5]
#4 ./libSDL-1.2.so.0(X11_FreeWMCursor+0x40) [0xb7ea1254]
#5 ./libSDL-1.2.so.0(SDL_FreeCursor+0x85) [0xb7e94435]
#6 ./libSDL-1.2.so.0(SDL_CursorQuit+0x63) [0xb7e93f87]
#7 ./libSDL-1.2.so.0(SDL_VideoQuit+0x43) [0xb7e998e3]
#8 ./libSDL-1.2.so.0(SDL_QuitSubSystem+0x8b) [0xb7e7a6b7]
#9 ./ut2004-bin [0x8829fa4]
#10 /lib/tls/i686/cmov/libc.so.6(exit+0xd4) [0xb7d09084]
#11 ./ut2004-bin [0x869e544]
#12 [0xb7f3e420]
#13 /lib/tls/i686/cmov/libc.so.6(abort+0x101) [0xb7d07a01]
#14 /lib/tls/i686/cmov/libc.so.6(__assert_fail+0xee) [0xb7cff10e]
#15 /usr/lib/libX11.so.6 [0xb7c33324]
#16 /usr/lib/libX11.so.6 [0xb7c334fd]
#17 /usr/lib/libX11.so.6(XWarpPointer+0x25) [0xb7c2a3e5]
#18 ./libSDL-1.2.so.0 [0xb7ea015f]
#19 ./libSDL-1.2.so.0(X11_ResizeFullScreen+0x67) [0xb7ea0d1f]
ut2004-bin: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
user@ubuntu:~$ 


```

---

### Post by caravel on 2009-06-04
Install the game as root, *but do not* run the game as root.  Delete the ~/.UT2004 directory again and try running the game again (open a new terminal first).

---

