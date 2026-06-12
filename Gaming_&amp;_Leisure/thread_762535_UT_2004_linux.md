---
title: "UT 2004 linux"
date: 2008-04-22
forum: Gaming &amp; Leisure
---

### Post by Predrag on 2008-04-22
hi i have installed ut 2004 but when i wanted to play tihis game i have this message

predrag@predrag:~/Plocha$ ut2004demo 
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7bb8767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7bb88b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb7c091bd]
#3 ./libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xb7e7a42d]
#4 ./libSDL-1.2.so.0(X11_GetVideoModes+0x170) [0xb7e75428]
#5 ./libSDL-1.2.so.0 [0xb7e77348]
#6 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7e6cf96]
#7 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7e4f4fe]
#8 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7e4f5fc]
#9 ./ut2004-bin(main+0x507f) [0x8154a2f]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7cc6450]
#11 ./ut2004-bin(getlogin+0xad) [0x814b121]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7bb8767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7bb881e]
#2 /usr/lib/libX11.so.6 [0xb7c08518]
#3 /usr/lib/libX11.so.6(XQueryExtension+0x26) [0xb7bf6fe6]
#4 /usr/lib/libX11.so.6(XInitExtension+0x3b) [0xb7bebd4b]
#5 /usr/lib/libXext.so.6(XextAddDisplay+0x53) [0xb7bc7443]
#6 ./libSDL-1.2.so.0 [0xb7ebf0e5]
#7 ./libSDL-1.2.so.0(XiGMiscQueryVersion+0x14) [0xb7ebf100]
#8 ./libSDL-1.2.so.0(X11_GetVideoModes+0x3b9) [0xb7e75671]
#9 ./libSDL-1.2.so.0 [0xb7e77348]
#10 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7e6cf96]
#11 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7e4f4fe]
#12 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7e4f5fc]
#13 ./ut2004-bin(main+0x507f) [0x8154a2f]
#14 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7cc6450]
#15 ./ut2004-bin(getlogin+0xad) [0x814b121]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7bb8767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7bb88b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb7c091bd]
#3 ./libSDL-1.2.so.0(SDL_XineramaIsActive+0x76) [0xb7e80a0a]
#4 ./libSDL-1.2.so.0(X11_GetVideoModes+0x857) [0xb7e75b0f]
#5 ./libSDL-1.2.so.0 [0xb7e77348]
#6 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7e6cf96]
#7 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7e4f4fe]
#8 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7e4f5fc]
#9 ./ut2004-bin(main+0x507f) [0x8154a2f]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7cc6450]
#11 ./ut2004-bin(getlogin+0xad) [0x814b121]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7bb8767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7bb881e]
#2 /usr/lib/libX11.so.6 [0xb7c08518]
#3 /usr/lib/libX11.so.6(XCreateColormap+0x26) [0xb7bdee76]
#4 ./libSDL-1.2.so.0 [0xb7e77480]
#5 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7e6cf96]
#6 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7e4f4fe]
#7 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7e4f5fc]
#8 ./ut2004-bin(main+0x507f) [0x8154a2f]
#9 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7cc6450]
#10 ./ut2004-bin(getlogin+0xad) [0x814b121]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7bb8767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7bb88b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb7c091bd]
#3 ./libSDL-1.2.so.0(SDL_XF86VidModeGetGamma+0x9a) [0xb7e7a6fe]
#4 ./libSDL-1.2.so.0 [0xb7e73609]
#5 ./libSDL-1.2.so.0(X11_SaveVidModeGamma+0x36) [0xb7e736ba]
#6 ./libSDL-1.2.so.0 [0xb7e7750b]
#7 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7e6cf96]
#8 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7e4f4fe]
#9 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7e4f5fc]
#10 ./ut2004-bin(main+0x507f) [0x8154a2f]
#11 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7cc6450]
#12 ./ut2004-bin(getlogin+0xad) [0x814b121]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7bb8767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7bb881e]
#2 /usr/lib/libX11.so.6 [0xb7c08518]
#3 /usr/lib/libX11.so.6(XCreateWindow+0x26) [0xb7bff616]
#4 ./libSDL-1.2.so.0 [0xb7e76ee9]
#5 ./libSDL-1.2.so.0 [0xb7e77531]
#6 ./libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7e6cf96]
#7 ./libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7e4f4fe]
#8 ./libSDL-1.2.so.0(SDL_Init+0x24) [0xb7e4f5fc]
#9 ./ut2004-bin(main+0x507f) [0x8154a2f]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7cc6450]
#11 ./ut2004-bin(getlogin+0xad) [0x814b121]
Can't find 'ini:Engine.Engine.GameEngine' in configuration file

History: 

Exiting due to error

---

### Post by Perfect Storm on 2008-04-22
Are you using 64-bit OS?

---

### Post by Predrag on 2008-04-22
no im using 32 bit os. hardy 8.04 alpha 6

---

### Post by Perfect Storm on 2008-04-22
> **Predrag said:**
> no im using 32 bit os. hardy 8.04 alpha 6

Maybe updating Hardy to RC could fix your problem.

Also I don't know if the demo have been patched. See if you can find a demo of UT2004 that have been patched.

---

### Post by Joeb454 on 2008-04-22
Do you have the UT 2004 disc? Not all of them...but quite a lot, have a Linux installer on them :) I know mine does.

Also if you have kept your Hardy install up-to-date, then you will be running the Hardy RC :)

---

### Post by Perfect Storm on 2008-04-22
> **Joeb454 said:**
> Do you have the UT 2004 disc? Not all of them...but quite a lot, have a Linux installer on them :) I know mine does.

Also if you have kept your Hardy install up-to-date, then you will be running the Hardy RC :)

It says ut2004demo ;)

---

### Post by madsmeg on 2008-04-22
Yeah Joeb454 learn2read :p, but as AI says, upgrade to the RC, though i have had some issues with gaming in Hardy.

---

### Post by Predrag on 2008-04-22
i will try it install on gutsy.i hope that it helps.

---

### Post by madsmeg on 2008-04-22
Good luck and let us know how you get on.

---

### Post by Joeb454 on 2008-04-22
:lolflag: My mistake :) **madsmeg** I knew you'd have me on that one...you always bully me :p

---

### Post by Perfect Storm on 2008-04-22
> **Joeb454 said:**
> :lolflag: My mistake :) **madsmeg** I knew you'd have me on that one...you always bully me :p

I'll just infract madsmeg for that :lolflag: :mrgreen:

---

### Post by Joeb454 on 2008-04-22
:lolflag: Don't do that! Well...you could, but Don't do it just because I said that, it stems from IRC :p

---

