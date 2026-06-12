---
title: "Unreal tournament 2004 Demo......."
date: 2009-01-27
forum: Gaming &amp; Leisure
---

### Post by RaiCoss on 2009-01-27
Ok, so I've installed the UT2004 demo, but when I click to play it brings up the splash screen then just disappears, anyone know how to fix this??:(

Heres the terminal output:

matt@matt-desktop:~$ /usr/local/games/ut2004demo/ut2004demo
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7cd57c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7cd5891]
#2 /usr/lib/libX11.so.6(_XReply+0x254) [0xb7d2a494]
#3 ./libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xb7fb142d]
#4 ./libSDL-1.2.so.0(X11_GetVideoModes+0x170) [0xb7fac428]
#5 ./libSDL-1.2.so.0 [0xb7fae348]
#6 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7fa3f96]
#7 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7f864fe]
#8 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7f865fc]
#9 ./ut2004-bin(main+0x507f) [0x8154a2f]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7ded685]
#11 ./ut2004-bin(getlogin+0xad) [0x814b121]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7cd57c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7cd596e]
#2 /usr/lib/libX11.so.6 [0xb7d29619]
#3 /usr/lib/libX11.so.6(XQueryExtension+0x26) [0xb7d17196]
#4 /usr/lib/libX11.so.6(XInitExtension+0x41) [0xb7d0b771]
#5 /usr/lib/libXext.so.6(XextAddDisplay+0x52) [0xb7ce5692]
#6 ./libSDL-1.2.so.0 [0xb7ff60e5]
#7 ./libSDL-1.2.so.0(XiGMiscQueryVersion+0x14) [0xb7ff6100]
#8 ./libSDL-1.2.so.0(X11_GetVideoModes+0x3b9) [0xb7fac671]
#9 ./libSDL-1.2.so.0 [0xb7fae348]
#10 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7fa3f96]
#11 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7f864fe]
#12 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7f865fc]
#13 ./ut2004-bin(main+0x507f) [0x8154a2f]
#14 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7ded685]
#15 ./ut2004-bin(getlogin+0xad) [0x814b121]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7cd57c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7cd5891]
#2 /usr/lib/libX11.so.6(_XReply+0x254) [0xb7d2a494]
#3 ./libSDL-1.2.so.0(SDL_XineramaIsActive+0x76) [0xb7fb7a0a]
#4 ./libSDL-1.2.so.0(X11_GetVideoModes+0x857) [0xb7facb0f]
#5 ./libSDL-1.2.so.0 [0xb7fae348]
#6 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7fa3f96]
#7 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7f864fe]
#8 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7f865fc]
#9 ./ut2004-bin(main+0x507f) [0x8154a2f]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7ded685]
#11 ./ut2004-bin(getlogin+0xad) [0x814b121]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7cd57c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7cd596e]
#2 /usr/lib/libX11.so.6 [0xb7d29619]
#3 /usr/lib/libX11.so.6(XCreateColormap+0x26) [0xb7cfe1d6]
#4 ./libSDL-1.2.so.0 [0xb7fae480]
#5 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7fa3f96]
#6 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7f864fe]
#7 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7f865fc]
#8 ./ut2004-bin(main+0x507f) [0x8154a2f]
#9 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7ded685]
#10 ./ut2004-bin(getlogin+0xad) [0x814b121]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7cd57c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7cd5891]
#2 /usr/lib/libX11.so.6(_XReply+0x254) [0xb7d2a494]
#3 ./libSDL-1.2.so.0(SDL_XF86VidModeGetGamma+0x9a) [0xb7fb16fe]
#4 ./libSDL-1.2.so.0 [0xb7faa609]
#5 ./libSDL-1.2.so.0(X11_SaveVidModeGamma+0x36) [0xb7faa6ba]
#6 ./libSDL-1.2.so.0 [0xb7fae50b]
#7 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7fa3f96]
#8 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7f864fe]
#9 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7f865fc]
#10 ./ut2004-bin(main+0x507f) [0x8154a2f]
#11 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7ded685]
#12 ./ut2004-bin(getlogin+0xad) [0x814b121]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7cd57c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7cd596e]
#2 /usr/lib/libX11.so.6 [0xb7d29619]
#3 /usr/lib/libX11.so.6(XCreateWindow+0x26) [0xb7d1fbc6]
#4 ./libSDL-1.2.so.0 [0xb7fadee9]
#5 ./libSDL-1.2.so.0 [0xb7fae531]
#6 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7fa3f96]
#7 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7f864fe]
#8 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7f865fc]
#9 ./ut2004-bin(main+0x507f) [0x8154a2f]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7ded685]
#11 ./ut2004-bin(getlogin+0xad) [0x814b121]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7cd57c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7cd5891]
#2 /usr/lib/libX11.so.6(_XReply+0x254) [0xb7d2a494]
#3 ./libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xb7fb142d]
#4 ./libSDL-1.2.so.0(SDL_XF86VidModeGetModeLine+0x5b) [0xb7fb17d7]
#5 ./libSDL-1.2.so.0 [0xb7fabfa8]
#6 ./libSDL-1.2.so.0(X11_EnterFullScreen+0x72) [0xb7facf02]
#7 ./libSDL-1.2.so.0 [0xb7faf1c2]
#8 ./libSDL-1.2.so.0 [0xb7faf41b]
#9 ./libSDL-1.2.so.0(SDL_SetVideoMode+0x1b3) [0xb7fa480f]
#10 ./ut2004-bin(ResizeViewport__12USDLViewportUiiii+0x179) [0x882ca39]
#11 ./ut2004-bin(SetRes__19UOpenGLRenderDeviceP9UViewportiiiii+0x202) [0x8832402]
#12 ./ut2004-bin(TryRenderDevice__12USDLViewportPCwiii+0x181) [0x882c655]
#13 ./ut2004-bin(OpenWindow__12USDLViewportUliiiii+0x1e6) [0x882b38a]
#14 ./ut2004-bin(Init__11UGameEngine+0x14b5) [0x8261ad5]
#15 ./ut2004-bin(__strtod_internal+0x4da6) [0x814f2fa]
#16 ./ut2004-bin(main+0x6019) [0x81559c9]
#17 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7ded685]
#18 ./ut2004-bin(getlogin+0xad) [0x814b121]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7cd57c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7cd596e]
#2 /usr/lib/libX11.so.6 [0xb7d29619]
#3 /usr/lib/libX11.so.6(XMoveResizeWindow+0x25) [0xb7cfd435]
#4 ./libSDL-1.2.so.0(X11_EnterFullScreen+0xca) [0xb7facf5a]
#5 ./libSDL-1.2.so.0 [0xb7faf1c2]
#6 ./libSDL-1.2.so.0 [0xb7faf41b]
#7 ./libSDL-1.2.so.0(SDL_SetVideoMode+0x1b3) [0xb7fa480f]
#8 ./ut2004-bin(ResizeViewport__12USDLViewportUiiii+0x179) [0x882ca39]
#9 ./ut2004-bin(SetRes__19UOpenGLRenderDeviceP9UViewportiiiii+0x202) [0x8832402]
#10 ./ut2004-bin(TryRenderDevice__12USDLViewportPCwiii+0x181) [0x882c655]
#11 ./ut2004-bin(OpenWindow__12USDLViewportUliiiii+0x1e6) [0x882b38a]
#12 ./ut2004-bin(Init__11UGameEngine+0x14b5) [0x8261ad5]
#13 ./ut2004-bin(__strtod_internal+0x4da6) [0x814f2fa]
#14 ./ut2004-bin(main+0x6019) [0x81559c9]
#15 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7ded685]
#16 ./ut2004-bin(getlogin+0xad) [0x814b121]
ut2004-bin: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
Signal: SIGIOT [iot trap]
Aborting.


Crash information will be saved to your logfile.
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7cd57c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7cd596e]
#2 /usr/lib/libX11.so.6 [0xb7d29619]
#3 /usr/lib/libX11.so.6(XFreeCursor+0x25) [0xb7d03f05]
#4 ./libSDL-1.2.so.0(X11_FreeWMCursor+0x40) [0xb7fad254]
#5 ./libSDL-1.2.so.0(SDL_FreeCursor+0x85) [0xb7fa0435]
#6 ./libSDL-1.2.so.0(SDL_CursorQuit+0x63) [0xb7f9ff87]
#7 ./libSDL-1.2.so.0(SDL_VideoQuit+0x43) [0xb7fa58e3]
#8 ./libSDL-1.2.so.0(SDL_QuitSubSystem+0x8b) [0xb7f866b7]
#9 ./ut2004-bin [0x8829fa4]
#10 /lib/tls/i686/cmov/libc.so.6(exit+0x89) [0xb7e05d69]
#11 ./ut2004-bin [0x869e544]
#12 [0xb8064400]
#13 /lib/tls/i686/cmov/libc.so.6(abort+0x188) [0xb7e04248]
#14 /lib/tls/i686/cmov/libc.so.6(__assert_fail+0xee) [0xb7dfb72e]
#15 /usr/lib/libX11.so.6 [0xb7d29424]
#16 /usr/lib/libX11.so.6 [0xb7d295fd]
#17 /usr/lib/libX11.so.6(XWarpPointer+0x25) [0xb7d1f9a5]
#18 ./libSDL-1.2.so.0 [0xb7fac15f]
#19 ./libSDL-1.2.so.0(X11_ResizeFullScreen+0x67) [0xb7facd1f]
ut2004-bin: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.


I'm using Ubuntu Intrepid 32bit, PC specs are as follows:~

2.0GHZ AMD Sempron 3600+
2GBDDR2@800MHZ
ASRock NF7G-FullHD 3.0 
XFX nVidia GeForce 8600GT 256MB
160GB Hitachi DataStar

Hope all of that helps!! :D

---

