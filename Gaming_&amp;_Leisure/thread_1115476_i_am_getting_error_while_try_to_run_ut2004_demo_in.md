---
title: "i am getting error while try to run ut2004 demo in ubuntu8.10 64bit"
date: 2009-04-03
forum: Gaming &amp; Leisure
---

### Post by rebelrex on 2009-04-03
it says:
./ut2004-bin: error while loading shared libraries: libstdc++.so.5: wrong ELF class: ELFCLASS32

can any1 help me get it working?

---

### Post by axelroo on 2009-04-04
Hello Rebel. It would appear you need to run the appropriate executable for your 64bit OS.  The 64bit executable for ut2004 is ut2004-bin-linux-amd64 under the "system" directory in the game.  If it doesn't show up, you should be able to download the patch to install it.

---

### Post by wolfyking2 on 2009-04-04
> **axelroo said:**
> Hello Rebel. It would appear you need to run the appropriate executable for your 64bit OS.  The 64bit executable for ut2004 is ut2004-bin-linux-amd64 under the "system" directory in the game.  If it doesn't show up, you should be able to download the patch to install it. I'm sorry, but that is wrong.  The ut2004 demo doesn't have ut-2004 bin and ut-amd-64-linux bin.  It only has the script to run.  So, you might wanna get the lib file from somewhere, if you still have trouble.  Also, make sure you downloading the LINUX version of the demo, not windows.

---

### Post by rebelrex on 2009-04-04
I tryed to download 64bit version of the demo and also the normal version, and both give me the same error.  
In both version , the system folder only has ut2004-bin and no 64 bit executable.

I try to do look for thr "libstdc++.so.5" file in my system , and it was found in both quake4demo folder and doom3demo folder (I have them both on my computer) , and also it was found in /usr/lib32 as a link to the file libstdc++.so.5.0.7 which also found in /usr/lib32
The files that in the doom3 and quake4 folders are 4 mb and the 1 which is in /usr/lib32 is 719kb

I dont know what I need to do with the files

---

### Post by wolfyking2 on 2009-04-04
Try putting the lib in the ut2004 system folder

---

### Post by rebelrex on 2009-04-04
I tryed that , and it didnt helped.

What I also tryed is to install via synaptic Libstdc++5 .
after doing that , the games starting to load up but crashes and I get new error:
```

Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7f3301d789fc]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x24) [0x7f3301d78ab4]
#2 /usr/lib/libX11.so.6(_XReply+0x268) [0x7f33023df698]
#3 ./libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0xb6) [0x7f3303b51eb6]
#4 ./libSDL-1.2.so.0(X11_GetVideoModes+0x5da) [0x7f3303b5069a]
#5 ./libSDL-1.2.so.0 [0x7f3303b4b193]
#6 ./libSDL-1.2.so.0(SDL_VideoInit+0x206) [0x7f3303b450e6]
#7 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x134) [0x7f3303b25ec4]
#8 ./libSDL-1.2.so.0(SDL_Init+0xf) [0x7f3303b25eef]
#9 ./ut2004-bin [0x50dbd4]
#10 ./ut2004-bin(main+0x3126) [0x50a626]
#11 /lib/libc.so.6(__libc_start_main+0xe6) [0x7f3302ba2466]
#12 ./ut2004-bin(strcat+0xaa) [0x50732a]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7f3301d789fc]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x17) [0x7f3301d78b77]
#2 /usr/lib/libX11.so.6 [0x7f33023de8c0]
#3 /usr/lib/libX11.so.6(XMatchVisualInfo+0x52) [0x7f33023d4f42]
#4 ./libSDL-1.2.so.0 [0x7f3303b4ff6d]
#5 ./libSDL-1.2.so.0(X11_GetVideoModes+0x365) [0x7f3303b50425]
#6 ./libSDL-1.2.so.0 [0x7f3303b4b193]
#7 ./libSDL-1.2.so.0(SDL_VideoInit+0x206) [0x7f3303b450e6]
#8 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x134) [0x7f3303b25ec4]
#9 ./libSDL-1.2.so.0(SDL_Init+0xf) [0x7f3303b25eef]
#10 ./ut2004-bin [0x50dbd4]
#11 ./ut2004-bin(main+0x3126) [0x50a626]
#12 /lib/libc.so.6(__libc_start_main+0xe6) [0x7f3302ba2466]
#13 ./ut2004-bin(strcat+0xaa) [0x50732a]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7f3301d789fc]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x24) [0x7f3301d78ab4]
#2 /usr/lib/libX11.so.6(_XReply+0x268) [0x7f33023df698]
#3 ./libSDL-1.2.so.0(SDL_XineramaIsActive+0x7c) [0x7f3303b593ec]
#4 ./libSDL-1.2.so.0(X11_GetVideoModes+0x23a) [0x7f3303b502fa]
#5 ./libSDL-1.2.so.0 [0x7f3303b4b193]
#6 ./libSDL-1.2.so.0(SDL_VideoInit+0x206) [0x7f3303b450e6]
#7 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x134) [0x7f3303b25ec4]
#8 ./libSDL-1.2.so.0(SDL_Init+0xf) [0x7f3303b25eef]
#9 ./ut2004-bin [0x50dbd4]
#10 ./ut2004-bin(main+0x3126) [0x50a626]
#11 /lib/libc.so.6(__libc_start_main+0xe6) [0x7f3302ba2466]
#12 ./ut2004-bin(strcat+0xaa) [0x50732a]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7f3301d789fc]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x17) [0x7f3301d78b77]
#2 /usr/lib/libX11.so.6 [0x7f33023de8c0]
#3 /usr/lib/libX11.so.6(XCreateColormap+0x3c) [0x7f33023b2d3c]
#4 ./libSDL-1.2.so.0 [0x7f3303b4b24f]
#5 ./libSDL-1.2.so.0(SDL_VideoInit+0x206) [0x7f3303b450e6]
#6 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x134) [0x7f3303b25ec4]
#7 ./libSDL-1.2.so.0(SDL_Init+0xf) [0x7f3303b25eef]
#8 ./ut2004-bin [0x50dbd4]
#9 ./ut2004-bin(main+0x3126) [0x50a626]
#10 /lib/libc.so.6(__libc_start_main+0xe6) [0x7f3302ba2466]
#11 ./ut2004-bin(strcat+0xaa) [0x50732a]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7f3301d789fc]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x24) [0x7f3301d78ab4]
#2 /usr/lib/libX11.so.6(_XReply+0x268) [0x7f33023df698]
#3 ./libSDL-1.2.so.0(SDL_XF86VidModeGetGamma+0xbd) [0x7f3303b521ed]
#4 ./libSDL-1.2.so.0 [0x7f3303b4a4fa]
#5 ./libSDL-1.2.so.0(X11_SaveVidModeGamma+0x25) [0x7f3303b4a5a5]
#6 ./libSDL-1.2.so.0 [0x7f3303b4b2aa]
#7 ./libSDL-1.2.so.0(SDL_VideoInit+0x206) [0x7f3303b450e6]
#8 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x134) [0x7f3303b25ec4]
#9 ./libSDL-1.2.so.0(SDL_Init+0xf) [0x7f3303b25eef]
#10 ./ut2004-bin [0x50dbd4]
#11 ./ut2004-bin(main+0x3126) [0x50a626]
#12 /lib/libc.so.6(__libc_start_main+0xe6) [0x7f3302ba2466]
#13 ./ut2004-bin(strcat+0xaa) [0x50732a]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7f3301d789fc]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x17) [0x7f3301d78b77]
#2 /usr/lib/libX11.so.6 [0x7f33023de8c0]
#3 /usr/lib/libX11.so.6(XCreateWindow+0x44) [0x7f33023d5704]
#4 ./libSDL-1.2.so.0 [0x7f3303b4ad52]
#5 ./libSDL-1.2.so.0 [0x7f3303b4b2c9]
#6 ./libSDL-1.2.so.0(SDL_VideoInit+0x206) [0x7f3303b450e6]
#7 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x134) [0x7f3303b25ec4]
#8 ./libSDL-1.2.so.0(SDL_Init+0xf) [0x7f3303b25eef]
#9 ./ut2004-bin [0x50dbd4]
#10 ./ut2004-bin(main+0x3126) [0x50a626]
#11 /lib/libc.so.6(__libc_start_main+0xe6) [0x7f3302ba2466]
#12 ./ut2004-bin(strcat+0xaa) [0x50732a]
open /dev/[sound/]dsp: No such file or directory
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7f3301d789fc]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x24) [0x7f3301d78ab4]
#2 /usr/lib/libX11.so.6(_XReply+0x268) [0x7f33023df698]
#3 ./libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0xb6) [0x7f3303b51eb6]
#4 ./libSDL-1.2.so.0(SDL_XF86VidModeGetModeLine+0xa5) [0x7f3303b52355]
#5 ./libSDL-1.2.so.0 [0x7f3303b4fe2a]
#6 ./libSDL-1.2.so.0(X11_EnterFullScreen+0x7f) [0x7f3303b50a6f]
#7 ./libSDL-1.2.so.0 [0x7f3303b4bc7a]
#8 ./libSDL-1.2.so.0 [0x7f3303b4c1a1]
#9 ./libSDL-1.2.so.0(SDL_SetVideoMode+0x16a) [0x7f3303b459ea]
#10 ./ut2004-bin(_ZN12USDLViewport14ResizeViewportEjiii+0x10b) [0xc7850b]
#11 ./ut2004-bin(_ZN19UOpenGLRenderDevice6SetResEP9UViewportiiiii+0x1b8) [0xc7e998]
#12 ./ut2004-bin(_ZN12USDLViewport15TryRenderDeviceEPKwiii+0x175) [0xc780e5]
#13 ./ut2004-bin(_ZN12USDLViewport10OpenWindowEmiiiii+0x123) [0xc76d53]
#14 ./ut2004-bin(_ZN11UGameEngine4InitEv+0xefd) [0x6478dd]
#15 ./ut2004-bin [0x50e4d3]
#16 ./ut2004-bin(main+0x2952) [0x509e52]
#17 /lib/libc.so.6(__libc_start_main+0xe6) [0x7f3302ba2466]
#18 ./ut2004-bin(strcat+0xaa) [0x50732a]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7f3301d789fc]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x17) [0x7f3301d78b77]
#2 /usr/lib/libX11.so.6 [0x7f33023de8c0]
#3 /usr/lib/libX11.so.6(XMoveResizeWindow+0x42) [0x7f33023b1e02]
#4 ./libSDL-1.2.so.0(X11_EnterFullScreen+0xd3) [0x7f3303b50ac3]
#5 ./libSDL-1.2.so.0 [0x7f3303b4bc7a]
#6 ./libSDL-1.2.so.0 [0x7f3303b4c1a1]
#7 ./libSDL-1.2.so.0(SDL_SetVideoMode+0x16a) [0x7f3303b459ea]
#8 ./ut2004-bin(_ZN12USDLViewport14ResizeViewportEjiii+0x10b) [0xc7850b]
#9 ./ut2004-bin(_ZN19UOpenGLRenderDevice6SetResEP9UViewportiiiii+0x1b8) [0xc7e998]
#10 ./ut2004-bin(_ZN12USDLViewport15TryRenderDeviceEPKwiii+0x175) [0xc780e5]
#11 ./ut2004-bin(_ZN12USDLViewport10OpenWindowEmiiiii+0x123) [0xc76d53]
#12 ./ut2004-bin(_ZN11UGameEngine4InitEv+0xefd) [0x6478dd]
#13 ./ut2004-bin [0x50e4d3]
#14 ./ut2004-bin(main+0x2952) [0x509e52]
#15 /lib/libc.so.6(__libc_start_main+0xe6) [0x7f3302ba2466]
#16 ./ut2004-bin(strcat+0xaa) [0x50732a]
ut2004-bin: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
Signal: SIGIOT [iot trap]
Aborting.


Crash information will be saved to your logfile.
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7f3301d789fc]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x17) [0x7f3301d78b77]
#2 /usr/lib/libX11.so.6 [0x7f33023de8c0]
#3 /usr/lib/libX11.so.6(XFreeCursor+0x1a) [0x7f33023b8fba]
#4 ./libSDL-1.2.so.0(X11_FreeWMCursor+0x5b) [0x7f3303b50cfb]
#5 ./libSDL-1.2.so.0(SDL_FreeCursor+0x79) [0x7f3303b41569]
#6 ./libSDL-1.2.so.0(SDL_CursorQuit+0x8f) [0x7f3303b4109f]
#7 ./libSDL-1.2.so.0(SDL_VideoQuit+0x53) [0x7f3303b46e03]
#8 ./libSDL-1.2.so.0(SDL_QuitSubSystem+0x5d) [0x7f3303b25f6d]
#9 /lib/libc.so.6(exit+0x9d) [0x7f3302bba6ad]
#10 ./ut2004-bin [0xa99963]
#11 /lib/libpthread.so.0 [0x7f330367e0f0]
#12 /lib/libc.so.6(gsignal+0x35) [0x7f3302bb7015]
#13 /lib/libc.so.6(abort+0x183) [0x7f3302bb8b83]
#14 /lib/libc.so.6(__assert_fail+0xe9) [0x7f3302bafd89]
#15 /usr/lib/libX11.so.6 [0x7f33023de701]
#16 /usr/lib/libX11.so.6(XWarpPointer+0x42) [0x7f33023d54a2]
#17 ./libSDL-1.2.so.0 [0x7f3303b4ff36]
#18 ./libSDL-1.2.so.0(X11_ResizeFullScreen+0x6a) [0x7f3303b508ba]
#19 ./libSDL-1.2.so.0(X11_EnterFullScreen+0x131) [0x7f3303b50b21]
ut2004-bin: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.

```

---

### Post by wolfyking2 on 2009-04-04
you might wanna install SDL libs

---

### Post by rebelrex on 2009-04-04
how do I install them?

---

### Post by wolfyking2 on 2009-04-04
google 'SDL lib for linux' :lolflag:

---

### Post by rebelrex on 2009-04-04
ok 
I installed sdl for linux 64 bit, and still getting same error

```
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7fe8a69d79fc]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x24) [0x7fe8a69d7ab4]
#2 /usr/lib/libX11.so.6(_XReply+0x268) [0x7fe8a703e698]
#3 ./libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0xb6) [0x7fe8a87afeb6]
#4 ./libSDL-1.2.so.0(X11_GetVideoModes+0x5da) [0x7fe8a87ae69a]
#5 ./libSDL-1.2.so.0 [0x7fe8a87a9193]
#6 ./libSDL-1.2.so.0(SDL_VideoInit+0x206) [0x7fe8a87a30e6]
#7 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x134) [0x7fe8a8783ec4]
#8 ./libSDL-1.2.so.0(SDL_Init+0xf) [0x7fe8a8783eef]
#9 ./ut2004-bin [0x50dbd4]
#10 ./ut2004-bin(main+0x3126) [0x50a626]
#11 /lib/libc.so.6(__libc_start_main+0xe6) [0x7fe8a7801466]
#12 ./ut2004-bin(strcat+0xaa) [0x50732a]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7fe8a69d79fc]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x17) [0x7fe8a69d7b77]
#2 /usr/lib/libX11.so.6 [0x7fe8a703d8c0]
#3 /usr/lib/libX11.so.6(XMatchVisualInfo+0x52) [0x7fe8a7033f42]
#4 ./libSDL-1.2.so.0 [0x7fe8a87adf6d]
#5 ./libSDL-1.2.so.0(X11_GetVideoModes+0x365) [0x7fe8a87ae425]
#6 ./libSDL-1.2.so.0 [0x7fe8a87a9193]
#7 ./libSDL-1.2.so.0(SDL_VideoInit+0x206) [0x7fe8a87a30e6]
#8 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x134) [0x7fe8a8783ec4]
#9 ./libSDL-1.2.so.0(SDL_Init+0xf) [0x7fe8a8783eef]
#10 ./ut2004-bin [0x50dbd4]
#11 ./ut2004-bin(main+0x3126) [0x50a626]
#12 /lib/libc.so.6(__libc_start_main+0xe6) [0x7fe8a7801466]
#13 ./ut2004-bin(strcat+0xaa) [0x50732a]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7fe8a69d79fc]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x24) [0x7fe8a69d7ab4]
#2 /usr/lib/libX11.so.6(_XReply+0x268) [0x7fe8a703e698]
#3 ./libSDL-1.2.so.0(SDL_XineramaIsActive+0x7c) [0x7fe8a87b73ec]
#4 ./libSDL-1.2.so.0(X11_GetVideoModes+0x23a) [0x7fe8a87ae2fa]
#5 ./libSDL-1.2.so.0 [0x7fe8a87a9193]
#6 ./libSDL-1.2.so.0(SDL_VideoInit+0x206) [0x7fe8a87a30e6]
#7 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x134) [0x7fe8a8783ec4]
#8 ./libSDL-1.2.so.0(SDL_Init+0xf) [0x7fe8a8783eef]
#9 ./ut2004-bin [0x50dbd4]
#10 ./ut2004-bin(main+0x3126) [0x50a626]
#11 /lib/libc.so.6(__libc_start_main+0xe6) [0x7fe8a7801466]
#12 ./ut2004-bin(strcat+0xaa) [0x50732a]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7fe8a69d79fc]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x17) [0x7fe8a69d7b77]
#2 /usr/lib/libX11.so.6 [0x7fe8a703d8c0]
#3 /usr/lib/libX11.so.6(XCreateColormap+0x3c) [0x7fe8a7011d3c]
#4 ./libSDL-1.2.so.0 [0x7fe8a87a924f]
#5 ./libSDL-1.2.so.0(SDL_VideoInit+0x206) [0x7fe8a87a30e6]
#6 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x134) [0x7fe8a8783ec4]
#7 ./libSDL-1.2.so.0(SDL_Init+0xf) [0x7fe8a8783eef]
#8 ./ut2004-bin [0x50dbd4]
#9 ./ut2004-bin(main+0x3126) [0x50a626]
#10 /lib/libc.so.6(__libc_start_main+0xe6) [0x7fe8a7801466]
#11 ./ut2004-bin(strcat+0xaa) [0x50732a]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7fe8a69d79fc]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x24) [0x7fe8a69d7ab4]
#2 /usr/lib/libX11.so.6(_XReply+0x268) [0x7fe8a703e698]
#3 ./libSDL-1.2.so.0(SDL_XF86VidModeGetGamma+0xbd) [0x7fe8a87b01ed]
#4 ./libSDL-1.2.so.0 [0x7fe8a87a84fa]
#5 ./libSDL-1.2.so.0(X11_SaveVidModeGamma+0x25) [0x7fe8a87a85a5]
#6 ./libSDL-1.2.so.0 [0x7fe8a87a92aa]
#7 ./libSDL-1.2.so.0(SDL_VideoInit+0x206) [0x7fe8a87a30e6]
#8 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x134) [0x7fe8a8783ec4]
#9 ./libSDL-1.2.so.0(SDL_Init+0xf) [0x7fe8a8783eef]
#10 ./ut2004-bin [0x50dbd4]
#11 ./ut2004-bin(main+0x3126) [0x50a626]
#12 /lib/libc.so.6(__libc_start_main+0xe6) [0x7fe8a7801466]
#13 ./ut2004-bin(strcat+0xaa) [0x50732a]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7fe8a69d79fc]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x17) [0x7fe8a69d7b77]
#2 /usr/lib/libX11.so.6 [0x7fe8a703d8c0]
#3 /usr/lib/libX11.so.6(XCreateWindow+0x44) [0x7fe8a7034704]
#4 ./libSDL-1.2.so.0 [0x7fe8a87a8d52]
#5 ./libSDL-1.2.so.0 [0x7fe8a87a92c9]
#6 ./libSDL-1.2.so.0(SDL_VideoInit+0x206) [0x7fe8a87a30e6]
#7 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x134) [0x7fe8a8783ec4]
#8 ./libSDL-1.2.so.0(SDL_Init+0xf) [0x7fe8a8783eef]
#9 ./ut2004-bin [0x50dbd4]
#10 ./ut2004-bin(main+0x3126) [0x50a626]
#11 /lib/libc.so.6(__libc_start_main+0xe6) [0x7fe8a7801466]
#12 ./ut2004-bin(strcat+0xaa) [0x50732a]
open /dev/[sound/]dsp: No such file or directory
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7fe8a69d79fc]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x24) [0x7fe8a69d7ab4]
#2 /usr/lib/libX11.so.6(_XReply+0x268) [0x7fe8a703e698]
#3 ./libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0xb6) [0x7fe8a87afeb6]
#4 ./libSDL-1.2.so.0(SDL_XF86VidModeGetModeLine+0xa5) [0x7fe8a87b0355]
#5 ./libSDL-1.2.so.0 [0x7fe8a87ade2a]
#6 ./libSDL-1.2.so.0(X11_EnterFullScreen+0x7f) [0x7fe8a87aea6f]
#7 ./libSDL-1.2.so.0 [0x7fe8a87a9c7a]
#8 ./libSDL-1.2.so.0 [0x7fe8a87aa1a1]
#9 ./libSDL-1.2.so.0(SDL_SetVideoMode+0x16a) [0x7fe8a87a39ea]
#10 ./ut2004-bin(_ZN12USDLViewport14ResizeViewportEjiii+0x10b) [0xc7850b]
#11 ./ut2004-bin(_ZN19UOpenGLRenderDevice6SetResEP9UViewportiiiii+0x1b8) [0xc7e998]
#12 ./ut2004-bin(_ZN12USDLViewport15TryRenderDeviceEPKwiii+0x175) [0xc780e5]
#13 ./ut2004-bin(_ZN12USDLViewport10OpenWindowEmiiiii+0x123) [0xc76d53]
#14 ./ut2004-bin(_ZN11UGameEngine4InitEv+0xefd) [0x6478dd]
#15 ./ut2004-bin [0x50e4d3]
#16 ./ut2004-bin(main+0x2952) [0x509e52]
#17 /lib/libc.so.6(__libc_start_main+0xe6) [0x7fe8a7801466]
#18 ./ut2004-bin(strcat+0xaa) [0x50732a]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7fe8a69d79fc]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x17) [0x7fe8a69d7b77]
#2 /usr/lib/libX11.so.6 [0x7fe8a703d8c0]
#3 /usr/lib/libX11.so.6(XMoveResizeWindow+0x42) [0x7fe8a7010e02]
#4 ./libSDL-1.2.so.0(X11_EnterFullScreen+0xd3) [0x7fe8a87aeac3]
#5 ./libSDL-1.2.so.0 [0x7fe8a87a9c7a]
#6 ./libSDL-1.2.so.0 [0x7fe8a87aa1a1]
#7 ./libSDL-1.2.so.0(SDL_SetVideoMode+0x16a) [0x7fe8a87a39ea]
#8 ./ut2004-bin(_ZN12USDLViewport14ResizeViewportEjiii+0x10b) [0xc7850b]
#9 ./ut2004-bin(_ZN19UOpenGLRenderDevice6SetResEP9UViewportiiiii+0x1b8) [0xc7e998]
#10 ./ut2004-bin(_ZN12USDLViewport15TryRenderDeviceEPKwiii+0x175) [0xc780e5]
#11 ./ut2004-bin(_ZN12USDLViewport10OpenWindowEmiiiii+0x123) [0xc76d53]
#12 ./ut2004-bin(_ZN11UGameEngine4InitEv+0xefd) [0x6478dd]
#13 ./ut2004-bin [0x50e4d3]
#14 ./ut2004-bin(main+0x2952) [0x509e52]
#15 /lib/libc.so.6(__libc_start_main+0xe6) [0x7fe8a7801466]
#16 ./ut2004-bin(strcat+0xaa) [0x50732a]
ut2004-bin: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
Signal: SIGIOT [iot trap]
Aborting.


Crash information will be saved to your logfile.
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7fe8a69d79fc]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x17) [0x7fe8a69d7b77]
#2 /usr/lib/libX11.so.6 [0x7fe8a703d8c0]
#3 /usr/lib/libX11.so.6(XFreeCursor+0x1a) [0x7fe8a7017fba]
#4 ./libSDL-1.2.so.0(X11_FreeWMCursor+0x5b) [0x7fe8a87aecfb]
#5 ./libSDL-1.2.so.0(SDL_FreeCursor+0x79) [0x7fe8a879f569]
#6 ./libSDL-1.2.so.0(SDL_CursorQuit+0x8f) [0x7fe8a879f09f]
#7 ./libSDL-1.2.so.0(SDL_VideoQuit+0x53) [0x7fe8a87a4e03]
#8 ./libSDL-1.2.so.0(SDL_QuitSubSystem+0x5d) [0x7fe8a8783f6d]
#9 /lib/libc.so.6(exit+0x9d) [0x7fe8a78196ad]
#10 ./ut2004-bin [0xa99963]
#11 /lib/libpthread.so.0 [0x7fe8a82dd0f0]
#12 /lib/libc.so.6(gsignal+0x35) [0x7fe8a7816015]
#13 /lib/libc.so.6(abort+0x183) [0x7fe8a7817b83]
#14 /lib/libc.so.6(__assert_fail+0xe9) [0x7fe8a780ed89]
#15 /usr/lib/libX11.so.6 [0x7fe8a703d701]
#16 /usr/lib/libX11.so.6(XWarpPointer+0x42) [0x7fe8a70344a2]
#17 ./libSDL-1.2.so.0 [0x7fe8a87adf36]
#18 ./libSDL-1.2.so.0(X11_ResizeFullScreen+0x6a) [0x7fe8a87ae8ba]
#19 ./libSDL-1.2.so.0(X11_EnterFullScreen+0x131) [0x7fe8a87aeb21]
ut2004-bin: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.

```

---

### Post by wolfyking2 on 2009-04-04
hmm...I'm not sure, I'm sorry, I'm not an expert at this stuff, just saw the SDL lib and made me suspicous.

---

### Post by madduck84 on 2009-06-10
I had this same problem tonight; after a google search i found on epic's forums that you need to install libstdc++5.  crack open synaptic package manager and search on libstdc, chances are you don't have version 5 installed.  install that and you should hopefully be good to go (as far as that error is concerned).

---

