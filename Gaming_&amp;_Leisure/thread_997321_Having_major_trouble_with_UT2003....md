---
title: "Having major trouble with UT2003..."
date: 2008-11-29
forum: Gaming &amp; Leisure
---

### Post by xeriouxi on 2008-11-29
Hi!

I've been having a lot of problems in getting UT2003 to work and I was wondering if anyone could help me out.

I fixed the problem with the linux_installer.sh file and managed to install the game fine. However, it then came up asking for my CD-KEY and it always said that they weren't the same after entering them twice. I closed it and found out that I could create a file called 'cdkey' and put my key in there. I used the format xxxxx-xxxxx-xxxxx-xxxxx for it.

I tried to run the game using the command ut2003 and I got the splash screen but then it just quit back to my desktop. I tried also to use the loki_update tool but it failed to install the latest patch... and when I ran it as sudo ./loki_update then it just doesn't manage to connect to any servers.

I've ran out of ideas on how to get this working. I'm using Intrepid. Anyone able to lend a hand? ^^

Thanks!

---

### Post by xeriouxi on 2008-12-01
Bump! =)

---

### Post by eragon100 on 2008-12-01
Start UT2003 from within the terminal and post back any error messages, please :wink:

---

### Post by xeriouxi on 2008-12-01
Thanks for your reply, eragon100! =)

Here's the results from the terminal:

```
xeriouxi@xeriouxi-desktop:~$ ut2003
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb724f7c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb724f891]
#2 /usr/lib/libX11.so.6(_XReply+0x254) [0xb72d6494]
#3 ./libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xb7fcb42d]
#4 ./libSDL-1.2.so.0(X11_GetVideoModes+0x170) [0xb7fc6428]
#5 ./libSDL-1.2.so.0 [0xb7fc8348]
#6 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7fbdf96]
#7 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7fa04fe]
#8 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7fa05fc]
#9 ./ut2003-bin(ValidateCDKey__Fv+0x115) [0x80512bd]
#10 ./ut2003-bin(main+0x1fbc) [0x805778c]
#11 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb73c4685]
#12 ./ut2003-bin(ValidateCDKey__Fv+0x49) [0x80511f1]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb724f7c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb724f96e]
#2 /usr/lib/libX11.so.6 [0xb72d5619]
#3 /usr/lib/libX11.so.6(XQueryExtension+0x26) [0xb72c3196]
#4 /usr/lib/libX11.so.6(XInitExtension+0x41) [0xb72b7771]
#5 /usr/lib/libXext.so.6(XextAddDisplay+0x52) [0xb7291692]
#6 ./libSDL-1.2.so.0 [0xb80100e5]
#7 ./libSDL-1.2.so.0(XiGMiscQueryVersion+0x14) [0xb8010100]
#8 ./libSDL-1.2.so.0(X11_GetVideoModes+0x3b9) [0xb7fc6671]
#9 ./libSDL-1.2.so.0 [0xb7fc8348]
#10 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7fbdf96]
#11 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7fa04fe]
#12 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7fa05fc]
#13 ./ut2003-bin(ValidateCDKey__Fv+0x115) [0x80512bd]
#14 ./ut2003-bin(main+0x1fbc) [0x805778c]
#15 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb73c4685]
#16 ./ut2003-bin(ValidateCDKey__Fv+0x49) [0x80511f1]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb724f7c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb724f891]
#2 /usr/lib/libX11.so.6(_XReply+0x254) [0xb72d6494]
#3 ./libSDL-1.2.so.0(SDL_XineramaIsActive+0x76) [0xb7fd1a0a]
#4 ./libSDL-1.2.so.0(X11_GetVideoModes+0x857) [0xb7fc6b0f]
#5 ./libSDL-1.2.so.0 [0xb7fc8348]
#6 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7fbdf96]
#7 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7fa04fe]
#8 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7fa05fc]
#9 ./ut2003-bin(ValidateCDKey__Fv+0x115) [0x80512bd]
#10 ./ut2003-bin(main+0x1fbc) [0x805778c]
#11 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb73c4685]
#12 ./ut2003-bin(ValidateCDKey__Fv+0x49) [0x80511f1]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb724f7c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb724f96e]
#2 /usr/lib/libX11.so.6 [0xb72d5619]
#3 /usr/lib/libX11.so.6(XCreateColormap+0x26) [0xb72aa1d6]
#4 ./libSDL-1.2.so.0 [0xb7fc8480]
#5 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7fbdf96]
#6 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7fa04fe]
#7 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7fa05fc]
#8 ./ut2003-bin(ValidateCDKey__Fv+0x115) [0x80512bd]
#9 ./ut2003-bin(main+0x1fbc) [0x805778c]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb73c4685]
#11 ./ut2003-bin(ValidateCDKey__Fv+0x49) [0x80511f1]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb724f7c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb724f891]
#2 /usr/lib/libX11.so.6(_XReply+0x254) [0xb72d6494]
#3 ./libSDL-1.2.so.0(SDL_XF86VidModeGetGamma+0x9a) [0xb7fcb6fe]
#4 ./libSDL-1.2.so.0 [0xb7fc4609]
#5 ./libSDL-1.2.so.0(X11_SaveVidModeGamma+0x36) [0xb7fc46ba]
#6 ./libSDL-1.2.so.0 [0xb7fc850b]
#7 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7fbdf96]
#8 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7fa04fe]
#9 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7fa05fc]
#10 ./ut2003-bin(ValidateCDKey__Fv+0x115) [0x80512bd]
#11 ./ut2003-bin(main+0x1fbc) [0x805778c]
#12 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb73c4685]
#13 ./ut2003-bin(ValidateCDKey__Fv+0x49) [0x80511f1]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb724f7c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb724f96e]
#2 /usr/lib/libX11.so.6 [0xb72d5619]
#3 /usr/lib/libX11.so.6(XCreateWindow+0x26) [0xb72cbbc6]
#4 ./libSDL-1.2.so.0 [0xb7fc7ee9]
#5 ./libSDL-1.2.so.0 [0xb7fc8531]
#6 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7fbdf96]
#7 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7fa04fe]
#8 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7fa05fc]
#9 ./ut2003-bin(ValidateCDKey__Fv+0x115) [0x80512bd]
#10 ./ut2003-bin(main+0x1fbc) [0x805778c]
#11 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb73c4685]
#12 ./ut2003-bin(ValidateCDKey__Fv+0x49) [0x80511f1]
fcntl: Operation not permitted
fcntl: Operation not permitted
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb724f7c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb724f891]
#2 /usr/lib/libX11.so.6(_XReply+0x254) [0xb72d6494]
#3 ./libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xb7fcb42d]
#4 ./libSDL-1.2.so.0(SDL_XF86VidModeGetModeLine+0x5b) [0xb7fcb7d7]
#5 ./libSDL-1.2.so.0 [0xb7fc5fa8]
#6 ./libSDL-1.2.so.0(X11_EnterFullScreen+0x72) [0xb7fc6f02]
#7 ./libSDL-1.2.so.0 [0xb7fc91c2]
#8 ./libSDL-1.2.so.0 [0xb7fc941b]
#9 ./libSDL-1.2.so.0(SDL_SetVideoMode+0x1b3) [0xb7fbe80f]
#10 /usr/local/games/ut2003/System/SDLDrv.so(ResizeViewport__12USDLViewportUiiii+0x39a) [0xb69ddd8a]
#11 /usr/local/games/ut2003/System/OpenGLDrv.so(SetRes__19UOpenGLRenderDeviceP9UViewportiiiii+0x180) [0xb484e9c0]
#12 /usr/local/games/ut2003/System/SDLDrv.so(TryRenderDevice__12USDLViewportPCwiii+0x11e) [0xb69dd806]
#13 /usr/local/games/ut2003/System/SDLDrv.so(OpenWindow__12USDLViewportUiiiiii+0x223) [0xb69dc7d3]
#14 ./Engine.so(Init__11UGameEngine+0x1043) [0xb78ba753]
#15 ./ut2003-bin [0x805513e]
#16 ./ut2003-bin(main+0x296e) [0x805813e]
#17 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb73c4685]
#18 ./ut2003-bin(ValidateCDKey__Fv+0x49) [0x80511f1]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb724f7c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb724f96e]
#2 /usr/lib/libX11.so.6 [0xb72d5619]
#3 /usr/lib/libX11.so.6(XMoveResizeWindow+0x25) [0xb72a9435]
#4 ./libSDL-1.2.so.0(X11_EnterFullScreen+0xca) [0xb7fc6f5a]
#5 ./libSDL-1.2.so.0 [0xb7fc91c2]
#6 ./libSDL-1.2.so.0 [0xb7fc941b]
#7 ./libSDL-1.2.so.0(SDL_SetVideoMode+0x1b3) [0xb7fbe80f]
#8 /usr/local/games/ut2003/System/SDLDrv.so(ResizeViewport__12USDLViewportUiiii+0x39a) [0xb69ddd8a]
#9 /usr/local/games/ut2003/System/OpenGLDrv.so(SetRes__19UOpenGLRenderDeviceP9UViewportiiiii+0x180) [0xb484e9c0]
#10 /usr/local/games/ut2003/System/SDLDrv.so(TryRenderDevice__12USDLViewportPCwiii+0x11e) [0xb69dd806]
#11 /usr/local/games/ut2003/System/SDLDrv.so(OpenWindow__12USDLViewportUiiiiii+0x223) [0xb69dc7d3]
#12 ./Engine.so(Init__11UGameEngine+0x1043) [0xb78ba753]
#13 ./ut2003-bin [0x805513e]
#14 ./ut2003-bin(main+0x296e) [0x805813e]
#15 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb73c4685]
#16 ./ut2003-bin(ValidateCDKey__Fv+0x49) [0x80511f1]
ut2003-bin: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.

Backtrace:
[ 1]  ./Core.so [0xb7611c32]
[ 2]  [0xb804e400]
[ 3]  /lib/tls/i686/cmov/libc.so.6(abort+0x188) [0xb73db248]
[ 4]  /lib/tls/i686/cmov/libc.so.6(__assert_fail+0xee) [0xb73d272e]
[ 5]  /usr/lib/libX11.so.6 [0xb72d5424]
[ 6]  /usr/lib/libX11.so.6 [0xb72d55fd]
[ 7]  /usr/lib/libX11.so.6(XWarpPointer+0x25) [0xb72cb9a5]
[ 8]  ./libSDL-1.2.so.0 [0xb7fc615f]
[ 9]  ./libSDL-1.2.so.0(X11_ResizeFullScreen+0x67) [0xb7fc6d1f]
[10]  ./libSDL-1.2.so.0(X11_EnterFullScreen+0x155) [0xb7fc6fe5]
[11]  ./libSDL-1.2.so.0 [0xb7fc91c2]
[12]  ./libSDL-1.2.so.0 [0xb7fc941b]
[13]  ./libSDL-1.2.so.0(SDL_SetVideoMode+0x1b3) [0xb7fbe80f]
[14]  /usr/local/games/ut2003/System/SDLDrv.so(ResizeViewport__12USDLViewportUiiii+0x39a) [0xb69ddd8a]
[15]  /usr/local/games/ut2003/System/OpenGLDrv.so(SetRes__19UOpenGLRenderDeviceP9UViewportiiiii+0x180) [0xb484e9c0]
[16]  /usr/local/games/ut2003/System/SDLDrv.so(TryRenderDevice__12USDLViewportPCwiii+0x11e) [0xb69dd806]
[17]  /usr/local/games/ut2003/System/SDLDrv.so(OpenWindow__12USDLViewportUiiiiii+0x223) [0xb69dc7d3]
[18]  ./Engine.so(Init__11UGameEngine+0x1043) [0xb78ba753]
[19]  ./ut2003-bin [0x805513e]
[20]  ./ut2003-bin(main+0x296e) [0x805813e]
[21]  /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb73c4685]
[22]  ./ut2003-bin(ValidateCDKey__Fv+0x49) [0x80511f1]
Signal: SIGIOT [iot trap]
Aborting.
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb724f7c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb724f96e]
#2 /usr/lib/libX11.so.6 [0xb72d5619]
#3 /usr/lib/libX11.so.6(XFreeCursor+0x25) [0xb72aff05]
#4 ./libSDL-1.2.so.0(X11_FreeWMCursor+0x40) [0xb7fc7254]
#5 ./libSDL-1.2.so.0(SDL_FreeCursor+0x85) [0xb7fba435]
#6 ./libSDL-1.2.so.0(SDL_CursorQuit+0x63) [0xb7fb9f87]
#7 ./libSDL-1.2.so.0(SDL_VideoQuit+0x43) [0xb7fbf8e3]
#8 ./libSDL-1.2.so.0(SDL_QuitSubSystem+0x8b) [0xb7fa06b7]
#9 /usr/local/games/ut2003/System/SDLDrv.so [0xb69dacc0]
#10 /lib/tls/i686/cmov/libc.so.6(exit+0x89) [0xb73dcd69]
#11 ./Core.so [0xb7611cd8]
#12 [0xb804e400]
#13 /lib/tls/i686/cmov/libc.so.6(abort+0x188) [0xb73db248]
#14 /lib/tls/i686/cmov/libc.so.6(__assert_fail+0xee) [0xb73d272e]
#15 /usr/lib/libX11.so.6 [0xb72d5424]
#16 /usr/lib/libX11.so.6 [0xb72d55fd]
#17 /usr/lib/libX11.so.6(XWarpPointer+0x25) [0xb72cb9a5]
#18 ./libSDL-1.2.so.0 [0xb7fc615f]
#19 ./libSDL-1.2.so.0(X11_ResizeFullScreen+0x67) [0xb7fc6d1f]
ut2003-bin: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
xeriouxi@xeriouxi-desktop:~$
```

---

### Post by stevja1 on 2008-12-06
> **xeriouxi said:**
> Thanks for your reply, eragon100! =)

Here's the results from the terminal:

```
xeriouxi@xeriouxi-desktop:~$ ut2003
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb724f7c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb724f891]
#2 /usr/lib/libX11.so.6(_XReply+0x254) [0xb72d6494]
#3 ./libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xb7fcb42d]
#4 ./libSDL-1.2.so.0(X11_GetVideoModes+0x170) [0xb7fc6428]
#5 ./libSDL-1.2.so.0 [0xb7fc8348]
#6 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7fbdf96]
#7 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7fa04fe]
#8 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7fa05fc]
#9 ./ut2003-bin(ValidateCDKey__Fv+0x115) [0x80512bd]
#10 ./ut2003-bin(main+0x1fbc) [0x805778c]
#11 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb73c4685]
#12 ./ut2003-bin(ValidateCDKey__Fv+0x49) [0x80511f1]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb724f7c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb724f96e]
#2 /usr/lib/libX11.so.6 [0xb72d5619]
#3 /usr/lib/libX11.so.6(XQueryExtension+0x26) [0xb72c3196]
#4 /usr/lib/libX11.so.6(XInitExtension+0x41) [0xb72b7771]
#5 /usr/lib/libXext.so.6(XextAddDisplay+0x52) [0xb7291692]
#6 ./libSDL-1.2.so.0 [0xb80100e5]
#7 ./libSDL-1.2.so.0(XiGMiscQueryVersion+0x14) [0xb8010100]
#8 ./libSDL-1.2.so.0(X11_GetVideoModes+0x3b9) [0xb7fc6671]
#9 ./libSDL-1.2.so.0 [0xb7fc8348]
#10 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7fbdf96]
#11 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7fa04fe]
#12 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7fa05fc]
#13 ./ut2003-bin(ValidateCDKey__Fv+0x115) [0x80512bd]
#14 ./ut2003-bin(main+0x1fbc) [0x805778c]
#15 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb73c4685]
#16 ./ut2003-bin(ValidateCDKey__Fv+0x49) [0x80511f1]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb724f7c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb724f891]
#2 /usr/lib/libX11.so.6(_XReply+0x254) [0xb72d6494]
#3 ./libSDL-1.2.so.0(SDL_XineramaIsActive+0x76) [0xb7fd1a0a]
#4 ./libSDL-1.2.so.0(X11_GetVideoModes+0x857) [0xb7fc6b0f]
#5 ./libSDL-1.2.so.0 [0xb7fc8348]
#6 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7fbdf96]
#7 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7fa04fe]
#8 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7fa05fc]
#9 ./ut2003-bin(ValidateCDKey__Fv+0x115) [0x80512bd]
#10 ./ut2003-bin(main+0x1fbc) [0x805778c]
#11 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb73c4685]
#12 ./ut2003-bin(ValidateCDKey__Fv+0x49) [0x80511f1]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb724f7c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb724f96e]
#2 /usr/lib/libX11.so.6 [0xb72d5619]
#3 /usr/lib/libX11.so.6(XCreateColormap+0x26) [0xb72aa1d6]
#4 ./libSDL-1.2.so.0 [0xb7fc8480]
#5 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7fbdf96]
#6 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7fa04fe]
#7 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7fa05fc]
#8 ./ut2003-bin(ValidateCDKey__Fv+0x115) [0x80512bd]
#9 ./ut2003-bin(main+0x1fbc) [0x805778c]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb73c4685]
#11 ./ut2003-bin(ValidateCDKey__Fv+0x49) [0x80511f1]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb724f7c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb724f891]
#2 /usr/lib/libX11.so.6(_XReply+0x254) [0xb72d6494]
#3 ./libSDL-1.2.so.0(SDL_XF86VidModeGetGamma+0x9a) [0xb7fcb6fe]
#4 ./libSDL-1.2.so.0 [0xb7fc4609]
#5 ./libSDL-1.2.so.0(X11_SaveVidModeGamma+0x36) [0xb7fc46ba]
#6 ./libSDL-1.2.so.0 [0xb7fc850b]
#7 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7fbdf96]
#8 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7fa04fe]
#9 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7fa05fc]
#10 ./ut2003-bin(ValidateCDKey__Fv+0x115) [0x80512bd]
#11 ./ut2003-bin(main+0x1fbc) [0x805778c]
#12 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb73c4685]
#13 ./ut2003-bin(ValidateCDKey__Fv+0x49) [0x80511f1]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb724f7c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb724f96e]
#2 /usr/lib/libX11.so.6 [0xb72d5619]
#3 /usr/lib/libX11.so.6(XCreateWindow+0x26) [0xb72cbbc6]
#4 ./libSDL-1.2.so.0 [0xb7fc7ee9]
#5 ./libSDL-1.2.so.0 [0xb7fc8531]
#6 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7fbdf96]
#7 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7fa04fe]
#8 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7fa05fc]
#9 ./ut2003-bin(ValidateCDKey__Fv+0x115) [0x80512bd]
#10 ./ut2003-bin(main+0x1fbc) [0x805778c]
#11 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb73c4685]
#12 ./ut2003-bin(ValidateCDKey__Fv+0x49) [0x80511f1]
fcntl: Operation not permitted
fcntl: Operation not permitted
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb724f7c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb724f891]
#2 /usr/lib/libX11.so.6(_XReply+0x254) [0xb72d6494]
#3 ./libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xb7fcb42d]
#4 ./libSDL-1.2.so.0(SDL_XF86VidModeGetModeLine+0x5b) [0xb7fcb7d7]
#5 ./libSDL-1.2.so.0 [0xb7fc5fa8]
#6 ./libSDL-1.2.so.0(X11_EnterFullScreen+0x72) [0xb7fc6f02]
#7 ./libSDL-1.2.so.0 [0xb7fc91c2]
#8 ./libSDL-1.2.so.0 [0xb7fc941b]
#9 ./libSDL-1.2.so.0(SDL_SetVideoMode+0x1b3) [0xb7fbe80f]
#10 /usr/local/games/ut2003/System/SDLDrv.so(ResizeViewport__12USDLViewportUiiii+0x39a) [0xb69ddd8a]
#11 /usr/local/games/ut2003/System/OpenGLDrv.so(SetRes__19UOpenGLRenderDeviceP9UViewportiiiii+0x180) [0xb484e9c0]
#12 /usr/local/games/ut2003/System/SDLDrv.so(TryRenderDevice__12USDLViewportPCwiii+0x11e) [0xb69dd806]
#13 /usr/local/games/ut2003/System/SDLDrv.so(OpenWindow__12USDLViewportUiiiiii+0x223) [0xb69dc7d3]
#14 ./Engine.so(Init__11UGameEngine+0x1043) [0xb78ba753]
#15 ./ut2003-bin [0x805513e]
#16 ./ut2003-bin(main+0x296e) [0x805813e]
#17 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb73c4685]
#18 ./ut2003-bin(ValidateCDKey__Fv+0x49) [0x80511f1]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb724f7c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb724f96e]
#2 /usr/lib/libX11.so.6 [0xb72d5619]
#3 /usr/lib/libX11.so.6(XMoveResizeWindow+0x25) [0xb72a9435]
#4 ./libSDL-1.2.so.0(X11_EnterFullScreen+0xca) [0xb7fc6f5a]
#5 ./libSDL-1.2.so.0 [0xb7fc91c2]
#6 ./libSDL-1.2.so.0 [0xb7fc941b]
#7 ./libSDL-1.2.so.0(SDL_SetVideoMode+0x1b3) [0xb7fbe80f]
#8 /usr/local/games/ut2003/System/SDLDrv.so(ResizeViewport__12USDLViewportUiiii+0x39a) [0xb69ddd8a]
#9 /usr/local/games/ut2003/System/OpenGLDrv.so(SetRes__19UOpenGLRenderDeviceP9UViewportiiiii+0x180) [0xb484e9c0]
#10 /usr/local/games/ut2003/System/SDLDrv.so(TryRenderDevice__12USDLViewportPCwiii+0x11e) [0xb69dd806]
#11 /usr/local/games/ut2003/System/SDLDrv.so(OpenWindow__12USDLViewportUiiiiii+0x223) [0xb69dc7d3]
#12 ./Engine.so(Init__11UGameEngine+0x1043) [0xb78ba753]
#13 ./ut2003-bin [0x805513e]
#14 ./ut2003-bin(main+0x296e) [0x805813e]
#15 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb73c4685]
#16 ./ut2003-bin(ValidateCDKey__Fv+0x49) [0x80511f1]
ut2003-bin: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.

Backtrace:
[ 1]  ./Core.so [0xb7611c32]
[ 2]  [0xb804e400]
[ 3]  /lib/tls/i686/cmov/libc.so.6(abort+0x188) [0xb73db248]
[ 4]  /lib/tls/i686/cmov/libc.so.6(__assert_fail+0xee) [0xb73d272e]
[ 5]  /usr/lib/libX11.so.6 [0xb72d5424]
[ 6]  /usr/lib/libX11.so.6 [0xb72d55fd]
[ 7]  /usr/lib/libX11.so.6(XWarpPointer+0x25) [0xb72cb9a5]
[ 8]  ./libSDL-1.2.so.0 [0xb7fc615f]
[ 9]  ./libSDL-1.2.so.0(X11_ResizeFullScreen+0x67) [0xb7fc6d1f]
[10]  ./libSDL-1.2.so.0(X11_EnterFullScreen+0x155) [0xb7fc6fe5]
[11]  ./libSDL-1.2.so.0 [0xb7fc91c2]
[12]  ./libSDL-1.2.so.0 [0xb7fc941b]
[13]  ./libSDL-1.2.so.0(SDL_SetVideoMode+0x1b3) [0xb7fbe80f]
[14]  /usr/local/games/ut2003/System/SDLDrv.so(ResizeViewport__12USDLViewportUiiii+0x39a) [0xb69ddd8a]
[15]  /usr/local/games/ut2003/System/OpenGLDrv.so(SetRes__19UOpenGLRenderDeviceP9UViewportiiiii+0x180) [0xb484e9c0]
[16]  /usr/local/games/ut2003/System/SDLDrv.so(TryRenderDevice__12USDLViewportPCwiii+0x11e) [0xb69dd806]
[17]  /usr/local/games/ut2003/System/SDLDrv.so(OpenWindow__12USDLViewportUiiiiii+0x223) [0xb69dc7d3]
[18]  ./Engine.so(Init__11UGameEngine+0x1043) [0xb78ba753]
[19]  ./ut2003-bin [0x805513e]
[20]  ./ut2003-bin(main+0x296e) [0x805813e]
[21]  /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb73c4685]
[22]  ./ut2003-bin(ValidateCDKey__Fv+0x49) [0x80511f1]
Signal: SIGIOT [iot trap]
Aborting.
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb724f7c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb724f96e]
#2 /usr/lib/libX11.so.6 [0xb72d5619]
#3 /usr/lib/libX11.so.6(XFreeCursor+0x25) [0xb72aff05]
#4 ./libSDL-1.2.so.0(X11_FreeWMCursor+0x40) [0xb7fc7254]
#5 ./libSDL-1.2.so.0(SDL_FreeCursor+0x85) [0xb7fba435]
#6 ./libSDL-1.2.so.0(SDL_CursorQuit+0x63) [0xb7fb9f87]
#7 ./libSDL-1.2.so.0(SDL_VideoQuit+0x43) [0xb7fbf8e3]
#8 ./libSDL-1.2.so.0(SDL_QuitSubSystem+0x8b) [0xb7fa06b7]
#9 /usr/local/games/ut2003/System/SDLDrv.so [0xb69dacc0]
#10 /lib/tls/i686/cmov/libc.so.6(exit+0x89) [0xb73dcd69]
#11 ./Core.so [0xb7611cd8]
#12 [0xb804e400]
#13 /lib/tls/i686/cmov/libc.so.6(abort+0x188) [0xb73db248]
#14 /lib/tls/i686/cmov/libc.so.6(__assert_fail+0xee) [0xb73d272e]
#15 /usr/lib/libX11.so.6 [0xb72d5424]
#16 /usr/lib/libX11.so.6 [0xb72d55fd]
#17 /usr/lib/libX11.so.6(XWarpPointer+0x25) [0xb72cb9a5]
#18 ./libSDL-1.2.so.0 [0xb7fc615f]
#19 ./libSDL-1.2.so.0(X11_ResizeFullScreen+0x67) [0xb7fc6d1f]
ut2003-bin: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
xeriouxi@xeriouxi-desktop:~$
```

I'm having the exact same problem. There are a few lines that interest me here... 
Most of the backtraces get to here
```

#16 ./ut2003-bin(ValidateCDKey__Fv+0x4d) [0x80512d1]

```

Finally, near the end, we get here:
```

ut2003-bin: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.

```

My guess is that its failing to authenticate our keys for some reason. I would also guess that this is the same problem the installer had. That probably doesn't help a whole lot - I'm not sure what to do with this.

---

### Post by stevja1 on 2008-12-07
Found something interesting on this forum that made a small difference...
Backup the copy of libSDL-1.2.so.0 in ut2003/System
Copy /usr/lib/libSDL-1.2.so.0 to ut2003/System

This gets the game to run, but it goes really really fast, and eventually dies with the error: 'Negative delta time!'

(Source: [http://ubuntuforums.org/showthread.php?t=382865](http://ubuntuforums.org/showthread.php?t=382865))

---

### Post by stevja1 on 2008-12-07
This 'Negative delta time!' error appears to only happen to people with dual-core systems like myself. In winders, the general fix is to run the game in Windows 98/2000 compatibility mode, or to install the AMD CPU utilities. I have no idea what to do for linux though.

---

### Post by stevja1 on 2008-12-07
During boot, if you modify your boot parameters and add the string:
```

acpi=force lapic

```

and then figure out a magical way of locking your processor clock speed (I used kpowersave in kubuntu), it will work fine. The textures in the menus are messed up a little, and the sound doesn't work for me at all.

BTW - to get to the point I am now, I did the following:

```

user@genesis:~$ cd /bin
user@genesis:/bin$ mv sh sh.old
user@genesis:/bin$ ln -s bash sh
user@genesis:/bin$ cd ~
user@genesis:~$ ./media/cdrom/linux_installer.sh

```

The game installs to ~/ut2003 on my computer. The CD key thing works too as a result of the shell switch-a-roo.

After its installed, I downloaded the linux 2225 patch from ut2k3, and installed it.
```

user@genesis:~$ wget "http://data.unrealtournament.com/ut2003lnx_patch2225.tar.tar"
user@genesis:~$ tar -xf ut2003lnx_patch2225.tar.tar
user@genesis:~$ cd ut2003-lnx-2225
user@genesis:~$ cp -R * ../ut2003/.

```

That should effectively install the patch. That also seemed to fix the libSDL problem as well.

At this point, (and after a ton of research), I rebooted my machine, hit 'ESC' so that I could modify my boot parameters, and added 'acpi=force lapic'. At some point I'll modify my menu.1st file on my hard drive to make the change pernament.

Lastly, I installed kpowersave (yay kubuntu), and locked both CPU cores at 2400 mHz. When I run the game, it starts, (has funny menu textures), but runs at a normal speed. The in game textures are fine.

---

