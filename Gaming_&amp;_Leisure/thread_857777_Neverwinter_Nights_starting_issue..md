---
title: "Neverwinter Nights starting issue."
date: 2008-07-12
forum: Gaming &amp; Leisure
---

### Post by senkila on 2008-07-12
Allo! Recently installed Neverwinter Nights for linux, everything went fine apart from running it.I've narrowed it down to a SDL issue, however..I'm utterly lost on what to do. Here's the output.

```
scarlet@e-v-a:~$ cd nwn
scarlet@e-v-a:~/nwn$ ./nwn
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6cb2767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb6cb28b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb6dfa1bd]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xb7d7753d]
#4 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x164) [0xb7d7278c]
#5 ./lib/libSDL-1.2.so.0 [0xb7d74457]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d69f66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7d4c7de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7d4c8dc]
#9 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7c08450]
#11 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6cb2767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb6cb281e]
#2 /usr/lib/libX11.so.6 [0xb6df9518]
#3 /usr/lib/libX11.so.6(XMatchVisualInfo+0x40) [0xb6deff70]
#4 ./lib/libSDL-1.2.so.0 [0xb7d7251a]
#5 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x408) [0xb7d72a30]
#6 ./lib/libSDL-1.2.so.0 [0xb7d74457]
#7 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d69f66]
#8 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7d4c7de]
#9 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7d4c8dc]
#10 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#11 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7c08450]
#12 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6cb2767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb6cb28b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb6dfa1bd]
#3 ./lib/libSDL-1.2.so.0(SDL_XineramaIsActive+0x76) [0xb7d7db1a]
#4 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x673) [0xb7d72c9b]
#5 ./lib/libSDL-1.2.so.0 [0xb7d74457]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d69f66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7d4c7de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7d4c8dc]
#9 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7c08450]
#11 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6cb2767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb6cb281e]
#2 /usr/lib/libX11.so.6 [0xb6df9518]
#3 /usr/lib/libX11.so.6(XCreateColormap+0x26) [0xb6dcfe76]
#4 ./lib/libSDL-1.2.so.0 [0xb7d74584]
#5 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d69f66]
#6 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7d4c7de]
#7 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7d4c8dc]
#8 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#9 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7c08450]
#10 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6cb2767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb6cb28b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb6dfa1bd]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeGetGamma+0x9a) [0xb7d7780e]
#4 ./lib/libSDL-1.2.so.0 [0xb7d70a89]
#5 ./lib/libSDL-1.2.so.0(X11_SaveVidModeGamma+0x36) [0xb7d70b3a]
#6 ./lib/libSDL-1.2.so.0 [0xb7d7460f]
#7 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d69f66]
#8 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7d4c7de]
#9 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7d4c8dc]
#10 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#11 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7c08450]
#12 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6cb2767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb6cb281e]
#2 /usr/lib/libX11.so.6 [0xb6df9518]
#3 /usr/lib/libX11.so.6(XCreateWindow+0x26) [0xb6df0616]
#4 ./lib/libSDL-1.2.so.0 [0xb7d73ff3]
#5 ./lib/libSDL-1.2.so.0 [0xb7d74635]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d69f66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7d4c7de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7d4c8dc]
#9 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7c08450]
#11 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6cb2767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb6cb28b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb6dfa1bd]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xb7d7753d]
#4 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeGetModeLine+0x5b) [0xb7d778e7]
#5 ./lib/libSDL-1.2.so.0 [0xb7d72368]
#6 ./lib/libSDL-1.2.so.0(X11_EnterFullScreen+0x72) [0xb7d73092]
#7 ./lib/libSDL-1.2.so.0 [0xb7d75375]
#8 ./lib/libSDL-1.2.so.0 [0xb7d7552b]
#9 ./lib/libSDL-1.2.so.0(SDL_SetVideoMode+0x1b3) [0xb7d6a7df]
#10 ./nwmain [0x84d1b4d]
#11 ./nwmain(strftime+0x1dfd) [0x80508b5]
#12 ./nwmain [0x805d896]
#13 ./nwmain [0x805adc0]
#14 ./nwmain [0x8059ae5]
#15 ./nwmain(SDL_SetVideoMode+0x45f) [0x804fb57]
#16 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7c08450]
#17 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6cb2767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb6cb281e]
#2 /usr/lib/libX11.so.6 [0xb6df9518]
#3 /usr/lib/libX11.so.6(XMoveResizeWindow+0x25) [0xb6dcf165]
#4 ./lib/libSDL-1.2.so.0(X11_EnterFullScreen+0xd4) [0xb7d730f4]
#5 ./lib/libSDL-1.2.so.0 [0xb7d75375]
#6 ./lib/libSDL-1.2.so.0 [0xb7d7552b]
#7 ./lib/libSDL-1.2.so.0(SDL_SetVideoMode+0x1b3) [0xb7d6a7df]
#8 ./nwmain [0x84d1b4d]
#9 ./nwmain(strftime+0x1dfd) [0x80508b5]
#10 ./nwmain [0x805d896]
#11 ./nwmain [0x805adc0]
#12 ./nwmain [0x8059ae5]
#13 ./nwmain(SDL_SetVideoMode+0x45f) [0x804fb57]
#14 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7c08450]
#15 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
nwmain: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
Aborted
```

---

### Post by NovruzeliH on 2008-07-13
there is something wrong with the files, it cannot play it, uhh try installing from other places, then retry, it

---

### Post by senkila on 2008-07-14
Funnily enough, to install the linux client for NWN, all the resources are on the Bioware website, all you have to do is extract the files from the archives and run.

---

### Post by senkila on 2008-07-14
Bump.

---

### Post by PandaGoat on 2008-07-15
Try using a different compiled version of SDL.  I compiled it so I could use alt+enter to enter windowed mode.  Attached are the shared libs I am using.  Replace the ones in [install dir]/nwn/libs with the attached files.

---

### Post by senkila on 2008-07-17
Wonderful! It works!

What did you do when compiling them, just for your system? I'm running on 64-bit arch so that might have been a problem.

Amazing how I can get NWN2 working, but not NWN1 XP

Thanks once again PandaGoat

---

### Post by Perfect Storm on 2008-07-17
You could also just deleted the sdl string the nwn script that pinpoint it to use its own sdl-libs instead.

---

