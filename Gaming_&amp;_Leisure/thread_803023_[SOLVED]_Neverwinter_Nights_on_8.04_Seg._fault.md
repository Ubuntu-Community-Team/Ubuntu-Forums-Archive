---
title: "[SOLVED] Neverwinter Nights on 8.04 Seg. fault"
date: 2008-05-21
forum: Gaming &amp; Leisure
---

### Post by Geezle on 2008-05-21
Well I've made a couple halfhearted attempts to get NWN running since I installed Hardy but I just haven't had any luck with it.  I'm at the point where I'm doing a fresh install of NWN using the linux resources from Bioware's site.  

Anyway, I install like I have before, but when I try to run nwn I get a segmentation fault and no other output.  I've tried modifying my nwn file and removed the reference to ./lib and I ran ./fixinstall but still no dice.  Also tried running with sudo with no luck.  Any help would be greatly appreciated as I have some free time on my hands and I would love to get back into this game.

Thanks.

Edit: I'm running this on an AMD64 system.

---

### Post by ajmorris on 2008-05-23
hi there,
is this the diamond/gold edition? or is this the normal cds, and you are using the linux packages from bioware to install them.

AJ

---

### Post by cprofitt on 2008-05-25
ajmorris -- does the diamond edition have the linux installer on the CDs?

---

### Post by Geezle on 2008-05-26
> **ajmorris said:**
> hi there,
is this the diamond/gold edition? or is this the normal cds, and you are using the linux packages from bioware to install them.

AJ
Yes, I'm using the linux packages from Bioware's site to install, so I'm presuming that it's just the regular edition and not the diamond/gold edition.

Any help with this would be awesome, I just found out I'll be off work for another week and I'd love to have my game back to burn some time.

Thanks!

---

### Post by Geezle on 2008-05-26
Well, I just recently installed my Hardy updates and just for kicks, I decided to try running NWN again.  

Well, now I'm no longer getting a segmentation fault...instead I get this:

```

jay@milehigh:/media/sdc6/nwn$ ./nwn
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf6ed3767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xf6ed38b1]
#2 /usr/lib32/libX11.so.6(_XReply+0xfd) [0xf701b1bd]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xf7d6d53d]
#4 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x164) [0xf7d6878c]
#5 ./lib/libSDL-1.2.so.0 [0xf7d6a457]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xf7d5ff66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xf7d427de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xf7d428dc]
#9 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#10 /lib32/libc.so.6(__libc_start_main+0xe0) [0xf7bfd450]
#11 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf6ed3767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xf6ed381e]
#2 /usr/lib32/libX11.so.6 [0xf701a518]
#3 /usr/lib32/libX11.so.6(XMatchVisualInfo+0x40) [0xf7010f70]
#4 ./lib/libSDL-1.2.so.0 [0xf7d6851a]
#5 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x408) [0xf7d68a30]
#6 ./lib/libSDL-1.2.so.0 [0xf7d6a457]
#7 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xf7d5ff66]
#8 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xf7d427de]
#9 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xf7d428dc]
#10 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#11 /lib32/libc.so.6(__libc_start_main+0xe0) [0xf7bfd450]
#12 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf6ed3767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xf6ed38b1]
#2 /usr/lib32/libX11.so.6(_XReply+0xfd) [0xf701b1bd]
#3 ./lib/libSDL-1.2.so.0(SDL_XineramaIsActive+0x76) [0xf7d73b1a]
#4 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x673) [0xf7d68c9b]
#5 ./lib/libSDL-1.2.so.0 [0xf7d6a457]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xf7d5ff66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xf7d427de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xf7d428dc]
#9 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#10 /lib32/libc.so.6(__libc_start_main+0xe0) [0xf7bfd450]
#11 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf6ed3767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xf6ed381e]
#2 /usr/lib32/libX11.so.6 [0xf701a518]
#3 /usr/lib32/libX11.so.6(XCreateColormap+0x26) [0xf6ff0e76]
#4 ./lib/libSDL-1.2.so.0 [0xf7d6a584]
#5 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xf7d5ff66]
#6 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xf7d427de]
#7 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xf7d428dc]
#8 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#9 /lib32/libc.so.6(__libc_start_main+0xe0) [0xf7bfd450]
#10 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf6ed3767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xf6ed38b1]
#2 /usr/lib32/libX11.so.6(_XReply+0xfd) [0xf701b1bd]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeGetGamma+0x9a) [0xf7d6d80e]
#4 ./lib/libSDL-1.2.so.0 [0xf7d66a89]
#5 ./lib/libSDL-1.2.so.0(X11_SaveVidModeGamma+0x36) [0xf7d66b3a]
#6 ./lib/libSDL-1.2.so.0 [0xf7d6a60f]
#7 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xf7d5ff66]
#8 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xf7d427de]
#9 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xf7d428dc]
#10 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#11 /lib32/libc.so.6(__libc_start_main+0xe0) [0xf7bfd450]
#12 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf6ed3767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xf6ed381e]
#2 /usr/lib32/libX11.so.6 [0xf701a518]
#3 /usr/lib32/libX11.so.6(XCreateWindow+0x26) [0xf7011616]
#4 ./lib/libSDL-1.2.so.0 [0xf7d69ff3]
#5 ./lib/libSDL-1.2.so.0 [0xf7d6a635]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xf7d5ff66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xf7d427de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xf7d428dc]
#9 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#10 /lib32/libc.so.6(__libc_start_main+0xe0) [0xf7bfd450]
#11 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf6ed3767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xf6ed38b1]
#2 /usr/lib32/libX11.so.6(_XReply+0xfd) [0xf701b1bd]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xf7d6d53d]
#4 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeGetModeLine+0x5b) [0xf7d6d8e7]
#5 ./lib/libSDL-1.2.so.0 [0xf7d68368]
#6 ./lib/libSDL-1.2.so.0(X11_EnterFullScreen+0x72) [0xf7d69092]
#7 ./lib/libSDL-1.2.so.0 [0xf7d6b375]
#8 ./lib/libSDL-1.2.so.0 [0xf7d6b52b]
#9 ./lib/libSDL-1.2.so.0(SDL_SetVideoMode+0x1b3) [0xf7d607df]
#10 ./nwmain [0x84d1b4d]
#11 ./nwmain(strftime+0x1dfd) [0x80508b5]
#12 ./nwmain [0x805d896]
#13 ./nwmain [0x805adc0]
#14 ./nwmain [0x8059ae5]
#15 ./nwmain(SDL_SetVideoMode+0x45f) [0x804fb57]
#16 /lib32/libc.so.6(__libc_start_main+0xe0) [0xf7bfd450]
#17 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf6ed3767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xf6ed381e]
#2 /usr/lib32/libX11.so.6 [0xf701a518]
#3 /usr/lib32/libX11.so.6(XMoveResizeWindow+0x25) [0xf6ff0165]
#4 ./lib/libSDL-1.2.so.0(X11_EnterFullScreen+0xd4) [0xf7d690f4]
#5 ./lib/libSDL-1.2.so.0 [0xf7d6b375]
#6 ./lib/libSDL-1.2.so.0 [0xf7d6b52b]
#7 ./lib/libSDL-1.2.so.0(SDL_SetVideoMode+0x1b3) [0xf7d607df]
#8 ./nwmain [0x84d1b4d]
#9 ./nwmain(strftime+0x1dfd) [0x80508b5]
#10 ./nwmain [0x805d896]
#11 ./nwmain [0x805adc0]
#12 ./nwmain [0x8059ae5]
#13 ./nwmain(SDL_SetVideoMode+0x45f) [0x804fb57]
#14 /lib32/libc.so.6(__libc_start_main+0xe0) [0xf7bfd450]
#15 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
nwmain: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
Aborted

```

I also tried running with sudo with the same results...anybody have any thoughts on this one?

---

### Post by Geezle on 2008-05-26
Nevermind that previous post...I realized that I had reinstalled NWN (again!) a few days ago and forgot about it...as soon as I removed the reference to ./lib I get my same ol' segmentation fault again.

```

jay@milehigh:/media/sdc6/nwn$ ./nwn
Segmentation fault

```

---

### Post by Perfect Storm on 2008-05-26
I read somewhere that someone deleted the sdl files in nwn folder, it's worth a try.

Have you tried re-download the files from bioware - maybe it's corrupt.

---

### Post by Geezle on 2008-05-26
> **Artificial Intelligence said:**
> I read somewhere that someone deleted the sdl files in nwn folder, it's worth a try.

Have you tried re-download the files from bioware - maybe it's corrupt.

I tried deleting the sdl files in the lib folder, but still get the same thing.  I'm going to try re-downloading the files from Bioware and see what happens a little later.

---

### Post by Geezle on 2008-05-27
Well, I think I figured it out...I'm reasonably sure I was using the 1.68 patch for Hordes of The Underdark instead of the patch for the original NWN campaign...I reinstalled everything with the proper patch and it seems to be working fine now.

I am having problems with it not showing all my saves so I'm set back a little in my progress of the game, but it's working again, and that's the most important thing.

Thanks guys!

---

