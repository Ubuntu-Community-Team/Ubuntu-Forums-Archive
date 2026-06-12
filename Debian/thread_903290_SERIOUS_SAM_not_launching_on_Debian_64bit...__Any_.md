---
title: "SERIOUS SAM not launching on Debian 64bit...  Any advice?"
date: 2008-08-28
forum: Debian
---

### Post by dudeofthedead on 2008-08-28
Hey guys,

I was looking forward to play SERIOUS SAM: GOLD EDITION.  Running both the beta installers available from [Loki](http://www.liflg.org/?catid=6&gameid=71) worked without a hitch but now launching the actual game prints out the following lines.

Terminal output with './ssamtfe'

```
hzf@hzf-desktop:~$ cd ssamtfe
hzf@hzf-desktop:~/ssamtfe$ ./ssamtfe
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf7c5f767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xf7c5f8b1]
#2 /usr/lib32/libX11.so.6(_XReply+0x244) [0xf7e06c14]
#3 ./ssam_lnx(SDL_XF86VidModeQueryVersion+0x8d) [0x82c1d5d]
#4 ./ssam_lnx(X11_GetVideoModes+0x170) [0x82c0608]
#5 ./ssam_lnx [0x829ee68]
#6 ./ssam_lnx(SDL_VideoInit+0x2b2) [0x829ba16]
#7 ./ssam_lnx(SDL_InitSubSystem+0x39) [0x82938e9]
#8 ./ssam_lnx(SDL_Init+0x18) [0x82939c8]
#9 ./ssam_lnx(Init__FPviG8CTString+0x29) [0x80c6bc5]
#10 ./ssam_lnx(SubMain__FPvT0Pci+0x2f) [0x80c8a6f]
#11 ./ssam_lnx(CommonMainline__FPvT0Pci+0x23) [0x80c94ab]
#12 ./ssam_lnx(main+0xfe) [0x80c95ce]
#13 /lib32/libc.so.6(__libc_start_main+0xe5) [0xf7c7742d]
#14 ./ssam_lnx(XMapRaised+0x39) [0x80c34c1]
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf7c5f767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xf7c5f81e]
#2 /usr/lib32/libX11.so.6 [0xf7e05dc9]
#3 /usr/lib32/libX11.so.6(XQueryExtension+0x26) [0xf7df3cf6]
#4 /usr/lib32/libX11.so.6(XInitExtension+0x41) [0xf7de82f1]
#5 /usr/lib32/libXext.so.6(XextAddDisplay+0x50) [0xf7dbf240]
#6 ./ssam_lnx [0x8300de5]
#7 ./ssam_lnx(XiGMiscQueryVersion+0x14) [0x8300e00]
#8 ./ssam_lnx(X11_GetVideoModes+0x3b9) [0x82c0851]
#9 ./ssam_lnx [0x829ee68]
#10 ./ssam_lnx(SDL_VideoInit+0x2b2) [0x829ba16]
#11 ./ssam_lnx(SDL_InitSubSystem+0x39) [0x82938e9]
#12 ./ssam_lnx(SDL_Init+0x18) [0x82939c8]
#13 ./ssam_lnx(Init__FPviG8CTString+0x29) [0x80c6bc5]
#14 ./ssam_lnx(SubMain__FPvT0Pci+0x2f) [0x80c8a6f]
#15 ./ssam_lnx(CommonMainline__FPvT0Pci+0x23) [0x80c94ab]
#16 ./ssam_lnx(main+0xfe) [0x80c95ce]
#17 /lib32/libc.so.6(__libc_start_main+0xe5) [0xf7c7742d]
#18 ./ssam_lnx(XMapRaised+0x39) [0x80c34c1]
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf7c5f767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xf7c5f8b1]
#2 /usr/lib32/libX11.so.6(_XReply+0x244) [0xf7e06c14]
#3 ./ssam_lnx(SDL_XineramaIsActive+0x76) [0x82c66ba]
#4 ./ssam_lnx(X11_GetVideoModes+0x857) [0x82c0cef]
#5 ./ssam_lnx [0x829ee68]
#6 ./ssam_lnx(SDL_VideoInit+0x2b2) [0x829ba16]
#7 ./ssam_lnx(SDL_InitSubSystem+0x39) [0x82938e9]
#8 ./ssam_lnx(SDL_Init+0x18) [0x82939c8]
#9 ./ssam_lnx(Init__FPviG8CTString+0x29) [0x80c6bc5]
#10 ./ssam_lnx(SubMain__FPvT0Pci+0x2f) [0x80c8a6f]
#11 ./ssam_lnx(CommonMainline__FPvT0Pci+0x23) [0x80c94ab]
#12 ./ssam_lnx(main+0xfe) [0x80c95ce]
#13 /lib32/libc.so.6(__libc_start_main+0xe5) [0xf7c7742d]
#14 ./ssam_lnx(XMapRaised+0x39) [0x80c34c1]
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf7c5f767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xf7c5f81e]
#2 /usr/lib32/libX11.so.6 [0xf7e05dc9]
#3 /usr/lib32/libX11.so.6(XCreateColormap+0x26) [0xf7ddb0f6]
#4 ./ssam_lnx [0x829efa0]
#5 ./ssam_lnx(SDL_VideoInit+0x2b2) [0x829ba16]
#6 ./ssam_lnx(SDL_InitSubSystem+0x39) [0x82938e9]
#7 ./ssam_lnx(SDL_Init+0x18) [0x82939c8]
#8 ./ssam_lnx(Init__FPviG8CTString+0x29) [0x80c6bc5]
#9 ./ssam_lnx(SubMain__FPvT0Pci+0x2f) [0x80c8a6f]
#10 ./ssam_lnx(CommonMainline__FPvT0Pci+0x23) [0x80c94ab]
#11 ./ssam_lnx(main+0xfe) [0x80c95ce]
#12 /lib32/libc.so.6(__libc_start_main+0xe5) [0xf7c7742d]
#13 ./ssam_lnx(XMapRaised+0x39) [0x80c34c1]
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf7c5f767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xf7c5f8b1]
#2 /usr/lib32/libX11.so.6(_XReply+0x244) [0xf7e06c14]
#3 ./ssam_lnx(SDL_XF86VidModeGetGamma+0x9a) [0x82c202e]
#4 ./ssam_lnx [0x82be7e9]
#5 ./ssam_lnx(X11_SaveVidModeGamma+0x36) [0x82be89a]
#6 ./ssam_lnx [0x829f02b]
#7 ./ssam_lnx(SDL_VideoInit+0x2b2) [0x829ba16]
#8 ./ssam_lnx(SDL_InitSubSystem+0x39) [0x82938e9]
#9 ./ssam_lnx(SDL_Init+0x18) [0x82939c8]
#10 ./ssam_lnx(Init__FPviG8CTString+0x29) [0x80c6bc5]
#11 ./ssam_lnx(SubMain__FPvT0Pci+0x2f) [0x80c8a6f]
#12 ./ssam_lnx(CommonMainline__FPvT0Pci+0x23) [0x80c94ab]
#13 ./ssam_lnx(main+0xfe) [0x80c95ce]
#14 /lib32/libc.so.6(__libc_start_main+0xe5) [0xf7c7742d]
#15 ./ssam_lnx(XMapRaised+0x39) [0x80c34c1]
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf7c5f767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xf7c5f81e]
#2 /usr/lib32/libX11.so.6 [0xf7e05dc9]
#3 /usr/lib32/libX11.so.6(XCreateWindow+0x26) [0xf7dfc696]
#4 ./ssam_lnx [0x829ea09]
#5 ./ssam_lnx [0x829f051]
#6 ./ssam_lnx(SDL_VideoInit+0x2b2) [0x829ba16]
#7 ./ssam_lnx(SDL_InitSubSystem+0x39) [0x82938e9]
#8 ./ssam_lnx(SDL_Init+0x18) [0x82939c8]
#9 ./ssam_lnx(Init__FPviG8CTString+0x29) [0x80c6bc5]
#10 ./ssam_lnx(SubMain__FPvT0Pci+0x2f) [0x80c8a6f]
#11 ./ssam_lnx(CommonMainline__FPvT0Pci+0x23) [0x80c94ab]
#12 ./ssam_lnx(main+0xfe) [0x80c95ce]
#13 /lib32/libc.so.6(__libc_start_main+0xe5) [0xf7c7742d]
#14 ./ssam_lnx(XMapRaised+0x39) [0x80c34c1]
STUB: load window icon in SeriousSam/MainWindow.cpp, line 153.
STUB: Need SDL invisible window or something in SeriousSam/MainWindow.cpp, line 356.
INFO: "SeriousSam is starting for the first time.
If you experience any problems, please consult
ReadMe file for troubleshooting information."
ALSA lib pcm_plug.c:1110:(_snd_pcm_plug_open) Unknown field hint
ALSA lib pcm_plug.c:1110:(_snd_pcm_plug_open) Unknown field hint
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf7c5f767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xf7c5f8b1]
#2 /usr/lib32/libX11.so.6(_XReply+0x244) [0xf7e06c14]
#3 ./ssam_lnx(SDL_XDGAQueryVersion+0x93) [0x82c4177]
#4 ./ssam_lnx(SDL_XF86DGAQueryVersion+0x26) [0x82c53fe]
#5 ./ssam_lnx(X11_EnableDGAMouse+0xdf) [0x82bd0d3]
#6 ./ssam_lnx(X11_CheckMouseModeNoLock+0x8e) [0x82c1ace]
#7 ./ssam_lnx(X11_CheckMouseMode+0x24) [0x82c1bbc]
#8 ./ssam_lnx [0x829e306]
#9 ./ssam_lnx(SDL_WM_GrabInput+0x63) [0x829e383]
#10 ./ssam_lnx [0x80f44b0]
#11 ./ssam_lnx(OpenMainWindowFullScreen__Fll+0x46) [0x80f466a]
#12 ./ssam_lnx(TryToSetDisplayMode__F10GfxAPITypelll12DisplayDepthi+0x134) [0x80c9784]
#13 ./ssam_lnx(StartNewMode__F10GfxAPITypelll12DisplayDepthi+0x44) [0x80c9b68]
#14 ./ssam_lnx(Init__FPviG8CTString+0xa13) [0x80c75af]
#15 ./ssam_lnx(SubMain__FPvT0Pci+0x2f) [0x80c8a6f]
#16 ./ssam_lnx(CommonMainline__FPvT0Pci+0x23) [0x80c94ab]
#17 ./ssam_lnx(main+0xfe) [0x80c95ce]
#18 /lib32/libc.so.6(__libc_start_main+0xe5) [0xf7c7742d]
#19 ./ssam_lnx(XMapRaised+0x39) [0x80c34c1]
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf7c5f767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xf7c5f81e]
#2 /usr/lib32/libX11.so.6 [0xf7e05dc9]
#3 /usr/lib32/libX11.so.6(XESetWireToEvent+0x33) [0xf7de7e83]
#4 ./ssam_lnx(SDL_XDGAQueryVersion+0x10a) [0x82c41ee]
#5 ./ssam_lnx(SDL_XF86DGAQueryVersion+0x26) [0x82c53fe]
#6 ./ssam_lnx(X11_EnableDGAMouse+0xdf) [0x82bd0d3]
#7 ./ssam_lnx(X11_CheckMouseModeNoLock+0x8e) [0x82c1ace]
#8 ./ssam_lnx(X11_CheckMouseMode+0x24) [0x82c1bbc]
#9 ./ssam_lnx [0x829e306]
#10 ./ssam_lnx(SDL_WM_GrabInput+0x63) [0x829e383]
#11 ./ssam_lnx [0x80f44b0]
#12 ./ssam_lnx(OpenMainWindowFullScreen__Fll+0x46) [0x80f466a]
#13 ./ssam_lnx(TryToSetDisplayMode__F10GfxAPITypelll12DisplayDepthi+0x134) [0x80c9784]
#14 ./ssam_lnx(StartNewMode__F10GfxAPITypelll12DisplayDepthi+0x44) [0x80c9b68]
#15 ./ssam_lnx(Init__FPviG8CTString+0xa13) [0x80c75af]
#16 ./ssam_lnx(SubMain__FPvT0Pci+0x2f) [0x80c8a6f]
#17 ./ssam_lnx(CommonMainline__FPvT0Pci+0x23) [0x80c94ab]
#18 ./ssam_lnx(main+0xfe) [0x80c95ce]
#19 /lib32/libc.so.6(__libc_start_main+0xe5) [0xf7c7742d]
ssam_lnx: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
./ssamtfe: line 123:  5550 Aborted                 ./${GAME_BINARY} ${CMD_ARGS} "$@"

```

Terminal output with './ssamtse'

```
hzf@hzf-desktop:~$ cd ssamtse
hzf@hzf-desktop:~/ssamtse$ ./ssamtse
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf7cb9767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xf7cb98b1]
#2 /usr/lib32/libX11.so.6(_XReply+0x244) [0xf7e60c14]
#3 ./ssam_lnx(SDL_XF86VidModeQueryVersion+0x8d) [0x82c1f4d]
#4 ./ssam_lnx(X11_GetVideoModes+0x170) [0x82c07f8]
#5 ./ssam_lnx [0x829f058]
#6 ./ssam_lnx(SDL_VideoInit+0x2b2) [0x829bc06]
#7 ./ssam_lnx(SDL_InitSubSystem+0x39) [0x8293ad9]
#8 ./ssam_lnx(SDL_Init+0x18) [0x8293bb8]
#9 ./ssam_lnx(Init__FPviG8CTString+0x29) [0x80c6bc5]
#10 ./ssam_lnx(SubMain__FPvT0Pci+0x2f) [0x80c8a6f]
#11 ./ssam_lnx(CommonMainline__FPvT0Pci+0x23) [0x80c94ab]
#12 ./ssam_lnx(main+0xfe) [0x80c95ce]
#13 /lib32/libc.so.6(__libc_start_main+0xe5) [0xf7cd142d]
#14 ./ssam_lnx(XMapRaised+0x39) [0x80c34c1]
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf7cb9767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xf7cb981e]
#2 /usr/lib32/libX11.so.6 [0xf7e5fdc9]
#3 /usr/lib32/libX11.so.6(XQueryExtension+0x26) [0xf7e4dcf6]
#4 /usr/lib32/libX11.so.6(XInitExtension+0x41) [0xf7e422f1]
#5 /usr/lib32/libXext.so.6(XextAddDisplay+0x50) [0xf7e19240]
#6 ./ssam_lnx [0x8300fd5]
#7 ./ssam_lnx(XiGMiscQueryVersion+0x14) [0x8300ff0]
#8 ./ssam_lnx(X11_GetVideoModes+0x3b9) [0x82c0a41]
#9 ./ssam_lnx [0x829f058]
#10 ./ssam_lnx(SDL_VideoInit+0x2b2) [0x829bc06]
#11 ./ssam_lnx(SDL_InitSubSystem+0x39) [0x8293ad9]
#12 ./ssam_lnx(SDL_Init+0x18) [0x8293bb8]
#13 ./ssam_lnx(Init__FPviG8CTString+0x29) [0x80c6bc5]
#14 ./ssam_lnx(SubMain__FPvT0Pci+0x2f) [0x80c8a6f]
#15 ./ssam_lnx(CommonMainline__FPvT0Pci+0x23) [0x80c94ab]
#16 ./ssam_lnx(main+0xfe) [0x80c95ce]
#17 /lib32/libc.so.6(__libc_start_main+0xe5) [0xf7cd142d]
#18 ./ssam_lnx(XMapRaised+0x39) [0x80c34c1]
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf7cb9767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xf7cb98b1]
#2 /usr/lib32/libX11.so.6(_XReply+0x244) [0xf7e60c14]
#3 ./ssam_lnx(SDL_XineramaIsActive+0x76) [0x82c68aa]
#4 ./ssam_lnx(X11_GetVideoModes+0x857) [0x82c0edf]
#5 ./ssam_lnx [0x829f058]
#6 ./ssam_lnx(SDL_VideoInit+0x2b2) [0x829bc06]
#7 ./ssam_lnx(SDL_InitSubSystem+0x39) [0x8293ad9]
#8 ./ssam_lnx(SDL_Init+0x18) [0x8293bb8]
#9 ./ssam_lnx(Init__FPviG8CTString+0x29) [0x80c6bc5]
#10 ./ssam_lnx(SubMain__FPvT0Pci+0x2f) [0x80c8a6f]
#11 ./ssam_lnx(CommonMainline__FPvT0Pci+0x23) [0x80c94ab]
#12 ./ssam_lnx(main+0xfe) [0x80c95ce]
#13 /lib32/libc.so.6(__libc_start_main+0xe5) [0xf7cd142d]
#14 ./ssam_lnx(XMapRaised+0x39) [0x80c34c1]
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf7cb9767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xf7cb981e]
#2 /usr/lib32/libX11.so.6 [0xf7e5fdc9]
#3 /usr/lib32/libX11.so.6(XCreateColormap+0x26) [0xf7e350f6]
#4 ./ssam_lnx [0x829f190]
#5 ./ssam_lnx(SDL_VideoInit+0x2b2) [0x829bc06]
#6 ./ssam_lnx(SDL_InitSubSystem+0x39) [0x8293ad9]
#7 ./ssam_lnx(SDL_Init+0x18) [0x8293bb8]
#8 ./ssam_lnx(Init__FPviG8CTString+0x29) [0x80c6bc5]
#9 ./ssam_lnx(SubMain__FPvT0Pci+0x2f) [0x80c8a6f]
#10 ./ssam_lnx(CommonMainline__FPvT0Pci+0x23) [0x80c94ab]
#11 ./ssam_lnx(main+0xfe) [0x80c95ce]
#12 /lib32/libc.so.6(__libc_start_main+0xe5) [0xf7cd142d]
#13 ./ssam_lnx(XMapRaised+0x39) [0x80c34c1]
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf7cb9767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xf7cb98b1]
#2 /usr/lib32/libX11.so.6(_XReply+0x244) [0xf7e60c14]
#3 ./ssam_lnx(SDL_XF86VidModeGetGamma+0x9a) [0x82c221e]
#4 ./ssam_lnx [0x82be9d9]
#5 ./ssam_lnx(X11_SaveVidModeGamma+0x36) [0x82bea8a]
#6 ./ssam_lnx [0x829f21b]
#7 ./ssam_lnx(SDL_VideoInit+0x2b2) [0x829bc06]
#8 ./ssam_lnx(SDL_InitSubSystem+0x39) [0x8293ad9]
#9 ./ssam_lnx(SDL_Init+0x18) [0x8293bb8]
#10 ./ssam_lnx(Init__FPviG8CTString+0x29) [0x80c6bc5]
#11 ./ssam_lnx(SubMain__FPvT0Pci+0x2f) [0x80c8a6f]
#12 ./ssam_lnx(CommonMainline__FPvT0Pci+0x23) [0x80c94ab]
#13 ./ssam_lnx(main+0xfe) [0x80c95ce]
#14 /lib32/libc.so.6(__libc_start_main+0xe5) [0xf7cd142d]
#15 ./ssam_lnx(XMapRaised+0x39) [0x80c34c1]
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf7cb9767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xf7cb981e]
#2 /usr/lib32/libX11.so.6 [0xf7e5fdc9]
#3 /usr/lib32/libX11.so.6(XCreateWindow+0x26) [0xf7e56696]
#4 ./ssam_lnx [0x829ebf9]
#5 ./ssam_lnx [0x829f241]
#6 ./ssam_lnx(SDL_VideoInit+0x2b2) [0x829bc06]
#7 ./ssam_lnx(SDL_InitSubSystem+0x39) [0x8293ad9]
#8 ./ssam_lnx(SDL_Init+0x18) [0x8293bb8]
#9 ./ssam_lnx(Init__FPviG8CTString+0x29) [0x80c6bc5]
#10 ./ssam_lnx(SubMain__FPvT0Pci+0x2f) [0x80c8a6f]
#11 ./ssam_lnx(CommonMainline__FPvT0Pci+0x23) [0x80c94ab]
#12 ./ssam_lnx(main+0xfe) [0x80c95ce]
#13 /lib32/libc.so.6(__libc_start_main+0xe5) [0xf7cd142d]
#14 ./ssam_lnx(XMapRaised+0x39) [0x80c34c1]
STUB: load window icon in SeriousSam/MainWindow.cpp, line 153.
STUB: Need SDL invisible window or something in SeriousSam/MainWindow.cpp, line 356.
INFO: "SeriousSam is starting for the first time.
If you experience any problems, please consult
ReadMe file for troubleshooting information."
ALSA lib pcm_plug.c:1110:(_snd_pcm_plug_open) Unknown field hint
ALSA lib pcm_plug.c:1110:(_snd_pcm_plug_open) Unknown field hint
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf7cb9767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xf7cb98b1]
#2 /usr/lib32/libX11.so.6(_XReply+0x244) [0xf7e60c14]
#3 ./ssam_lnx(SDL_XDGAQueryVersion+0x93) [0x82c4367]
#4 ./ssam_lnx(SDL_XF86DGAQueryVersion+0x26) [0x82c55ee]
#5 ./ssam_lnx(X11_EnableDGAMouse+0xdf) [0x82bd2c3]
#6 ./ssam_lnx(X11_CheckMouseModeNoLock+0x8e) [0x82c1cbe]
#7 ./ssam_lnx(X11_CheckMouseMode+0x24) [0x82c1dac]
#8 ./ssam_lnx [0x829e4f6]
#9 ./ssam_lnx(SDL_WM_GrabInput+0x63) [0x829e573]
#10 ./ssam_lnx [0x80f44b0]
#11 ./ssam_lnx(OpenMainWindowFullScreen__Fll+0x46) [0x80f466a]
#12 ./ssam_lnx(TryToSetDisplayMode__F10GfxAPITypelll12DisplayDepthi+0x134) [0x80c9784]
#13 ./ssam_lnx(StartNewMode__F10GfxAPITypelll12DisplayDepthi+0x44) [0x80c9b68]
#14 ./ssam_lnx(Init__FPviG8CTString+0xa13) [0x80c75af]
#15 ./ssam_lnx(SubMain__FPvT0Pci+0x2f) [0x80c8a6f]
#16 ./ssam_lnx(CommonMainline__FPvT0Pci+0x23) [0x80c94ab]
#17 ./ssam_lnx(main+0xfe) [0x80c95ce]
#18 /lib32/libc.so.6(__libc_start_main+0xe5) [0xf7cd142d]
#19 ./ssam_lnx(XMapRaised+0x39) [0x80c34c1]
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf7cb9767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xf7cb981e]
#2 /usr/lib32/libX11.so.6 [0xf7e5fdc9]
#3 /usr/lib32/libX11.so.6(XESetWireToEvent+0x33) [0xf7e41e83]
#4 ./ssam_lnx(SDL_XDGAQueryVersion+0x10a) [0x82c43de]
#5 ./ssam_lnx(SDL_XF86DGAQueryVersion+0x26) [0x82c55ee]
#6 ./ssam_lnx(X11_EnableDGAMouse+0xdf) [0x82bd2c3]
#7 ./ssam_lnx(X11_CheckMouseModeNoLock+0x8e) [0x82c1cbe]
#8 ./ssam_lnx(X11_CheckMouseMode+0x24) [0x82c1dac]
#9 ./ssam_lnx [0x829e4f6]
#10 ./ssam_lnx(SDL_WM_GrabInput+0x63) [0x829e573]
#11 ./ssam_lnx [0x80f44b0]
#12 ./ssam_lnx(OpenMainWindowFullScreen__Fll+0x46) [0x80f466a]
#13 ./ssam_lnx(TryToSetDisplayMode__F10GfxAPITypelll12DisplayDepthi+0x134) [0x80c9784]
#14 ./ssam_lnx(StartNewMode__F10GfxAPITypelll12DisplayDepthi+0x44) [0x80c9b68]
#15 ./ssam_lnx(Init__FPviG8CTString+0xa13) [0x80c75af]
#16 ./ssam_lnx(SubMain__FPvT0Pci+0x2f) [0x80c8a6f]
#17 ./ssam_lnx(CommonMainline__FPvT0Pci+0x23) [0x80c94ab]
#18 ./ssam_lnx(main+0xfe) [0x80c95ce]
#19 /lib32/libc.so.6(__libc_start_main+0xe5) [0xf7cd142d]
ssam_lnx: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
./ssamtse: line 123:  5615 Aborted                 ./${GAME_BINARY} ${CMD_ARGS} "$@"

```

Needless to say, I have all the dependecies installed.

Maybe we can all figure out how to work around this problem?

Thanks for your help. :-)

---

### Post by dudeofthedead on 2008-08-28
I've found this [link](http://liflg.org/forum/viewtopic.php?t=923&highlight=serious+usam), which states this problem of mine is a known bug.  However, the help page it refers you to just loads and then dies.

---

### Post by markharding557 on 2008-08-30
just a thought but does it work on 32bit debian or ubuntu

---

### Post by agentunix on 2008-09-04
Hi, I had the same error but I found a solution for myself, maybe you can try it. Go into your Serious Sam install and change directory to 'Bin'. Try executing ssam_lnx.dynamic
It should try using dynamic libraries instead of the static ones included with the Serious Sam binary, is my understanding. It should run fine, if you want to make the change permanent you can open up your 'ssamtfe' and 'ssamtse' scripts with your favourite text editor. Change GAME_BINARY="ssam_lnx" to GAME_BINARY="ssam_lnx.dynamic".

Hope this resolves your problems! :)

---

### Post by lordxale on 2008-12-06
> **agentunix said:**
> Hi, I had the same error but I found a solution for myself, maybe you can try it. Go into your Serious Sam install and change directory to 'Bin'. Try executing ssam_lnx.dynamic
It should try using dynamic libraries instead of the static ones included with the Serious Sam binary, is my understanding. It should run fine, if you want to make the change permanent you can open up your 'ssamtfe' and 'ssamtse' scripts with your favourite text editor. Change GAME_BINARY="ssam_lnx" to GAME_BINARY="ssam_lnx.dynamic".

Hope this resolves your problems! :)

Works for me on Ubuntu 8.04 64-bit!  Thank you agentunix!

---

