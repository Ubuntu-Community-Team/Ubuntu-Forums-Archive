---
title: "Unreal Tournament 2003 on Kubuntu 7.10"
date: 2007-11-13
forum: Gaming &amp; Leisure
---

### Post by Walkboss on 2007-11-13
Hi all! I'm having issues installing (and running) UT2003 on my Kubuntu 7.10 box.

I installed UT2003 using the instructions via [this]("http://ubuntuforums.org/archive/index.php/t-420743.html") guide and I make it without a hitch to where you enter the CD key. I, like the author, had issues with the CDs keys somehow not matching. I Ctrl+C'd out of the terminal and made a file named "cdkey" containing my CD key in the folder /usr/local/games/ut2003/System/. When I run ./ut2003-bin I get this error:
```
[ 1]  ./Core.so [0xb752871a]
[ 2]  [0xffffe420]
[ 3]  /lib/tls/i686/cmov/libc.so.6(abort+0x101) [0xb72e5201]
[ 4]  /lib/tls/i686/cmov/libc.so.6(__assert_fail+0xee) [0xb72dcb6e]
[ 5]  /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x81) [0xb7188651]
[ 6]  /usr/lib/libX11.so.6(_XReply+0xff) [0xb720c16f]
[ 7]  ./libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xb7f2542d]
[ 8]  ./libSDL-1.2.so.0(X11_GetVideoModes+0x170) [0xb7f20428]
[ 9]  ./libSDL-1.2.so.0 [0xb7f22348]
[10]  ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7f17f96]
[11]  ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7efa4fe]
[12]  ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7efa5fc]
[13]  ./ut2003-bin(ValidateCDKey__Fv+0x119) [0x805139d]
[14]  ./ut2003-bin(main+0x1fbc) [0x805785c]
[15]  /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb72cf050]
[16]  ./ut2003-bin(ValidateCDKey__Fv+0x4d) [0x80512d1]
Signal: SIGIOT [iot trap]
Aborting.
```
Any help is appreciated help.

---

