---
title: "Neverwinter Nights on Ubuntu 8.04"
date: 2008-03-09
forum: Gaming &amp; Leisure
---

### Post by bloodandsoil on 2008-03-09
Hi, I'm having a problem getting Neverwinter Nights working on Ubuntu 8.04.

I have my 3D drivers all setup correctly.  I followed the instructions from the NWN website exactly.

When I run ./nwn I get this error:

> Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6e42767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb6e428b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb6f8d29d]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xb7ce053d]
#4 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x164) [0xb7cdb78c]
#5 ./lib/libSDL-1.2.so.0 [0xb7cdd457]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7cd2f66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7cb57de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7cb58dc]
#9 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7b71450]
#11 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
nwmain: xcb_xlib.c:82: xcb_xlib_unlock: Assertion `c->xlib.lock' failed.
Aborted (core dumped)

I tried editing the nwn file and removing ./lib, and when I run ./nwn I get a black screen for a couple seconds, and then the game quits and the console has this error:

> Segmentation fault (core dumped)

Anyone know what the problem is?  Thanks.

---

### Post by roderick on 2008-03-09
It might be a permissions problem.

Did you run the fixinstall script to set permissions?

---

### Post by bloodandsoil on 2008-03-10
Yes, I did run ./fixinstall and it said everything was ok.  Yes, I also gave everything proper permissions.

Has anyone else gotten NWN to work under Ubuntu 8.04?

---

### Post by Perfect Storm on 2008-03-10
Check here: [http://ubuntuforums.org/showthread.php?t=666726](http://ubuntuforums.org/showthread.php?t=666726)

---

### Post by roderick on 2008-03-10
I have mine working, but I copied my install from a previous Gentoo install, and I have made lots of changes that deviate from the normal setup.

I am using an Intel 945 GME and it works flawlessly.

It's possible that the problem is with audio.

Instead of removing the ./lib in the path, why not rename or move the libSDL in the lib directory under nwn? Try that and see if you get any further.

Also, what are the contents of your nwn file (there are some SDL commands that should be set/included if not already that may help.

---

### Post by bloodandsoil on 2008-03-10
> **roderick said:**
> I have mine working, but I copied my install from a previous Gentoo install, and I have made lots of changes that deviate from the normal setup.

I am using an Intel 945 GME and it works flawlessly.

It's possible that the problem is with audio.

Instead of removing the ./lib in the path, why not rename or move the libSDL in the lib directory under nwn? Try that and see if you get any further.

Also, what are the contents of your nwn file (there are some SDL commands that should be set/included if not already that may help.

What would I rename the libSDL to, or where would I move it?  The contents of my nwn file are just the default contents.  This is a fresh install of Hardy and a default install of NWN.

---

### Post by roderick on 2008-03-10
Technically, you don't need the libSDL in the nwn/lib directory, as the system one should work perfectly fine. Rename it, move it or delete it. Doesn't really matter. 

I only suggested renaming or moving it just in case. 

My nwn script contains the following variables. I suggest you look and see if these are set in yours or not:

export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0
export SDL_AUDIODRIVER=alsa


If that doesn't fix it (and after you've moved the libSDL from nwn/lib), you can try debugging nwn using a program called strace. Install it if you do not have it (sudo apt-get strace). Then you can modify your nwn by changing the last entry to:

strace ./nwmain $@

Now, run ./nwn from a terminal prompt, and you should see a lot of messages being printed. After it dumps from the segfault, have a look at the last few entries for a hint of why it failed. Most likely it's unable to do the audio or some file it cannot access properly (i.e. wrong permissions).

---

