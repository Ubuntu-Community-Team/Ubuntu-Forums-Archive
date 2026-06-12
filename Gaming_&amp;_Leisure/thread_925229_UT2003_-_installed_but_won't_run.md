---
title: "UT2003 - installed but won't run"
date: 2008-09-20
forum: Gaming &amp; Leisure
---

### Post by Belgatom on 2008-09-20
I get the following code when trying to run UT2003demo : 

```
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb710e767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb710e8b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb718f1bd]
#3 ./libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xb7e9f42d]
#4 ./libSDL-1.2.so.0(X11_GetVideoModes+0x170) [0xb7e9a428]
#5 ./libSDL-1.2.so.0 [0xb7e9c348]
#6 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7e91f96]
#7 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7e744fe]
#8 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7e745fc]
#9 ./ut2003-bin(Printf__7FStringPCwe+0x159) [0x805139d]
#10 ./ut2003-bin(main+0x1fbc) [0x805785c]
#11 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7250450]
#12 ./ut2003-bin(GetFullName__C7UObjectPw+0x7d) [0x80512d1]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb710e767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb710e81e]
#2 /usr/lib/libX11.so.6 [0xb718e518]
#3 /usr/lib/libX11.so.6(XQueryExtension+0x26) [0xb717cfe6]
#4 /usr/lib/libX11.so.6(XInitExtension+0x3b) [0xb7171d4b]
#5 /usr/lib/libXext.so.6(XextAddDisplay+0x53) [0xb714d443]
#6 ./libSDL-1.2.so.0 [0xb7ee40e5]
#7 ./libSDL-1.2.so.0(XiGMiscQueryVersion+0x14) [0xb7ee4100]
#8 ./libSDL-1.2.so.0(X11_GetVideoModes+0x3b9) [0xb7e9a671]
#9 ./libSDL-1.2.so.0 [0xb7e9c348]
#10 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7e91f96]
#11 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7e744fe]
#12 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7e745fc]
#13 ./ut2003-bin(Printf__7FStringPCwe+0x159) [0x805139d]
#14 ./ut2003-bin(main+0x1fbc) [0x805785c]
#15 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7250450]
#16 ./ut2003-bin(GetFullName__C7UObjectPw+0x7d) [0x80512d1]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb710e767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb710e8b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb718f1bd]
#3 ./libSDL-1.2.so.0(SDL_XineramaIsActive+0x76) [0xb7ea5a0a]
#4 ./libSDL-1.2.so.0(X11_GetVideoModes+0x857) [0xb7e9ab0f]
#5 ./libSDL-1.2.so.0 [0xb7e9c348]
#6 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7e91f96]
#7 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7e744fe]
#8 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7e745fc]
#9 ./ut2003-bin(Printf__7FStringPCwe+0x159) [0x805139d]
#10 ./ut2003-bin(main+0x1fbc) [0x805785c]
#11 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7250450]
#12 ./ut2003-bin(GetFullName__C7UObjectPw+0x7d) [0x80512d1]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb710e767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb710e81e]
#2 /usr/lib/libX11.so.6 [0xb718e518]
#3 /usr/lib/libX11.so.6(XCreateColormap+0x26) [0xb7164e76]
#4 ./libSDL-1.2.so.0 [0xb7e9c480]
#5 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7e91f96]
#6 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7e744fe]
#7 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7e745fc]
#8 ./ut2003-bin(Printf__7FStringPCwe+0x159) [0x805139d]
#9 ./ut2003-bin(main+0x1fbc) [0x805785c]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7250450]
#11 ./ut2003-bin(GetFullName__C7UObjectPw+0x7d) [0x80512d1]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb710e767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb710e8b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb718f1bd]
#3 ./libSDL-1.2.so.0(SDL_XF86VidModeGetGamma+0x9a) [0xb7e9f6fe]
#4 ./libSDL-1.2.so.0 [0xb7e98609]
#5 ./libSDL-1.2.so.0(X11_SaveVidModeGamma+0x36) [0xb7e986ba]
#6 ./libSDL-1.2.so.0 [0xb7e9c50b]
#7 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7e91f96]
#8 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7e744fe]
#9 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7e745fc]
#10 ./ut2003-bin(Printf__7FStringPCwe+0x159) [0x805139d]
#11 ./ut2003-bin(main+0x1fbc) [0x805785c]
#12 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7250450]
#13 ./ut2003-bin(GetFullName__C7UObjectPw+0x7d) [0x80512d1]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb710e767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb710e81e]
#2 /usr/lib/libX11.so.6 [0xb718e518]
#3 /usr/lib/libX11.so.6(XCreateWindow+0x26) [0xb7185616]
#4 ./libSDL-1.2.so.0 [0xb7e9bee9]
#5 ./libSDL-1.2.so.0 [0xb7e9c531]
#6 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7e91f96]
#7 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7e744fe]
#8 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7e745fc]
#9 ./ut2003-bin(Printf__7FStringPCwe+0x159) [0x805139d]
#10 ./ut2003-bin(main+0x1fbc) [0x805785c]
#11 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7250450]
#12 ./ut2003-bin(GetFullName__C7UObjectPw+0x7d) [0x80512d1]
fcntl: Operation not permitted
fcntl: Operation not permitted
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb710e767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb710e8b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb718f1bd]
#3 ./libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xb7e9f42d]
#4 ./libSDL-1.2.so.0(SDL_XF86VidModeGetModeLine+0x5b) [0xb7e9f7d7]
#5 ./libSDL-1.2.so.0 [0xb7e99fa8]
#6 ./libSDL-1.2.so.0(X11_EnterFullScreen+0x72) [0xb7e9af02]
#7 ./libSDL-1.2.so.0 [0xb7e9d1c2]
#8 ./libSDL-1.2.so.0 [0xb7e9d41b]
#9 ./libSDL-1.2.so.0(SDL_SetVideoMode+0x1b3) [0xb7e9280f]
#10 /home/belgatom/ut2003_demo/System/SDLDrv.so(ResizeViewport__12USDLViewportUiiii+0x39a) [0xb6875eea]
#11 /home/belgatom/ut2003_demo/System/OpenGLDrv.so(SetRes__19UOpenGLRenderDeviceP9UViewportiiiii+0x191) [0xb4713b01]
#12 /home/belgatom/ut2003_demo/System/SDLDrv.so(TryRenderDevice__12USDLViewportPCwiii+0x11e) [0xb6875966]
#13 /home/belgatom/ut2003_demo/System/SDLDrv.so(OpenWindow__12USDLViewportUiiiiii+0x223) [0xb68748a3]
#14 ./Engine.so(Init__11UGameEngine+0x12d1) [0xb7766565]
#15 ./ut2003-bin [0x805520e]
#16 ./ut2003-bin(main+0x296e) [0x805820e]
#17 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7250450]
#18 ./ut2003-bin(GetFullName__C7UObjectPw+0x7d) [0x80512d1]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb710e767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb710e81e]
#2 /usr/lib/libX11.so.6 [0xb718e518]
#3 /usr/lib/libX11.so.6(XMoveResizeWindow+0x25) [0xb7164165]
#4 ./libSDL-1.2.so.0(X11_EnterFullScreen+0xca) [0xb7e9af5a]
#5 ./libSDL-1.2.so.0 [0xb7e9d1c2]
#6 ./libSDL-1.2.so.0 [0xb7e9d41b]
#7 ./libSDL-1.2.so.0(SDL_SetVideoMode+0x1b3) [0xb7e9280f]
#8 /home/belgatom/ut2003_demo/System/SDLDrv.so(ResizeViewport__12USDLViewportUiiii+0x39a) [0xb6875eea]
#9 /home/belgatom/ut2003_demo/System/OpenGLDrv.so(SetRes__19UOpenGLRenderDeviceP9UViewportiiiii+0x191) [0xb4713b01]
#10 /home/belgatom/ut2003_demo/System/SDLDrv.so(TryRenderDevice__12USDLViewportPCwiii+0x11e) [0xb6875966]
#11 /home/belgatom/ut2003_demo/System/SDLDrv.so(OpenWindow__12USDLViewportUiiiiii+0x223) [0xb68748a3]
#12 ./Engine.so(Init__11UGameEngine+0x12d1) [0xb7766565]
#13 ./ut2003-bin [0x805520e]
#14 ./ut2003-bin(main+0x296e) [0x805820e]
#15 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7250450]
#16 ./ut2003-bin(GetFullName__C7UObjectPw+0x7d) [0x80512d1]
ut2003-bin: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.

Backtrace:
[ 1]  ./Core.so [0xb74a978a]
[ 2]  [0xb7f08420]
[ 3]  /lib/tls/i686/cmov/libc.so.6(abort+0x101) [0xb7266a01]
[ 4]  /lib/tls/i686/cmov/libc.so.6(__assert_fail+0xee) [0xb725e10e]
[ 5]  /usr/lib/libX11.so.6 [0xb718e324]
[ 6]  /usr/lib/libX11.so.6 [0xb718e4fd]
[ 7]  /usr/lib/libX11.so.6(XWarpPointer+0x25) [0xb71853e5]
[ 8]  ./libSDL-1.2.so.0 [0xb7e9a15f]
[ 9]  ./libSDL-1.2.so.0(X11_ResizeFullScreen+0x67) [0xb7e9ad1f]
[10]  ./libSDL-1.2.so.0(X11_EnterFullScreen+0x155) [0xb7e9afe5]
[11]  ./libSDL-1.2.so.0 [0xb7e9d1c2]
[12]  ./libSDL-1.2.so.0 [0xb7e9d41b]
[13]  ./libSDL-1.2.so.0(SDL_SetVideoMode+0x1b3) [0xb7e9280f]
[14]  /home/belgatom/ut2003_demo/System/SDLDrv.so(ResizeViewport__12USDLViewportUiiii+0x39a) [0xb6875eea]
[15]  /home/belgatom/ut2003_demo/System/OpenGLDrv.so(SetRes__19UOpenGLRenderDeviceP9UViewportiiiii+0x191) [0xb4713b01]
[16]  /home/belgatom/ut2003_demo/System/SDLDrv.so(TryRenderDevice__12USDLViewportPCwiii+0x11e) [0xb6875966]
[17]  /home/belgatom/ut2003_demo/System/SDLDrv.so(OpenWindow__12USDLViewportUiiiiii+0x223) [0xb68748a3]
[18]  ./Engine.so(Init__11UGameEngine+0x12d1) [0xb7766565]
[19]  ./ut2003-bin [0x805520e]
[20]  ./ut2003-bin(main+0x296e) [0x805820e]
[21]  /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7250450]
[22]  ./ut2003-bin(GetFullName__C7UObjectPw+0x7d) [0x80512d1]
Signal: SIGIOT [iot trap]
Aborting.
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb710e767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb710e81e]
#2 /usr/lib/libX11.so.6 [0xb718e518]
#3 /usr/lib/libX11.so.6(XFreeCursor+0x25) [0xb716a8f5]
#4 ./libSDL-1.2.so.0(X11_FreeWMCursor+0x40) [0xb7e9b254]
#5 ./libSDL-1.2.so.0(SDL_FreeCursor+0x85) [0xb7e8e435]
#6 ./libSDL-1.2.so.0(SDL_CursorQuit+0x63) [0xb7e8df87]
#7 ./libSDL-1.2.so.0(SDL_VideoQuit+0x43) [0xb7e938e3]
#8 ./libSDL-1.2.so.0(SDL_QuitSubSystem+0x8b) [0xb7e746b7]
#9 /home/belgatom/ut2003_demo/System/SDLDrv.so [0xb6872d50]
#10 /lib/tls/i686/cmov/libc.so.6(exit+0xd4) [0xb7268084]
#11 ./Core.so [0xb74a9835]
#12 [0xb7f08420]
#13 /lib/tls/i686/cmov/libc.so.6(abort+0x101) [0xb7266a01]
#14 /lib/tls/i686/cmov/libc.so.6(__assert_fail+0xee) [0xb725e10e]
#15 /usr/lib/libX11.so.6 [0xb718e324]
#16 /usr/lib/libX11.so.6 [0xb718e4fd]
#17 /usr/lib/libX11.so.6(XWarpPointer+0x25) [0xb71853e5]
#18 ./libSDL-1.2.so.0 [0xb7e9a15f]
#19 ./libSDL-1.2.so.0(X11_ResizeFullScreen+0x67) [0xb7e9ad1f]
ut2003-bin: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.

```

I'm still taking my first steps in linux. Getting comfortable with the commandline. I'd like to see gaming on Linux in action with something I know. Please advise. I have a feeling it has something to do with rendering and openGL but that's just a feeling.

---

### Post by PaulReaver on 2009-03-18
The libSDL included in the retail package is not compatible with newer ubuntu installs.  
I think if you delete libSDL-1.2.so from /usr/local/games/ut2003/system/
and replace it by _COPYING_ your libSDL from /usr/lib/  

for reference mine was libSDL-1.2.so.0.11.1
Yours may be different. 
Remember to grant user permissions to the player using it.  If you use a file manager like nautilus you will need to open it in a terminal as sudo.  type "sudo nautilus".  To grant permissions the easy way, right click the file scroll down to properties and click the permissions tab.

also make sure you have the cdkey in /usr/local/games/ut2003/system/
in this format XXXXX-XXXXX-XXXXX-XXXXX
all upper case.

hope it helps.

---

### Post by ob2 on 2009-03-20
Wow!  I have been battling this problem since last week and searching everywhere for a solution.  Yours worked for me.

Thanks PaulReaver.

---

